PASSOS PARA CRIAÇÃO DO PROJETO - ESTRUTURAÇÃO

*** IMPORTANTE CRIAR OS PROJETOS SE POSSIVEL NA MESMA VERSAO DO .NET CORE (3.1.1)

1 - CRIAR PROJETO (OTHER) E ADICIONAR AS PASTAS:
	sql, src, tests;

2 - CRIAR UM PROJETO WEB APPLICATION .NET CORE

3 - CRIAR UM PROJETO CLASS LIBRARY .NET CORE (BUSINESS);
	- CRIAR AS PASTAS: Interfaces, Models, Notificacoes, Services, Validations
	- Adicionar as classes do modelo nas pasta Models;

4 - CRIAR UM PROJETO CLASS LIBRARY .NET CORE (DATA);
		- CRIAR AS PASTAS: Context, Mappings, Repository

5 - INSTALAR BIBLIOTECA DO EF NO PROJETO DATA 
	-  Install-Package Microsoft.EntityFrameworkCore;

6 - ADICIONAR OS MODELS E RELACIONAR AO DBCONTEXT DA APLICAÇÃO

7 - UTILIZAR O FLUENT-API PARA FAZER O MAPEAMENTO DAS TABELAS NO BANCO DE DADOS

8 - MAPEAR AS CLASSES NA PASTA MAPPINGS, PARA CADA CLASSE SERA REPRESENTADO EM UMA TABELA NO BD;

9 - INSTAlAR OS PACOTES PARA RELACIONAMENTO ENTRE OS MODELS 
	- Install-Package Microsoft.EntityFrameworkCore.Relational;

10 - CONFIGURAR NO STARTUO DO PROJETO WEB A REFERENCIA PARA O PROJETO DE CLASSES (DATA)
		
		*** IMPORTANTE *** 
		Os pacotes só funcionaram na vs 3.1.3, eles precisam estar na mesma vs em ambos os projetos;

		- Instalação:
			-  Install-Package Microsoft.EntityFrameworkCore -v 3.1.3;
			-  Install-Package Microsoft.EntityFrameworkCore.SqlServer -v 3.1.3;
			-  Install-Package Microsoft.EntityFrameworkCore.Relational -v 3.1.3;		
			
			# Cria uma Migration
				- Add-Migration Initial -Verbose -Context MeuDbContext;

			# Atualiza o BD
				- Update-Database -Context MeuDbContext

 11 - Criação de Repositorio genérico - IRepository para implementação das classes Repository (Data)
	
	- Criação de classe abstrata Repository para ser apenas herdada, ela faz a implementação 
	da interface IRepository que possuem os métodos genéricos em comum para todas as classes;	

	- Criação dos Repositorios no projeto (DATA) que implementam as interfaces correspondentes;

12 - Mapeando as entidades em ViewModels com Automapper
	
	- Mapeando as ViewModels (replicando os models da Business) porém com customização de DataAnnotations;
	- Instalando o AutoMApper no projeto App 
	- Install-Package automapper.extensions.microsoft.dependencyinjection
	- Criado classe de configuração do AutoMapper na Pasta App/AutoMapper/AutoMapperConfig:
		Nesta classe criamos o mapeamento entre a Model e a ViewModel;

13 -  Scaffolding das Controllers e Views (Fornecedores e Produtos)
	- Criação de Controllers e Views;
	- Utilização do mapper para maperar uma viewModel para um modelo e vice-versa;

 14 - Customização das Views
	







			