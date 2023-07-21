# atv-teste-software-bdd-ifs
Atividade de teste de software BDD

#**Código Python Completo**

```python
import behave

def cadastrar_usuario(usuarios, nome, senha):
    if nome in usuarios:
        return "Usuário já cadastrado. Tente outro nome de usuário."
    else:
        usuarios[nome] = senha
        return "Usuário cadastrado com sucesso!"

def fazer_login(usuarios, nome, senha):
    if nome in usuarios and usuarios[nome] == senha:
        return "Login bem-sucedido. Bem-vindo, " + nome
    else:
        return "Nome de usuário ou senha inválidos."

def main():
    usuarios = {}
    
    while True:
        print("\nEscolha uma opção:")
        print("1 - Cadastrar usuário")
        print("2 - Fazer login")
        print("3 - Sair")
        opcao = input("Opção: ")

        if opcao == "1":
            nome = input("Digite o nome de usuário: ")
            senha = input("Digite a senha: ")
            print(cadastrar_usuario(usuarios, nome, senha))

        elif opcao == "2":
            nome = input("Digite o nome de usuário: ")
            senha = input("Digite a senha: ")
            print(fazer_login(usuarios, nome, senha))

        elif opcao == "3":
            print("Saindo...")
            break

        else:
            print("Opção inválida. Tente novamente.")

if __name__ == "__main__":
    main()
import behave

def cadastrar_usuario(usuarios, nome, senha):
    if nome in usuarios:
        return "Usuário já cadastrado. Tente outro nome de usuário."
    else:
        usuarios[nome] = senha
        return "Usuário cadastrado com sucesso!"

def fazer_login(usuarios, nome, senha):
    if nome in usuarios and usuarios[nome] == senha:
        return "Login bem-sucedido. Bem-vindo, " + nome
    else:
        return "Nome de usuário ou senha inválidos."

def main():
    usuarios = {}
    
    while True:
        print("\nEscolha uma opção:")
        print("1 - Cadastrar usuário")
        print("2 - Fazer login")
        print("3 - Sair")
        opcao = input("Opção: ")

        if opcao == "1":
            nome = input("Digite o nome de usuário: ")
            senha = input("Digite a senha: ")
            print(cadastrar_usuario(usuarios, nome, senha))

        elif opcao == "2":
            nome = input("Digite o nome de usuário: ")
            senha = input("Digite a senha: ")
            print(fazer_login(usuarios, nome, senha))

        elif opcao == "3":
            print("Saindo...")
            break

        else:
            print("Opção inválida. Tente novamente.")

if __name__ == "__main__":
    main()

```

#**Descrição das Funcionalidades**

##**Funcionalidade 01:  Cadastro de usuário**

**Descrição:** Como usuário, desejo me cadastrar no sistema.

**Cenário**: Cadastrar um novo usuário  

*   ***Dado*** que o sistema está aberto
*   ***Quando*** o usuário cadastrar um novo usuário com nome "jonas.freitas" e senha "jf00@123"
*   ***Então*** o sistema deve exibir a mensagem "Usuário cadastrado com sucesso!"

##**Funcionalidade 02:  Cadastro de usuário já existente**

**Descrição:** Como usuário, por engano tento cadastrar um usuário já existente no sistema.

**Cenário**: Tentar cadastrar um usuário já existente  

*   ***Dado*** que o sistema está aberto
*   ***E*** um usuário com nome "jonas.freitas" e senha "jf00@123" já está cadastrado
*   ***Quando*** o usuário tentar cadastrar um novo usuário com nome "jonas.freitas" e senha "jf00@123"
*   ***Então*** o sistema deve exibir a mensagem "Usuário já cadastrado. Tente outro nome de usuário!"

##**Funcionalidade 03:  Login com sucesso**

**Descrição:** Como usuário, realizo login.

**Cenário**: Adicionar algo com informações válidas  

*   ***Dado*** que o sistema está aberto
*   ***E*** um usuário com nome "jonas.freitas" e senha "jf00@123" já está cadastrado
*   ***Quando*** o usuário fizer login com nome "jonas.freitas" e senha "jonas.freitas"
*   ***Então*** o sistema deve exibir a mensagem "Login bem-sucedido." e seus dados cadastrais

##**Funcionalidade 04:  Login com credenciais inválidas**

**Descrição:** Como usuário, tento realizar login com credenciais erradas.

**Cenário**: Adicionar algo com informações válidas  

*   ***Dado*** que o sistema está aberto
*   ***E*** um usuário com nome "jonas.freitas" e senha "jf00@123" já está cadastrado
*   ***Quando*** o usuário tentar fazer login com nome "jonas.freitas" e senha "jf00@123"
*   ***Então*** o sistema deve exibir a mensagem "Nome de usuário ou senha inválidos!"

# Código com a lib behave

```python
from behave import *

usuarios = {}

@given("que o sistema está aberto")
def step_impl(context):
    usuarios.clear()

@when('o usuário cadastrar um novo usuário com nome "{nome}" e senha "{senha}"')
def step_impl(context, nome, senha):
    context.resultado = cadastrar_usuario(usuarios, nome, senha)

@when('o usuário tentar cadastrar um novo usuário com nome "{nome}" e senha "{senha}"')
def step_impl(context, nome, senha):
    context.resultado = cadastrar_usuario(usuarios, nome, senha)

@when('o usuário fizer login com nome "{nome}" e senha "{senha}"')
def step_impl(context, nome, senha):
    context.resultado = fazer_login(usuarios, nome, senha)

@when('o usuário tentar fazer login com nome "{nome}" e senha "{senha}"')
def step_impl(context, nome, senha):
    context.resultado = fazer_login(usuarios, nome, senha)

@then('o sistema deve exibir a mensagem "{mensagem}"')
def step_impl(context, mensagem):
    assert context.resultado == mensagem
```
