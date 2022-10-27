<h2 align="center">
  🎓<br>Trabalho de refatoração de códigos
</h2>

<h4 align="center">
   Projeto: Lista de exercicio em java - <a href="https://github.com/Geessyca/POO-List3"/>Repositório</a> 
</h4>
</br>
<h4>✔️ Todos os arquivos que ultizam o input de dados por parte de usuario foi criado a class GetUserUtils para evitar duplicação de codigo</h4></br>
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
public class question01 {
	static void Print(float num[]) {
	    float menor=num[0], maior=num[0], media=0;
	    
	    for (int i=0; i<10; i++) {
	    	media=media+num[i];
	    	if (num[i]>maior){
	    		maior=num[i];
	    	}
	    	else if (num[i]<menor){
	    		menor=num[i];
	    	}
	    }
	    
	    System.out.printf("Maior número: " + maior + "\n" +
	    				  "Menor número: " + menor + "\n" +
	    				  "Média: " + (media/10));
	    
	}
	
	public static void main(String args[]) {
		  Scanner readUser = new Scanner(System.in);
		  float num[] = new float [10];
		  for(int i=0; i<10; i++) {
			  System.out.printf("Informe o " + (i+1) + "º valor: ");
			  num[i] = readUser.nextFloat();
		  }
		  
		  for(int i=9; i>=0; i--) {
			  System.out.printf(num[i] + "  ");

		  }
		  
		  int opcao;
		  System.out.printf("\nDeseja a imprimir qual é o maior valor, o menor valor e a média dos valores informados?\n"
		  		+ "0 - sim   ||  1 - não \n");
		  opcao = readUser.nextInt();
		  if (opcao == 0) {
			 	Print(num);
		  }
		  else {
			  System.out.printf("Finaliza o programa");
		  }
	    }
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class BigSmallAndAverageOfTenValues {
	static void DefineValues(float arrayNumeric[]) {
	    float smallValue=arrayNumeric[0], bigValue=arrayNumeric[0], mediumValue=0;
	    
	    for (int itemOfArray=0; itemOfArray<10; itemOfArray++) {
	    	mediumValue=mediumValue+arrayNumeric[itemOfArray];
	    	if (arrayNumeric[itemOfArray]>bigValue){
	    		bigValue=arrayNumeric[itemOfArray];
	    	}
	    	else if (arrayNumeric[itemOfArray]<smallValue){
	    	}
	    }
	    
	    System.out.printf("Maior número: " + bigValue + "\n" +
	    				  "Menor número: " + smallValue + "\n" +
	    				  "Média: " + (mediumValue/10));
	    
	}
	
	public static void main(String args[]) {
		  float arrayNumeric[] = new float [10];
		  for(int itemOfArray=0; itemOfArray<10; itemOfArray++) {
			  arrayNumeric[itemOfArray] = GetUserUtils.getNumberFloat("Informe o " + (itemOfArray+1) + "º valor: ");
		  }
		  
		  for(int itemOfArray=9; itemOfArray>=0; itemOfArray--) {
			  System.out.printf(arrayNumeric[itemOfArray] + "  ");

		  }
		  
		  int menu;
		  menu = GetUserUtils.getNumberInt("\nDeseja a imprimir qual é o maior valor, o menor valor e a média dos valores informados?\n"
			  		+ "0 - sim   ||  1 - não \n");
		  if (menu == 0) {
			 	DefineValues(arrayNumeric);
		  }
		  else {
			  System.out.printf("Finaliza o programa");
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
public class question2 {
	static double Hipotenusa(double b, double c) {
		return Math.sqrt((b*b+c*c));
	}

	public static void main(String args[]) {
	  Scanner readUser = new Scanner(System.in);
	  
	  double b, c;
	  System.out.printf("Informe o valor do cateto b: ");
	  b = readUser.nextDouble();
	  System.out.printf("Informe o valor do cateto c: ");
	  c = readUser.nextDouble();
	  
	  System.out.printf("A hipotenusa é: " + Hipotenusa(b,c));
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class HypotenuseCalculus {
	static double Hypotenuse(double b, double c) {
		return Math.sqrt((b*b+c*c));
	}

	public static void main(String args[]) {
	double b = GetUserUtils.getNumberDouble("Informe o valor do cateto b: ");
	double c = GetUserUtils.getNumberDouble("Informe o valor do cateto c: ");
	  
	  System.out.printf("A hipotenusa é: " + Hypotenuse(b,c));
	}
}
```

</br>
<h4>Questão 3 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class question3 {
	public static void main(String args[]) {
	  Scanner readUser = new Scanner(System.in);
	  
	  Random random = new Random();

	  int aleatorio = random.nextInt(10 + 1) + 1;
	  
	  int adv;
	  System.out.printf("Digite seu numero: ");
	  adv = readUser.nextInt();
	  
	  if (adv == aleatorio) {
		 System.out.printf("\nVocê acertou!"); 
	  }
	  else {
		  System.out.printf("Você errou, o número era " + aleatorio);
	  }
	  
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class GuessNumber01 {
	public static void main(String args[]) {
	  Random random = new Random();

	  int randomNumber = random.nextInt(10 + 1) + 1;
	  
	  int drawnNumber = GetUserUtils.getNumberInt("Digite seu numero: ");
	  
	  if (drawnNumber == randomNumber) {
		 System.out.printf("\nVocê acertou!"); 
	  }
	  else {
		  System.out.printf("Você errou, o número era " + randomNumber);
	  }
	  
	}
}
```
</br>
<h4>Questão 4 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class question4 {
	static int Numero () {
		Random random = new Random();
		int aleatorio = random.nextInt(10 + 1) + 1;
		return aleatorio;
	}
	static int Tentativa (int aleatorio, int adv) {
		  if (adv == aleatorio) {
			 return 1;
		  }
		  else {
			  return 0;
		  }
	}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class GuessNumber02 {
	static int RandomNumber () {
		Random randomNumber = new Random();
		return randomNumber.nextInt(10 + 1) + 1;
	}
	static int TryValue (int randomNumber, int drawnNumber) {
		  if (drawnNumber == randomNumber) {
			 return 1;
		  }
		  else {
			  return 0;
		  }
	}
	public static void main(String args[]) {	  
	  int drawnNumber, returnNumber=0;
	  int randomNumber = RandomNumber();
	  
	  drawnNumber = GetUserUtils.getNumberInt("Digite seu numero: ");
	  returnNumber = TryValue(randomNumber,drawnNumber);
	  
	  while (returnNumber!=1) {
	    
	  returnNumber = TryValue(randomNumber,drawnNumber);
	  
	  Object[] options = { "Tentar novamente", "Sair" };
	  int option = JOptionPane.showOptionDialog(null, "Você errou!", "Tentar novamente", JOptionPane.DEFAULT_OPTION, JOptionPane.WARNING_MESSAGE, null, options, options[0]);
	  if(option == 0) {
		  System.out.printf("Digite seu numero: ");
		  drawnNumber = GetUserUtils.getNumberInt("Digite seu numero: ");
		  returnNumber = TryValue(randomNumber,drawnNumber);
	  }
	  else {
		  break;
	  }
	  }
	  if (returnNumber ==1) {
	  System.out.printf("\nVocê acertou!");}
	}
}
```
</br>
<h4>Questão 5 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class question5 {
	static void SomaMatriz (int[][] m1, int[][] m2) {
		
		int[][] soma = new int [3][3];
		
		for(int i=0;i<3;i++) {
			for(int j=0;j<3;j++) {
				soma[i][j]=m1[i][j]+m2[i][j];
			}
		}

		for(int i=0;i<3;i++) {
			for(int j=0;j<3;j++) {
				System.out.printf(soma[i][j] + " ");
			}
			System.out.printf("\n");
		}
	}
	public static void main(String args[]) {
		Scanner readUser = new Scanner(System.in);
		int[][] m1 = {{1,2,3},{4,5,6},{7,8,9}};
		int[][] m2 = {{9,8,7},{6,5,4},{3,2,1}};
		SomaMatriz(m1,m2);
				
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class MatrixSum {
	static void Sum (int[][] firstMatrix, int[][] secondMatrix) {
		
		int[][] matrixSummed = new int [3][3];
		
		for(int line=0;line<3;line++) {
			for(int column=0;column<3;column++) {
				matrixSummed[line][column]=firstMatrix[line][column]+secondMatrix[line][column];
			}
		}

		for(int line=0;line<3;line++) {
			for(int column=0;column<3;column++) {
				System.out.printf(matrixSummed[line][column] + " ");
			}
			System.out.printf("\n");
		}
	}
	public static void main(String args[]) {
		int[][] firstMatrix = {{1,2,3},{4,5,6},{7,8,9}};
		int[][] secondMatrix = {{9,8,7},{6,5,4},{3,2,1}};
		Sum(firstMatrix,secondMatrix);
				
	}
}
```
</br>
<h4>Questão 6 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class question6 {
	public static void main(String args[]) {
	  Scanner readUser = new Scanner(System.in);
	  Random random = new Random();

	  int vetor[] = new int[10];

	  for (int i=0;i<10;i++) {
		  vetor[i]=random.nextInt(100 + 1) + 1;
	  }
	  
	  int alternativa, c=1;
	  
	  System.out.printf("\nDigite seu numero: ");
	  alternativa = readUser.nextInt();
	  
	  for (int i=0;i<10;i++) {
		    if(alternativa==vetor[i]) {
		    	 System.out.printf("Você acertou!");
		    	 c=0;
			}
		  }
	  
	  if(c!=0){System.out.printf("Nenhum dos 10 numeros são iguais ao digitado por você :(");}
	  
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class GuessNumber03 {
	public static void main(String args[]) {
	  Random randomNumber = new Random();

	  int vectorNumeric[] = new int[10];

	  for (int i=0;i<10;i++) {
		  vectorNumeric[i]=randomNumber.nextInt(100 + 1) + 1;
	  }
	  
	  int drawnNumber, validation=1;

	  drawnNumber = GetUserUtils.getNumberInt("\nDigite seu numero: ");
	  
	  for (int i=0;i<10;i++) {
		    if(drawnNumber==vectorNumeric[i]) {
		    	 System.out.printf("Você acertou!");
		    	 validation=0;
			}
		  }
	  
	  if(validation!=0){System.out.printf("Nenhum dos 10 numeros são iguais ao digitado por você :(");}
	  
	}
}
```
</br>
<h4>Questão 7 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```

public class question7 {
	static int Maior (int[][] m1) {
		
		int maior = m1[0][0];
		
		for(int i=0;i<4;i++) {
			for(int j=0;j<3;j++) {
				if(m1[i][j]>maior) {
					maior=m1[i][j];
				}
			}
		}

		return maior;
	}
	public static void main(String args[]) {
		Scanner readUser = new Scanner(System.in);
		int[][] m1 = new int[4][3];
		
		for(int i=0;i<4;i++) {
			for(int j=0;j<3;j++) {
				System.out.printf("Elemento [" + i + "][" +j + "]: ");
				m1[i][j]=readUser.nextInt();
			}
		}
		
		System.out.printf("O maior valor é: " + Maior(m1));
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class GetBigValueOfMatrix {
	static int GetBigValue (int[][] matrix) {
		
		int bigValue = matrix[0][0];
		
		for(int line=0;line<4;line++) {
			for(int column=0;column<3;column++) {
				if(matrix[line][column]>bigValue) {
					bigValue=matrix[line][column];
				}
			}
		}

		return bigValue;
	}
	public static void main(String args[]) {
		int[][] matrix = new int[4][3];
		
		for(int line=0;line<4;line++) {
			for(int column=0;column<3;column++) {
				matrix[line][column]=GetUserUtils.getNumberInt("Elemento [" + line + "][" +column + "]: ");
			}
		}
		
		System.out.printf("O maior valor é: " + GetBigValue(matrix));
	}
}
```
</br>
<h4>Questão 8 foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class question8 {
	static int Diagonal(int[][] m1) {
		
		int soma=m1[0][1]+m1[0][2]+m1[1][2];
		
		return soma;
	}
	
	static int[] Vetor(int[][] m1) {
		
		int vet[] = {m1[0][0],m1[0][1],m1[0][2]};

		return vet;
	}
	
	static void Menu(int[][] m1) {
		Scanner readUser = new Scanner(System.in);
		int opcao;
		System.out.printf("Escolha uma opção\n"
				+ "1- Soma dos dos elementos que estão acima da diagonal principal\n"
				+ "2- Elementos da primeira linha da matriz\n"
				+ "3- Os dois metodos\n");
		opcao=readUser.nextInt();
		
		if (opcao==1) {System.out.printf("A soma dos dos elementos que estão acima da diagonal principal é: " + Diagonal(m1));}
		else if (opcao==2) {int vet[] = Vetor(m1);
				System.out.printf("Os elementos da primeira linha da matriz são: " + vet[0]+","+vet[1]+","+vet[2]);}
		else if (opcao==3) {int vet[] = Vetor(m1);
		System.out.printf("A soma dos dos elementos que estão acima da diagonal principal é: " + Diagonal(m1) +
				"\nOs elementos da primeira linha da matriz são: " + vet[0]+","+vet[1]+","+vet[2]);}
		else {System.out.printf("Opcao Invalida\n"); Menu(m1);}

	}
	
	public static void main(String args[]) {
		Scanner readUser = new Scanner(System.in);
		int[][] m1 = new int[4][3];
		
		for(int i=0;i<4;i++) {
			for(int j=0;j<3;j++) {
				System.out.printf("Elemento [" + i + "][" +j + "]: ");
				m1[i][j]=readUser.nextInt();
			}
		}
		Menu(m1);
		
		
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class MatrixFunctions {
	static int Diagonal(int[][] matriz) {
		
		int sum=matriz[0][1]+matriz[0][2]+matriz[1][2];
		
		return sum;
	}
	
	static int[] Vector(int[][] matriz) {
		
		int vector[] = {matriz[0][0],matriz[0][1],matriz[0][2]};

		return vector;
	}
	
	static void Menu(int[][] matriz) {
		int option = GetUserUtils.getNumberInt("Escolha uma opção\n"
				+ "1- Soma dos dos elementos que estão acima da diagonal principal\n"
				+ "2- Elementos da primeira linha da matriz\n"
				+ "3- Os dois metodos\n");
		
		if (option==1) {System.out.printf("A sum dos dos elementos que estão acima da diagonal principal é: " + Diagonal(matriz));}
		else if (option==2) {int vector[] = Vector(matriz);
				System.out.printf("Os elementos da primeira linha da matriz são: " + vector[0]+","+vector[1]+","+vector[2]);}
		else if (option==3) {int vector[] = Vector(matriz);
		System.out.printf("A soma dos dos elementos que estão acima da diagonal principal é: " + Diagonal(matriz) +
				"\nOs elementos da primeira linha da matriz são: " + vector[0]+","+vector[1]+","+vector[2]);}
		else {System.out.printf("Opcao Invalida\n"); Menu(matriz);}

	}
	
	public static void main(String args[]) {
		int[][] matriz = new int[4][3];
		
		for(int line=0;line<4;line++) {
			for(int column=0;column<3;column++) {
				matriz[line][column]=GetUserUtils.getNumberInt("Elemento [" + line + "][" +column + "]: ");
			}
		}
		Menu(matriz);
		
		
	}
}
```
