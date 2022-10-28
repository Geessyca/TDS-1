<h2 align="center">
  🎓<br>Trabalho de refatoração de códigos
</h2>

<h4 align="center">
   Projeto: Sistema de gestão de vendas - <a href=" "/>Repositório</a> 
</h4>
</br>
<h4>
	  <h5>Bad-Smell: Nomeclatura</br></h5>
✔️ Durante a criação dessa atividade a nomeclatura nãoera o principal objetivo, por isso foi aplicado a refatoração por meio da renomeação das mesmas </br></h4>
</br>

</br>
<h4>Na class Main foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class Main {
	public static void main(String[] args) {	
		cliente clt1 = new cliente("Gessyca","111",142);
		cliente clt2 = new cliente("Quezia","222",444);
		cliente clt3 = new cliente("Eyshila","333",666);
		
		funcionario fun1 = new funcionario("Moreira1","123");		
		fun1.Venda("Batata", 10,clt1);
		funcionario fun2 = new funcionario("Moreira2","123");		
		fun2.Venda("carne", 20,clt2);
		funcionario fun3 = new funcionario("Moreira3","123");		
		fun1.Venda("sorvete", 30,clt3);
		
		
		gerente gr1 = new gerente("Gerente","123456");
		gr1.fechamentoCaixa();
	}

}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class Main {
	public static void main(String[] args) {	
		Client firstClient = new Client("Gessyca","111",142);
		Client secondClient = new Client("Quezia","222",444);
		Client thirdClient = new Client("Eyshila","333",666);
		
		Employee firstEmployee = new Employee("Moreira1","123");		
		firstEmployee.Venda("Batata", 10,firstClient);
		Employee secondEmployee = new Employee("Moreira2","123");		
		secondEmployee.Venda("carne", 20,secondClient);
		Employee thirdEmployee = new Employee("Moreira3","123");		
		thirdEmployee.Venda("sorvete", 30,thirdClient);
		
		
		Manager manager = new Manager("Gerente","123456");
		manager.cashierClosing();
	}

}
```

</br>
<h4>Na classe User foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class usuario {
	private String nome;
	private String senha;
	
	public usuario(String nome,String senha) {
		this.nome = nome;
		this.senha = senha;
	}
	
	public void setNome(String nome) {
		this.nome = nome;
	}
	public String getNome() {
		return this.nome;
	}
	
	public void setSenha(String senha) {
		this.senha = senha;
	}
	public String getSenha() {
		return this.senha;
	}
	public void DadosGerais(){
		System.out.println("Nome: "+ getNome());
		System.out.println("Senha: "+ getSenha());
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class User {
	private String name;
	private String password;
	
	public User(String name,String password) {
		this.name = name;
		this.password = password;
	}
	
	public void setName(String name) {
		this.name = name;
	}
	public String getName() {
		return this.name;
	}
	
	public void setPassword(String password) {
		this.password = password;
	}
	public String getPassword() {
		return this.password;
	}
	public void generalData(){
		System.out.println("Name: "+ getName());
		System.out.println("Password: "+ getPassword());
	}
}
```

</br>
<h4>Na sub-classe Client herdada da classe de User foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class cliente extends usuario{
	private int cpf;
	private int a=0;
	public cliente(String nome,String senha,int cpf){
		super(nome,senha);
		this.cpf=cpf;
	}
	
	public int getCpf() {
		return cpf;
	}
	public void setCpf(int cpf) {
		this.cpf = cpf;
	}
	public void DadosGerais(){
		System.out.println("Nome: "+ getNome());
		System.out.println("Senha: "+ getSenha());
		System.out.println("CPF: "+ getCpf());
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class Client extends User{
	private int cpf;
	public Client(String name,String password,int cpf){
		super(name,password);
		this.cpf=cpf;
	}
	
	public int getCpf() {
		return cpf;
	}
	public void setCpf(int cpf) {
		this.cpf = cpf;
	}
	public void generalData(){
		System.out.println("Name: "+ getName());
		System.out.println("Password: "+ getPassword());
		System.out.println("CPF: "+ getCpf());
	}
}
```

</br>
<h4>Na sub-classe Employee herdade da classe User foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class funcionario extends usuario {
	public funcionario(String nome,String senha){
		super(nome,senha);
	}
	private static float totalVendido = 0;
	
	public void Venda(String NomeProduto,float preco,cliente clt1) {
		System.out.println("\n"+getNome()+" vendeu o produto "+NomeProduto+" por RS"+preco);
		System.out.println("Dados do cliente:");
		clt1.DadosGerais();
		this.totalVendido = this.totalVendido+preco;
	}
	
	public float getTotalVendido(){
		return this.totalVendido;
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class Employee extends User {
	public Employee(String name,String password){
		super(name,password);
	}
	private static float salesAmount = 0;
	
	public void Venda(String nameProduct, float price, Client client) {
		System.out.println("\n"+getName()+" vendeu o produto "+nameProduct+" por R$ "+price);
		System.out.println("Dados do cliente:");
		client.generalData();
		Employee.salesAmount = Employee.salesAmount+price;
	}
	
	public float getSalesAmount(){
		return Employee.salesAmount;
	}
}
```

</br>
<h4>Na sub-classe Manager heradada da classe Employee foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class gerente extends funcionario{
	gerente(String nome, String senha){
		super(nome,senha);
	}
	float total = getTotalVendido();
	public void fechamentoCaixa() {
		System.out.print("\n\nGerente: " + this.getNome());
		System.out.print("\n\nFechamento do caixa\n Valor total R$: " + this.total);
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class Manager extends Employee{
	Manager(String name, String password){
		super(name,password);
	}
	float salesAmount = getSalesAmount();
	public void cashierClosing() {
		System.out.print("\n\nGerente: " + this.getName());
		System.out.print("\n\nFechamento do caixa\n Valor salesAmount R$: " + this.salesAmount);
	}
}
```
