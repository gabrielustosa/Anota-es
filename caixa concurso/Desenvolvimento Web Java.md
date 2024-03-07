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
Permite a criação de páginas Web que tenha componentes estáticos e dinâmicos. A tecnologia JSP disponibiliza todos os recursos dinâmicos da tecnologia Java Servlet, mas fornece uma abordagem mais natural para a criação de conteúdo estático. Na verdade, os JSPs são compilados em Servlets pelo servidor. Dessa forma, JSP são executados em um Container de Servlets, que é uma parte da plataforma Java EE. Objetos referenciados neste escopo possuem o menor ciclo de vida, pois estão vinculados a uma única solicitação de página (uma página JSP, por exemplo). Quando a resposta é enviada ao cliente, os objetos neste escopo não estão mais disponíveis. Portanto, eles são adequados para dados temporários usados durante a geração de uma resposta específica.

```jsp
<html>
	<body>
		Modelo: <%= req.getAttribute("modelo") %>
		Ano do Modelo: <%= req.getAttribute("anoModelo") %> // avalia e imprime
		<% List deps = (List) request.getAttribute("automoveis"); %> // código java
	</body>
</html>
```

Essas são algumas diretivas, as quais são utilizadas para informações especiais dentro de páginas, sendo dividido em três tipos:

- `@include` - Utilizado para inserir os códigos de arquivos à página corrente;
- `@page` - Responsável por trazer informações sobre a página JSP;
- `@taglib` - Responsável por habilitar uma biblioteca de tags personalizada (item que será abordado em outro artigo com mais detalhes).
```jsp
<%@page contentType="text/html" import="java.util.Date, java.text."pageEncoding="ISO-8859-1"%>
<html>
    <body>
        <h1>
            <%=new Date()=%>
        </h1>
    </body>
</html>
```

Alguns métodos JSP.

- `invalidate():` serve para terminar uma sessão de usuário que não é mais necessária e interrompe a conexão da sessão com todos os objetos armazenados.
- `isNew():` Este método é usado para verificar se a sessão é nova ou não. O valor booleano (verdadeiro ou falso) é retornado por ele.
- `getId():` ao criar uma sessão, o contêiner de servlet atribui um identificador de string distinto à sessão. Este identificador de string distinto é retornado pelo método `getId()`.
- `getAttributeNames():` Todos os objetos armazenados na sessão são retornados pelo método `getAttributeNames()`.
- `getCreationTime():` A hora de criação da sessão (a hora em que a sessão se tornou ativa ou a sessão começou).
- `getAttribute (String name):` Usando o método `getAttribute()`, o objeto que é armazenado pelo método `setAttribute()` é recuperado da sessão.
- `setAttribute (String, object):` O método `setAttribute()` é usado para armazenar um objeto na sessão atribuindo uma string única ao objeto. Posteriormente, usando a mesma string, este objeto pode ser acessado da sessão até que ela esteja ativa. No JSP, ao lidar com a sessão, `setAttribute()` e `getAttribute()` são os dois métodos mais usados regularmente.
- `removeAttribute (String name):` Usando o método `removeAttribute(String name)`, os objetos que estão armazenados na sessão podem ser removidos da sessão.
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
#### Componentes 
Frameworks de componentes: PrimeFaces, ICEfaces, RichFaces.

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

```ad-tip
##### Facelets
Tecnologia de renderização de páginas para JSF que substituiu a tecnologia JSP.
- `xmlns:ui="http://java.sun.com/jsf/facelets">`
```
#### Request Scope
O escopo disponíveis são ``request``, ``session``, ``application`` e ``view``. 

