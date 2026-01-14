# Домашняя работа: Инструменты GIT

## Выполнение
Репозиторий https://github.com/hashicorp/terraform был клонирован с помощью команды:

```bash
git clone https://github.com/hashicorp/terraform.git


## 1. Коммит с префиксом aefea

Команда:
```bash
git show -s --format="%H %s" aefea

root@github:/home/shiyanovmn/terraform# git show -s --format="%H %s" aefea
aefead2207ef7e2aa5dc81a34aedf0cad4c32545 Update CHANGELOG.md


## 2. Тег для коммита 85024d3

Команда:
```bash
git tag --points-at 85024d3

root@github:/home/shiyanovmn/terraform# git tag --points-at 85024d3
v0.12.23


## 3. Сколько родителей у коммита b8d720? Написать их хеши

Команда:
```bash
git show -s --format="parents: %P" b8d720

root@github:/home/shiyanovmn/terraform# git show -s --format="parents: %P" b8d720
parents: 56cd7859e05c36c06b56d013b55a252d0bb7e158 9ea88f22fc6269854151c571162c5bcf958bee2b


## 4. Коммиты между v0.12.23 и v0.12.24

Команда:
```bash
git log --format="%H %s" v0.12.23..v0.12.24


root@github:/home/shiyanovmn/terraform# git log --format="%H %s" v0.12.23..v0.12.24
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

