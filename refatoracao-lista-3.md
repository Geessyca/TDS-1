<h2 align="center">
  🎓<br>Trabalho de refatoração de códigos
</h2>

<h4 align="center">
   Projeto: Lista de exercicio em java - <a href="https://github.com/Geessyca/POO-List3"/>Repositório</a> 
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
	 
	 public static float getNumberFloat(String textDisplayed) {
		  System.out.printf(textDisplayed);
	      return readUser.nextFloat();
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
<h4>Na classe BigSmallAndAverageOfTenValues além do uso da nova classe criada GetUserUtils para evitar duplicações, foi realizado a refatoração de renomeação e assim pagando o debito tecnico do uso de i na utilização de for</h4></br>
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
<h4>Na classe MatrixSum além do uso da nova classe criada GetUserUtils para evitar duplicações, foi realizado a refatoração de renomeação e assim pagando o debito tecnico do uso de i e j na criação de matrizes</h4></br>
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
