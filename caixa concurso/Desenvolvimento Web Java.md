# Servlet 
O nome “servlet” vem do inglês e dá uma ideia de servidor pequeno cujo objetivo basicamente é receber requisições HTTP, processá-las e responder ao cliente, essa resposta pode ser um HTML, uma imagem etc.

``` java
@WebServlet(urlPatterns="/visualizar")
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
# JSP
As JSPs, são páginas HTML que podem ter dentro de si trechos de código Java. Nas JSPs temos a possibilidade da escrita direta do HTML, que além de deixar o código mais legível, deixa-o mais manutenível.

```html 
<html>
	<body>
		Modelo: <%= req.getAttribute("modelo") %>
		Ano do Modelo: <%= req.getAttribute("anoModelo") %>
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