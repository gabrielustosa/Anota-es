# Arquitetura e Padrões de Projeto Java EE8
### Camada de Apresentação (Web)
A camada de apresentação, também conhecida como camada web, contém os componentes que criam um aplicativo web. Esta camada possui diversos componentes que utilizam o protocolo HTTP, constroem visualizações e interfaces para usuários e fornecem um serviço web. Esses componentes são chamados de componentes web.

![[web-java-pp-overview.png]]

Existem dois tipos de camada de apresentação.

**Camada orientada à apresentação**: Esse tipo de camada de apresentação contém os componentes para construir uma página web interativa e conteúdo dinâmico usando HTML e XHTML. Esses componentes são a tecnologia JavaServer Faces (JSF), a tecnologia Java Servlet e a tecnologia JavaServer Pages (JSP), que nos permitem construir uma página web interativa.

**Camada orientada ao servidor**: Esta camada contém os componentes para construir um ponto de extremidade de um serviço web. Esses componentes são JAX-RS e JAX-WS.

![[web-java-pp-wt.png]]
#### Padrão Intercepting Filter 
Quando um cliente envia uma requisição ao servidor, o servidor muita das vezes precisa realizar uma série de processos como: autenticação, logs, validação, adicionar cookies, para finalmente enviar a resposta ao solicitante. Entretanto, não é interessante misturar esses processos junto com a lógica principal da requisição. 

O padrão Intercepting Filter resolve esse problema separando a lógica que não faz parte do processo principal de processamento da requisição. Esse padrão cria um filtro para processar a requisição antes (pré-processamento) e depois (pós-processamento) dela ser tratada pela lógica principal da aplicação. Isso permite a criação de um bloco de lógica separado para resolver problemas que não fazem parte da funcionalidade central, separando assim as duas partes. Utilizando este padrão, podemos criar soluções plugáveis sem precisar modificar a lógica principal.

![[web-java-pp-wt-if.png]]
#### Padrão Front Controller
Frequentemente, é necessário lidar com multiplos controladores para ser capaz de lidar com as várias requisições. As vezes, criar dezenas de classes de controladores é visto como uma má prática e pode se custoso de se manter. Dessa forma, existe a necessidade de criar um ponto central de controle que irá lidar com cada requisição e enviar diretamente para o processo certo.

O padrão Controlador Frontal (Front Controller) cria um gerenciador central para tratar todas as requisições ou um grupo de requisições de uma aplicação. Esse gerenciador então encaminha as requisições para o processo específico responsável por tratá-las.

![[web-java-pp-wt-fc.png]]
#### Padrão Application Controller
Algumas aplicações web têm uma lógica complexa para definir a view correta, conteúdo ou ação a ser invocada. O controlador MVC pode ser usado para tomar essa decisão e obter a visualização, conteúdo ou ação correta. No entanto, às vezes a lógica para definir uma decisão é muito difícil, e usar o controlador MVC para fazer isso pode causar duplicação de muito código.

O padrão Application Controller é o padrão que permite a centralização de toda lógica de visualização e promove um processo único para definir o fluxo de páginas. Este padrão é usado em conjunto com o Front Controller, e é um intermediário entre o Front Controller e o Command. Usando este padrão, promoveremos o desacoplamento entre o tratamento da visualização e o tratamento da solicitação.

![[web-java-pp-wt-ap.png]]
###### Diferença entre Front Controller e Application Controller
Esses dois padrões podem ser facilmente confundidos, visto que os dois resolvem o mesmo problema de centralizar a lógica em um só lugar. A principal diferença entre o Application Controller e o Front Controller é que o Application Controller trabalha para resolver a complexidade da lógica de visualização e fluxo de páginas, enquanto o Front Controller trabalha para resolver a complexidade das solicitações e suas configurações. Quando a lógica de visualização e de fluxo é simples, toda a lógica é por vezes inserida no Front Controller, e o Application Controller não é utilizado. No entanto, quando a lógica dentro da visualização e do fluxo de páginas é complexa, é recomendado usar o Application Controller para desacoplar a lógica de visualização e de fluxo e organizar o código.
#### Padrão View Helper
Ajuda a separar a lógica do negócio dos componentes de visualização.

![[web-java-pp-wt-vh.png]]
#### Padrão Composite View
Permite a construção de uma visualização a partir de componentes modulares e atômicos que são combinados para criar um todo composto. Este padrão permite gerenciar o conteúdo e o layout de forma independente. Suponha que você quer construir uma visualização a partir de partes componentes modulares e atômicas que são combinadas para criar só composto por esse componentes, enquanto gerencia o conteúdo e o layout de forma independente.

![[web-java-pp-wt-cv.png]]
#### Padrão Dispatcher View
Permite que uma view lide com uma solicitação e gere uma resposta, enquanto gerencia quantidades limitadas de processamento relacionadas ao negócios, geralmente com a utilização de controladores. Este padrão é útil quando você tem visualizações estáticas, visualizações geradas a partir de um modelo de apresentação existente, visualizações que são independentes de qualquer resposta de serviço de negócios e quando você tem processamento de negócios limitado.

![[web-java-pp-wt-dv.png]]
### Camada de Business
Basicamente o nível do núcleo no qual é definida a lógica de negócio do projeto. As tecnologias que compõem essa camada incluem Enterprise Java Beans (EJB) e Java Persistence API (JPA). 

![[web-java-pp-bt.png]]
#### Padrão Business Delegate
Para evitar responsabilidades adicionais na camada de apresentação, é interessante utilizar alguma interface que delegue responsabilidades das requisições para os serviços necessários. Essa é a função do Business Delegate, no qual impede que a camada de apresentação tenha acesso aos detalhes de implementação da camada business, simplificando e impondo a transparência na comunicação entre essas camadas. 

Dessa forma, ele atua como uma porta de entrada para o cliente. Ele é responsável por receber a solicitação, identificar ou localizar o serviço empresarial real e chamar o serviço enviando a solicitação. Após isso, o delegado recebe a resposta do serviço e então envia a resposta de volta para o cliente.

![[web-java-pp-bt-bd.png]]
#### Session Facade
Similar ao padrão de projeto Facade, no qual abstrai a complexidade do negócio em uma interface simples com métodos bem definidos. 

![[web-java-pp-bt-sf.png]]
#### Business Object Pattern
Como o nome sugere, esse padrão está associado à algo do mundo real que está ligado a lógica do negócio. Quando para esse objeto não existe muitas lógicas de negócio a implementação desse padrão é desnecessária. Nesse sentido, a POJO (JPA) entity pode ser reconhecida como um BO (Business Object). Uma entidade ou um POJO representativo de uma entidade (como um POJO JPA) está mais próximo da tecnologia e da estrutura do que de um objeto de modelo de negócio.

![[web-java-pp-bt-bo.png]]

Ás vezes, a aplicação é tão simples que clientes da camada de negócios, como uma Session Facade (ou até mesmo clientes da camada de apresentação), podem acessar diretamente o modelo de dados através do DAO. Não há necessidade de um objeto de modelo lidar com uma complexidade maior para os negócios da aplicação.

Estrutura gerenciamento de um BO complexo, separando a lógica de negócio da de persistência.

![[web-java-pp-bt-bo-ex.png]]
### Camada de Integração
A camada de integração é responsável por desacoplar a lógica de negócios da lógica de integração em toda a aplicação. Esta camada possui a lógica de comunicação com um recurso ou sistema externo, mantendo-a separada da lógica de negócios. Essa camada tornará possível ler e escrever dados de fontes externas, viabilizando a comunicação entre aplicativos e componentes do ecossistema de negócios. Além disso, essa camada ocultará toda a complexidade de comunicação da camada de negócios. A camada de negócios, então, receberá os dados sem conhecer a complexidade da comunicação entre os componentes e como eles estão estruturados.
#### Padrão Data Access Object (DAO)
O padrão Data Access Object é um padrão utilizado para abstrair e ocultar todo o acesso às fontes de dados da camada de negócios. Se desejarmos substituir a fonte de dados por outra, precisaremos apenas modificar o código do padrão Data Access Object, e essa modificação não será visível na camada de negócios.

