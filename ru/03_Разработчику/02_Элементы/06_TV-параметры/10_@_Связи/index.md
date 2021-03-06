Зв'язки потрібні для заповнення значення ТВ-параметра якимись наперед зумовленими даними.

`Приклад: вам необхідно в ТВ-параметрі передбачити вибір id ресурса з дерева документів.`

Джерело данних для ТВ може бути з будь-якого з наступних джерел:

* зовнішній файл, який вирушає через FTP на сервер
* таблиця бази данних, доступна Evolution
* документ в дереві документів
* чанк
* результат виконуваного скрипта PHP

Ці джерела данних можуть бути прив'язані до ТВ для форматування і відображення в документі. 

Крім того, отримані таким чином данні легко відформатувати за допомогою налаштування "Тип введення". Скажімо, для списку підійде тип введення "DropDown List Menu" або ж будь-який з типів "Listbox" - в залежності від ваших потреб.

Формат використання наступний:
```
@FILE file_path
@DOCUMENT document_id
@CHUNK chunk_name
@SELECT sql_query
@EVAL php_code
@DIRECTORY _path_to_folder
```
**@-зв'зки будуть працювати за використанням всередині полів «Можливі значення» або «Значення заумовчання» в налаштуваннях ТВ-параметра.**

Значення, що повертається з джерела даних може бути або строковим (включаючи числа, дати і т.д.), або масивом або набором записів. 

Значення, що повертається залежить від використовуваного типу прив'язки. Деякі елементи управління відображенням намагатимуться перетворити значення, що повертається в рядок або масив.

Наприклад, елементи управління, які приймають строкові значення, такі як група перемикачів або список вибору, будуть намагатися перетворити набір записів (рядки і стовпці) в наступний формат:
```
col1row1Value==col2row1Value||col1row2Value==col2row2Value,…
```

При розміщенні @-зв'язків всередині поля «Можливі значення» вони використовуються для форматування тільки при редагуванні документа в интерфейсі адміністратора, наприклад, для створення розкривного списку міст або країн.

При розміщенні @-зв'язків в середині поля «Значення за замовчуванням» повернене значення використовується для рендеринга на веб-сторінку.
Це дає дозвіл швидко створювати важкі форми для введення данних.
