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
JSF é um framework para a construção backend de um servidor que utiliza a arquitetura **MVC**. As telas do JSF podem ser escritas utilizando XHTML. O JSF conhece todo o estado da nossa tela, e guarda isso através das requisições, por isso ele é considerado um framework stateful.

- `h:<tag>` faz referência a taglibs fornecida pelo próprio JSF.
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
1. Restore View: Quando uma requisição chega ao JSF, a primeira tarefa realizada por ele é construir ou restaurar a árvore de componentes correspondente ao arquivo XHTML lido.
2. Apply Request Values:  O JSF irá buscar os valores informados pelo usuário e colocá-los nos seus respectivos componentes.
3. Process Validation: Os dados que foram submetidos com o formulário são validados.
4. Update Model Values: Após todas essas validações terminarem, os objetos de negócio que criam a aplicação são atualizados com os dados validados da requisição.
5. Invoke Application: Os métodos de ação de qualquer botão ou link que foi ativado serão chamados.
6. Render Response: Essa fase renderizará a página de resposta requisitada pelo usuário.

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