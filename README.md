---
marp: true

---

# Cоздание нового репозитория

Для того чтобы создать новый репозиторий git, необходимо выполнить команду

```
git init
```

---

# Получение репозитория

Создать локальную рабочую копию репозитория 
```
git clone git://url
```

Ваш локальный git репозиторий состоит из трех частей:

- Рабочий каталог (Working Directory) содержит файлы. 
- Область подготовленных файлов (Staging Area), содержит информацию о том, что войдет следующий коммит 
- HEAD указывает на последний коммит что вы сделали.

Можно подключить существующий локальный репозиторий, не клонируя удаленный
```
git remote add origin git://url
```

Теперь вы можете отправлять изменения на удаленный репозиторий

---

# Подготовка к коммиту

Чтобы подготовить изменения (добавить их в Индекс), используйте
```
git add file
git add *
```

Сделать коммит подготовленных изменений можно командой
```
git commit -m "cсообщение"
```

Теперь изменения закреплены в **локальном репозитории**, и на них указывает HEAD

---

# Отправка изменений

Чтобы отправить эти изменения в origin репозиторий, выполните
```
git push origin main
```

---
# Бранчи (ветки)

Бранчи используются для изолированной разработки. 
Ветка main используется по умолчанию, когда вы создаете репозиторий.

Создать новую ветку с названием "feature/new-code" и переключиться на неё можно командой
```
git checkout -b feature/new-code
```
переключиться обратно на main
```
git checkout main
```
удалить ветку локально
```
git branch -d feature/new-code
```
ветка не будет доступна в удаленном репозитории, пока вы не отправите её туда
```
git push origin feature/new-code
```
---

# Обновление и слияние

Обновить ваш локальный репозиторий из удаленного можно командой
```
git fetch (pull)
```
fetch заберет изменения из удаленного репозитория , pull заодно проведет слияние с активной веткой.

Для того чтобы слить другую ветку с активной (например main), используйте команду
```
git merge main
```
В обоих случаях git пытается автоматически слить изменения, это не всегда возможно и результатом может стать конфликт. 
Вы ответственны за разрешение возникших конфликтов, путем ручного редактирования файлов, указанных git. После изменений вам нужно добавить файлы
```
git add file
```
перед слиянием вы можете предварительно посмотреть на изменения

```
git diff main feature/new-code
```

---
# Тэги (метки)

Рекомендуется использовать метки для закрепления момента выпуска версий. Создать новый тэг 1.0.0 можно, выполнив
```
git tag 1.0.0 beef1
```
beef1 это первые цифры уникального идентификатора коммита, с которым будет связана метка. Чтобы посмотреть идентификаторы коммитов, выполните

```
git log
```

---

# Замена локальных изменений

В случае, если вы все сломали, вы можете заменить локальные изменения, используя команду
```
git checkout -- file
```
произойдет замена изменений в вашем рабочем каталоге, на то, что сейчас находится в HEAD. Новые файлы будут сохранены.

Если же вы хотите удалить все ваши локальные изменения и коммиты, получите (fetch) последние изменения с сервера и сделайте reset
```
git fetch origin
git reset --hard origin/main
```

