# Как разместить свой проект на сервере glitch.com
## Теперь уже никак, хотя раньше было так:

1. Зарегистрируйтесь на Glitch (https://glitch.com/). 
2. Переименуйте основной запускаемый файл вашего проекта и назовите его "server.py"
3. В корне проекта создайте файл ".gitignore"со следующим содержимым:
.idea
venv
4. Создайте файл "requirements.txt" со списком библиотек, которые необходимы для вашего приложения.
5. В корне проекта создайте файл "start.sh"со следующим содержимым:
```
#!/bin/bash

# Exit early on errors
set -eu

# Python buffers stdout. Without this, you won't see what you "print" in the Activity Logs
export PYTHONUNBUFFERED=true

# Install Python 3 virtual env
VIRTUALENV=./venv

if [ ! -d $VIRTUALENV ]; then
  python3 -m venv $VIRTUALENV
fi

# Install pip into virtual environment
if [ ! -f $VIRTUALENV/bin/pip ]; then
  curl --silent --show-error --retry 5 #!/bin/bash

# Exit early on errors
set -eu

# Python buffers stdout. Without this, you won't see what you "print" in the Activity Logs
export PYTHONUNBUFFERED=true

# Install Python 3 virtual env
VIRTUALENV=./venv

if [ ! -d $VIRTUALENV ]; then
  python3 -m venv $VIRTUALENV
fi

# Install pip into virtual environment
if [ ! -f $VIRTUALENV/bin/pip ]; then
  curl --silent --show-error --retry 5 https://bootstrap.pypa.io/pip/3.7/get-pip.py | $VIRTUALENV/bin/python
fi

# Install the requirements
$VIRTUALENV/bin/pip install -r requirements.txt

# Run your glorious application
$VIRTUALENV/bin/python3 server.py | $VIRTUALENV/bin/python
fi

# Install the requirements
$VIRTUALENV/bin/pip install -r requirements.txt

# Run your glorious application
$VIRTUALENV/bin/python3 server.py
```

6. Создайте git репозиторий и разместите его на github. Репозиторий должен быть публичным.
7. На верхней панели справа нажмите на кнопку "New project", затем надо выбрать "Import from Github", в появившееся диалоговое окно вставьте полный путь до вашего репозитирия с приложением.

После этого все файлы вашего приложения будут загружены на сервер Glitch, будет запущен скрипт start.sh, и примерно через 3-5 минут ваше приложение будет работать. Об этом будет свидетельствовать смайлик на панели внизу экрана рядом с надписью Status.

8. В этой же панели нажмите на кнопку Preview далее Preview in new window, и у ваше приложение откроется в новом окне.