São aplicados no Managed Beans dessa forma:
```java
@ManagedBean
// @RequestScoped, @SessionScoped, @ApplicationScoped, @ViewScoped
public class MeuBean {
}
```
##### Request
Apenas sobrevivem por uma passada de vida no ciclo do JSF, ou seja, da fase 1 até a fase 6. Por ser um escopo que tem o tempo de vida curto é apropriado quando não precisamos memorizar dados entre as requisições dos usuários. É o padrão dos Managed Beans, dessa forma, ao não anotar sua classe, esse escopo será utilizado.
##### Session
Nesse escopo, tudo que armazenarmos ficará disponível enquanto a sessão do usuário estiver ativa. Ela é útil para armazenar informação sobre a última operação realizada por uma sessão, para proporcionar uma forma fácil de voltar a ela.
##### Application
Tudo que é armazenado no escopo de aplicação permanece enquanto a aplicação estiver executando, e é compartilhada entre todos os usuários. 
##### View
Esse escopo consiste em manter os dados contidos nele por quantas requisições forem feitas, mas desde que sejam todas para a mesma view. No momento em que trocamos de página o escopo é zerado. Isso é muito bom, porque evita que acumulemos objetos que ficam vivos por muito tempo, como no escopo de sessão, mas ao mesmo tempo permite ações feitas em sequência, como combos em cascata, que nesse escopo funcionam perfeitamente.

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
Propriedade que a computação herdou da matemática. uando falamos que uma operação é idempotente significa que, se a aplicarmos uma vez ou várias vezes, o resultado é o mesmo. 
```

# XHTML
É a versão estendida do HTML que combina regras de XML ao HTML para melhoria na semântica. (foi substituída pelo HTML5)
# XML
São formados com árvores de documentos, com somente uma raiz e elementos únicos em cada nó, dispostos de forma hierárquica. 

- Todos os documentos XML devem começam com uma declaração do tipo `<?xml version="1.1" encoding="UTF-8"?>`.
- XML são bastante abrangentes e incluem tipos primitivos como string, integer, booleans, e tipos complexos que podem ser definidos pelo usuário.
- É case sensitive.
# XSLT - eXtensible Stylesheet Language Transformations
Uma linguagem de folhas de estilo projetada para transformar documentos XML em outros formatos de documentos, como HTML, XHTML ou até mesmo outro documento XML com estrutura diferente.  O processo de transformação realizado pelo XSLT envolve a adição ou remoção de elementos e atributos no documento de saída, conforme especificado na folha de estilo XSLT. Isso permite que os dados contidos em um documento XML sejam reapresentados de maneira completamente nova, adequando-se a diferentes propósitos ou padrões de visualização.

Além disso, com o XSLT, é possível reorganizar a estrutura do documento, alterar os valores dos elementos e atributos e até criar outputs em formatos não XML, como textos simples ou HTML, que é amplamente utilizado para a exibição de dados na web. Neste contexto, a transformação para HTML ou XHTML é particularmente valiosa, pois permite que informações originalmente armazenadas em XML sejam acessíveis e apresentáveis em navegadores de internet, ampliando sua usabilidade.
# WSDL - Web Services Description Language
É uma linguagem baseada em XML utilizada para descrever os serviços oferecidos por um serviço web. Ela detalha a interface pública de acesso, incluindo os métodos disponíveis, os parâmetros necessários e os formatos de mensagem esperados.

Existem 4 padrões de mensagem WSDL:

- Request-response
- One-way
- Notification
- Solicit-response
# UDDI - Universal Description, Discovery and Integration
É uma plataforma que permite que serviços web sejam listados e descobertos. Funciona como uma espécie de diretório, onde se pode buscar por serviços web disponíveis e obter informações para acessá-los.
# SOAP - Simple Object Access Protocol
É um protocolo de comunicação que utiliza XML para a troca de informações entre aplicações em uma rede. Ao contrário do gRPC, o SOAP exige um documento WSDL compartilhado pelo servidor para implementar um cliente. Ele usa HTTP e XML, com cada serviço tendo um endpoint dedicado. Enquanto o REST usa diferentes verbos HTTP, o SOAP geralmente usa apenas POST, com GET sendo usado apenas para obter a documentação. O SOAP encapsula as chamadas de serviço em corpos de mensagem XML, sem depender dos detalhes do protocolo HTTP. Apesar de suas diferenças, o SOAP compartilha uma arquitetura semelhante ao gRPC, mas usa XML em vez de protocol buffers e HTTP/2.

- Pode ser transportado por protocolos como HTTP, SMTP e JMS.

 #### Composição
- Body - Contém a informação a ser transportada para o seu destino final. - OBRIGATÓRIO
- Fault - Contém informações e status de erro da mensagem. - OPCIONAL 
- Envelope - É o container de toda a mensagem SOAP, podendo conter a declaração de namespace que indica a versão de SOAP usada. - OBRIGATÓRIO
- Cabeçalho - Possui informações de controle e processamento, responsável por carregar informações adicionais, tal como se a mensagem deve ser processada por um determinado nó intermediário. - OPCIONAL
# Web Services
Web services são serviços de aplicação que podem ser acessados usando os protocolos padrões da Web, como HTTP e SOAP. Eles permitem que aplicações se comuniquem umas com as outras através da web, independentemente de sua plataforma ou linguagem de programação. Web Services são fracamente acoplados por foram projetados para viabilizar comunicação entre sistemas, plataformas e linguagens e padrões totalmente incompatíveis.
# Quarkus
É um framework para desenvolvimento de aplicações cloud native. foi desenvolvido com o objetivo de ser portado dentro de
contêineres (a infraestrutura imutável).

#TODO JAVA JAX-RS https://www.youtube.com/watch?v=xkKcdK1u95s&list=PLqq-6Pq4lTTZh5U8RbdXq0WaYvZBz2rbn
#TODO Microservices Patterns: With examples in Java - Livro
#TODO Sistemas distribuidos TUNEBAUM 
#TODO Beging Quarkus - Livro
