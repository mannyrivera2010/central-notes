Ideas on how to convert Django Relational Sql Based backend

1)Dumping all data to xml file
````shell
python manage.py dumpdata  --indent 4 --format xml --all --natural-foreign > dump.xml
````
