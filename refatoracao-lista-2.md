<h2 align="center">
  🎓<br>Trabalho de refatoração de códigos
</h2>

<h4 align="center">
   Projeto: Lista de exercicio em java - <a href="https://github.com/Geessyca/POO-List2"/>Repositório</a> 
</h4>
</br>
<h4>
✔️ Todos os arquivos foram renomeados para nomes relacionados as suas devidas funções </br></h4>
<h4>
✔️ Renomeação das variáveis para nomeclaturas mais claras das suas responsabilidades </br></h4>
<h4>
✔️ Extrações de funções que são utilizadas mais de uma vez </br></h4>
</br>

</br>
<h4>Questão 1 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
class pessoa{
	String nome;
	int idade;
	
	void fazAniversario(int i) {
		int newIdade = this.idade+i;
		System.out.println(this.nome + " tem " + newIdade);
	}
}
public class programa1 {
	public static void main(String[] args) {
		pessoa teste = new pessoa();
		
		teste.nome="Gessyca";
		teste.idade=21;
		
		for (int i=1;i<5;i++) {
			teste.fazAniversario(i);
		}
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
class User{
	String name;
	int age;
	
	void ageAfterBirthday(int quantityBrithday) {
		int newIdade = this.age+quantityBrithday;
		System.out.println("No "+quantityBrithday+"º aniversario, depois do de "+this.age+" anos, "+this.name + " terá " + newIdade + " anos.");
	}
}
public class UserAgeAfterBirthday {
	public static void main(String[] args) {
		User userInfo = new User();
		
		userInfo.name="Gessyca";
		userInfo.age=21;
		
		for (int quantityBirthday=1; quantityBirthday<5; quantityBirthday++) {
			userInfo.ageAfterBirthday(quantityBirthday);
		}
	}
}
```
</br>
<h4>Questão 2 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
class porta{
	boolean aberta;
	double dimensaoX, dimensaoY, dimensaoZ;
	String cor;
	
	void abre() {
		this.aberta = true;
	}
	void fecha() {
		this.aberta = false;
	}
	void tamanho(double dimensaoX, double dimensaoY, double dimensaoZ) {
		this.dimensaoX = dimensaoX;
		this.dimensaoY = dimensaoY;
		this.dimensaoZ = dimensaoZ;
	}
	void pinta(String s) {
		this.cor = s;
	}
	boolean	estaAberta() {
		return this.aberta;
	}
}
public class programa2 {
	public static void main(String[] args) {
		porta Porta = new porta();
		Porta.aberta=false;
		Porta.dimensaoX=0.6;
		Porta.dimensaoY=1.2;
		Porta.dimensaoZ=0.15;
		Porta.cor="Preta";
		String status;
		
		if (Porta.estaAberta() == true) {
			status = "Sim está aberta!";
		}
		else {
			status = "Não está aberta!";
		}
		
		System.out.println(status + 
						   "\nSua cor é " + Porta.cor +
						   "\nSua Dimensão é " + Porta.dimensaoX + " X "+
							Porta.dimensaoY + " X "+ Porta.dimensaoZ);
		
		Porta.abre();
		Porta.pinta("Rosa");
		Porta.tamanho(1, 3, 0.15);
		
		if (Porta.estaAberta() == true) {
			status = "Sim está aberta!";
		}
		else {
			status = "Não está aberta!";
		}
		
		System.out.println(status + 
				   "\nSua cor é " + Porta.cor +
				   "\nSua Dimensão é " + Porta.dimensaoX + " X "+
					Porta.dimensaoY + " X "+ Porta.dimensaoZ);
		
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
class Door{
	boolean doorIsOpen;
	double doorWidth, doorHeight, doorDepth;
	String doorColor;
	
	void openDoor() {
		this.doorIsOpen = true;
	}
	void closeDoor() {
		this.doorIsOpen = false;
	}
	void sizeDoor(double doorWidth, double doorHeight, double doorDepth) {
		this.doorWidth = doorWidth;
		this.doorHeight = doorHeight;
		this.doorDepth = doorDepth;
	}
	void coloredDoor(String color) {
		this.doorColor = color;
	}
	boolean	isOpen() {
		return this.doorIsOpen;
	}
}
public class CreateDoor {
	public static void main(String[] args) {
		Door door = new Door();
		door.doorIsOpen=false;
		door.doorWidth=0.6;
		door.doorHeight=1.2;
		door.doorDepth=0.15;
		door.doorColor="Preta";
		
		showInfoDoor(door);
		
		door.openDoor();
		door.coloredDoor("Rosa");
		door.sizeDoor(1, 3, 0.15);
		showInfoDoor(door);		
	}
	private static void showInfoDoor(Door doorInfo) {
		String doorStatus;
		if (doorInfo.isOpen() == true) {
			doorStatus = "Sim está aberta!";
		}
		else {
			doorStatus = "Não está aberta!";
		}
		
		System.out.println("\n"+doorStatus + 
				   "\nSua cor é " + doorInfo.doorColor +
				   "\nSua Dimensão é " + doorInfo.doorWidth + " X "+
				   doorInfo.doorHeight + " X "+ doorInfo.doorDepth);
	}
}
```
</br>
<h4>Questão 3 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
class casa{
	boolean porta1, porta2, porta3;
	String cor;
	
	void pinta(String s) {
		this.cor = s;
	}
	int	quantasPortasEstaoAbertas(boolean porta1, boolean porta2,boolean porta3) {
		int quantidade=0;
		if (porta1==true) {
			quantidade=quantidade+1;
		}
		if (porta2==true) {
			quantidade=quantidade+1;
		}
		if (porta3==true) {
			quantidade=quantidade+1;
		}
		
		return quantidade;
	}
}
public class programa3 {
	public static void main(String[] args) {
		casa Casa = new casa();
		Casa.cor="Azul";
		Casa.porta1=true;
		Casa.porta2=false;
		Casa.porta3=true;
		
		System.out.println("\nSua cor é " + Casa.cor +
						   "\nE tem " + Casa.quantasPortasEstaoAbertas(Casa.porta1, Casa.porta2, Casa.porta3) +
						   " portas abertas!");
		
		Casa.cor="Rosa";
		Casa.porta1=true;
		Casa.porta2=false;
		Casa.porta3=false;
		
		System.out.println("\nSua cor é " + Casa.cor +
						   "\nE tem " + Casa.quantasPortasEstaoAbertas(Casa.porta1, Casa.porta2, Casa.porta3) +
						   " portas abertas!");
		
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
class Home{
	boolean firstDoor, secondDoor, thirdDoor;
	String color;
	
	void coloredHome(String color) {
		this.color = color;
	}
	int	howManyDoorsAreOpen(boolean firstDoor, boolean secondDoor,boolean thirdDoor) {
		int numberOfOpenDoors=0;
		if (firstDoor==true) {
			numberOfOpenDoors=numberOfOpenDoors+1;
		}
		if (secondDoor==true) {
			numberOfOpenDoors=numberOfOpenDoors+1;
		}
		if (thirdDoor==true) {
			numberOfOpenDoors=numberOfOpenDoors+1;
		}
		
		return numberOfOpenDoors;
	}
}
public class CreateHome {
	public static void main(String[] args) {
		Home home = new Home();
		home.color="Azul";
		home.firstDoor=true;
		home.secondDoor=false;
		home.thirdDoor=true;
		
		showInfoHome(home);
		
		home.color="Rosa";
		home.firstDoor=true;
		home.secondDoor=false;
		home.thirdDoor=false;
		
		showInfoHome(home);
		
	}
	private static void showInfoHome(Home homeInfo) {
		System.out.println("\nSua casa tem color " + homeInfo.color +
				   "\nE tem " + homeInfo.howManyDoorsAreOpen(homeInfo.firstDoor, homeInfo.secondDoor, homeInfo.thirdDoor) +
				   " portas abertas!");
	}
}
```
</br>
<h4>Questão 4 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
class SaldoInsuficienteException extends RuntimeException {

    public SaldoInsuficienteException(double valor) {
        super("Saldo insuficiente para sacar o valor de: " + valor);
    }
}
class conta{
	String titular,agencia;
	int numero;
	double saldo;
	data dataDeAbertura;
	
	void saque(double valor) {
		 if (valor < 0) {
		        throw new IllegalArgumentException("Você tentou sacar um valor negativo");
		    }
		    if (this.saldo < valor) {
		        throw new SaldoInsuficienteException(valor);
		    }
		    this.saldo -= (valor + 0.10);
	}
	
	void deposito(double valor) {
		if (valor < 0) {	
	        throw new IllegalArgumentException("Você tentou depositar um valor negativo");
	    } else {
	        this.saldo += valor;        
	    }       
	}
	void calculaRendimento() {
		return this.saldo*0.1;
	}
	void recuperaDadosParaImpressao() {

		System.out.println("Conta: " + this.numero + " - " + this.agencia + "\n" +
				   "Data de abertura: " + this.dataDeAbertura.formatada() + "\n" +
				   "Titular: "+ this.titular +
				   "Saldo: " + this.saldo);
	}
}
class data{
	int dia, mes, ano;
	
	void preencher(int dia, int mes, int ano) {
		this.dia=dia;
		this.mes=mes;
		this.ano=ano;
	}
	
	String formatada() {

		return this.dia + "/" + this.mes + "/" + this.ano;
	}
}
public class question412_2 {
	public static void main(String[] args) {
		conta teste = new conta();
		
		teste.titular="Gessyca";
		teste.numero=194300031;
		teste.agencia="ufsj";
		teste.saldo=2019.1;
		
		teste.dataDeAbertura = new data();
		teste.dataDeAbertura.preencher(7, 2, 2019);

		//teste.saque(30000);
		//teste.saque(-30000);
		teste.deposito(-30000);
		
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
class InsufficientFunds extends RuntimeException {

    public InsufficientFunds(double withdrawalValue) {
        super("Saldo insuficiente para sacar o valor de: " + withdrawalValue);
    }
}
class BankAccount{
	String holder,bankBranch;
	int number;
	double balance;
	Date openingDate;
	
	void withdrawal(double withdrawalValue) {
		 if (withdrawalValue < 0) {
		        throw new IllegalArgumentException("Você tentou sacar um valor negativo");
		    }
		    if (this.balance < withdrawalValue) {
		        throw new InsufficientFunds(withdrawalValue);
		    }
		    this.balance -= (withdrawalValue + 0.10);
	}
	
	void deposit(double depositValue) {
		if (depositValue < 0) {	
	        throw new IllegalArgumentException("Você tentou depositar um valor negativo");
	    } else {
	        this.balance += depositValue;        
	    }       
	}
	double calculationIncome() {
		return this.balance*0.1;
	}
	void showBankAccountInfo() {

		System.out.println("Conta: " + this.number + " - " + this.bankBranch + "\n" +
				   "Data de abertura: " + this.openingDate.formatDate() + "\n" +
				   "Titular: "+ this.holder +
				   "Saldo: " + this.balance);
	}
}
class Date{
	int day, month, year;
	
	void fillDate(int day, int month, int year) {
		this.day=day;
		this.month=month;
		this.year=year;
	}
	
	String formatDate() {

		return this.day + "/" + this.month + "/" + this.year;
	}
}
public class CreatBankAccount {
	public static void main(String[] args) {
		BankAccount bankAccount = new BankAccount();
		
		bankAccount.holder="Gessyca";
		bankAccount.number=194300031;
		bankAccount.bankBranch="ufsj";
		bankAccount.balance=2019.1;
		
		bankAccount.openingDate = new Date();
		bankAccount.openingDate.fillDate(7, 2, 2019);

		//bankAccount.withdrawal(30000);
		//bankAccount.withdrawal(-30000);
		bankAccount.deposit(30000);
		bankAccount.showBankAccountInfo();
	
```
