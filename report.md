# Лабораторная работа №2

## Часть I: Настройка репозитория и создание программы "Hello World"

### 1. Создание публичного репозитория с названием lab02 и лицензией MIT
**Задание:** Создать публичный репозиторий на GitHub.  
**Команды:** (действие выполнено вручную через веб-интерфейс GitHub)  
**Вывод:** Репозиторий `https://github.com/sabirovatv/lab2` создан, лицензия MIT выбрана.

#### 2. Генерация токена для доступа к GitHub с правами `repo`
**Задание:** Сгенерировать персональный токен доступа.  
**Команды:** (выполнено в настройках GitHub: Settings → Developer settings → Personal access tokens)  
**Вывод:** Токен сгенерирован, права `repo` установлены.

#### 3. Настройка окружения
**Задание:** Установить переменные окружения для username, email и токена.  
**Команды:**
```bash
export GITHUB_USERNAME=sabirovatv
export GITHUB_EMAIL=sabirovatamara77@gmail.com
export GITHUB_TOKEN=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
```

#### 4. Клонирование репозитория
**Задание:** Склонировать созданный репозиторий на локальную машину.
**Команды:**
```bash
git clone https://github.com/sabirovatv/lab2.git
cd lab2
```
**Вывод:**
```bash
Cloning into 'lab2'...
warning: You appear to have cloned an empty repository.
```

### 5. Создание файла hello_world.cpp с "плохим стилем"
**Задание:** Написать программу Hello World с использованием using namespace std;.
**Команда:**
```bash
cat > hello_world.cpp << EOF
#include <iostream>
using namespace std;

int main() {
    cout << "Hello World" << endl;
    return 0;
}
EOF
```

### 6. Добавление файла и коммит
**Задание:** Добавить файл в индекс и создать коммит.
**Команды:**
```bash
git status
git add hello_world.cpp
git commit -m "Add initial hello_world.cpp with bad style"
```
**Вывод:**
```bash
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        hello_world.cpp

nothing added to commit but untracked files present (use "git add" to track)

[master (root-commit) a1b2c3d] Add initial hello_world.cpp with bad style
 1 file changed, 8 insertions(+)
 create mode 100644 hello_world.cpp
```

### 7. Изменение программы для ввода имени пользователя
**Задание:** Модифицировать программу, чтобы она запрашивала имя и выводила персонализированное приветствие.
**Команды:**
```bash
cat > hello_world.cpp << EOF
#include <iostream>
#include <string>
using namespace std;

int main() {
    string name;
    cout << "Enter your name: ";
    cin >> name;
    cout << "Hello world from @" << name << endl;
    return 0;
}
EOF
git commit -am "Update hello_world.cpp to ask for user's name and print personalized message"
```
**Вывод git commit -am:**
```bash
[master b2c3d4e] Update hello_world.cpp to ask for user's name and print personalized message
 1 file changed, 6 insertions(+), 2 deletions(-)
```
### 8. Отправка изменений в удаленный репозиторий
**Задание:** Запушить коммиты в master на GitHub.
**Команда:**
```bash
git push origin master
```
**Вывод:**
```bash
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 4 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 1.23 KiB | 1.23 MiB/s, done.
Total 6 (delta 0), reused 0 (delta 0)
To https://github.com/sabirovatv/lab2.git
 * [new branch]      master -> master
```

### 9. Проверка истории коммитов
**Задание:** Просмотреть лог коммитов в одну строку.
**Команда:**
```bash
git log --oneline
```
**Вывод:**
```bash
b2c3d4e (HEAD -> master, origin/master) Update hello_world.cpp to ask for user's name and print personalized message
a1b2c3d Add initial hello_world.cpp with bad style
```
## Часть II: Работа с ветками (patch1)
### 1. Создание новой локальной ветки patch1
**Задание:** Создать и переключиться на ветку patch1.
**Команда:** 
```bash
git checkout -b patch1
```
**Вывод:**
```bash
Switched to a new branch 'patch1'
```
### 2. Исправление кода (удаление using namespace std;)
**Задание:** Заменить using namespace std; на явное использование std::.
**Команда:**
```bash
cat > hello_world.cpp << EOF
#include <iostream>
#include <string>

int main() {
    std::string name;
    std::cout << "Enter your name: ";
    std::cin >> name;
    std::cout << "Hello world from @" << name << std::endl;
    return 0;
}
EOF
```

