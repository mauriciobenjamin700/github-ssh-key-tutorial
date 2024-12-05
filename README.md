# Tutorial Simplificado para Configurar a Chave SSH no GitHub

## Passo 1

Abra o terminal e digite o seguinte comando para verificar se você já possui uma chave SSH:

```bash
ls -al ~/.ssh
```

Se você vir arquivos como id_rsa e id_rsa.pub, você já tem uma chave SSH. Caso contrário, prossiga para o próximo passo.

## Passo 2

Se você não tem uma chave SSH, gere uma nova com o comando:

```bash
ssh-keygen -t rsa -b 4096 -C "seu_email"
```

Substitua "seu_email" pelo seu email do GitHub. Quando solicitado, pressione Enter para aceitar o local padrão para salvar a chave.

A próxima pergunta é se você deseja definir uma senha para a chave de segurança, mas isso é opcional e fica a seu critério.

você irá visualizar algo semelhante a isto em caso de sucesso!

```bash
Your identification has been saved in /home/your_user/.ssh/id_rsa
Your public key has been saved in /home/your_user/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:imzSrzNnHFBCNYkcnIQx9k/vveSg9ATF7FbvOVdfh/0 seu email
The key's randomart image is:
+---[RSA 4096]----+
|  +B+=o.         |
| ..o* o+         |
|    .o. + .      |
|    .o + . .   o |
|     .o S   . . =|
|   o ..= . . . .=|
|  . =.o.+ o + . E|
|   000++ + . o   |
|    .*o . o      |
+----[SHA256]-----+
```

## Passo 3

Adicione a chave SSH ao agente SSH

Inicie o agente SSH:

```bash
eval "$(ssh-agent -s)"
```

Adicione a chave SSH ao agente

```bash
ssh-add ~/.ssh/id_rsa
```

## Passo 4

Adicione a chave SSH ao GitHub

Visualize o conteúdo da chave pública:

```bash
cat ~/.ssh/id_rsa.pub
```

Selecione e copie o conteúdo exibido

acesse o [github](https://github.com/settings/keys) e clique em adicionar nova chave

preencha o conteúdo com a nova chave e coloque o nome que desejar

## Passo 6

Teste se deu certo usando o comando:

```bash
ssh -T git@github.com
```

Você deve ver uma mensagem de sucesso indicando que a autenticação foi bem-sucedida.

Pronto! Agora você configurou sua chave SSH para o GitHub.

caso apareça um aviso

```bash
The authenticity of host 'github.com (20.201.28.151)' can't be established.
ED25519 key fingerprint is SHA256:+/aaaaaaaaa.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com' (ED25519) to the list of known hosts.
```

digite `yes` no terminal e pressione enter para validar a autenticação e estará tudo ok
