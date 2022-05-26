# Virtualização da Serra da Piedade

Este é um projeto desenvolvido pelo Compet para realizar a virtualização da serra da piedade, levando em consideração detalhes importantes como história, vegetação e arquitetura para que o modelo criado seja o mais representativo possível.

## Como colaborar

Para colaborar com este projeto utilizaremos o modelo de ramificação chamado ***gitflow***, que é um modelo alternativo de ramificação do Git que consiste no uso de ramificações de recursos e várias ramificações primárias.
> caso não esteja familiarizado com esse modelo, recomendo a [breve leitura deste artigo](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow).

Uma vez familiarizado com esse modelo de ramificação, colaborar é bem simples, e basta seguir este passo-a-passo.

1. Clone o projeto no seu repositório local usando o comando `git clone git@github.com:competdev/realidadevirtualserra.git`.

    > É necessário que você possua uma chave SSH no seu computador cadastrada na sua conta do github.

2. Certifique-se de que está no diretório `/realidadevirtualserra` e então digite o seguinte comando:

    `git flow init`
    >O comando responderá com um conjunto de perguntas,basta dar enter em todas elas por enquanto.

3. Para criar uma nova funcionalidade, basta utilizar o comando: `git flow feature start <nome_da_feature>`.

4. Uma vez que a feature foi finalizada  utilize o comando:

    `git flow feature publish <nome_da_feature>`.
    > Esse comando não finalizará a feature, apenas será publicada no github para ser avaliado.

    Uma vez que o código foi aprovado, a feature pode ser finalizada utilizando o comando:

     `git flow feature finish <nome_da_feature`.

## Adicionando novas atualizações (Releases) ao projeto

Ao serem adicionadas novas funcionalidades e/ou dado um tempo especificado o código desenvolvido no projeto deve ser testado, analisado e revisado para que possa ser atualizado, e o código em questão passará então a ser parte do ambiente de produção.

### O que são as versões do código

Você já deve ter visto em algum lugar tags com versões de programas, como 1.0.0, e o que cada número significa foge do contexto desse repositório, entretanto, você pode ler este [excelente artigo](https://semver.org/) sobre versionamento semântico.

### Como adicionar uma Release

Parecido com as features, as releases são adicionadas através do comando `git flow release start release_tag`, e esse comando irá fazer o seguinte procedimento:

1. Executa o comando `git checkout develop`

2. cria uma branch com o nome : "release/" + nome da release designada, e então faz o Head apontar para essa branch( `git checkout -b release/release_tag` ).

### O que adicionar na branch Release

Essa nova atualização irá adicionar todas as funcionalidades atuais que foram adicionadas a branch de desenvolvimento, portanto nenhum novo recurso pode ser adicionado depois deste ponto — apenas atualizações de segurança, geração de documentação e outras tarefas relacionadas ao lançamento da nova versão devem ser feitas nesta ramificação.

### Release finalizada, e agora?

Agora é hora de tornar essa nova versão parte do ambiente de produção. Entretanto vale ressaltar que a branch de desenvolvimento também deve ser atualizada, pois, novos recursos importantes podem ter sido adicionados na branch de desenvolvimento atual de forma que as novas funcionalidades que estão sendo desenvolvidas devem conter esses recursos. Para isso é necessário executar o comando : `git flow release finish release_tag`, que vai efetuar as seguintes ações :

1. Mudar o Head para a branch de produção ( `git checkout main`)

2. Efetuar o merge da branch da nova atualização para a branch de produção ( `git merge release/release_tag`).

3. Mudar o Head para a branch de desenvolvimento( `git checkout develop`).

4. Efetuar o merge da branch da nova atualização para a branch de desenvolvimento ( `git merge release/release_tag`).

5. Atualizar a tag do projeto ( `git tag -a prefix_tag1.4` )

6. Excluir a branch da Release criada ( `git branch -D release/release_tag`)

## Tecnologias utilizadas

Até o presente momento, nosso projeto está iniciando, e ainda deveremos decidir a game-engine que vamos utilizar, mas até o presente momento, devido a possibilidade de se fazer um projeto com qualidade profissional, estamos nos limitando a 3 engines:

* [Unreal](https://docs.unrealengine.com/5.0/en-US/)

* [Unity](https://unity.github.com/)

* [godot](https://github.com/godotengine/godot)

Além dessas três, a tecnologia utilizada para criação de um modelo protótipo da serra foi feita usando [Blender](https://github.com/blender/blender).