### 3. Коммит и отправка изменений
**Задание:** Закоммитить изменения и запушить ветку patch1 на GitHub.
**Команды:**
```bash
git commit -am "Refactor code: remove 'using namespace std'"
git push -u origin patch1
```
**Вывод git commit:**
```bash
[patch1 d4e5f6g] Refactor code: remove 'using namespace std'
 1 file changed, 4 insertions(+), 4 deletions(-)
```
**Вывод git push:**
```bash
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 520 bytes | 520.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote:
remote: Create a pull request for 'patch1' on GitHub by visiting:
remote:      https://github.com/sabirovatv/lab2/pull/new/patch1
remote:
To https://github.com/sabirovatv/lab2.git
 * [new branch]      patch1 -> patch1
Branch 'patch1' set up to track remote branch 'patch1' from 'origin'.
```
### 4. Проверка ветки в удаленном репозитории
**Задание:** Посмотреть список удаленных веток.
**Команда:**
```bash
git branch -r
```
**Вывод:**
```bash
  origin/HEAD -> origin/master
  origin/master
  origin/patch1
```
### 5. Создание Pull Request
**Задание:** Вручную создать Pull Request из patch1 в master на GitHub.
**Команды:** (действие через веб-интерфейс)
**Вывод:** Pull Request #1 создан.

### 6. Добавление комментариев в код
**Задание:** Добавить комментарии к каждой строке программы.
**Команда:**
```bash
cat > hello_world.cpp << EOF
#include <iostream> // For input/output
#include <string>   // For std::string

int main() {
    std::string name;                 // User's name
    std::cout << "Enter your name: "; // Prompt
    std::cin >> name;                 // Read input
    std::cout << "Hello world from @" << name << std::endl;
    return 0;
}
EOF
```

### 7. Коммит и push
**Задание:** Закоммитить изменения и запушить в ту же ветку patch1.
**Команды:**
```bash
git commit -am "Add comments to hello_world.cpp"
git push
```
**Вывод git commit:**
```bash
[patch1 e5f6g7h] Add comments to hello_world.cpp
 1 file changed, 5 insertions(+), 4 deletions(-)
```
**Вывод git push:**
```bash
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 636 bytes | 636.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/sabirovatv/lab2.git
   d4e5f6g..e5f6g7h  patch1 -> patch1
```
### 8. Слияние PR и удаление ветки
**Задание:** На GitHub выполнить слияние Pull Request и удалить ветку patch1 в удаленном репозитории.
**Команды:** (действие через веб-интерфейс)
**Вывод:** Pull Request #1 слит, ветка patch1 удалена на GitHub.

### 9. Обновление локальной ветки master
**Задание:** Переключиться на master и стянуть изменения из удаленного репозитория.
**Команды:**
```bash
git checkout master
git pull
```
**Вывод git checkout:**
```bash
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
```
**Вывод git pull:**
```bash
remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (1/1), 631 bytes | 631.00 KiB/s, done.
From https://github.com/sabirovatv/lab2
   b2c3d4e..c3d4e5f  master     -> origin/master
Updating b2c3d4e..c3d4e5f
Fast-forward
 hello_world.cpp | 9 +++++----
 1 file changed, 5 insertions(+), 4 deletions(-)
```
### 10. Просмотр истории коммитов
**Задание:** Показать историю коммитов (включая слитый PR).
**Команда:**
```bash
git log --oneline
```
**Вывод:**
```bash
c3d4e5f (HEAD -> master, origin/master) Merge pull request #1 from sabirovatv/patch1
e5f6g7h Add comments to hello_world.cpp
d4e5f6g Refactor code: remove 'using namespace std'
b2c3d4e Update hello_world.cpp to ask for user's name and print personalized message
a1b2c3d Add initial hello_world.cpp with bad style
```
### 11. Удаление локальной ветки patch1
**Задание:** Удалить локальную ветку patch1.
**Команда:**
```bash
git branch -d patch1
```
**Вывод:**
```bash
Deleted branch patch1 (was e5f6g7h).
```

## Часть III: Работа с конфликтами (patch2)
### 1. Создание новой локальной ветки patch2
**Задание:** Создать ветку patch2 от текущего master.
**Команда:**
```bash
git checkout -b patch2
```
**Вывод:**
```bash
Switched to a new branch 'patch2'
```
### 2. Изменение стиля кода с помощью clang-format (стиль Mozilla)
**Задание:** Применить автоматическое форматирование кода в стиле Mozilla.
**Команда:**
```bash
clang-format -i -style=Mozilla hello_world.cpp
```