![[web-java-pp-bi-dao.png]]
#### Padrão Domain-Store
Alguns problemas têm uma relação complexa entre os dados, e a persistência dos dados precisa ser feita por meio de um processo inteligente. Para promover essa característica, o padrão DAO não atende. Isso ocorre porque o DAO não deve manter estados, não deve conter processos inteligentes e só precisa conter um processo para salvar ou atualizar. Para resolver esse problema, foi criado o padrão Domain-Store — um padrão que pode adicionar funcionalidades ao DAO.

O padrão de Domain-Store é um padrão que torna a persistência do modelo de objeto transparente, separando a lógica de persistência do modelo de objeto, possibilitando que a aplicação selecione a lógica de persistência de acordo com o estado do objeto. Dentro desse padrão, existe um DAO, projetado para comunicar e manipular dados com a fonte de dados, mas este DAO é ocultado da aplicação. Esse padrão raramente é implementado pelos desenvolvedores, pois o JPA já funciona como um padrão de domínio-armazenamento.

![[web-java-pp-bi-ds.png]]
#### Padrão Service Activator
Suponha que um cliente precise solicitar um business service, o qual é um processo que leva muito tempo. Nesse caso, o cliente não deve esperar de forma síncrona até o final do processo. Em vez disso, deve haver uma maneira de fazer uma chamada de serviço assíncrona que não bloqueie o cliente ou usuário. Esse serviço pode então ser ativado em algum momento futuro. Pode haver várias razões para o atraso de um processo. Por exemplo, pode haver uma consulta ao banco de dados que consome muito tempo, ou um acesso a um sistema legado que está além do controle da aplicação atual. O padrão de realizar de forma assíncrona a tarefa necessária é conhecido como o service activator.

A especificação JEE nos fornece soluções muito boas que são usadas para implementar esse padrão. Essas soluções são:
- Java Message Service (JMS)
- EJB asynchronous methods
- Asynchronous events: producers e observers
# Aplicações Web Java EE
Em plataformas Java EE, os componentes web fornecem as capacidades de extensão dinâmica para um servidor web. Esses componentes podem ser servlets Java, páginas web implementadas com a tecnologia JavaServer Faces, APIs de serviços ou páginas JSP.

![[web-diagram.png]]

Na figura, o cliente envia uma requisição para a aplicação web que utiliza um servidor que implementa um Servlet convertendo a solicitação em um objeto `HttpServletRequest`. Este objeto é entregue a um componente web, que pode interagir com componentes JavaBeans ou um banco de dados para gerar conteúdo dinâmico. O componente web pode então gerar um `HTTPServletResponse` ou passar a solicitação para outro componente web, para então mandar uma resposta ao cliente.
#### Java EE Server e Containers
- **Servidor Java EE**: A parte em tempo de execução de um produto Java EE. Um servidor Java EE fornece contêineres EJB e web.
- **Contêiner EJB**: Gerencia a execução de beans empresariais para aplicativos Java EE. Os beans empresariais e seu contêiner funcionam no servidor Java EE.
- **Contêiner web**: Gerencia a execução de páginas web, servlets e alguns componentes EJB para aplicativos Java EE. Os componentes web e seu contêiner funcionam no servidor Java EE.
- **Contêiner de cliente de aplicativo**: Gerencia a execução de componentes de cliente de aplicativo. Clientes de aplicativos e seu contêiner funcionam no cliente.
- **Contêiner de applet**: Gerencia a execução de applets. Consiste em um navegador da web e um plug-in Java em execução no cliente juntos.

![[web-java-ee-container.png]]

```ad-summary
##### Java Applets
Pequenos programas escritos na linguagem de programação Java que podem ser incorporados em páginas da web. Eles são executados no navegador do usuário por meio de uma máquina virtual Java (JVM). Quando uma página da web contendo um applet Java é carregada, o código do applet é transferido para a máquina do usuário e executado pela JVM no navegador. Isso permite que os applets forneçam funcionalidades interativas, como jogos ou calculadoras, diretamente na página da web.
```
### Java Message Service (JMS)
A Java Message Service (JMS) é uma interface de programação de aplicativos (API) que fornece uma interface MOM (Message-Oriented Middleware) para clientes que desejam um processo assíncrono.

Um bean MDB (Message-Driven Bean) é um bean de sessão sem estado que é usado para ouvir solicitações ou objetos que chegam em uma fila JMS (Java Message Service). É importante observar que um MDB pode implementar qualquer tipo de mensagem, mas é mais comumente usado para lidar com mensagens JMS.

Um MDB escuta mensagens que foram enviadas para uma fila ou para um tópico. Mensagens podem ser enviadas por qualquer componente JEE ou por outra aplicação fora do contexto JEE.

```ad-summary
##### Message-Driven Middleware (MOM)
Arquitetura que utiliza trocas de mensagens, referindo-se ao envio e recebimento de mensagens, entre os módulos de uma aplicação ou entre sistemas distribuídos. O MOM oferece alguns serviços importantes, como persistência de mensagens ou garantias de entrega de mensagens. Um message broker é baseado em um MOM, por exemplo.
```

![[web-java-ee-jms.png]]
# JavaBeans   
Escrito no idioma de programação Java, um `EjB` é um componente do lado do servidor que encapsula a lógica de negócios de uma aplicação. A lógica de negócios é o código que cumpre o propósito da aplicação. Você pode pensar em um enterprise bean como um bloco de construção que pode ser usado sozinho ou com outros enterprise beans para executar a lógica de negócios no servidor Java EE. É dividido em dois principais, Session Beans (usados para a lógica de negócios, tanto em estado quanto sem estado, pode implementar um Web Service), Message Driven Beans (manipulação de mensagens assíncronas, como JMS). 

```java
import java.math.BigDecimal;
import javax.ejb.*;

@Stateless
public class ConverterBean {
	private BigDecimal yenRate = new BigDecimal("83.0602");
	private BigDecimal euroRate = new BigDecimal("0.0093016");
	
	public BigDecimal dollarToYen(BigDecimal dollars) {
		BigDecimal result = dollars.multiply(yenRate);
		return result.setScale(2, BigDecimal.ROUND_UP);
	}
	public BigDecimal yenToEuro(BigDecimal yen) {
		BigDecimal result = yen.multiply(euroRate);
		return result.setScale(2, BigDecimal.ROUND_UP);
	}
}
```
## Tipos
#### Stateful Session Bean
Esse tipo de Session Bean mantém o estado de seus atributos, não é compartilhado e pode ter apenas um cliente. Ou seja, enquanto a sessão do cliente estiver ativa, os valores das variáveis de instância desse tipo de objeto serão preservados. Porque o cliente interage “conversa” com seu bean, esse estado é frequentemente chamado `conversational state`.
##### Ciclo de Vida
![[web-jeb-stful-lc.png]]
#### Stateless Session Bean
Não mantém o estado de seus atributos, ou seja, não há garantia que os valores das variáveis de instância desse tipo de objeto sejam preservados entre as chamadas de seus métodos. Eles podem suportar vários clientes, visto que este tipo de bean pode oferecer melhor escalabilidade para aplicações que requerem um grande número de clientes. 
- Pode implementar um serviço web, mas um **Stateful Session Bean** não pode.
##### Ciclo de Vida
![[web-jeb-stless-lc.png]]
#### Singleleton Session Bean
É instanciado apenas uma vez por aplicação e mantido durante todo ciclo de vida dela. Os **singleton session beans** oferecem funcionalidades semelhantes aos **stateless session beans**, mas diferem deles no sentido de que há apenas **um singleton session bean por aplicação**, em oposição a um pool de **stateless session beans**, dos quais qualquer um pode responder a uma solicitação do cliente. Assim como os **stateless session beans**, os **singleton session beans** também podem implementar **pontos de extremidade de serviço da web**.
##### Ciclo de Vida
![[web-jeb-stless-lc.png]]
## Serviços
#### Transação
O contêiner EJB gerencia as transações, o que permite aos desenvolvedores controlarem o comportamento transacional dos métodos EJB. Isso inclui o início, o commit e o rollback de transações para garantir a consistência dos dados.
#### Persistência
A persistência é o serviço que permite que o estado dos beans seja mantido entre chamadas de método, seja em um banco de dados ou outro tipo de armazenamento de dados. O EJB oferece o Entity Bean e o uso de JPA (Java Persistence API) para abstrair e facilitar a persistência de dados.
#### Segurança
O contêiner EJB também oferece serviços robustos de segurança, permitindo a configuração de autorização e autenticação, além do controle de acesso aos componentes EJB de acordo com as regras definidas.
# Servlet 
Servlets são classes Java do lado do servidor que recebem requisições HTTP, processam-nas (podendo interagir com o Model) e geram respostas, que podem ser um HTML, redirecionamento para outra página, dentre outros. Dessa forma, servlets são ideais para o papel de Controller no MVC pois gerenciam e orquestram o fluxo dentro da aplicação. Estes são executados dentro de um container de Servlets, como o Apache Tomcat ou o Jetty, que gerencia seu ciclo de vida.

