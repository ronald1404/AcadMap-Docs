# Workflow: Passo-a-Passo

Este documento tem como objetivo ser um guia e tutorial para o desenvolvedor.
Nele, abordaremos os seguintes assuntos:

- Criar uma nova branch de trabalho
- Como enviar essa branch ao github
- Como resolver conflitos de merge

## Índice

- [0. Clonando o repositório](#0-clonando-o-repositório)
- [1. Criando a Branch](#1-criando-a-branch)
  - [1.1 Commitando suas modificações](#11-commitando-suas-modificações)
- [2. Enviando suas mudanças ao github](#2-enviando-suas-mudan%C3%A7as-ao-github)
- [3. Finalizando o ciclo de vida de uma branch de feature](#3-finalizando-o-ciclo-de-vida-de-uma-branch-de-feature)
  - [3.1 Atualizando a branch dev](#31-verificando-e-atualizando-mudan%C3%A7as-feitas-na-branch-dev)
  - [3.2 Fazendo o merge local](#32-fazendo-o-merge-local)
    - [3.2.1 Resolvendo conflitos](#321-resolvendo-conflitos)
  - [3.3 Enviando o merge ao github](#33-enviando-o-merge-ao-github)
  - [3.4 Criando o Pull Request](#34-criando-o-pull-request)
  - [3.5 Encerrando a branch de feature](#35-Encerrando-a-branch)

## 0. Clonando o repositório

O passo inical de todo fluxo de trabalho é fazer o clone do repositório, para isso, utilize o seguinte comando:

```
git clone https://github.com/acadmap-project/AcadMap.git
```

## 1. Criando a Branch

Com o repositório clonado, iniciaremos a criação de uma nova branch de funcionalidade. Para fins de exemplificação, chamarei de "feature/teste"

Sendo assim, todo o fluxo de trabalho sempre se iniciará a partir branch Dev, então vamos dar o mudar para ela:

```
git checkout dev
```

Estando na branch correta, temos de atualiza-la com as mudanças mais recentes antes de iniciar o nosso trabalho:

```
git pull
```

Com as atualizações feitas, podemos criar nossa branch nova baseada na dev:

```
git checkout -b feature/teste
```

Neste momento, na nova branch, podemos iniciar o desenvolvimento normalmente, fazendo as modificações necessárias para implementar a feature.

**_Nota:_** Lembre-se de manter seu código organizado, estruturado e bem documentado.

### 1.1 Commitando suas modificações

Com a branch criada localmente e seu trabalho do dia completo, deve-se adicionar as mudanças feitas ao seu repositório local:

```
git add <nome-arquivo>
git commit -m 'feat: added new button'
```

## 2. Enviando suas mudanças ao Github

Com o fim do seu dia de trabalho e seu repositório local contendo as suas últimas mudanças feitas, é importante manda-las para o repositório remoto para mante-lo sempre atualizado:

```
git push origin feature/teste
```

## 3. Finalizando o ciclo de vida de uma branch de feature

Ao terminar o desenvolvimento da sua feature, você deve criar um Pull Request no Github, mas para isso, têm alguns passos que devem ser feitos antes:

1. Verificar e atualizar o conteúdo da branch dev.
2. Fazer o merge local.

   2.1 Resolver os conflitos localmente.

3. Criar o Pull Request
4. Encerrar as branch

### 3.1. Verificando e atualizando mudanças feitas na branch dev

Primeiro, nós atualizamos nossa branch dev local com as mudanças que ocorreram na dev remote.

Mudamos para a branch dev local:

```
git checkout dev
```

Atualizamos ela:

```
git pull origin dev
```

Verificamos a existência de divergências entre a nossa branch de feature e a branch dev atualizada:

```
git log feature/teste..dev --oneline
```

### 3.2. Fazendo o merge local

Caso existam diferenças, é necessário executar o merge da feature/teste <- dev localmente para garantir que nossa branch esteja atualizada.

Mudamos novamente para nossa branch de feature:

```
git checkout feature/teste
```

Fazemos o merge:

```
git merge dev
```

#### 3.2.1 Resolvendo conflitos

Durante a execução do merge, podem surgir 2 tipos de conflitos diferente:

- Conflito por exclusão de arquivo
- Conflito por mudanças no mesmo conteúdo de um mesmo arquivo

Para garantir a continuação correta do fluxo, precisamos resolve-los para concluir o merge com sucesso.

##### Conflito por exclusão de arquivo

Esse tipo de conflito ocorre quando um arquivo foi excluído na branch dev, mas ainda está presente e possivelmente foi modificado na sua branch de feature.

O Git não sabe se deve manter o arquivo (por causa das suas alterações) ou excluí-lo (seguindo o que aconteceu na dev). Nesse caso, você precisa decidir manualmente o que deve ser feito.

Para visualizar os arquivos com conflito, utilize:

```
git status
```

Você verá uma mensagem similar a essa:

```
both deleted: nome-do-arquivo
```

A partir desse momento, existem dois caminhos a serem tomados:

- Aceitar a exclusão do arquivo
- Manter o arquivo

_Caso você escolha aceitar a exclusão do arquivo_:

```
git rm nome-do-arquivo
git commit
```

_Caso você julgue que o arquivo é importante e escolha manter o arquivo_:

```
git add nome-do-arquivo
git commit
```

##### Conflito por mudanças no mesmo conteúdo de um mesmo arquivo

Esse tipo de conflito acontece quando o mesmo trecho de um arquivo foi alterado tanto na branch dev quanto na sua branch de feature. O Git não consegue decidir automaticamente qual alteração manter, então você precisa resolver o conflito manualmente.

Ao executar o git merge dev, você verá mensagens de conflito como:

```
CONFLICT (content): Merge conflict in nome-do-arquivo.
```

rodando git status você verá:

```
both modified: nome-do-arquivo
```

Quando isso ocorrer, você dever abrir o arquivo o qual o conflito ocorreu utilizando seu editor de código de preferência.

Ao abrir o arquivo, você verá algo como:

```
<<<<<<< HEAD
// Esta é a versão da sua branch atual (feature/teste)
console.log('Mensagem da sua feature');
=======
 // Esta é a versão da branch dev
console.log('Mensagem da dev');
>>>>>>> dev

```

Note que o Git nos ajuda marcando o local que ocorreram as diferenças

Agora, você deve editar esse trecho para que o código final reflita o que realmente deve permanecer. Pode ser:

- A versão da sua feature
- A versão da dev
- Uma combinação das duas (mais comum)

Como exemplo:

```
console.log('Mensagem da dev com melhorias da feature');
```

**_Nota:_**
Depois de resolver todos os conflitos, remova os marcadores <<<<<<<, =======, >>>>>>>, salve o arquivo e faça o commit com as alterações concluídas:

```
git add nome-do-arquivo
git commit
```

**_IMPORTANTE_**: Sempre converse com outros membros da sua equipe que trabalhou na dev, isso definitivamente ajudará a resolver os conflitos da melhor forma possível

Ao resolver os conflitos e realizar o merge com sucesso, você deve enviar essas alterações para seu repositório remoto:

```
git push origin feature/teste
```

### 3.4 Criando o Pull Request

Com as alterações enviadas a sua branch remota com sucesso, você pode criar o Pull Request pelo site do Github, no seguinte sentido:

    main <- feature/teste

Etapas para criar um Pull Request:

1. Acesse o repositório no GitHub
2. Verifique se a sua branch foi enviada corretamente
3. Clique em “Compare & pull request”
4. Preencha as informações do PR
5. Envie o Pull Request

Com o Pull Request criado, basta esperar a aprovação pelo líder do seu time.
**_Importante_**: Nunca faça o merge do seu próprio PR sem aprovação.

_Nota:_ Após esse proce

### 3.5 Encerrando a branch

Após o seu Pull Request ser aprovado e feito o merge na branch dev, você pode deletar sua branch de feature. Isso é importante para manter o repositório limpo e organizado, evitando o acúmulo de branches antigas e já integradas.

- Deletando branch remota:

  Caso o merge do seu Pull Request já tenha sido realizado no GitHub, você poderá deletar a branch remota acessando a aba "Pull Requests", clicando em "Closed" e selecionando o PR correspondente à sua branch. Na página do PR, haverá um botão "Delete branch", clique nele para remover a branch do repositório remoto.

- Deletando branch localmente:

  Para excluir a branch local (após ter certeza de que o trabalho foi integrado corretamente):

  ```
  git branch -d feature/teste

  ```

Dessa forma, concluimos o passo-a-passo do fluxo completo de trabalho no repositório de desenvolvimento!
Em casos de dúvidas quanto a gerência do repositório, contate o líder da sua equipe ou um Arquiteto!
