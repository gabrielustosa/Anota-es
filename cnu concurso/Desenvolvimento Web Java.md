# Spring Boot
O Spring foi criado como uma alternativa aos modelos mais pesados e complexos da época, promovendo uma programação orientada a aspectos (AOP), acesso a dados simplificados, transações e abstração da camada de persistência, entre outras funcionalidades. Framework que segue o padrão estrutural MVC para construir aplicativos web e APIs RESTful.
#### Model
Representa as entidades de negócios, como representação de uma tabela no banco de dados, da sua aplicação, como usuários, produtos, pedidos, etc. Sendo mapeadas pela anotação `@Entity` da API de persistência de dados do Java.

```java
@Entity
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private long id;
    private String nome;
```
#### Repository 
Responsável pela interação com o banco de dados, fornecendo métodos para realizar operações CRUD (Create, Read, Update, Delete) nas entidades do modelo. Este modelo necessita da anotação `@Repository` além de estende a classe padrão `JpaRepository` que fornecem métodos prontos para realizar essas operações.

```java
@Repository
public interface UserRepository extends JpaRepository<User, Long> {

    User findByCpf(String cpf);
    List<User> queryByNomeLike(String name);

}
```

A nomenclatura implica na implementação dos métodos que são realizadas automaticamente pelo Spring Data JPA.

`findByCampo` - Busca entidades relacionadas ao "campo".
`queryByCampo` - Geralmente é usado quando a consulta requer condições mais complexas ou junções entre várias entidades.
`getByCampo` - Retorna uma única entidade com base no atributo campo.

Estes, também podem ser utilizados com Keyword Clauses:

**`And`** - `findByFirstNameAndLastName(String firstName, String lastName)`
**`Or`** - `findByCityOrCountry(String city, String country)`
**`Between`** - `findByAgeBetween(int minAge, int maxAge)`
**`LessThan`** - `findBySalaryLessThan(double salary)`
**`GreaterThan`** - `findByAgeGreaterThan(int age)`
**`IsNull`** - `findByLastNameIsNull()`
**`IsNotNull`** - `findByLastNameIsNotNull()`
**`Like`** - `findByFirstNameLike(String pattern)`
**`StartingWith`** - `findByLastNameStartingWith(String prefix)`
**`EndingWith`** - `findByLastNameEndingWith(String suffix)`
**`Containing`** - `findByFirstNameContaining(String part)`

#### DTO
São objetos utilizados para transferir dados entre o cliente e o servidor. Eles encapsulam os dados necessários para uma operação específica, muitas vezes sendo uma representação simplificada de uma entidade do modelo.

```java
import com.example.models

public class UserDTO {
    private String nome;
    private String cpf;
    private String endereco;
    private String email;
    private String telefone;
    private LocalDateTime dataCadastro;

    public static UserDTO convert(User user) {
        UserDTO userDTO = new UserDTO();
        userDTO.setNome(user.getNome());
        userDTO.setEndereco(user.getEndereco());
        userDTO.setCpf(user.getCpf());
        userDTO.setEmail(user.getEmail());
        userDTO.setTelefone(user.getTelefone());
        userDTO.setDataCadastro(user.getDataCadastro());
        return userDTO;
    }
}
```
#### Service
Contém a lógica de negócios da aplicação. Ele coordena as operações entre os repositórios e os controladores, encapsulando a lógica de manipulação de dados. Os serviços são geralmente classes anotadas com `@Service`, que são injetadas nos controladores e outras partes da aplicação. Eles usam os repositórios para acessar os dados e podem converter entre modelos e DTOs, conforme necessário, antes de retornar dados para os controladores.

```java
@Service
public class UserService {

    @Autowired
    private UserRepository userRepository;

    public List<UserDTO> getAll() {
        List<User> usuarios = userRepository.findAll();
        return usuarios.stream().map(UserDTO::convert).collect(Collectors.toList());
    }

    public UserDTO findById(long userId) {
        Optional<User> usuario = userRepository.findById(userId);
        if (usuario.isPresent()) {
            return UserDTO.convert(usuario.get());
        }
        return null;
    }

    public UserDTO save(UserDTO userDTO) {
        User user = userRepository.save(User.convert(userDTO));
        return UserDTO.convert(user);
    }
```
#### Controller
Responsável por lidar com as requisições HTTP, mapeando-as para métodos Java, geralmente das classes **DTO**, que executam a lógica de negócios apropriada e retornam respostas HTTP adequadas. Os controladores são classes anotadas com `@RestController` ou `@Controller`, as rotas definidas contêm métodos anotados com `@GetMapping`, `@PostMapping` (ou  `verboHTTPMapping`), para lidar com diferentes tipos de requisições HTTP.

```java
@RestController
public class UserController {
	@Autowired
	private UserService userService;
	
	@GetMapping("/user/")
	public List<UserDTO> getUsers() {
		List<UserDTO> usuarios = userService.getAll();
		return usuarios;
	}
	@GetMapping("/user/{id}")
	UserDTO findById(@PathVariable Long id) {
		return userService.findById(id);
	}
	
	@PostMapping("/user")
	UserDTO newUser(@RequestBody UserDTO userDTO) {
		return userService.save(userDTO);
	}

```
