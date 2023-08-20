# Git em Equipe

## Para criar um Token para o Linux

```conf
Clique no Avatar ➜ Settings ➜ Developer settings ➜ Personal access token ➜ Tokens (classic) ➜ Generate new token
```

## Inicializar o repositório

```sh
# Criando
git init

# Configurações globais
git config --global user.name "usuario"
git config --global user.email "email@dominio.com"
git config --global core.editor vim
git config --global merge.tool vimdiff
git config --global color.ui true

# Listar configurações globais
git config --list

# Vincular a minha pasta local a um repositório do GitHub
# Linux para não pedir a senha toda vez
git remote add origin https://usuario:token@github.com/usuario/aula3.git
# Windows
git remote add origin https://github.com/usuario/aula3.git

# Para alterar o repositório do GitHub na pasta local
# Linux para não pedir a senha toda vez
git remote set-url origin https://usuario:token@github.com/usuario/aula3.git
# Windows
git remote set-url origin https://github.com/usuario/aula3.git

# Criar a branch main (principal)
git branch -M main
git push -u origin main
```

## Clonar pasta do GitHub

```sh
git clone https://github.com/usuario/pastaProjeto.git .
```

## Adicionar todos os arquivos no Stage

```sh
git add -A
# ou
git add .
```

## Adicionar um arquivo no Stage

```sh
git add arquivo.php
```

## Criar commit

```sh
git commit -m 'nome do commit'
```

## Ver se tem alguma coisa para fazer commit

```sh
git status
```

## Listar commits

```sh
git log --oneline
```

## Andar na linha do tempo

```sh
git checkout 4eb96e7
```

## Ver a diferença de um arquivo

```sh
git diff arquivo.php
```

## Restaurar ao último estado salvo

```sh
git restore arquivo.php
```

## Enviar para GitHub (Upload)

```sh
# subindo apenas uma
git push -f origin main

# subindo todas
git push -f --all
```

## Baixar versão do GitHub (Download)

```sh
# baixando apenas uma
git pull -f origin main

# baixando todas
git pull -f --all
```

# Branchs

## Criar uma nova Branch

```sh
git branch -b nomeBranch
```

## Listar todas as Branchs

```sh
git branch
```

## Trocar Branch

```sh
git checkout nomeBranch
```

## Criação de um branch a partir de outro branch

```sh
git checkout -b feature4 develop
```

# Git Flow (Equipe)

## Iniciar o Git Flow

```sh
git flow init
```

## Adicionar uma nova feature (Função)

```sh
git flow feature start css
```

## Publicar as alterações da feature (Função) na Develop (Desenvolvimento)

```sh
git flow feature publish css
```

## Finalizar, transferir para a Develop (Desenvolvimento) e excluir a feature (Função)

```sh
git flow feature finish css
```

## Criar uma versão de release (Testes)

```sh
git flow release start 1.0
```

## finalizar a versão de release (Testes)

```sh
git flow release finish 1.0
```

## Fazer pequnas correções na versão final

```sh
# Criar
git flow hotfix start 1.1

# Publicar e deixar aberta para a equipe
git flow hotfix pulish 1.1

# Finalizar, excluir e publicar na Develop e Main
git flow hotfix finish 1.1
```

## Ver as tags das versões produzidas pela release (Testes) e hotfix (Correções)

```sh
git tag
```

# Merge

## Merge de uma Branch na outra

```sh
# ir para Branch que ainda não tem as alterações
git checkout main

# copiar as alterações feitas na outra Branch
git merge develop
```

# Resumo

```sh
main
develop
	FEATURE # FUNÇÃO - FUNCIONALIDADE
		# envia para o github e mantem a branch
		git flow feature publish css

		# exclui a branch e faz o merge apenas na develop
		git flow feature finish css

	RELEASE # TESTES - APROVAÇÃO
		# exclui a branch e faz o merge na develop e main
		# também gera uma nova tag
		git flow release finish 1.0

	HOTFIX # CORREÇÕES NA VERSÃO FINAL
		# exclui a branch e faz o merge na develop e main
		# também gera uma nova tag
		git flow hotfix finish 1.1
```