A classe `HttpServlet` gera aplicações Web baseadas no protocolo HTTP. Nessa classe, além de possuir os verbos padrões do protocolo HTTP ainda possui os métodos de ciclo `init()`, `service()`, `destroy()`.

``` java
@WebServlet(urlPatterns="/visualizar") // Substitui os mapeamentos de Servlet presentes no web.xml
public class VisualizaAutomovelServlet extends HttpServlet {
	protected void doGet(HttpServletRequest req, HttpServletResponse res) throws IOException, ServletException {
	    AutomovelDAO dao = new AutomovelDAO();
		Automovel auto = dao.busca(request.getParameter("id"));
		
		// coloca as informações no request para seguirem adiante
		req.setAttribute("modelo", auto.getModelo());
		req.setAttribute("anoModelo", auto.getAnoModelo());
		
		RequestDispatcher rd = req.getRequestDispatcher("/visualiza.jsp");
		// encaminha para o JSP, levando o request com os dados
		rd.forward(req, res);
	}
}
```

Deve-se observar que Servlets não foram criadas somente para o protocolo HTTP.

```java
public class HelloWorldServlet extends GenericServlet {

    @Override
    public void service(ServletRequest req, ServletResponse res) throws ServletException, IOException {
        // código
    }
}
```

As rotas também podem ser definidas no arquivo web.xml da seguinte maneira.

```xml
<servlet>
  <servlet-name >watermelon< /servlet-name>
  <servlet-class >myservlets.watermelon</servlet-class>
</servlet>
<servlet-mapping>
  <servlet-name>watermelon< /servlet-name>
  <url-pattern>/fruit/summer/*</url-pattern>
</servlet-mapping>
```
#### Ciclo do Servlet
Quando um Servlet é inicializado, o servidor web cria uma única instância deste Servlet para atender todas as requisições dos clientes. Essa instância gera diversas threads, cada uma pra atender uma requisição diferente. Isso significa que todas as variáveis de instância dentro do Servlet são compartilhadas e podem afetar simultaneamente o estado do objeto durante o processamento de múltiplas requisições. Essa característica de compartilhamento de estado pode levar a condições de corrida se não for gerenciada corretamente. Portanto, é típico sincronizar o acesso a recursos compartilhados ou utilizar mecanismos como o `HttpSession` para armazenar dados relacionados a uma sessão de usuário específica. 
 ##### Init()
 É o que é chamado quando o Servlet é criado pela primeira vez. Este método é utilizado para inicializar recursos que o Servlet possa necessitar durante sua vida útil. Ele é invocado uma única vez e é aqui onde o Servlet é colocado em um estado de serviço.
 ##### Service()
 É chamado cada vez que o Servlet é requisitado para processar uma requisição. Portanto, ele será chamado várias vezes durante o ciclo de vida do Servlet, lidando com múltiplas requisições de diferentes clientes.
 ##### Destroy()
 É chamado uma única vez quando o Servlet está sendo retirado de serviço, normalmente quando o container web está sendo desligado ou o Servlet está sendo descarregado por algum outro motivo.
# JSP
Permite a criação de páginas Web que tenha componentes estáticos e dinâmicos. A tecnologia JSP disponibiliza todos os recursos dinâmicos da tecnologia Java Servlet, mas fornece uma abordagem mais natural para a criação de conteúdo estático. Na verdade, os JSPs são compilados em Servlets pelo servidor. Dessa forma, JSP são compiladas e interpretadas em um Container de Servlets, que é uma parte da plataforma Java EE. Objetos referenciados neste escopo possuem o menor ciclo de vida, pois estão vinculados a uma única solicitação de página (uma página JSP, por exemplo). Quando a resposta é enviada ao cliente, os objetos neste escopo não estão mais disponíveis. Portanto, eles são adequados para dados temporários usados durante a geração de uma resposta específica.

```jsp
<html>
	<body>
		Ano do Modelo: <%= req.getAttribute("anoModelo") %> // avalia e imprime 
		<% List deps = (List) request.getAttribute("automoveis"); %> // código java (Scriptlets JSP)
		
		// acesso ao query param
		${param.nome} 
		<%= request.getParameter("nome")%> 
		<% out.print(request.getParameter("nome")); %>
	</body>
</html>
```

```ad-summary
#### Linguagem EL (Expression Language)
Basicamente a EL é utilizada em páginas JSF ou JSP, para ler dinâmicamente informações armazenadas em componenetes `JavaBeans`, escrever dados dinâmicamente, invocar métodos, perfomar operações aritméticas ou executar código `Java`.
##### Formas de Evaluação
Existem dois tipos de avaliação de expressões: a avaliação **imediata** e a avaliação **deferida**. A avaliação imediata ocorre quando uma expressão é avaliada e o resultado é retornado imediatamente na primeira renderização da página. Por outro lado, a avaliação deferida permite que a expressão seja avaliada em um momento posterior do ciclo de vida da página, de acordo com a necessidade da tecnologia que está utilizando a EL.
- A **imediata** usa ${expression}
- A **deferida** usa #{expression}
```

Essas são algumas diretivas, as quais são utilizadas para informações especiais dentro de páginas, sendo dividido em três tipos:

- `@include` - Utilizado para inserir os códigos de arquivos à página corrente;
- `@page` - Responsável por trazer informações sobre a página JSP;
- `@taglib` - Responsável por habilitar uma biblioteca de tags personalizada;

```jsp
<%@ taglib prefix = "fmt" uri = "http://java.sun.com/jsp/jstl/fmt" %>
<%@page contentType="text/html" import="java.util.Date, java.text."pageEncoding="ISO-8859-1"%>
<%@page import="java.util.ArrayList"%>_
<html>
	<%@ include file="header.jsp" %>
    <body>
        <h1>
            <% =new Date() %>
        </h1>
    </body>
</html>
```
##### Métodos
- `invalidate():` serve para terminar uma sessão de usuário que não é mais necessária e interrompe a conexão da sessão com todos os objetos armazenados.
- `isNew():` Este método é usado para verificar se a sessão é nova ou não. O valor booleano (verdadeiro ou falso) é retornado por ele.
- `getId():` ao criar uma sessão, o contêiner de servlet atribui um identificador de string distinto à sessão. Este identificador de string distinto é retornado pelo método `getId()`.
- `getAttributeNames():` Todos os objetos armazenados na sessão são retornados pelo método `getAttributeNames()`.
- `getCreationTime():` A hora de criação da sessão (a hora em que a sessão se tornou ativa ou a sessão começou).
- `getAttribute (String name):` Usando o método `getAttribute()`, o objeto que é armazenado pelo método `setAttribute()` é recuperado da sessão.
- `setAttribute (String, object):` O método `setAttribute()` é usado para armazenar um objeto na sessão atribuindo uma string única ao objeto. Posteriormente, usando a mesma string, este objeto pode ser acessado da sessão até que ela esteja ativa. No JSP, ao lidar com a sessão, `setAttribute()` e `getAttribute()` são os dois métodos mais usados regularmente.
- `removeAttribute (String name):` Usando o método `removeAttribute(String name)`, os objetos que estão armazenados na sessão podem ser removidos da sessão.
##### Tags de Ação
A especificação JSP fornece uma tag padrão chamada Action tag, usada dentro do código JSP e destinada a remover ou eliminar o código Scriptlet do seu código JSP, já que os Scriptlets JSP são obsoletos e não são considerados atualmente. Existem muitas tags ou elementos de ação JSP, e cada um deles possui seus próprios usos e características. Cada tag de ação JSP é implementada para realizar tarefas específicas.

A tag de ação também é implementada para otimizar o fluxo entre páginas e para empregar um Java Bean. Como coincide com o padrão XML, a sintaxe para o elemento de ação é:

```jsp
<jsp:action_name attribute = "attribute_value" />
```

