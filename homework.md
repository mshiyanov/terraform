# Домашняя работа: Инструменты GIT

## Выполнение
Репозиторий https://github.com/hashicorp/terraform был клонирован с помощью команды:


git clone https://github.com/hashicorp/terraform.git


## 1. Коммит с префиксом aefea

Команда:

git show -s --format="%H %s" aefea

root@github:/home/shiyanovmn/terraform# git show -s --format="%H %s" aefea
aefead2207ef7e2aa5dc81a34aedf0cad4c32545 Update CHANGELOG.md


## 2. Тег для коммита 85024d3

Команда:

git tag --points-at 85024d3

root@github:/home/shiyanovmn/terraform# git tag --points-at 85024d3
v0.12.23


## 3. Сколько родителей у коммита b8d720? Написать их хеши

Команда:

git show -s --format="parents: %P" b8d720

root@github:/home/shiyanovmn/terraform# git show -s --format="parents: %P" b8d720
parents: 56cd7859e05c36c06b56d013b55a252d0bb7e158 9ea88f22fc6269854151c571162c5bcf958bee2b



## 4. Коммиты между v0.12.23 и v0.12.24

Команда:
```bash
git log --format="%H %s" v0.12.23..v0.12.24

33ff1c03bb960b332be3af2e333462dde88b279e v0.12.24
b14b74c4939dcab573326f4e3ee2a62e23e12f89 [Website] vmc provider links
3f235065b9347a758efadc92295b540ee0a5e26e Update CHANGELOG.md
6ae64e247b332925b872447e9ce869657281c2bf registry: Fix panic when server is unreachable
5c619ca1baf2e21a155fcdb4c264cc9e24a2a353 website: Remove links to the getting started guide's old location
06275647e2b53d97d4f0a19a0fec11f6d69820b5 Update CHANGELOG.md
d5f9411f5108260320064349b757f55c09bc4b80 command: Fix bug when using terraform login on Windows
4b6d06cc5dcb78af637bbb19c198faff37a066ed Update CHANGELOG.md
dd01a35078f040ca984cdd349f18d0b67e486c35 Update CHANGELOG.md
225466bc3e5f35baa5d07197bbc079345b77525e Cleanup after v0.12.23 release
```

## 5. Найдите коммит, в котором была создана функция func providerSource

Для поиска коммита, в котором была создана функция `providerSource`,
использовалась команда:

Команда:
```bash
git log -S "func providerSource" --oneline --reverse

git log -S "func providerSource" --oneline --reverse
8c928e8358 main: Consult local directories as potential mirrors of providers
5af1e6234a main: Honor explicit provider_installation CLI config when present
```

Далее я посмотрел git show 8c928e8358 и убедился, что в выводе есть:

diff --git a/provider_source.go b/provider_source.go
new file mode 100644


##6. Коммиты, где менялась globalPluginDirs

Команда:

git log -S "globalPluginDirs" --oneline

root@github:/home/shiyanovmn/terraform# git log -S "globalPluginDirs" --oneline
7c4aeac5f3 stacks: load credentials from config file on startup (#35952)
65c4ba7363 Remove terraform binary
125eb51dc4 Remove accidentally-committed binary
22c121df86 Bump compatibility version to 1.3.0 for terraform core release (#30988)
7c7e5d8f0a Don't show data while input if sensitive
35a058fb3d main: configure credentials from the CLI config file
c0b1761096 prevent log output during init
8364383c35 Push plugin discovery down into command package

Посмотрел один из коммитов:

Команда:
git show 8364383c35

В нем нашел подтверждение:

diff --git a/plugins.go b/plugins.go
new file mode 100644

func globalPluginDirs() []string {

## 7. Кто автор функции synchronizedWriters

В текущей версии репозитория определение функции не найдено:

Команда:

root@github:/home/shiyanovmn/terraform# git grep -n "func synchronizedWriters"
root@github:/home/shiyanovmn/terraform#
root@github:/home/shiyanovmn/terraform#
root@github:/home/shiyanovmn/terraform# git grep -n "synchronizedWriters"
root@github:/home/shiyanovmn/terraform# git grep -n "synchronizedWriter"
root@github:/home/shiyanovmn/terraform# git grep -n "SynchronizedWriters"

Поэтому был выполнен поиск по истории репозитория:

Команда:

git log -G "func synchronizedWriters" --oneline --reverse

root@github:/home/shiyanovmn/terraform# git log -G "func synchronizedWriters" --oneline --reverse
5ac311e2a9 main: synchronize writes to VT100-faker on Windows
bdfea50cc8 remove unused

Команда показала, что функция была добавлена в коммите:

5ac311e2a9 — main: synchronize writes to VT100-faker on Windows

Автор функции был получен из информации о коммите:

Команда:

git show -s --format="%an <%ae>" 5ac311e2a9

root@github:/home/shiyanovmn/terraform# git show -s --format="%an <%ae>" 5ac311e2a9
Martin Atkins <mart@degeneration.co.uk>
