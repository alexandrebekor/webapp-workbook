# Problema
Um arquivo grande havia ficado na memória remota do github impossibilitando que um novo código fosse salvo no repositório e também que o arquivo fosse deletado diretamente no repositório virtual.

```
alexandrebekor@Bekor-2:~/Github/webapp-satisfaction-survey$ git push
Enumerating objects: 308, done.
Counting objects: 100% (308/308), done.
Delta compression using up to 4 threads
Compressing objects: 100% (192/192), done.
Writing objects: 100% (308/308), 21.23 MiB | 859.00 KiB/s, done.
Total 308 (delta 154), reused 171 (delta 94)
remote: Resolving deltas: 100% (154/154), done.
remote: error: Trace: 574dfe435e3500f1deb238041c8a3e5ce51ddacd1c49675247521fdd11f6abbe
remote: error: See http://git.io/iEPt8g for more information.
remote: error: File .next/cache/webpack/client-development/0.pack is 105.65 MB; this exceeds GitHub's file size limit of 100.00 MB
remote: error: GH001: Large files detected. You may want to try Git Large File Storage - https://git-lfs.github.com.
To https://github.com/alexandrebekor/webapp-satisfaction-survey.git
 ! [remote rejected] main -> main (pre-receive hook declined)
error: failed to push some refs to 'https://github.com/alexandrebekor/webapp-satisfaction-survey.git'
```
Para resolver:
```
git filter-branch --tree-filter 'rm -rf .next/' HEAD
git push
```

Caso você tenha mais de um commit que precisa ser deletado adicione o `-f`:
```
git filter-branch -f --tree-filter 'rm -rf diretorio/' HEAD
```