1. `jsp:forward`: é usado para encaminhar a solicitação e a resposta para outros recursos. `<jsp:forward page="outra_pagina.jsp"/>`
2. `jsp:include`: é usado para incluir outro recurso. `<jsp:include page="cabecalho.jsp"/>`
3. `jsp:useBean`: é usado para criar ou localizar objetos bean. `<jsp:useBean id= "instanceName" scope= "page | request | session | application"  class= "packageName.className" type= "packageName.className"  beanName="packageName.className" />`
4.  `jsp:setProperty`: é usado para definir o valor do objeto bean. `<jsp:setProperty name="meuBean" property="nome" value="João"/>
5. `jsp:getProperty`: é usado para imprimir o valor da propriedade do bean. `<jsp:getProperty name="meuBean" property="nome"/>`
##### Objetos Implícitos
Durante a fase de tradução (ou seja, durante a conversão de JSP para Servlet), o mecanismo JSP produz esses objetos. Eles são criados dentro do método de serviço para que os desenvolvedores JSP possam usá-los diretamente no Scriptlet sem declaração e inicialização.

- **out**: `javax.servlet.jsp.JspWriter`: Usado para escrever saída para a resposta HTTP.
- **request**: `javax.servlet.http.HttpServletRequest`: Representa a requisição HTTP do cliente.
- **response**: `javax.servlet.http.HttpServletResponse`: Representa a resposta HTTP que será enviada de volta ao cliente.
- **session**: `javax.servlet.http.HttpSession`: Representa a sessão do usuário, permitindo armazenar informações específicas do usuário entre múltiplas requisições.
- **application**: `javax.servlet.ServletContext`: Representa o contexto da aplicação web, permitindo o compartilhamento de informações entre todos os componentes da aplicação.
- **exception**: `javax.servlet.jsp.JspException`: Usado para representar exceções que ocorrem durante a execução da página JSP.
- **page**: `java.lang.Object`: Referência para o objeto da página JSP.
- **pageContext**: `javax.servlet.jsp.PageContext`: Fornece acesso aos diversos objetos relacionados ao ciclo de vida da página JSP.
- **config**: `javax.servlet.ServletConfig`: Fornece acesso à configuração do servlet, permitindo a leitura de parâmetros de inicialização.
##### JSLT Tags
As tags JSTL podem ser classificadas, de acordo com suas funções, nos seguintes grupos de bibliotecas de tags JSTL que podem ser usados ao criar uma página JSP:
- **Core Tags**
- **Formatting tags**
- **SQL tags**
- **XML tags**
- **JSTL Functions**

```jsp
<%@ taglib uri = "http://java.sun.com/jsp/jstl/core" prefix = "c" %>
<%@ taglib prefix = "fmt" uri = "http://java.sun.com/jsp/jstl/fmt" %>
<%@ taglib prefix = "x" uri = "http://java.sun.com/jsp/jstl/xml" %>

<html>
   <head>
      <title> <c:out> Tag Example</title>
   </head>

   <body>
	    <c:out value = "${'<tag> , &'}"/>
		<p>Parsed Number (1) : <c:out value = "${i}" /></p>
		<fmt:parseNumber var = "i" integerOnly = "true" type = "number" value = "${balance}" />
		<x:out select = "$output/books/book[2]/price" /> <!-- Xpath expressions -->
   </body>
</html>
```
# JPA
JPA é uma camada que descreve uma interface comum para frameworks ORM. Todos os objetos mapeados com o JPA são de responsabilidade do ``EntityManager``, ou seja, se algum atributo for alterado ele acabará salvo no banco de dados através dele.

![[web-jpa-ciclo.png]]

```ad-tip
##### Detached
Objetos detached são objetos que já foram gerenciados, ou seja, que existem no banco de dados, mas a EntityManager que os trouxe do banco de dados já foi fechada, ou explicitamente desanexou o objeto do seu contexto via o método detach.
```
# JSF 
JSF é um framework para a construção backend de um servidor que utiliza a arquitetura **MVC**. As telas do JSF podem ser escritas utilizando XHTML. O JSF conhece todo o estado da nossa tela, e guarda isso através das requisições, por isso ele é considerado um framework stateful. Para começar a usá-lo, é preciso configurar a servlet do JSF no ``web.xml`` ou ``faces-config.xml`` da aplicação. Esse Servlet é responsável por receber as requisições e delegá-las ao JSF. 

![[web-jfs.png]]

- Faces Servlet processa as requisições HTTP, cria ou restaura a árvore de componentes da visão correspondente, executa o ciclo de vida do JSF para essa árvore e, por fim, renderiza a resposta (normalmente uma página HTML) de volta ao usuário. Dessa forma, ele faz parte da camada de controle.

- Tag `<f>`: As ações personalizadas centrais do JavaServer Faces que são independentes de qualquer RenderKit específico.
- Tag `<h>`: Esta biblioteca de tags contém tags de componentes JFS para todas as combinações de UIComponent + HTML RenderKit Renderer definidas na Especificação do JFS.

```xhtml
<html xmlns="http://www.w3.org/1999/xhtml" xmlns:h="http://java.sun.com/jsf/html">
	<h:head>
		<title>Cadastro de automóvel</title>
	</h:head>
	<h:body>
		<h:form>
			<h:panelGrid columns="2">
				Marca: <h:inputText value="#{automovelBean.automovel.marca}"/>
				Modelo: <h:inputText value="#{automovelBean.automovel.modelo}"/>
				Ano de Fabricação: <h:inputText value="#{automovelBean.automovel.anoFabricacao}"/>
				Ano do Modelo: <h:inputText value="#{automovelBean.automovel.anoModelo}"/>
				Observações: <h:inputTextarea value="#{automovelBean.automovel.observacoes}"/>
				<h:commandButton value="Salvar" action="#{automovelBean.salva(automovelBean.automovel)}" />
			</h:panelGrid>
		</h:form>
	</h:body>
</html>
```

```xhtml
<html xmlns="http://www.w3.org/1999/xhtml" xmlns:h="http://java.sun.com/jsf/html" xmlns:f="http://java.sun.com/jsf/core">
	<h:body>
		<h:dataTable value="#{automovelBean.automoveis}" var="automovel" border="1">
			<h:column>
				<f:facet name="header">
					Marca
				</f:facet>
				#{automovel.marca}
				<!-- outras colunas aqui -->
			</h:column>
		</h:dataTable>
	</h:body>
</html>
```

JSF chama classes de código Java através do Management Bean, dessa forma:

```java
@ManagedBean
public class AutomovelBean {
	private Automovel automovel = new Automovel();
	private List<Automovel> automoveis;

	public void salva(Automovel automovel) 
		EntityManager em = MyClass.getEntityManager();
		em.getTransaction().begin();
		em.persist(automovel);
		em.getTransaction().commit();
		em.close();
	}
	
	public List<Automovel> getAutomoveis() {
		if(this.automoveis == null) {
			EntityManager em = MyClass.getEntityManager();
			Query q = em.createQuery("select a from Automoveis a", Automovel.class);
			this.automoveis = q.getResultList();
			em.close();
		}
		return automoveis;
	}

	// getter and setters
}
```
#### Ciclo de Vida
O ciclo de vida pode ser dividido em duas fases principais: **Executar** e **Renderizar**. A fase de Execução é ainda dividida em subfases para suportar a sofisticada árvore de componentes. Essa estrutura exige que os dados do componente sejam convertidos e validados, que eventos do componente sejam tratados e que os dados do componente sejam propagados para beans de maneira ordenada.

 ##### Restore View - Fase 1 
 Quando uma requisição chega ao JSF, a primeira tarefa realizada por ele é construir ou restaurar a árvore de componentes correspondente ao arquivo XHTML lido. Se a requisição for um **postback**, o JSF tentará restaurar a view existente. Depois que a árvore é restaurada, seja buscando na sessão ou via deserialização, a requisição do usuário segue para a fase 2.
 ##### Apply Request Values - Fase 2
 Os valores de entrada são lidos e atribuídos aos componentes correspondentes, mas não são mapeados para as propriedades do Managed Bean nesta fase.
 ##### Process Validation - Fase 3
 Os dados que foram submetidos com o formulário são validados. Essa fase é dividida em partes converte e valida. Normalmente provocará uma chamada recursiva do método `processValidators()` de cada componente da árvore.
 ##### Update Model Values  - Fase 4
 Os valores inseridos pelo usuário são mapeados para os respectivos atributos da classe Bean, envolvendo os procedimentos de conversão de valores, quando necessário. Se tivéssemos o objeto Funcionário ligado à EL `#{cadastroBean.cadastro.funcionario}`, o JSF recuperaria o objeto cadastro que é propriedade do `#{cadastroBean}` e chamaria o método `setFuncionario` do objeto cadastro.
 ##### Invoke Application - Fase 5
 Nessa fase acontece a lógica da aplicação, como chamadas para métodos nos Managed Beans. A aplicação tem os insumos necessários para aplicar a lógica de negócio. Outro fator importante dessa fase, é o direcionamento do usuário de acordo com as submissões realizadas pelo mesmo.
 ##### Render Response - Fase 6
 Nessa fase acontece a geração do HTML a partir da árvore de componentes do JSF. Se ocorrer um erro de conversão ou validação, as fases 4 e 5 são puladas e vamos direto para a fase 6. Também podemos chegar aqui logo depois da fase 1, quando o usuário pede a página pela primeira vez. Nesse caso o JSF monta a árvore e já manda a fase 6, já que, na primeira requisição à aplicação, não haverá formulário sendo submetido e nem ação para ser invocada. 

