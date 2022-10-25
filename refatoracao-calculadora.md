<h2 align="center">
  🎓<br>Trabalho de refatoração de códigos
</h2>

<h4 align="center">
   Projeto: Calculadora básica em python - <a href="https://github.com/Geessyca/calculadora_basica_py/"/>Repositório</a> 
</h4>
</br>
<h4>Nesse projeto foi realizado a refatoração de renomeação das funções e variáveis  ↷</h4></br>
<h4>
❌ Nomes das funções em português </br>
❌ Variáveis com nomes genericos </br></h4>

```
soma = lambda a,b: a + b
sub = lambda a,b : a - b
mult = lambda a,b: a * b
div = lambda a,b: a / b

def cal():
    print("BEM VINDO A CALCULADORA PYTHON\n\n***** Digite dois números ******\n\n")
    a = float(input("Numero 1: "))
    b = float(input("Numero 2: "))

    print("\nEscolha uma operação: \n** 1 - SOMA\n** 2 - SUBTRAÇÃO\n** 3 - MULTIPLICAÇÃO\n** 4 - DIVISÃO\n\n")
    op = int(input("Operação: "))

    if op == 1:
        print(soma(a,b))

    elif op == 2:
        print(sub(a,b))

    elif op == 3:
        print(mult(a,b))

    elif op == 4:
        print(div(a,b))

    else:
        print("***** OPERAÇÃO INVALIDA *****")

    print("\nRETORNAREMOS AO MENU....\n")
    menu()

def menu():
    print("Escolha uma opção:\n\n1 - ABRIR CALCULADORA\n\n0 - SAIR DO PROGRAMA")
    op = int(input("\n"))
    if op == 1:
        cal()
    elif op == 0:
        quit()
    else:
        print("OPÇÃO INVALIDA, RETORNATEMOS AO MENU...")
        menu()
menu()

```

</br>
<h4>
✔️ Nomes das funções em claros e globais </br>
✔️ Variáveis com nomes que as identificam facilmente </br></h4>
</br>

```
functionSum = lambda firstNumber,secondNumber: firstNumber + secondNumber
functionSubtraction = lambda firstNumber,secondNumber : firstNumber - secondNumber
functionMultiplication = lambda firstNumber,secondNumber: firstNumber * secondNumber
functionDivision = lambda firstNumber,secondNumber: firstNumber / secondNumber

def cal():
    print("BEM VINDO A CALCULADORA PYTHON\n\n***** Digite dois números ******\n\n")
    firstNumber = float(input("Numero 1: "))
    secondNumber = float(input("Numero 2: "))

    print("\nEscolha uma operação: \n** 1 - SOMA\n** 2 - SUBTRAÇÃO\n** 3 - MULTIPLICAÇÃO\n** 4 - DIVISÃO\n\n")
    optionSelect = int(input("Operação: "))

    if optionSelect == 1:
        print(functionSum(firstNumber,secondNumber))

    elif optionSelect == 2:
        print(functionSubtraction(firstNumber,secondNumber))

    elif optionSelect == 3:
        print(functionMultiplication(firstNumber,secondNumber))

    elif optionSelect == 4:
        print(div(firstNumber,secondNumber))

    else:
        print("***** OPERAÇÃO INVALIDA *****")

    print("\nRETORNAREMOS AO MENU....\n")
    main()

def main():
    print("Escolha uma opção:\n\n1 - ABRIR CALCULADORA\n\n0 - SAIR DO PROGRAMA")
    optionSelect = int(input("\n"))
    if optionSelect == 1:
        cal()
    elif optionSelect == 0:
        quit()
    else:
        print("OPÇÃO INVALIDA, RETORNATEMOS AO MENU...")
        main()
main()

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
