# Aula Rápida — Boas práticas de projeto no VS Code com Python

## Objetivo da aula

Nesta aula de até 10 minutos, a ideia é mostrar um fluxo simples, profissional e reutilizável para começar projetos Python no VS Code da forma certa.

Você vai ensinar:

⬎ como instalar o Python do zero  
⬎ como instalar o UV  
⬎ como criar um projeto organizado  
⬎ como criar e usar ambiente virtual  
⬎ como instalar pacotes do jeito certo  
⬎ como usar `.gitignore`  
⬎ como evitar erros comuns no começo de um projeto  

---

# 1. O que vamos montar na aula

Ao final da aula, o aluno terá uma estrutura parecida com essa:

```bash
meu_projeto/
├── .venv/
├── src/
│   └── main.py
├── .gitignore
├── pyproject.toml
└── README.md
```

Essa estrutura já é suficiente para começar projetos pequenos e médios de forma organizada.

---

# 2. Instalar o Python do zero

## Windows

A forma mais simples é:

1. Baixar o Python no site oficial
2. Durante a instalação, marcar a opção:

```bash
Add python.exe to PATH
```

3. Finalizar a instalação

## Como validar no terminal

Abra o terminal do VS Code, PowerShell ou CMD e rode:

```bash
python --version
```

ou

```bash
py --version
```

Se aparecer a versão do Python, está tudo certo.

## Dica importante

Sempre confira se o Python está realmente instalado antes de sair instalando biblioteca, VS Code ou ambiente virtual.

---

# 3. Instalar o VS Code

Depois de instalar o Python, instale o VS Code normalmente.

Ao abrir o VS Code, vale instalar estas extensões:

⬎ Python  
⬎ Pylance  
⬎ Jupyter, se for trabalhar com notebooks  

Essas extensões ajudam com autocomplete, execução de código e leitura melhor do projeto.

---

# 4. O que é o UV

O **UV** é uma ferramenta moderna para gerenciar ambientes virtuais e dependências Python de forma rápida.

Ele substitui vários comandos mais antigos e deixa o fluxo mais limpo.

Com ele você consegue:

⬎ criar ambiente virtual  
⬎ instalar dependências  
⬎ gerenciar projeto  
⬎ executar comandos com mais praticidade  

---

# 5. Instalar o UV

No terminal, rode:

```bash
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Depois feche e abra o terminal novamente.

Agora valide:

```bash
uv --version
```

Se retornar a versão, está instalado corretamente.

---

# 6. Criar a pasta do projeto

No terminal:

```bash
mkdir meu_projeto
cd meu_projeto
```

Depois abra essa pasta no VS Code.

Você pode fazer isso com:

```bash
code .
```

---

# 7. Criar o projeto Python do jeito certo

Dentro da pasta do projeto, rode:

```bash
uv init
```

Esse comando cria a base inicial do projeto com arquivos importantes, incluindo o `pyproject.toml`.

## O que é o `pyproject.toml`

Esse é o arquivo central do projeto Python moderno.

É nele que ficam configurações como:

⬎ nome do projeto  
⬎ versão  
⬎ dependências  
⬎ configurações de ferramentas  

Hoje ele é muito mais profissional do que sair criando projeto solto só com arquivo `.py`.

---

# 8. Criar o ambiente virtual

Agora crie o ambiente virtual:

```bash
uv venv
```

Isso criará uma pasta chamada:

```bash
.venv
```

Essa pasta guarda o ambiente isolado do projeto.

---

# 9. Ativar o ambiente virtual

## No PowerShell

```bash
.venv\Scripts\Activate.ps1
```

## No CMD

```bash
.venv\Scripts\activate.bat
```

Depois de ativar, normalmente o terminal mostra algo como:

```bash
(.venv)
```

na frente da linha de comando.

Isso indica que o ambiente virtual está ativo.

---

# 10. Por que usar ambiente virtual

Ambiente virtual serve para isolar as dependências de cada projeto.

Sem isso, acontece o caos:

⬎ um projeto precisa de uma versão  
⬎ outro projeto precisa de outra  
⬎ tudo fica misturado no Python da máquina  
⬎ começam os conflitos e erros difíceis de entender  

A boa prática é:

**cada projeto, seu próprio ambiente virtual**

---

# 11. Instalar bibliotecas com UV

Exemplo com pandas:

```bash
uv add pandas
```

Exemplo com requests:

```bash
uv add requests
```

Esses comandos já registram as dependências no projeto.

Isso é melhor do que sair usando `pip install` solto sem controle.

---

# 12. Criar uma estrutura mínima de código

Crie uma pasta chamada `src` e dentro dela um arquivo `main.py`.

Exemplo:

```python
print("Projeto configurado com sucesso")
```

Estrutura:

```bash
meu_projeto/
├── src/
│   └── main.py
```

---

# 13. Executar o projeto

No terminal:

```bash
python src/main.py
```

Se tudo estiver certo, o projeto já está funcionando.

---

# 14. Configurar o interpretador no VS Code

Mesmo com tudo instalado, às vezes o VS Code não seleciona o ambiente virtual automaticamente.

Então faça manualmente:

1. Pressione `Ctrl + Shift + P`
2. Procure por:

```bash
Python: Select Interpreter
```

3. Escolha o interpretador da pasta `.venv`

Exemplo de caminho:

```bash
.venv\Scripts\python.exe
```

Isso evita erro de biblioteca não encontrada dentro do editor.

---

# 15. Criar o `.gitignore`

Esse arquivo serve para dizer ao Git quais arquivos **não devem subir** para o repositório.

Crie um arquivo chamado:

```bash
.gitignore
```

Com este conteúdo:

```gitignore
# Ambiente virtual
.venv/

