# Визуализатор зависимостей

![График](https://i.imgur.com/rXSSrRX.png)

**Визуализатор зависимостей** — это инструмент на Python, который помогает визуализировать дерево зависимостей для пакета NPM. Он извлекает зависимости последней версии и генерирует граф, который можно экспортировать в различные форматы (например, PNG, JPG). Проект предназначен для анализа зависимостей пакетов до заданной глубины и вывода графического представления этих связей.

## Функции

- Извлекает последние зависимости для указанного NPM пакета.
- Позволяет настроить глубину для исследования зависимостей.
- Генерирует и визуализирует граф зависимостей с использованием Graphviz и NetworkX.
- Выводит граф в различных форматах (например, PNG, JPG).
- Сохраняет граф как файл Graphviz (.dot) и генерирует изображение.

## Установка

1. Скачайте или клонируйте репозиторий:

   ```bash
   git clone hhttps://github.com/snaping1/config_2.git
   ```

2. Установите необходимые зависимости:

   ```bash
   pip install -r requirements.txt
   ```

   Убедитесь, что у вас установлен Graphviz и добавлен в системный путь (если вы используете его для генерации изображений).

3. Установите Graphviz:

   - Для **Ubuntu/Debian**:

     ```bash
     sudo apt-get install graphviz
     ```

   - Для **macOS**:

     ```bash
     brew install graphviz
     ```

   - Для **Windows**:

     Скачайте и установите Graphviz с [официального сайта](https://graphviz.gitlab.io/download/), добавив его в системный путь.

## Использование

### 1. Подготовьте конфигурационный файл

Конфигурационный файл (например, `config.xml`) должен содержать следующие параметры:

```xml
<config>
    <graphviz_path>/path/to/graphviz</graphviz_path>
    <package_name>your-package-name</package_name>
    <max_depth>3</max_depth>
    <output>
        <file_name>dependency_graph</file_name>
        <format>png</format>
    </output>
</config>
```

### 2. Запустите скрипт

Используйте команду ниже, чтобы запустить скрипт, передав путь к конфигурационному файлу:

```bash
python visualize_dependencies.py config.xml
```

### 3. Результаты

- Граф зависимостей будет сохранен в формате `.dot` и изображение (например, `.png`), в зависимости от настроек в конфигурации.
- Пример выходных файлов:
  - `dependency_graph.dot`
  - `dependency_graph.png`

## Параметры конфигурации

- **graphviz_path**: Путь к установке Graphviz на вашем компьютере.
- **package_name**: Имя NPM пакета для анализа.
- **max_depth**: Максимальная глубина для поиска зависимостей.
- **output**: Настройки вывода графа:
  - **file_name**: Имя файла для сохранения.
  - **format**: Формат выходного изображения (например, `png`, `jpg`).

## Пример работы

1. Укажите NPM пакет (например, `express`).
2. Установите максимальную глубину поиска зависимостей (например, `3`).
3. Получите граф зависимостей в указанном формате (например, PNG).

## Тестирования

Проект включает в себя набор тестов, использующих библиотеку `unittest` для проверки различных функций. Тесты покрывают следующие аспекты:

- Загрузка конфигурации из XML файла.
- Извлечение зависимостей для указанного пакета с использованием NPM API.
- Визуализация графа зависимостей с использованием Graphviz.

Для тестирования мокаются внешние зависимости, такие как запросы к API и визуализация графов. Для запуска тестов выполните следующую команду:

```bash
pytest .
```

![Тесты](https://i.imgur.com/CpA2Q9S.png)
