## Gerar a chave pública do SSH

## Acessar o terminal e execute

ssh-keygen -t rsa -b 4096 -C "ribafs@gmail.com"

Enter 3 vezes

## Mostrar chave

cat ~/.ssh/id_rsa.pub

## Copiar e colar na textarea Key no GitHub

E clicar em Add SSH Key

Enviar Conteúdo via Git

Enviar do desktop via git para o repositório no GitHub.

cd /var/www/html
```php                            
git config --global user.email "ribafs@gmail.com"
git init
git add .
git commit -m "Commit da primeira versão"
git remote add origin git@github.com:ribafs/ribafs.github.io.git
git push -f origin master
```
Para enviar novamente após alterações ou falhas remover a pasta .git e repetir os passos acima

IMPORTANTE: se precisar usar sudo no comandos lembre de não usar no último:

git push -f origin master