# Cache do Python
__pycache__/
*.pyc

# Arquivos do VS Code
.vscode/

# Arquivos de sistema
.DS_Store

# Arquivos de ambiente
.env
```

## Por que isso importa

Você não deve subir:

⬎ ambiente virtual  
⬎ cache  
⬎ arquivos locais do editor  
⬎ segredos e variáveis sensíveis  

Isso deixa o projeto mais limpo e profissional.

---

# 16. Boas práticas simples para ensinar

Durante a aula, vale reforçar estas regras:

## 1. Um projeto por pasta
Não misture vários projetos dentro da mesma estrutura.

## 2. Um ambiente virtual por projeto
Nada de reaproveitar o mesmo ambiente para tudo.

## 3. Nome de pasta e arquivo com padrão
Prefira nomes claros e sem bagunça.

Exemplo bom:

```bash
pipeline_vendas
```

Exemplo ruim:

```bash
Projeto Novo Final Agora Vai
```

## 4. Dependências registradas
Tudo que for instalado deve ficar controlado no projeto.

## 5. Não subir `.venv` para o GitHub
Ambiente virtual é local.

## 6. Separar código de configuração
Seu código deve ficar organizado, não tudo jogado na raiz.

---

# 17. Erros comuns de iniciantes

## Erro 1. Instalar biblioteca fora do ambiente virtual
Resultado: projeto funciona em um lugar e quebra em outro.

## Erro 2. Não selecionar o interpretador certo no VS Code
Resultado: import dá erro mesmo com pacote instalado.

## Erro 3. Subir `.venv` para o GitHub
Resultado: repositório pesado, bagunçado e nada profissional.

## Erro 4. Criar projeto sem estrutura mínima
Resultado: depois fica difícil crescer o projeto.

## Erro 5. Misturar arquivos pessoais com arquivos do projeto
Resultado: manutenção ruim e confusão.

---

# 18. Roteiro falado para aula de 10 minutos

## Abertura
“Hoje eu vou te mostrar como começar um projeto Python no VS Code da forma certa, com ambiente virtual, UV, organização e boas práticas que evitam muita dor de cabeça.”

## Parte 1
Mostrar instalação do Python e validar no terminal.

## Parte 2
Instalar o UV e validar versão.

## Parte 3
Criar pasta do projeto e rodar:

```bash
uv init
uv venv
```

## Parte 4
Ativar ambiente virtual e instalar uma biblioteca.

```bash
uv add pandas
```

## Parte 5
Criar `src/main.py` e rodar o projeto.

## Parte 6
Criar `.gitignore` e explicar por que isso é importante.

## Fechamento
“Se você começar seus projetos assim desde o início, já evita boa parte dos erros que travam quem está aprendendo Python e VS Code.”

---

# 19. Resumo final para deixar na tela

## Fluxo ideal

⬎ instalar Python  
⬎ instalar VS Code  
⬎ instalar UV  
⬎ criar pasta do projeto  
⬎ rodar `uv init`  
⬎ rodar `uv venv`  
⬎ ativar o ambiente  
⬎ instalar dependências com `uv add`  
⬎ configurar interpretador no VS Code  
⬎ criar `.gitignore`  

---

# 20. Comandos principais da aula

```bash
python --version
uv --version
mkdir meu_projeto
cd meu_projeto
uv init
uv venv
.venv\Scripts\Activate.ps1
uv add pandas
python src/main.py
```

---

# 21. Sugestão de fechamento da aula

“Projeto bem organizado não é frescura. É o que faz você conseguir evoluir, manter e compartilhar código sem virar bagunça. Mesmo em projeto simples, começar certo já faz diferença.”

---
