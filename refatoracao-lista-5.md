<h2 align="center">
  🎓<br>Trabalho de refatoração de códigos
</h2>

<h4 align="center">
   Projeto: Sons de cada tipo de animal em java - <a href="[ ](https://github.com/Geessyca/POO-List5)"/>Repositório</a> 
</h4>
</br>
<h4>
✔️ Todos os arquivos foram renomeados para nomes relacionados as suas devidas funções </br></h4>
<h4>
✔️ Renomeação das variáveis para nomeclaturas mais claras das suas responsabilidades </br></h4>
</br>

</br>
<h4>Na classe Main foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class Main {
	public static void main(String[] args) {
		animal[] vetor = new animal[10];

		vetor[0] = new homem();
		vetor[1] = new dog();
		vetor[2] = new cat();
		vetor[3] = new homem();
		vetor[4] = new dog();
		vetor[5] = new cat();
		vetor[6] = new homem();
		vetor[7] = new dog();
		vetor[8] = new cat();
		vetor[9] = new homem();
		
		for (int i =0;i<10;i++) {
			vetor[i].fala();
			System.out.print("\n");
		}
		
	}

}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class Main {
	public static void main(String[] args) {
		AnimalSound[] vectorWithAnimalSound = new AnimalSound[10];

		vectorWithAnimalSound[0] = new ManSound();
		vectorWithAnimalSound[1] = new DogSound();
		vectorWithAnimalSound[2] = new CatSound();
		vectorWithAnimalSound[3] = new ManSound();
		vectorWithAnimalSound[4] = new DogSound();
		vectorWithAnimalSound[5] = new CatSound();
		vectorWithAnimalSound[6] = new ManSound();
		vectorWithAnimalSound[7] = new DogSound();
		vectorWithAnimalSound[8] = new CatSound();
		vectorWithAnimalSound[9] = new ManSound();
		
		for (int i =0;i<10;i++) {
			vectorWithAnimalSound[i].sound();
			System.out.print("\n");
		}
		
	}

}
```
</br>
<h4>Na classe AnimalSound foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class animal {
	public void fala() {
		System.out.print("Som: ");
	}
}

```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class AnimalSound {
	public void sound() {
		System.out.print("Som: ");
	}
}
```
</br>
<h4>Nas sub-classes herdadas de AnimalSound foi realizados as seguintes refatorações   ↷</h4></br>
</br>
<h4>
❌ Código antes da refatoração</br></h4>

```
public class cat extends animal{
	public void fala() {
		System.out.print(" Miau ");
	}
}
---------------------------------
public class dog extends animal{
	public void fala() {
		System.out.print(" AuAu ");
	}
}
---------------------------------
public class homem extends animal{
	public void fala() {
		System.out.print(" Oi ");
	}
}
```

<h4>
✔️ Código após da refatoração</br></h4>

```
public class CatSound extends AnimalSound{
	public void sound() {
		System.out.print(" Miau ");
	}
}
---------------------------------
public class DogSound extends AnimalSound{
	public void sound() {
		System.out.print(" AuAu ");
	}
}
---------------------------------
public class ManSound extends AnimalSound{
	public void sound() {
		System.out.print(" Oi ");
	}
}
```
