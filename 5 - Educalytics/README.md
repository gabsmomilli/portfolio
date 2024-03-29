# EDUCALYTICS

## Introdução

A empresa Ionic Health propôs um desafio acadêmico para os alunos do 5º semestre do curso de Banco de Dados da FATEC-SJC, a fim de estimular o desenvolvimento do período, preparando para o mercado de trabalho, e encontrar uma solução tecnológica para sanar e atender às necessidades do cliente. 

## Proposta
O objetivo da parceria era o desenvolvimento de indicadores e avaliar o uso e gerenciamento de sua plataforma de cursos, buscando os alunos que estão com boa frequência nas aulas, entrar em contato por chat para sanar dúvidas e avaliar as aulas dadas. 

A Ionic Health solicitou uma plataforma funcional com capacidade analítica, com dashboards, histórico de chat e armazenamento desses dados. Para a realização da análise deverá ter especialmente:


* Ativação: quantos usuários ativos (aluno/colaboradores) na plataforma legado;
* Engajamento: conhecer o número de usuários, tipos, seu comportamento (matrícula, curso, disciplina, participação);
* Desempenho: qual o aproveitamento do aluno(nota atingida) e do professor (andamento da turma);
* Participação: x taxas de conclusão x desempenho dos alunos/colaboradores;
* Avaliação de reação: quanto ao conteúdo apresentado, experiência do aluno/colaborador durante o curso;
* Registro do tempo de participação no curso;
* Guardar logs e histórico das conversas do chat;

## Contribuições individuais
 
Nesse projeto a equipe em que atuei estava reduzida perto dos demais grupos da turma, o Projeto Integrador foi o mais desafiador com requisitos complexos e exigindo conhecimentos específicos para compor a aplicação. Com isso, dividimos a equipe deixando os integrantes assumir as tarefas que mais tinham conhecimento para ganharmos tempo e posteriormente dedicarmos em correr atrás das features que não tínhamos habilidades.

Portanto, optei por continuar no desenvolvimento do back-end da aplicação criando as entidades e demais camadas do sistema.

Desenvolvi no back-end as classes para integração com o front-end e para o ETL.

<details>
  <summary>Click aqui pra visualizar</summary>
  
  ```js
  @Entity
@Table(name = "performance")
public class Performance {

    @Id
	@Column(name = "prf_std_id")
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long id;

	@Column(name = "prf_course")
	private String course;

	@Column(name = "prf_partial_grade")
	private Double grade;

	@Column(name = "prf_partial_classes")
	private Integer parClasses;

	@Column(name = "prf_total_classes")
	private Integer totClasses;

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getCourse() {
        return course;
    }

    public void setCourse(String course) {
        this.course = course;
    }
  ```
</details>


Implementei Testes Unitários para cobertura do código e integração com o CI:

<details>
  <summary>Click aqui pra visualizar</summary>
  
  ```js
  @Test
    void profileRepositorySaveProfileWithLoginOk(){

        Auth auth = new Auth();
        auth.setPermission("teste12346");
        authRepository.save(auth);

        Login login = new Login();
        login.setEmail("login@login.comm");
        login.setPassword("teste123");
        login.setAuthorizations(new HashSet<Auth>());
		login.getAuthorizations().add(auth);
		loginRepository.save(login);

        Profile profile = new Profile();
        profile.setLogin(login);
        profile.setName("Teste");
        profile.setDoc("111.111.111-11");
        profile.setGender("Masculino");
        profile.setBirthday(new Date(1220227200L * 1000));
        profile.setPhone("(12) 2121-2121");
        profile.setMobile("(12) 1 2121-2121");
        profileRepository.save(profile);

        assertNotNull(profile.getId());
  
  ```
</details>

Implementei dois bancos de dados no sistema, sendo um relacional e outro não relacional 

<details>
  <summary>Click aqui pra visualizar</summary>
  
  ```js
    educalytics.datasource.jdbcUrl=jdbc:mysql://localhost:3306/educalytics
    educalytics.datasource.username=root
    educalytics.datasource.password=root

    performance.datasource.jdbcUrl=jdbc:mysql://localhost:3306/dw_educalytics
    performance.datasource.username=root
    performance.datasource.password=root

    participation.datasource.jdbcUrl=jdbc:mysql://localhost:3306/dw_participation
    participation.datasource.username=root
    participation.datasource.password=root
  ```
</details>
	
## Tecnologias

- Java: É uma linguagem de programação orientada a objetos. Foi utilizado essa linguagem para o desenvolvimento do back-end da aplicação.

- VS CODE: O Visual Studio Code é um editor de código-fonte desenvolvido pela Microsoft para Windows, Linux e macOS. Foi usado para rodar a aplicação frontend e back-end no ambiente de alguns integrantes do grupo.

- JavaScript/NodeJS: É uma linguagem de programação interpretada estruturada, de script em alto nível com tipagem dinâmica fraca e multiparadigma. Juntamente com HTML e CSS. Foi usada para desenvolver o frontend.

- MicrosoftSQLServer: Sistema gerenciador de Banco de dados relacional desenvolvido pela Sybase em parceria com a Microsoft. Foi usado para o desenvolvimento do ETL.

- MySQL: O MySQL é um sistema de gerenciamento de banco de dados, que utiliza a linguagem SQL como interface. Foi usado para o desenvolvimento do banco relacional da aplicação.

- React: É uma biblioteca JavaScript de código aberto com foco em criar interfaces de usuário em páginas web.

- Insomnia/Postman: É um API Client que facilita aos desenvolvedores criar, compartilhar, testar e documentar APIs. Utizada para testar o GET, PUT, POST e DELETE das classes controllers da aplicação.

- GitLab/GitFlow: Gerenciador de repositório de software baseado em git, com suporte a Wiki, gerenciamento de tarefas e CI/CD, para armazenar o código do projeto e desenvolver o CI/CD GitFLow da aplicação.

- MongoDB: É um software de banco de dados orientado a documentos. Foi usado para armazenar os logs do chat da aplicação legada no banco não relacional.

- OBS Studio/Kdenlive: É um programa de streaming e gravação gratuito. Usada para gravar vídeos das sprints.

## Aprendizados efetivos

### Hard Skills

- Gestão de tasks;
- Implementação de tres bancos no mesmo back-end;
- Criação e utilização da ferramenta ETL;
- Desenvolvimento de API em Java, com a framework Spring.

### Soft Skills
 
- Liderança na equipe de back-end: como era o membro da equipe que mais tinha conhecimentos sobre Java com Spring, os liderei;
- Proatividade: este projeto foi um pouco maior do que os outros, sendo assim, tomei a frente pra realizar algumas tarefas que ainda não tinham sido determinadas para um membro especifico do grupo;
- Trabalho em equipe: revisei o código de meus colegas e os ajudei a realizar suas tarefas.
