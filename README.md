# Modelo de git barnching do repositório

Este é um workflow de git muito simples. É uma variante de um modelo que já é utilizado por muitas pessoas.
É necessário seguir esse modelo para que possamos garantir que o deploy do projeto não terá erros e evitar possíveis falhas no projeto.

### O princípio

1. A branch `master` deve ser sempre o deploy.
1. **Todas as alterações** serão feitas por branchs temporárias (pull-request + merge)
1. rebase para evitar conflitos; merge na `master`

De uma forma bem simples:

master -> sua branch -> merge da sua branch + master

### O passo a passo

```bash
# Verificar se tudo está atualizado com a master
git checkout master
git pull origin master

# Crie sua branch para adicionar o post
git checkout -b minha-branch

# Agora você vai elaborar o seu arquivo MD.

# Commita seu arquivo na pasta content
git add -p
git commit -m "Meu post"

# Atualize para verificar se não ocorreu alguma mudança na master que possa ter conflito com sua branch.
# rebasing serve pra manter nosso código top, merge mais fácil e um histórico limpo.
git fetch origin
git rebase origin/minha-branch
git rebase origin/master

# faça o push da sua branch para revisão/discussão (pull-request)
#           Você pode fazer isso várias vezes durante o processo de desenvolvimento.
git push origin my-new-feature

### DOs and DON'Ts

Essas são regras vitais para o desenvolvimento do blog. Podemos ter exceções, mas essas são as regras principais

#### Faça

- mantenha o `master` em funcionamento.
- aprenda a rebase

#### Não faça

- **NÃO** faça merge com código que tenha bugs.
- **NÃO** commita diretamente no `master`.
- **NÃO** rebase `master`.
- **NÃO** faça merge com conflitos. Conflitos devem ser lidados durante o rebase.