![[web-jsf-ciclo.png]]
#### Phase Listeners
Antes e depois de cada fase é possível realizar ações através da implementação da classe ``PhaseListener`` 

``` java
public class LifeCycleListener implements PhaseListener {

    public PhaseId getPhaseId() {
        return PhaseId.ANY_PHASE; // ou posso específicar um fase
    }

    public void beforePhase(PhaseEvent event) {
        System.out.println("INICIANDO FASE: " + event.getPhaseId());
    }

    public void afterPhase(PhaseEvent event) {
        System.out.println("FINALIZANDO FASE: " + event.getPhaseId());
    }

}```
#### Event Handling
Quando um usuário clica em um botão ou link do JSF ou altera qualquer valor no campo de texto, o componente de interface do usuário do JSF dispara um evento, que será tratado pelo código da aplicação. Para lidar com esse evento, um manipulador de eventos deve ser registrado no código da aplicação ou no bean gerenciado.

A seguir estão alguns manipuladores de eventos importantes no JSF.
##### ValueChangeListener
Os eventos `ValueChangeListener` são disparados quando o usuário faz alterações nos componentes de entrada.

```java
public class LocaleChangeListener implements ValueChangeListener {
   
   @Override
   public void processValueChange(ValueChangeEvent event)
      throws AbortProcessingException {
     
      //access country bean directly
      UserData userData = (UserData) FacesContext.getCurrentInstance().
      getExternalContext().getSessionMap().get("userData"); 
      userData.setSelectedCountry(event.getNewValue().toString());
   }
}
```

```xhtml
<h:selectOneMenu value = "#{userData.selectedCountry}" onchange = "submit()">
   <f:valueChangeListener type = "com.tutorialspoint.test.LocaleChangeListener"
      />
   <f:selectItems value = "#{userData.countries}" />
</h:selectOneMenu>
```
##### ActionListener
Os eventos `ActionListener` são disparados quando o usuário clica em um botão ou componente de link.

```java
public class UserActionListener implements ActionListener {
   
   @Override
   public void processAction(ActionEvent arg0) throws AbortProcessingException {
      
      //access userData bean directly
      UserData userData = (UserData) FacesContext.getCurrentInstance().
      getExternalContext().getSessionMap().get("userData"); 
      userData.setData("Hello World");
   }
}
```

```xhtml
<h:commandButton id = "submitButton1" 
   value = "Submit" action = "#{userData.showResult}" >
   <f:actionListener type = "com.tutorialspoint.test.UserActionListener" />
</h:commandButton>
```
##### Application Events
Eventos disparados durante o ciclo de vida do JSF
- **`PostConstructApplicationEvent`**: Disparado quando a aplicação é iniciada. Pode ser usado para realizar tarefas de inicialização após a aplicação ter iniciado.
- **`PreDestroyApplicationEvent`**: Disparado quando a aplicação está prestes a ser encerrada. Pode ser usado para realizar tarefas de limpeza antes que a aplicação seja encerrada.
- **`PreRenderViewEvent`**:  Disparado antes de uma página JSF ser exibida. Pode ser usado para autenticar o usuário e fornecer acesso restrito à Visualização JSF.
#### Request Scope
O escopo disponíveis são ``request``, ``session``, ``application`` e ``view``. 

São aplicados no Managed Beans dessa forma:
```java
@ManagedBean
// @RequestScoped, @SessionScoped, @ApplicationScoped, @ViewScoped, @ConversationScoped, @Dependent
public class MeuBean {
}
```
##### Request
Apenas sobrevivem por uma passada de vida no ciclo do JSF, ou seja, da fase 1 até a fase 6. Por ser um escopo que tem o tempo de vida curto é apropriado quando não precisamos memorizar dados entre as requisições dos usuários. É o padrão dos Managed Beans, dessa forma, ao não anotar sua classe, esse escopo será utilizado.
- O bean é criado e destruído a cada requisição HTTP.
##### Session
Nesse escopo, tudo que armazenarmos ficará disponível enquanto a sessão do usuário estiver ativa. Ela é útil para armazenar informação sobre a última operação realizada por uma sessão, para proporcionar uma forma fácil de voltar a ela.
##### Application
Tudo que é armazenado no escopo de aplicação permanece enquanto a aplicação estiver executando, e é compartilhada entre todos os usuários. 
##### View
Esse escopo consiste em manter os dados contidos nele por quantas requisições forem feitas, mas desde que sejam todas para a mesma view. No momento em que trocamos de página o escopo é zerado. Isso é muito bom, porque evita que acumulemos objetos que ficam vivos por muito tempo, como no escopo de sessão, mas ao mesmo tempo permite ações feitas em sequência, como combos em cascata, que nesse escopo funcionam perfeitamente.
- O bean é mantido durante a visualização de uma mesma página JSF.
##### Conversation
Escopo que oferece um meio-termo entre o `@RequestScoped` e o `@SessionScoped`. O bean existe durante uma 'conversa' que pode abranger múltiplas requisições de um mesmo usuário.
- O bean pode manter seu estado durante várias interações, que podem abranger múltiplas requisições e páginas.
##### Dependent
Escopo padrão quando nenhum outro é especificado. O ciclo de vida do bean dependente é vinculado ao bean que o está injetando. Se o bean injetor for destruído, o bean dependente também será.
# Facelets
Facelets é uma parte da especificação JavaServer Faces e também a tecnologia de apresentação preferida para construir aplicações baseadas em tecnologia JavaServer Faces.

| Tag Library                           | URI                               | Prefix | Example          | Contents                                                                                 |
| ------------------------------------- | --------------------------------- | ------ | ---------------- | ---------------------------------------------------------------------------------------- |
| JavaServer Faces Facelets Tag Library | http://xmlns.jcp.org/jsf/facelets | ui     | ui:component     | Tags para templates UI                                                                   |
|                                       |                                   |        | ui:insert        |                                                                                          |
| JavaServer Faces HTML Tag Library     | http://xmlns.jcp.org/jsf/html     | h      | h:head           | Tags para elementos HTML                                                                 |
|                                       |                                   |        | h:body           |                                                                                          |
|                                       |                                   |        | h:outputText     |                                                                                          |
|                                       |                                   |        | h:inputText      |                                                                                          |
| JavaServer Faces Core Tag Library     | http://xmlns.jcp.org/jsf/core     | f      | f:actionListener | Tags para ações personalizadas independentes de qualquer kit de renderização específico. |
|                                       |                                   |        | f:attribute      |                                                                                          |

