<h2 align="center">
  🎓<br>Trabalho de refatoração de códigos
</h2>

<h4 align="center">
   Projeto: Teste de eficiencia entre dois metodos de ordenção em java - <a href="[https://github.com/Geessyca/Jogo-Pedra-Papel-e-Tesoura--em-Python](https://github.com/Geessyca/-tests-to-verify-the-efficiency-of-sorting-values)"/>Repositório</a> 
</h4>
</br>
<h4>Arquivo de geração de um array inteiro de numeros aleatórios, que foi criado com o intuito de não gerar duplicação do metódo e foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
✔️ Renomeação do arquivo Generate.java->GenerateArrayOfInt.java </br></h4>
<h4>
✔️ Renomeação da função arrayIntGenerate->createArray.java </br></h4>
<h4>
✔️ Renomeação das variáveis para nomeclaturas mais claras das suas responsabilidades </br></h4>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class Generate {

    Random radom  = new Random();
    
	public int[] arrayIntGenerate(int lenght){
		 int[] numeros = new int[lenght];
	        for(int i=0;i<lenght; i++) {
	            numeros[i]= Math.abs(radom.nextInt(lenght*2));
	        }
	     return numeros;
	}
	
	
}
```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class GenerateArrayOfInt {

    Random radom  = new Random();
    
	public int[] createArray(int lenght){
		 int[] arrayOfInteger = new int[lenght];
	        for(int positionOfNumber=0;positionOfNumber<lenght; positionOfNumber++) {
	            arrayOfInteger[positionOfNumber]= Math.abs(radom.nextInt(lenght*2));
	        }
	     return arrayOfInteger;
	}
	
	
}
```
</br>
<h4>Arquivo do cálculo de recorrência de cada metodo de ordenação e foi realizado a seguinte refatoração   ↷</h4></br>
</br>
<h4>
✔️ Renomeação do arquivo CalculeRec.java->RecurrenceCalculator.java </br></h4>
<h4>
</br>
<h4>Arquivo de ordenação por InsertionSort onde foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
✔️ Renomeação da função ordena->inserctionSort </br></h4>
<h4>
✔️ Renomeação da função inserctionSortInit->sorting </br></h4>
<h4>
✔️ Renomeação das variáveis para nomeclaturas mais claras das suas responsabilidades </br></h4>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class InserctionSort {
	static int contador = 0;
	 public  void ordena(int[] v, int i) {
		    if(i == v.length)
		        return;
		        
		    for(int c = i; c > 0; c--){
		        if(v[c-1] > v[c]){
		        	contador++;
		            int aux = v[c-1];
		            v[c-1] = v[c];
		            v[c] = aux;
		        }
		    }
		    ordena(v, ++i);
		    
		}

		public void inserctionSortInit(int[] arr) {
			ordena(arr, 0);
		    System.out.println("Sorted Inserction: "+arr.length);
		    System.out.println("Sorted Array: "+Arrays.toString(arr)+"\nContador:"+contador);
		}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class InserctionSort {
	static int recurrenceCount = 0;
	 public  void inserctionSort(int[] arrayForSorting, int firstPosition) {
		    if(firstPosition == arrayForSorting.length)
		        return;
		        
		    for(int itemPosition = firstPosition; itemPosition > 0; itemPosition--){
		        if(arrayForSorting[itemPosition-1] > arrayForSorting[itemPosition]){
		        	recurrenceCount++;
		            int aux = arrayForSorting[itemPosition-1];
		            arrayForSorting[itemPosition-1] = arrayForSorting[itemPosition];
		            arrayForSorting[itemPosition] = aux;
		        }
		    }
		    inserctionSort(arrayForSorting, ++firstPosition);
		    
		}

		public void sorting(int[] arrayForSorting) {
			inserctionSort(arrayForSorting, 0);
			System.out.println("O valor da recorrencia foi: "+recurrenceCount);
		}
}
```
</br>
<h4> Arquivo de ordenação por MergeSort onde foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
✔️ Renomeação da função mergeSortInit->sorting</br></h4>
<h4>
✔️ Renomeação das variáveis para nomeclaturas mais claras das suas responsabilidades </br></h4>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class MergeSort {
	 static int contador = 0;
	
	  void merge(int array[], int p, int q, int r) {

	    int n1 = q - p + 1;
	    int n2 = r - q;

	    int L[] = new int[n1];
	    int M[] = new int[n2];

	    for (int i = 0; i < n1; i++)
	      L[i] = array[p + i];
	    for (int j = 0; j < n2; j++)
	      M[j] = array[q + 1 + j];

	    int i, j, k;
	    i = 0;
	    j = 0;
	    k = p;

	    while (i < n1 && j < n2) {
	      if (L[i] <= M[j]) {
	        array[k] = L[i];
	        i++;
	      } else {
		    	contador ++;
	        array[k] = M[j];
	        j++;
	      }
	      k++;
	    }

	    while (i < n1) {
	      array[k] = L[i];
	      i++;
	      k++;
	    }

	    while (j < n2) {
	      array[k] = M[j];
	      j++;
	      k++;
	    }
	  }
	   void mergeSort(int array[], int left, int right) {

	    if (left < right) {

	      int mid = (left + right) / 2;

	      mergeSort(array, left, mid);
	      mergeSort(array, mid + 1, right);

	      merge(array, left, mid, right);
	    }
	  }

	  public void mergeSortInit(int array[], int left, int right) {		
		  mergeSort(array, 0, array.length - 1);
		  System.out.println("Sorted Merge: "+array.length);
		    System.out.println("Sorted Array: "+Arrays.toString(array)+"\nContador:"+contador);
	  }
}
```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class MergeSort {
	 static int recurrenceCount = 0;
	
	  void merge(int[] arrayForSorting, int positionOfLeft, int positionOfMiddle, int positionOfRight) {

	    int quantityItemsOfFirstPart = positionOfMiddle - positionOfLeft + 1;
	    int quantityItemsOfSecondPart = positionOfRight - positionOfMiddle;

	    int arrayOfFirstPart[] = new int[quantityItemsOfFirstPart];
	    int arrayOfSecondPart[] = new int[quantityItemsOfSecondPart];

	    for (int itemOfFirstPart = 0; itemOfFirstPart < quantityItemsOfFirstPart; itemOfFirstPart++)
	      arrayOfFirstPart[itemOfFirstPart] = arrayForSorting[positionOfLeft + itemOfFirstPart];
	    for (int itemOfSecondPart = 0; itemOfSecondPart < quantityItemsOfSecondPart; itemOfSecondPart++)
	      arrayOfSecondPart[itemOfSecondPart] = arrayForSorting[positionOfMiddle + 1 + itemOfSecondPart];

	    int firstAux, secondAux, thirdAux;
	    firstAux = 0;
	    secondAux = 0;
	    thirdAux = positionOfLeft;

	    while (firstAux < quantityItemsOfFirstPart && secondAux < quantityItemsOfSecondPart) {
	      if (arrayOfFirstPart[firstAux] <= arrayOfSecondPart[secondAux]) {
	        arrayForSorting[thirdAux] = arrayOfFirstPart[firstAux];
	        firstAux++;
	      } else {
		    	recurrenceCount ++;
	        arrayForSorting[thirdAux] = arrayOfSecondPart[secondAux];
	        secondAux++;
	      }
	      thirdAux++;
	    }

	    while (firstAux < quantityItemsOfFirstPart) {
	      arrayForSorting[thirdAux] = arrayOfFirstPart[firstAux];
	      firstAux++;
	      thirdAux++;
	    }

	    while (secondAux < quantityItemsOfSecondPart) {
	      arrayForSorting[thirdAux] = arrayOfSecondPart[secondAux];
	      secondAux++;
	      thirdAux++;
	    }
	  }
	   void mergeSort(int[] arrayForSorting, int positionOfLeft, int positionOfRight) {

	    if (positionOfLeft < positionOfRight) {

	      int positionOfMiddle = (positionOfLeft + positionOfRight) / 2;

	      mergeSort(arrayForSorting, positionOfLeft, positionOfMiddle);
	      mergeSort(arrayForSorting, positionOfMiddle + 1, positionOfRight);

	      merge(arrayForSorting, positionOfLeft, positionOfMiddle, positionOfRight);
	    }
	  }

	  public void sorting(int[] arrayForSorting) {		
		  mergeSort(arrayForSorting, 0, arrayForSorting.length - 1);
		  System.out.println("O valor da recorrencia foi: "+recurrenceCount);
	  }
}
```
</br>
<h4>Arquivo principal, que foi criado com o intuito de não gerar duplicação do metódo e foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
✔️ Melhoria na estrutura da class </br></h4>
<h4>
✔️ Extrações dos métodos utlizados mais de uma vez </br></h4>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```

public class Main {
	  static CalculeRec calcu = new CalculeRec();
	  public static void main(String args[]) {
		  int lenghtArray = 16;
		  mergeSort(lenghtArray);
		    System.out.println("\n");
		  mergeBubble(lenghtArray);   
	  }
	  
	  public static void mergeSort(int lenght) {
			long tempoInicial = System.currentTimeMillis();
			int[] array = new Generate().arrayIntGenerate(lenght);
		    System.out.println("Antigo: "+Arrays.toString(array));

			new MergeSort().mergeSortInit(array, 0, array.length - 1);
			System.out.println("A recorrencia é "+ 	calcu.recMergeSort(lenght));
			System.out.println("o metodo executou em " + (System.currentTimeMillis() - tempoInicial)+"ms");
	  }
	  
	  public static void mergeBubble(int lenght) {
			long tempoInicial = System.currentTimeMillis();
		    int[] arrayInserction = new Generate().arrayIntGenerate(lenght);
		    System.out.println("Antigo: "+Arrays.toString(arrayInserction));
		    new InserctionSort().inserctionSortInit(arrayInserction);
			System.out.println("A recorrencia é "+ 	calcu.recInserctionSort(lenght));
		    System.out.println("o metodo executou em " + (System.currentTimeMillis() - tempoInicial)+"ms");
	  }
}
```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class Main {
	  static RecurrenceCalculator recurrenceCalculator = new RecurrenceCalculator();
	  public static void main(String args[]) {
		  int lenghtArray = 10;
		  sortByMergeSort(lenghtArray);
		  sortByInserctionSort(lenghtArray);   
	  }
	  
	  public static void sortByMergeSort(int lenghtArray) {
		    System.out.println("Dados da ordenação por MergeSort de um array com " + lenghtArray +" numeros inteiros.");
			long initialTime = System.currentTimeMillis();
			int[] arrayRandom = new GenerateArrayOfInt().createArray(lenghtArray);
			new MergeSort().sorting(arrayRandom);
		    responseSort(recurrenceCalculator.recurrenceOfMergeSort(arrayRandom.length), (System.currentTimeMillis() - initialTime));
	  }
	  
	  public static void sortByInserctionSort(int lenghtArray) {
		    System.out.println("Dados da ordenação por InserctionSort de um array com " + lenghtArray +" numeros inteiros.");
			long initialTime = System.currentTimeMillis();
			int[] arrayRandom = new GenerateArrayOfInt().createArray(lenghtArray);
		    new InserctionSort().sorting(arrayRandom);
		    responseSort(recurrenceCalculator.recurrenceOfInserctionSort(arrayRandom.length), (System.currentTimeMillis() - initialTime));
		    }
	  
	  private static void responseSort(int recorrenceResult, long compliteTimeResult) {
			System.out.println("O calculo de recorrencia resulta em: "+ 	recorrenceResult);
		    System.out.println("A ordenação executou em " + compliteTimeResult +" ms\n");
	  }
}
```

##  👩🏻‍💻 Autora<br>
<table>
  <tr>
    <td align="center">
      <a href="https://github.com/geessyca">
        <img src="https://avatars.githubusercontent.com/u/72661229?v=4" width="100px;" alt="Icon GitHub"/><br>
        <sub>
          <b>Gessyca Moreira</b>
        </sub>
      </a>
    </td>
  </tr>
</table>
