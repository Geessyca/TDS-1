<h2 align="center">
  🎓<br>Trabalho de refatoração de códigos
</h2>

<h4 align="center">
   Projeto: Conta Bancária em java - <a href=" "/>Repositório</a> 
</h4>
</br>
<h4>✔️ Todos as classes que possuiam o mesmo escopo foi convertido em somente uma classe para evitar duplicação de codigo</h4></br>
<h4>
✔️ Todos os arquivos foram renomeados para nomes relacionados as suas devidas funções </br></h4>
<h4>
✔️ Renomeação das variáveis para nomeclaturas mais claras das suas responsabilidades </br></h4>
</br>

</br>
<h4>Na Classe Main foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class Main {
public static void main(String[] args) {
		
		//question2 TesteConta2 = new question2();
		//System.out.println(TesteConta2.nome);
		//TesteConta2.nome = "Gessyca";
		
		
		question2 TesteConta3 = new question2();
		TesteConta3.setAgencia("1111");
		TesteConta3.setData(22,22,22);
		TesteConta3.setNome("Gessyca");
		TesteConta3.setNumero(3333);
		TesteConta3.setSaldo(4444);
		TesteConta3.recuperaDadosParaImpressao();
		
		question4 TesteConta4 =new question4("Gessyca");
		TesteConta4.recuperaDadosParaImpressao();

		question5 TesteConta51 =new question5("Gessyca");
		TesteConta51.recuperaDadosParaImpressao();
		question5 TesteConta52 =new question5("Gessyca");
		TesteConta52.recuperaDadosParaImpressao();
		
		question6 TesteConta61 =new question6("Gessyca");
		TesteConta61.setData(10, 20, 12);	
		
		
		
		
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class Main {
public static void main(String[] args) {
		BankAccountInfo newAccount = new BankAccountInfo();
		newAccount.setBankBranch("1111");
		newAccount.setDate(22,22,22);
		newAccount.setName("Gessyca");
		newAccount.setNumber(3333);
		newAccount.setWithdrawal(4444);
		newAccount.showBankAccountInfo();
	}
}
```
</br>
<h4>Na classe Que tinha como função trazer a data de abertura da conta foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class Data {
	int dia;
	int mes;
	int ano;
	Data(int dia,int mes,int ano){
		this.dia = dia;
		this.mes = mes;
		this.ano = ano;
	}
	public void Dados() {
		System.out.print("\ndia:"+this.dia);
		System.out.print(" mes:"+this.mes);
		System.out.print(" ano:"+this.ano);
	}
	
	String formatada() {
		String res = Integer.toString(dia)+"/"+Integer.toString(mes)+"/"+Integer.toString(ano);
		
		return res;
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class Date {
	int day;
	int month;
	int year;
	Date(int day,int month,int year){
		this.day = day;
		this.month = month;
		this.year = year;
	}
	public void showDate() {
		System.out.print("\nDia:"+this.day);
		System.out.print(" Mês:"+this.month);
		System.out.print(" Ano:"+this.year);
	}
	
	String formatada() {
		String res = Integer.toString(day)+"/"+Integer.toString(month)+"/"+Integer.toString(year);
		
		return res;
	}
}
```
</br>
<h4>As classes question2.java - question4.java - question5.java - question6.java, foram convertida em uma só classe onde foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class question2 {
	private String nome;
	private int numero;
	private String agencia;
	private double saldo;
	private Data data = new Data(0,0,0);
	
	
	public void setSaldo(double valor) {
		this.saldo = valor;
	}
	public double getSaldo() {
		return this.saldo ;
	}
	
	
	public void setNome(String valor) {
		this.nome = valor;
	}
	public String getNome() {
		return this.nome;
	}
	
	
	public void setNumero(int valor) {
		this.saldo = valor;
	}
	public int getNumero() {
		return this.numero ;
	}
	
	
	public void setAgencia(String valor) {
		this.agencia = valor;
	}
	public String getAgencia() {
		return this.agencia ;
	}
	
	
	public void setData(int dia,int mes,int ano) {
		this.data.dia = dia;
		this.data.mes = mes;
		this.data.ano = ano;
	}
	public Data  getData() {
		return this.data ;
	}
	
	
	
	public void saca(double valorsacado) {
		this.saldo = this.saldo-valorsacado;
		System.out.print("\nsaldo : "+ this.saldo);
	}
	
	public void deposita(double deposito) {
		this.saldo = this.saldo+deposito;
		System.out.print("\nsaldo : "+ this.saldo);
	}
	
	public void CalcRendimento() {
		System.out.print("\nRendimento:"+this.saldo*0.1);
	}
	public void recuperaDadosParaImpressao() {
		System.out.print("\nNome:"+this.nome);
		System.out.print("\nNumero:"+this.numero);
		System.out.print("\nAgencia:"+this.agencia);
		System.out.print("\nSaldo:"+this.saldo);
		System.out.print("\nData:"  );
		this.data.Dados();

	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class BankAccountInfo {
	UserBankAccount userInfo = new UserBankAccount();
	
	public void setWithdrawal(double value) {
		userInfo.balance = value;
	}
	public double getWithdrawal() {
		return userInfo.balance ;
	}
	
	
	public void setName(String value) {
		userInfo.name = value;
	}
	public String getName() {
		return userInfo.name;
	}
	
	
	public void setNumber(int value) {
		userInfo.balance = value;
	}
	public int getNumber() {
		return userInfo.number ;
	}
	
	
	public void setBankBranch(String value) {
		userInfo.bankBranch = value;
	}
	public String getBankBranch() {
		return userInfo.bankBranch ;
	}
	
	
	public void setDate(int day,int month,int year) {
		userInfo.openingDate.day = day;
		userInfo.openingDate.month = month;
		userInfo.openingDate.year = year;
	}
	public Date getDate() {
		return userInfo.openingDate ;
	}
	
	public void withdrawal(double withdrawalValue) {
		userInfo.balance = userInfo.balance-withdrawalValue;
		System.out.print("\nsaldo : "+ userInfo.balance);
	}
	
	public void deposit(double depositValue) {
		userInfo.balance = userInfo.balance+depositValue;
		System.out.print("\nsaldo : "+ userInfo.balance);
	}
	
	public void calculationIncome() {
		System.out.print("\nRendimento:"+userInfo.balance*0.1);
	}
	public void showBankAccountInfo() {
		System.out.print("\nNome:"+userInfo.name);
		System.out.print("\nNumero:"+userInfo.number);
		System.out.print("\nAgencia:"+userInfo.bankBranch);
		System.out.print("\nSaldo:"+userInfo.balance);
		System.out.print("\nData:"  );
		userInfo.openingDate.showDate();
	}
	
}
```
</br>
<h4>Foi criado uma classe com o tipo de variável que um usuario possuia ↷</h4></br>
</br>
```
public class UserBankAccount {
	 String name;
	 int number;
	 String bankBranch;
	 double balance;
	 Date openingDate = new Date(0,0,0);
}

```