Praticamente todos os componentes podem possuir esses dois atributos:
```html
<h:inputText style="padding: 10px;" styleClass="valor_numerico" />
```
##### h:form
Gera um formulário HTML com o id formulario e o inputText com id formulario:campo_id, para desativar isso ``prependId="false"`` .
```xhtml
<h:form id="formulario">
	Idade: <h:inputText id="campo_idade"/>
</h:form>
```
##### h:dataTable
Utilizado para mostrar dados tabulares. As duas principais propriedades são ``value``  que é a lista que queremos iterar e ``var`` que  define um nome de variável que usaremos para referenciar cada objeto da lista.
```xhtml
<h:dataTable value="#{automovelBean.automoveis}" var="auto" rowClasses="table-linha-par,table-linha-impar" border="1">
	<h:column>
		<f:facet name="header">Marca</f:facet> #{auto.modelo.marca}
	</h:column>
	<h:column>
		<f:facet name="header">Modelo</f:facet> #{auto.modelo}
	</h:column>
	<h:column>
		<f:facet name="header">Ano Fabricação</f:facet> #{auto.anoFabricacao}
	</h:column>
	<h:column>
		<f:facet name="header">Ano Modelo</f:facet> #{auto.anoModelo}
	</h:column>
</h:dataTable>
```
##### h:input
Gera um input HTML. A principal propriedade é value, é a ela que é ligada a ``Expression Language`` que depois das conversões e validações, permitirá ao JSF colocar o valor que o usuário digitou no campo diretamente na propriedade especificada.
```xhtml
<h:inputText value="#{managedBean.objeto.descricao}"/>
	Descrição: <h:inputTextarea value="#{managedBean.objeto.descricao}"/>
	Senha: <h:inputSecret value="#{managedBean.usuario.senha}"/>
<h:inputHidden value="#{managedBean.objeto.id}"/>
```
##### h:outputText
Usado para escrever alguma saída na nossa aplicação.
```xhtml 
<h:outputText value="#{automovel.preco}">
	<f:convertNumber type="currency" />
</h:outputText>
<h:outputFormat value="Eu moro em {0}, {1}" >
	<f:param value="Campo Grande" />
	<f:param value="MS" />
</h:outputFormat>
```
##### h:outputLabel
Label semântica do próprio HTML.
```xhtml
<h:outputLabel value="Ano de Fabricação:" for="anoFabricacao"/>
<h:inputText value="#{automovel.anoFabricacao}" id="anoFabricacao"/>
```
##### h:commandButton
Executa ações de código ou escuta eventos.
```xhtml
<h:dataTable value="#{automovelBean.automoveis}" var="automovel">
	<h:commandLink value="Editar" action="editar">
		<f:setPropertyActionListener value="#{automovel}" target="#{automovelBean.automovel}"/> 
	</h:commandLink> 
</h:dataTable> 
<h:commandButton value="Salvar" action="#{automovelBean.salvar(automovel)}"/>
```
 
 ## Diferença entre action e listener
 Action é utilizado para executar uma lógica de código Java.
```xhtml
<h:commandButton id="botaoSalvar" value="Salvar"
actionListener="#{automovelBean.listener}"
action="#{automovelBean.salvar(automovel)}"/>
```
 Listener serve para observarmos eventos de tela.
```java
public class LoggerActionListener implements ActionListener{
	@Override
	public void processAction(ActionEvent event) throws AbortProcessingException {
		UIComponent source = event.getComponent();
		System.out.println("Ação executada no componente " + source.getId());
	}
}
```
##### f:facet
É utilizada para definir uma área dentro de um componente JSF para a qual podem ser adicionados componentes filhos.
```xhtml
<h:column>
	<f:facet name="header">
	Marca
	</f:facet>
	#{automovel.marca}
</h:column>
```
##### f:ajax
Atualização parcial de view utilizando AJAX. 

``` jsp
<h:form> 
	<h:commandButton value="Atualizar" action="#{bean.atualizar}">        
		<f:ajax render="conteudo" />   
	</h:commandButton>      
	<h:panelGroup id="conteudo">        
		<p>Conteúdo inicial</p>   
	</h:panelGroup> 
</h:form>
```
# HTTP Status Code
#### Respostas 100-199
São respostas informativas.
- 100 - Continue a requisição
- 101 - Mudança de protocolo 
- 102 - O servidor recebeu e está processando.
#### Respostas  200-299
Respostas bem-sucedidas. 
- 202 - Solicitação recebida mas não atendida.
- 205 - Redefinir a solicitação o documento enviado.
- 206 - Usado quando o cabeçalho range é enviado do cliente para solicitar apenas parte de um recurso.
#### Repostas 300-399
Respostas de redirecionamento.
- 300 - A solicitação tem mais de uma resposta possível.
- 301 - Movido permanentemente.
- 302 - Encontrada mas foi temporariamente movida.
- 307 - mesmo do 302, só mantenha o método HTTP utilizado.
- 309 - Recurso movido permanentemente para outro URI, localizado no cabeçalho em `Location:`.
#### Respostas 400-499
Respostas de erro do cliente. 
- 402 - Pagamento necessário
- 407 - Semelhante ao 401 porém necessita de um proxy para autenticação.
- 408 - Timeout.
- 411 - Cabeçalho `content-length:`  é obrigatório.
- 413 - Payload muito grande.
- 414 - URI muito grande.
- 429 - Muitas requisições.
#### Respostas 500-599
Respostas de erro do servidor
501 - Não implementado.
502 - Gateway inválido.
503 - Serviço indisponível.
# REST
Representa uma abordagem para desenvolver serviços web baseados nos métodos do protocolo HTTP, como GET, POST, PUT, DELETE, etc. RESTful não é um protocolo ou um padrão, mas sim um conjunto de princípios arquiteturais que baseia na estrutura de conexões síncronas entre cliente servidor. 

 #### Propriedades REST
1. O servidor deve ser stateless, isto é, toda informação de estado deve ser armazenada no cliente e a requisição deve conter toda a informação necessária para ser respondida.
2. As requisições podem ser cacheadas. Criando-se uma interface uniforme e onde o recurso é identificado pela URI. O cache pode ser adicionado tanto no cliente como no servidor.
3. Interface uniforme. APIs REST são construídas levando em conta que os recursos podem ser identificados através da URI e a ação identificada pelo verbo HTTP.
4. Ela pode ser distribuída entre vários componentes. Podemos ter componentes de cache, componentes específicos para recursos e componentes para recursos estáticos.
5. O código pode ser provido sob demanda. Uma API REST pode prover, além de recursos, arquivos contendo a lógica de negócios. Essa propriedade permite termos o que hoje conhecemos como Single Page Application e Progressive Web Applications.

```ad-info
##### Idempotência
Propriedade que a computação herdou da matemática. Quando falamos que uma operação é idempotente significa que, se a aplicarmos uma vez ou várias vezes, o resultado é o mesmo. 
```
# XHTML
É a versão estendida do HTML que combina regras de XML ao HTML para melhoria na semântica. (foi substituída pelo HTML5)

- É uma versão mais rigorosa.
- - `<!DOCTYPE>` é obrigatório.
- O atributo xmlns em `<html>` é obrigatório.
- `<html>`, `<head>`, `<title>` e `<body>` são obrigatórios.
- Os elementos sempre devem ser corretamente aninhados.
- Os elementos sempre devem ser fechados. (exceção de elementos self-closed `<br />`)
- Os elementos sempre devem estar em minúsculas.
- Os nomes dos atributos sempre devem estar em minúsculas.
- Os valores dos atributos sempre devem estar entre aspas.
- A minimização de atributos é proibida. (Todos os atributos devem possuir valor  `checked=""`)

```xhtml
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">  
<html xmlns="http://www.w3.org/1999/xhtml">  
	<head>  
	  <title>Título do documento</title>  
	</head>  
	<body>  
		 conteúdo aqui  
	</body>  
</html>
```
# XML
São formados com árvores de documentos, com somente uma raiz e elementos únicos em cada nó, dispostos de forma hierárquica. 

- Documentos XML precisam ter um elemento root. 
- Todos os documentos XML podem começam com uma declaração do tipo `<?xml version="1.1" encoding="UTF-8"?>`.
- XML são bastante abrangentes e incluem tipos primitivos como string, integer, booleans, e tipos complexos que podem ser definidos pelo usuário.
- XDM (XML Data Model) usado em tecnologias de consulta e transformação de XML.
- PSVI (Post-Schema-Validation Infoset) Validação de um documento XML contra seu esquema XML
- Os nomes dos elementos são sensíveis a maiúsculas e minúsculas.
- Os nomes dos elementos devem começar com uma letra ou sublinhado.
- Os nomes dos elementos não devem começar com um número.
- Os nomes dos elementos não podem começar com as letras xml (ou XML, ou Xml, etc).
- Os nomes dos elementos podem conter letras, dígitos, hifens, sublinhados e pontos.
- Os nomes dos elementos não podem conter espaços.
- Os atributos não podem conter múltiplos valores (os elementos podem) 
- Os atributos não podem conter estruturas de árvore (os elementos podem) 
- Os atributos não são facilmente expansíveis (para mudanças futuras)

