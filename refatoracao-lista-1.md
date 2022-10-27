<h2 align="center">
  🎓<br>Trabalho de refatoração de códigos
</h2>

<h4 align="center">
   Projeto: Lista de exercicio em java - <a href="[ciency-of-sorting-values)](https://github.com/Geessyca/POO-lista1)"/>Repositório</a> 
</h4>
</br>
<h4>✔️ Todos os arquivos que ultizam o input de dados por parte de usuario foi criado a class GetUserUtils para evitar duplicação de codigo</h4></br>

```
public class GetUserUtils {
	 private static Scanner readUser = new Scanner(System.in);;
	 public String getText(String textDisplayed) {
		  System.out.printf(textDisplayed);
	      return readUser.nextLine();
	 }
	 
	 public static int getNumberInt(String textDisplayed) {
		  System.out.printf(textDisplayed);
	      return readUser.nextInt();
	 }
	 
	 public static double getNumberDouble(String textDisplayed) {
		  System.out.printf(textDisplayed);
	      return readUser.nextDouble();
	 }
}
```

<h4>
✔️ Todos os arquivos foram renomeados para nomes relacionados as suas devidas funções </br></h4>
<h4>
✔️ Renomeação das variáveis para nomeclaturas mais claras das suas responsabilidades </br></h4>
</br>
</br>
<h4>Questão 1 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class Question1 {
	 public static void main(String args[]) {
		  Scanner readUser = new Scanner(System.in);
	      int old;
	      String name;
	      System.out.printf("Informe seu nome:");
	      name = readUser.nextLine();
	      System.out.printf("Informe sua idade:");
	      old = readUser.nextInt();

	      System.out.println(name +", sua idade é:"+old);
	    }
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class ShowNameAndAge {
	private static GetUserUtils getUser = new GetUserUtils();;
	 
	public static void main(String args[]) {
	      System.out.println(getUser.getText("Informe seu nome:") +", sua idade é:"+ GetUserUtils.getNumberInt("Informe sua idade:"));
	    }
}
```
<br/>
<h4>Questão 2 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class Question2 {
	 public static void main(String args[]) {
		  Scanner readUser = new Scanner(System.in);
		  int one,two;
	      System.out.printf("Informe o primeiro numero:");
	      one = readUser.nextInt();
	      System.out.printf("Informe o segundo numero:");
	      two = readUser.nextInt();

	      System.out.println("A soma destes numeros é: " + (one+two) + "\n" +
				    		 "A subtacao destes numeros é: " + (one-two) + "\n" +
				    		 "A divisao destes numeros é: " + ((double)one/two) + "\n" +
				    		 "A multiplicacao destes numeros é: " + (one*two) + "\n");
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class BasicEquationsInTwoNumbers {
	 public static void main(String args[]) {
	      int firstNumber =  GetUserUtils.getNumberInt("Informe o primeiro numero:");
	      int secondNumber =  GetUserUtils.getNumberInt("Informe o segundo numero:");

	      System.out.println("A soma destes numeros é: " + (firstNumber+secondNumber) + "\n" +
				    		 "A subtacao destes numeros é: " + (firstNumber-secondNumber) + "\n" +
				    		 "A divisao destes numeros é: " + ((double)firstNumber/secondNumber) + "\n" +
				    		 "A multiplicacao destes numeros é: " + (firstNumber*secondNumber) + "\n");
	    }
}
```
<br/>
<h4>Questão 3 foi realizados as seguintes refatorações   ↷</h4></br>
</br>

<h4>
❌ Código antes da refatoração</br></h4>

```
public class Question3 {
	 public static void main(String args[]) {
		  Scanner readUser = new Scanner(System.in);
		  int one,two;
	      System.out.printf("Informe o primeiro valor:");
	      one = readUser.nextInt();
	      System.out.printf("Informe o segundo valor:");
	      two = readUser.nextInt();
	      
	      if (one>two) {
	    	  System.out.println("O maior é " + one);
	      }else if (one<two) {
	    	  System.out.println("O maior " + two);
	      }else {
	    	  System.out.println("Os valores são iguais!");
	      }

	    }
 }     

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class ComparisonInTwoNumbers {
	 public static void main(String args[]) {
	      int firstNumber = GetUserUtils.getNumberInt("Informe o primeiro valor:");
	      int secondNumber = GetUserUtils.getNumberInt("Informe o segundo valor:");
      
	      if (firstNumber>secondNumber) {
	    	  System.out.println("O maior é " + firstNumber);
	      }else if (firstNumber<secondNumber) {
	    	  System.out.println("O maior é" + secondNumber);
	      }else {
	    	  System.out.println("Os valores são iguais!");
	      }

	    }
}
```
<br/>
<h4>Questão 4 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```

public class Question4 {
	 public static void main(String args[]) {
		  Scanner readUser = new Scanner(System.in);
		  int exp;
	      System.out.printf("Informe ultimo valor:");
	      exp = readUser.nextInt();
	      for(int i=1;i<=exp;i++) {
	    	  System.out.println(i*i);
	      }

	    }
}


```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class ExponentialCalculation {
	 public static void main(String args[]) {
		  int exp = GetUserUtils.getNumberInt("Informe o valor:");
	      for(int i=1;i<=exp;i++) {
	    	  System.out.println(i*i);
	      }

	    }
}
```
<br/>
<h4>Questão 5 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class Question5 {
	 public static void main(String args[]) {
		 Scanner readUser = new Scanner(System.in);
		 int val,soma=0;
		 System.out.printf("Informe o valor de parada do somatorio:");
		 val = readUser.nextInt();
		 for(int i=1;i<=val;i++) {
		 	  soma=(soma+i);
		 }
		 System.out.println("O somatorio de "+val+" é: "+soma);
	 }
}


```

<h4>
✔️ Código após da refatoração</br></h4>

```
 class SumCalculation {
	 public static void main(String args[]) {
		 int valueByUser,valueByUserueAux=0;
		 valueByUser = GetUserUtils.getNumberInt("Informe o valor de parada do somatorio:");
		 for(int i=1;i<=valueByUser;i++) {
		 	  valueByUserueAux=(valueByUserueAux+i);
		 }
		 System.out.println("O somatorio de "+valueByUser+" é: "+valueByUserueAux);
	 }
}
```
<br/>
<h4>Questão 6 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class Question6 {
	 public static void main(String args[]) {
		 for (int i=0; i<6; i++){  
	            for (int j=0; j<6; j++){
	                System.out.print("*");
	            }
	            System.out.println();
	        }
	     System.out.print(' ');
	  }
}


```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class Printing6x6Matrix {
	 public static void main(String args[]) {
		 for (int line=0; line<6; line++){  
	            for (int column=0; column<6; column++){
	                System.out.print("*");
	            }
	            System.out.println();
	        }
	     System.out.print(' ');
	  }
}
```
<br/>
<h4>Questão 7 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class Question7 {
	 public static void main(String args[]) {
		 for (int i=0; i<=6; i++){  
	            for (int j=i; j>=1; j--){
	                System.out.print("*");
	            }
	            System.out.println();
	        }
	     System.out.print(' ');
	  }
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class Printing6x1Matrix {
	 public static void main(String args[]) {
		 for (int line=0; line<6; line++){  
	            for (int column=1; column>=1; column--){
	                System.out.print("*");
	            }
	            System.out.println();
	        }
	  }
}
```
<br/>
<h4>Questão 8 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class Question8 {
	 public static void main(String args[]) {
		 Scanner readUser = new Scanner(System.in);
		 int func=0;
		 double salario=0,media=0;
		 System.out.printf("Digite o valor -1 quando todos salarios forem inseridos!\n");
		 while(salario != -1) {
    		 System.out.printf("Informe o valor do salario: ");
		     salario = readUser.nextDouble();
		     media=media+salario;
		     func++;
		 }
		 System.out.print("A media dos salarios é: "+(media+1)/(func-1));
	     
	  }
}


```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class AverageSalaryReceived {
	 public static void main(String args[]) {
		 int quantityOfSalary=0;
		 double salary=0, medium=0;
		 System.out.printf("Digite o valor -1 quando todos salarios forem inseridos!\n");
		 while(salary != -1) {
		     salary = GetUserUtils.getNumberDouble("Informe o valor do salarios: ");
		     medium=medium+salary;
		     quantityOfSalary++;
		 }
		 System.out.print("A media dos salarios é: "+(medium+1)/(quantityOfSalary-1));
	     
	  }
}
```
<br/>
<h4>Questão 9 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class Question9 {
	 public static void main(String args[]) {
		 Scanner readUser = new Scanner(System.in);
		 int km, lt, play=1;
		 while(play != 0) {
			System.out.printf("Digite quantos quilômetros foram percorridos:");
		    km = readUser.nextInt();
		    System.out.printf("Digite quantos litros foram gastos:");
		    lt = readUser.nextInt();
		    System.out.printf("\n\nForam percorridos "+((float)km/lt)+" quilometros por litro!\n\nDigite 0 para encerrar o programa e 1 para realizar outro calculo: ");
		    play = readUser.nextInt();
		    System.out.printf("\n\n");
		 }	  
		 System.out.printf("Programa Encerrado!");
	  }
}


```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class KilometerPerLiterRelation {
	 public static void main(String args[]) {
		 int kmQuantity, literQuantity, startProgram=1;
		 while(startProgram != 0) {
			kmQuantity = GetUserUtils.getNumberInt("Digite quantos quilômetros foram percorridos: ");
			literQuantity = GetUserUtils.getNumberInt("Digite quantos litros foram gastos: ");
		    float relation = ((float)kmQuantity/literQuantity);
		    startProgram = GetUserUtils.getNumberInt("\nForam percorridos " + relation + " quilometros por litro!\nDigite 0 para encerrar o programa e 1 para realizar outro calculo: ");
		    System.out.printf("\n\n");
		 }	  
		 System.out.printf("Programa Encerrado!");
	  }
}
```
<br/>
<h4>Questão 10 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class Question10 {
	 public static void main(String args[]) {
		 Scanner readUser = new Scanner(System.in);
		 int a,b,c;
		 System.out.printf("Digite o valor de a: ");
		 a = readUser.nextInt();
		 System.out.printf("Digite o valor de b: ");
		 b = readUser.nextInt();
		 System.out.printf("Digite o valor de c: ");
		 c = readUser.nextInt();
		 float x1,x2;
		 double raiz=((b*b)+(-4*a*c));
		 if (raiz >= 0) {
			 raiz=Math.sqrt(raiz);
			 System.out.printf("O valor de x1 é: "+((-b+raiz)/(2*a))+" e o valor de x2 é: "+((-b-raiz)/(2*a)));
		 }
		 else {
			 System.out.printf("Essa equação não possui raiz real!");
		 }
		 
		 
	  }
}


```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class BhaskaraCalculation {
	 public static void main(String args[]) {
		 int a,b,c;
		 a = GetUserUtils.getNumberInt("Digite o valor de a: ");
		 b = GetUserUtils.getNumberInt("Digite o valor de b: ");
		 c = GetUserUtils.getNumberInt("Digite o valor de c: ");
		 double squareRoot = ((b*b)+(-4*a*c));
		 if (squareRoot >= 0) {
			 squareRoot=Math.sqrt(squareRoot);
			 System.out.printf("O valor de x1 é: "+((-b+squareRoot)/(2*a))+" e o valor de x2 é: "+((-b-squareRoot)/(2*a)));
		 }
		 else {
			 System.out.printf("Essa equaçăo năo possui raiz real!");
		 }
		 
		 
	  }
}
```
