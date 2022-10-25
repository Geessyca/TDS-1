<h2 align="center">
  🎓<br>Trabalho de refatoração de códigos
</h2>

<h4 align="center">
   Projeto: Jogo Pedra, Papel e Tesoura em python - <a href="https://github.com/Geessyca/Jogo-Pedra-Papel-e-Tesoura--em-Python"/>Repositório</a> 
</h4>
</br>
<h4>Nesse projeto foi realizado a refatoração de renomeação das funções e variáveis  ↷</h4></br>
<h4>
❌ Variáveis com nomes genericos e em português</br></h4>


```
import random 

escolha = int(input("\n 1 - Pedra\n 2- Papel\n 3 - Tesoura\n Sua escolha é? "))
computador = random.randint(1, 3)
    
if escolha > 3 or escolha < 0:
    print ("\nOperação invalida")
        
elif escolha == 1:
    if computador == 1:
        print(f"\nEmpate\nEssa foi a escolha do computador: {computador}")
    elif computador == 2 :
        print(f"\nVitoria do Computador\nEssa foi a escolha do computador: {computador}")
    elif computador == 3:
        print(f"\nVitoria do Usuario\nEssa foi a escolha do computador: {computador}")
            
elif escolha == 2:
    if computador == 1:
        print(f"\nVitoria do Usuario\nEssa foi a escolha do computador: {computador}")
    elif computador == 2 :
        print(f"\nEmpate\nEssa foi a escolha do computador: {computador}")
    elif computador == 3:
        print(f"\nVitoria do Computador\nEssa foi a escolha do computador: {computador}")

elif escolha == 3:
    if computador == 1:
        print(f"\nVitoria do Computador\nEssa foi a escolha do computador: {computador}")
    elif computador == 2 :
        print(f"\nVitoria do Usuario\nEssa foi a escolha do computador: {computador}")
    elif computador == 3:
        print(f"\nEmpate\nEssa foi a escolha do computador: {computador}") 

```

</br>
<h4>
✔️ Variáveis com nomes que as identificam facilmente e globais </br></h4>
</br>

```

import random 

userChoice = int(input("\n 1 - Pedra\n 2- Papel\n 3 - Tesoura\n Sua escolha é? "))
randomChoice = random.randint(1, 3)
    
if userChoice > 3 or userChoice < 0:
    print ("\nOperação invalida")
        
elif userChoice == 1:
    if randomChoice == 1:
        print(f"\nEmpate\nEssa foi a escolha do computador:{randomChoice}")
    elif randomChoice == 2 :
        print(f"\nVitoria do Computador\nEssa foi a escolha do computador:{randomChoice}")
    elif randomChoice == 3:
        print(f"\nVitoria do Usuario\nEssa foi a escolha do computador:{randomChoice}")
            
elif userChoice == 2:
    if randomChoice == 1:
        print(f"\nVitoria do Usuario\nEssa foi a escolha do computador:{randomChoice}")
    elif randomChoice == 2 :
        print(f"\nEmpate\nEssa foi a escolha do computador:{randomChoice}")
    elif randomChoice == 3:
        print(f"\nVitoria do Computador\nEssa foi a escolha do computador:{randomChoice}")

elif userChoice == 3:
    if randomChoice == 1:
        print(f"\nVitoria do Computador\nEssa foi a escolha do computador:{randomChoice}")
    elif randomChoice == 2 :
        print(f"\nVitoria do Usuario\nEssa foi a escolha do computador:{randomChoice}")
    elif randomChoice == 3:
        print(f"\nEmpate\nEssa foi a escolha do computador: {randomChoice}") 

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