``` xml
<?xml version="1.0" encoding="UTF-8"?>  
<bookstore>  
  <book category="cooking">  
    <title lang="en">Everyday Italian</title>  
    <author>Giada De Laurentiis</author>  
    <year>2005</year>  
    <price>30.00</price>  
  </book>  
  <book category="children">  
    <title lang="en">Harry Potter</title>  
    <author>J K. Rowling</author>  
    <year>2005</year>  
    <price>29.99</price>  
  </book>  
  <book category="web">  
    <title lang="en">Learning XML</title>  
    <author>Erik T. Ray</author>  
    <year>2003</year>  
    <price>39.95</price>  
  </book>  
</bookstore>
```

Fechando aninhamento corretamente
```xml
<b><i>This text is bold and italic</i></b>
```

Atributos nos elementos
 ``` xml
<note date="12/11/2007">  
  <to>Tove</to>  
  <from>Jani</from>  
</note>

<gangster name='George "Shotgun" Ziegler'>
```

Comentários 
``` xml
<!-- This is a comment -->
```

Vazio
```xml
<element></element>
<element />
```

##### Validação
Um documento XML "bem formado" não é o mesmo que um documento XML "válido".
Um documento XML "válido" deve ser bem formado. Além disso, ele deve conformar-se a uma definição de tipo de documento.

Existem duas definições de tipo de documento diferentes que podem ser usadas com XML:

- DTD - A Definição de Tipo de Documento original
- XML Schema - Uma alternativa baseada em XML para DTD

Uma definição de tipo de documento define as regras e os elementos e atributos legais para um documento XML.
#### DTD
DTD significa Definição de Tipo de Documento.

Uma DTD define a estrutura e os elementos e atributos legais de um documento XML. Porém, menos expressivo e flexível, não oferece suporte a tipos de dados complexos e restrições avançadas.

```xml
<?xml version="1.0" encoding="UTF-8"?>  
<!DOCTYPE note SYSTEM "Note.dtd">  
<note>  
	<to>Tove</to>  
	<from>Jani</from>  
	<heading>Reminder</heading>  
	<body>Don't forget me this weekend!</body>  
</note>
```

Note.dtd
```dtd 
<!DOCTYPE note  
[  
<!ELEMENT note (to,from,heading,body)>  
<!ELEMENT to (#PCDATA)>  
<!ELEMENT from (#PCDATA)>  
<!ELEMENT heading (#PCDATA)>  
<!ELEMENT body (#PCDATA)>  
]>
```

Esse DTO vai se interpretado da seguinte forma:

- !DOCTYPE note - Define que o elemento raiz do documento é note.
- !ELEMENT note - Define que o elemento note deve conter os elementos: "to, from, heading, body".
- !ELEMENT to - Define que o elemento to deve ser do tipo "#PCDATA".
- !ELEMENT from - Define que o elemento from deve ser do tipo "#PCDATA".
- !ELEMENT heading - Define que o elemento heading deve ser do tipo "#PCDATA".
- !ELEMENT body - Define que o elemento body deve ser do tipo "#PCDATA".

```ad-tip
"#PCDATA" significa data caractere "parseavel".
```
#### Schema
Um XML Schema descreve a estrutura de um documento XML, assim como uma DTD.

- Esquemas XML são escritos em XML.
- Esquemas XML são extensíveis para adições.
- Esquemas XML suportam tipos de dados.
- Esquemas XML suportam namespaces.

```xml
<?xml version="1.0"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="https://www.w3schools.com" xmlns="https://www.w3schools.com" elementFormDefault="qualified">
	<xs:element name="note">  
		<xs:complexType>  
		  <xs:sequence>  
		    <xs:element name="to" type="xs:string"/>  
		    <xs:element name="from" type="xs:string"/>  
		    <xs:element name="heading" type="xs:string"/>  
		    <xs:element name="body" type="xs:string"/>  
		  </xs:sequence>  
		</xs:complexType>  
	</xs:element>
</xs:schema>
```

Esse schema deve ser interpretado da seguinte forma

- `<xs:element name="note">` define o elemento chamado "note".
- `<xs:complexType>` o elemento "note" é um tipo complexo.
- `<xs:sequence>` o tipo complexo é uma sequência de elementos.
- `<xs:element name="to" type="xs:string">` o elemento "to" é do tipo string.
- `<xs:element name="from" type="xs:string">` o elemento "from" é do tipo string.
- `<xs:element name="heading" type="xs:string">` o elemento "heading" é do tipo string.
- `<xs:element name="body" type="xs:string">` o elemento "body" é do tipo string.
# XSLT - eXtensible Stylesheet Language Transformations
Uma linguagem de folhas de estilo projetada para transformar documentos XML em outros formatos de documentos, como HTML, XHTML ou até mesmo outro documento XML com estrutura diferente.  O processo de transformação realizado pelo XSLT envolve a adição ou remoção de elementos e atributos no documento de saída, conforme especificado na folha de estilo XSLT. Isso permite que os dados contidos em um documento XML sejam reapresentados de maneira completamente nova, adequando-se a diferentes propósitos ou padrões de visualização.

No processo de transformação, XSLT usa XPath para definir partes do documento de origem que devem corresponder a um ou mais modelos predefinidos. Quando uma correspondência é encontrada, o XSLT transformará a parte correspondente do documento de origem no documento de resultado.

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
	<xsl:template match="/">
		<html> 
			<body>
			  <h2>My CD Collection</h2>
			  <table border="1">
			    <tr bgcolor="#9acd32">
			      <th style="text-align:left">Title</th>
			      <th style="text-align:left">Artist</th>
			    </tr>
			    <xsl:for-each select="catalog/cd">
			    <tr>
			      <td><xsl:value-of select="title"/></td>
			      <td><xsl:value-of select="artist"/></td>
			    </tr>
			    </xsl:for-each>
			  </table>
			</body>
		</html>
	</xsl:template>
</xsl:stylesheet>
```
# WSDL - Web Services Description Language
É uma linguagem baseada em XML utilizada para descrever os serviços oferecidos por um serviço web. Ela detalha a interface pública de acesso, incluindo os métodos disponíveis, os parâmetros necessários e os formatos de mensagem esperados.
##### Estrutura
Um documento WSDL descreve um serviço da web. Ele especifica a localização do serviço e os métodos do serviço, usando estes elementos principais.

`<types>` Define os tipos de dados (XML Schema) usados pelo serviço da web. 
`<message>` Define os elementos de dados para cada operação.
`<portType>` Descreve as operações que podem ser realizadas e as mensagens envolvidas.
`<binding>` Define o protocolo e o formato de dados para cada tipo de porta.

```xml
<message name="getTermRequest">  
  <part name="term" type="xs:string"/>  
</message>  
  
<message name="getTermResponse">  
  <part name="value" type="xs:string"/>  
</message>  
  
<portType name="glossaryTerms">  
  <operation name="getTerm">  
    <input message="getTermRequest"/>  
    <output message="getTermResponse"/>  
  </operation>  
