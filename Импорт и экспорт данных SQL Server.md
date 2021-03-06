#  Импорт данных из Excel документа в MSSQL
## Создаем тестовые данные в документе Excel

Данные будут вот такие, файл я назвал test_file.xls:
| number | field1       | field2       |
|--------|--------------|--------------|
| 1      | line1 field1 | line1 field2 |
| 2      | line2 field1 | line2 field2 |
| 3      | line3 field1 | line3 field2 |

В данном примере мы будем импортировать данные в новую таблицу, 
поэтому на название полей мы не обращаем внимания. 
Но если бы мы импортировали бы уже в существующую таблицу, 
то нам в процессе импорта пришлось бы задавать соответствие этих полей
или изначально в файле создать столько полей с тем же названием 
и в той же последовательности, как и в таблице. 
А если этого не сделать, то те поля, которые отсутствуют в таблице в базе, будут со значением null.
Как задать соответствие этих полей и как импортировать данные в уже существующую таблицу будет показано 
в процессе импорта.

***Примечание! Сервер располагается локально, база данных называется test.***

### Шаг 1
Итак, приступим, у нас есть файл, теперь запускаем средство импорта, и у нас открывается следующее окно:

![image](https://user-images.githubusercontent.com/45891293/162893287-ae51f03a-bf70-4d8a-8a6f-944ba9220ee6.png)

### Шаг 2
Нажимаем далее, где нам предлагают выбрать источник данных, в нашем случае это Excel, 
мы выбираем файл, версию excel и ставим галочку, что первая строка — это заголовок:

![image](https://user-images.githubusercontent.com/45891293/162893337-8fbed89e-a97d-4f7c-9503-83fe07a15173.png)

### Шаг 3
Жмем далее, нам предлагают выбрать назначение, куда копировать эти данные, 
мы выбираем SQL Server, указываем имя сервера, 
т.е. его адрес, в нашем случае, расположен локально. 
Также не забудьте про проверку подлинности, выбирайте тот метод, который у Вас настроен на сервере, 
и, конечно же, про базу данных, в которую копировать:

![image](https://user-images.githubusercontent.com/45891293/162893396-0d73131b-f668-4f52-ad45-89ceba591752.png)

### Шаг 4
Снова жмем далее, где мы укажем все ли данные копировать, в нашем случае мы говорим что все:

![image](https://user-images.githubusercontent.com/45891293/162893472-c1db94d0-264a-48ab-8d92-a77f660d72ee.png)

### Шаг 5
Жмем далее, и попадаем на окно выбора листа с данными и задания названия таблицы в нашей базе, 
выбираем лист 1 и называем таблицу test_table:

![image](https://user-images.githubusercontent.com/45891293/162893614-aa5f6f64-ff85-4e91-bb4d-56bcc6b6e153.png)

И, кстати, на этом этапе можно задать соответствие полей. 
В случае если Вы импортируете данные в существующую таблицу, 
для соответствия полей Вам необходимо выбрать таблицу из выпадающего списка и нажать изменить, 
где Вы также можете задать такие параметры как назначение, тип данных и другие, 
для примера вот это окно:

![image](https://user-images.githubusercontent.com/45891293/162893715-312e5e49-96d8-4cac-bf0a-5c3deed3f68e.png)

### Шаг 6
Это было небольшое отступление, а в нашем примере мы жмем далее, и попадаем в окно, 
в котором можно сохранить все наше действия в пакет, но мы этого делать не будем, 
а сразу же нажмем готово:

![image](https://user-images.githubusercontent.com/45891293/162894041-44b072ef-93f6-4c4c-93f1-329a5c18c077.png)

### Шаг 7
После появится окно, где мы все проверяем и жмем готово:

![image](https://user-images.githubusercontent.com/45891293/162894118-fb0647a2-fff8-42da-b3f9-8b00a2e826d3.png)

### Шаг 8
И в заключение у нас появится еще одно окно - результат наших действий, жмем закрыть:

![image](https://user-images.githubusercontent.com/45891293/162894183-de9f7fa4-0272-4a6f-ae1b-93a85c70a5dc.png)

Как видно, передано 3 строки, т.е. импортировано — это означает, что все наши данные, 
которые были в файле, импортировались.

## Экспорт данных из Microsoft SQL Server в файл Excel

А теперь давайте рассмотрим пример экспорта данных 
из нашей только что созданной таблицы в Excel документ.

### Шаг 1
Для этого делаем практически то же самое, открываем средство экспорта, 
но уже здесь в качестве источника указываем нашу базу:

![image](https://user-images.githubusercontent.com/45891293/162894868-6e6c89b8-b893-4294-b4b7-04ce7ab35e67.png)

### Шаг 2
Жмем далее, где нам предлагают указать назначение экспорта, 
мы соответственно выбираем Excel, и задаем путь и название выгружаемого файла:

![image](https://user-images.githubusercontent.com/45891293/162894879-5cd0b206-00f2-4bd0-aa1c-51642a69f434.png)

### Шаг 3
После того как Вы нажмете далее, Вы попадете в окно выбора данных, 
т.е. какие именно данные мы будем выгружать, 
и здесь давайте укажем — выгружать данные на основе запроса. 
Так как, когда мы импортировали данные, мы выбрали все, а теперь для примера выберем не все,
а на основе запроса, можно также выбрать все и указать таблицу или представление VIEWS, 
в котором уже будут отфильтрованные данные, но мы напишем SQL запрос:

![image](https://user-images.githubusercontent.com/45891293/162894892-8df6d489-0b5c-4b71-aa91-84c4691b0371.png)

### Шаг 4
И в следующем окне вставляем свой запрос, например, вот такой:

![image](https://user-images.githubusercontent.com/45891293/162894913-7288e0cb-f47e-4249-b1b1-566c89424c59.png)

Также в этом окне Вы можете выполнить анализ своего запроса, 
на предмет наличия ошибок или выбрать файл, который содержит текст запроса, 
и, если все хорошо, жмем далее.

### Шаг 5
На следующем окне сразу же можем нажимать далее, 
если конечно Вы не хотите задать свои названия полей в выгружаемом файле.

### Шаг 6
Затем на следующем окне все проверяем и жмем готово.

### Шаг 7
Далее, как и в импорте, жмем последний раз готово. 
И все, после этого у Вас в той папке, которую Вы указали, появится документ Excel с Вашими данными.