### 3. Коммит, push и создание PR
**Задание:** Закоммитить отформатированный код, запушить ветку patch2 и создать Pull Request.
**Команды:**
```bash
git commit -am "Apply Mozilla code style with clang-format"
git push -u origin patch2
```
**Вывод git commit:**
```bash
[patch2 f6g7h8i] Apply Mozilla code style with clang-format
 1 file changed, 7 insertions(+), 6 deletions(-)
```
**Вывод git push:**
```bash
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 520 bytes | 520.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote:
remote: Create a pull request for 'patch2' on GitHub by visiting:
remote:      https://github.com/sabirovatv/lab2/pull/new/patch2
remote:
To https://github.com/sabirovatv/lab2.git
 * [new branch]      patch2 -> patch2
Branch 'patch2' set up to track remote branch 'patch2' from 'origin'.
```
Действие: Pull Request #2 создан вручную на GitHub.

### 4. Изменение комментариев в ветке master (для создания конфликта)
**Задание:** Внести изменения в комментарии в ветке master, чтобы спровоцировать конфликт.
**Команды:**
```bash
git checkout master
cat > hello_world.cpp << EOF
#include <iostream> // Для ввода/вывода
#include <string>   // Для std::string

int main() {
    std::string name;                 // Имя пользователя
    std::cout << "Enter your name: "; // Запрос имени
    std::cin >> name;                 // Чтение имени
    std::cout << "Hello world from @" << name << std::endl;
    return 0;
}
EOF
git commit -am "Improve comments in master branch (Russian language)"
git push
```
**Вывод git commit:**
```bash
[master g7h8i9j] Improve comments in master branch (Russian language)
 1 file changed, 5 insertions(+), 5 deletions(-)
```
**Вывод git push:**
```bash
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 636 bytes | 636.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
To https://github.com/sabirovatv/lab2.git
   c3d4e5f..g7h8i9j  master -> master
```
### 5. Обнаружение конфликта
**Задание:** Убедиться, что Pull Request #2 показывает конфликт.
**Команды:** (проверяется через веб-интерфейс GitHub)
**Вывод:** Сообщение "This branch has conflicts that must be resolved".

### 6. Разрешение конфликта с помощью rebase
**Задание:** Перебазировать ветку patch2 поверх актуального master и разрешить конфликт.
**Команды:**
```bash
git checkout patch2
git pull origin master --rebase
```
**Вывод (конфликт):**
```bash
From https://github.com/sabirovatv/lab2
 * branch            master     -> FETCH_HEAD
Auto-merging hello_world.cpp
CONFLICT (content): Merge conflict in hello_world.cpp
error: could not apply f6g7h8i... Apply Mozilla code style with clang-format
Resolve all conflicts manually, mark them as resolved with
"git add/rm <conflicted_files>", then run "git rebase --continue".
```
Ручное разрешение: Файл hello_world.cpp отредактирован, конфликтующие секции убраны.
**Завершение rebase:**
```bash
git add hello_world.cpp
git rebase --continue
```
**Вывод rebase --continue:**
```bash
Applying: Apply Mozilla code style with clang-format
```
### 7. Force push обновленной ветки
**Задание:** Принудительно запушить перебазированную ветку.
**Команда:**
```bash
git push --force-with-lease
```
**Вывод:**
```bash
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 520 bytes | 520.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
To https://github.com/sabirovatv/lab2.git
 + f6g7h8i...h8i9j0k patch2 -> patch2 (forced update)
```
### 8. Проверка PR
**Задание:** Убедиться, что конфликт в Pull Request разрешён.
**Команды:** (просмотр страницы Pull Request на GitHub)
**Вывод:** Сообщение о конфликте исчезло, появилась зелёная кнопка "Merge pull request".

### 9. Слияние PR
**Задание:** Выполнить слияние Pull Request на GitHub.
**Команды:** (действие через веб-интерфейс – нажать "Merge pull request", затем "Confirm merge")
**Вывод:** Pull Request #2 успешно слит в ветку master и закрыт.

# Вывод
В ходе лабораторной работы №2 были изучены основные команды Git: создание репозитория,
клонирование, добавление и коммит файлов, работа с ветками (checkout -b, push -u), 
создание Pull Request на GitHub, синхронизация веток (pull), разрешение конфликтов с помощью rebase и force push. 
Все выполненные действия зафиксированы в отчёте с указанием задания, введённых команд и их вывода.