</portType>
```

##### Elemento portType
O elemento `<portType>` define um serviço da web, as operações que podem ser realizadas e as mensagens envolvidas.

- One-way: A operação pode receber uma mensagem, mas não retornará uma resposta. 
- Request-response: A operação pode receber uma solicitação e retornará uma resposta. 
- Solicit-response: A operação pode enviar uma solicitação e aguardará por uma resposta.
- Notification: A operação pode enviar uma mensagem, mas não aguardará por uma resposta.
# UDDI - Universal Description, Discovery and Integration
É uma plataforma que permite que serviços web sejam listados e descobertos. Funciona como uma espécie de diretório, onde se pode buscar por serviços web disponíveis e obter informações para acessá-los.
# AJAX
técnica de desenvolvimento web que permite que páginas da web sejam atualizadas de forma assíncrona, ou seja, sem recarregar a página inteira. Usando JavaScript para enviar e receber dados do servidor em segundo plano, geralmente em formato JSON ou XML, sem interromper a experiência do usuário.

![[web-ajax.png]]
#### XMLHttpRequest
Basta utilizar o método `XMLHttpRequest` para se comunicar e interagir com o servidor através de algum evento sem que a página seja recarregada.

| Propriedades do objeto XMLHttpRequest |                                                                                                                                                                                                   |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **readyState**                        | A requisição se apresenta em 4 (quatro) estágios; ambos representando por um número.<br><br> 0 - não inicializado;<br> 1 - carregamento;<br> 2 - carregado;<br> 3 - interativo;<br> 4 - completo. |
| **status**                            | Código númerico do status HTTP retornado pelo servidor web.                                                                                                                                       |
| **statusText**                        | Texto associado ao código númerico do status HTTP. Por exemplo: 200 significa "OK" e 404 significa "Página não encontrada".                                                                       |
| **responseText**                      | String que contém os dados retornados pelo servidor web.                                                                                                                                          |
| **responseXML**                       | Se o servidor web retornar um documento XML, lhe permitindo acessá-lo através de funções JavaScript utilizando o DOM.                                                                             |

| Métodos do objeto XMLHttpRequest                |                                                                                                                                                                                                                                                                                                                                                              |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **open(método, url, síncrono, usuário, senha)** | Inicia uma nova requisição, onde:<br><br>método - Requisição HTTP, na maioria da das vezes "GET", ou "POST";<br>url - endereço da URL que será requisitada no servidor web;<br>síncrono - se o método trabalhará de forma síncrona ou assíncrona; o valor padrão é true - assíncrona;<br>usuário e senha - se o servidor web necessitar de uma autenticação. |
| **setRequestHeader(nome, valor)**               | Informa um cabeçalho (header) para a requisição.                                                                                                                                                                                                                                                                                                             |
| **send(dados)**                                 | Envia a requisição. Enviando opcionalmente os dados.                                                                                                                                                                                                                                                                                                         |
| **abort()**                                     | Aborta uma requisição em atividade.                                                                                                                                                                                                                                                                                                                          |
| **getResponseHeader(nome)**                     | Retorna o valor do cabeçalho (header) informado.                                                                                                                                                                                                                                                                                                             |
| **getAllResponseHeaders()**                     | Retorna uma string contendo todos os cabeçalhos (header).                                                                                                                                                                                                                                                                                                    |

|Eventos do objeto XMLHttpRequest|   |
|---|---|
|**onreadystatechange**|Elevando a cada mudança da propriedade readyState.

# SOAP - Simple Object Access Protocol
É um protocolo de comunicação que utiliza XML para a troca de informações entre aplicações em uma rede. Ao contrário do gRPC, o SOAP exige um documento WSDL compartilhado pelo servidor para implementar um cliente. Ele usa HTTP e XML, com cada serviço tendo um endpoint dedicado. Enquanto o REST usa diferentes verbos HTTP, o SOAP geralmente usa apenas POST, com GET sendo usado apenas para obter a documentação. O SOAP encapsula as chamadas de serviço em corpos de mensagem XML, sem depender dos detalhes do protocolo HTTP. Apesar de suas diferenças, o SOAP compartilha uma arquitetura semelhante ao gRPC, mas usa XML em vez de protocol buffers e HTTP/2.

- Pode ser transportado por outros protocolos como SMTP e JMS.
- DEVE ser codificada usando XML.
- DEVE usar o namespace Envelope do SOAP.
- NÃO deve conter uma referência a DTD.
- NÃO deve conter Instruções de Processamento XML.
#### Composição
- Um elemento Envelope que identifica o documento XML como uma mensagem SOAP  - OBRIGATÓRIO
- Um elemento Header que contém informações de cabeçalho  - OPCIONAL
- Um elemento Body que contém informações de chamada e resposta - OBRIGATÓRIO
- Um elemento Fault contendo erros e informações de status - OPCIONAL

```xml
<?xml version="1.0"?>  
<soap:Envelope  
xmlns:soap="http://www.w3.org/2003/05/soap-envelope/"  
soap:encodingStyle="http://www.w3.org/2003/05/soap-encoding">  
<soap:Header>  
...  
</soap:Header>  
<soap:Body>  
...
  <soap:Fault>  
  ...  
  </soap:Fault>  
</soap:Body>  
</soap:Envelope>
```
# Web Services
Web services são serviços de aplicação que podem ser acessados usando os protocolos padrões da Web, como HTTP e SOAP. Eles permitem que aplicações se comuniquem umas com as outras através da web, independentemente de sua plataforma ou linguagem de programação. Web Services são fracamente acoplados por foram projetados para viabilizar comunicação entre sistemas, plataformas e linguagens e padrões totalmente incompatíveis.

- São componentes de aplicativos 
- Se comunicam usando protocolos abertos 
- São autocontidos e auto descritivos
- Podem ser descobertos usando UDDI 
- Podem ser usados por outras aplicações HTTP e XML são a base para os serviços da web
- O maior foco é na interoperabilidade
- Geralmente são usadas para reutilização de componentes de aplicação ou conectar softwares já existentes.
### JAX-WS
A **Java API para Serviços Web XML (JAX-WS)** é uma tecnologia para construir serviços web e clientes que se comunicam usando XML. O JAX-WS permite que os desenvolvedores escrevam serviços web orientados a mensagens, bem como serviços web orientados a Chamada de Procedimento Remoto (RPC).

```java
@WebServlet(name="HelloServlet", urlPatterns={"/HelloServlet"})
public class HelloServlet extends HttpServlet {

	@WebServiceRef(wsdlLocation = "http://localhost:8080/helloservice-war/HelloService?WSDL")
	private HelloService service;
	
	protected void processRequest(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.setContentType("text/html;charset=UTF-8");
		try (PrintWriter out = response.getWriter()) {
			out.println("<html lang=\"en\">");
			out.println("<head>");
			out.println("<title>Servlet HelloServlet</title>");
			out.println("</head>");
			out.println("<body>");
			out.println("<h1>Servlet HelloServlet at " +
			request.getContextPath () + "</h1>");
			out.println("<p>" + sayHello("world") + "</p>");
			out.println("</body>");
			out.println("</html>");
			}
		}
	}
	
	private String sayHello(java.lang.String arg0) {
		javaeetutorial.helloservice.endpoint.Hello port = service.getHelloPort();
		return port.sayHello(arg0);
	}
} 
```
### JAX-RS
Facilita a criação de Web Services RESTful com a linguagem Java. 

```java
@Path("helloword")
public class HelloWorld {
	@Context
	private UriInfo context;
	
	public HelloWorld() {
	}
	
	@GET
	@Produces("text/html")
	public String getHtml(@QueryParam("test") String test) {
		return "<html lang=\"en\"><body><h1>Hello, World!!</h1></body></html>";
	}
	
	@GET
	@Produces("text/xml")
	@Path("users/{username: [a-zA-Z][a-zA-Z_0-9]*}")
	public String getUser(@PathParam("username") String userName) {
		...
	}
	
	@POST
	@Consumes("application/x-www-form-urlencoded")
	public String doPost2(FormURLEncodedProperties formData) {
		...
	}
}
```

```ad-summary
##### Anotações
Além das demais anotações relacionadas aos verbos HTTP como `@GET`, `@POST`, `@PATCH`, etc. Existem outras anotações para definir as estruturas dos endpoint relacionados ao Web Service.

- **`@Path`**: Define um caminho URI relativo que mostra onde a classe Java será hospedada, como `/helloworld`. Você também pode colocar variáveis nos URIs para criar um modelo de caminho URI. Por exemplo, você pode pedir o nome de um usuário e passá-lo para a aplicação como uma variável no URI: `/helloworld/{nomeDoUsuario}`. Isso permite que a aplicação responda de forma personalizada para diferentes usuários.
- **`@PathParam`**: é um tipo de parâmetro que você pode extrair para uso na sua classe de recurso. Os parâmetros do caminho URI são retirados do URI de solicitação, e os nomes dos parâmetros correspondem aos nomes das variáveis do modelo de caminho URI especificados na anotação de nível de classe `@Path`.
- **`@QueryParam`**: Os parâmetros de consulta são extraídos dos parâmetros de consulta do URI de solicitação. Eles permitem que você passe informações adicionais para a sua aplicação através do URI
- **`@Consumes`**: Especifica os tipos de mídia MIME que uma representação que um endpoint pode consumir, os quais foram enviados pelo cliente.
- **`@Produces`**: Usada para especificar os tipos de mídia MIME que uma representação de recurso pode produzir e enviar de volta ao cliente. Por exemplo, “text/plain” indica que o recurso pode produzir uma representação de texto simples para o cliente
```
# Quarkus
É um framework para desenvolvimento de aplicações cloud native. foi desenvolvido com o objetivo de ser portado dentro de
contêineres (a infraestrutura imutável).