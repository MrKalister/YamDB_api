## ������ API ��� Yamdb

### ��������:

������ ������������ ����� ���-��� ��� ����-���������� ����, ����������� ��������� ������ � �������������, ����������� �� ���� �������, ��������� �� �������� � �����, � ��� �� ������������� ��� ������. ������ ����� API � REST-��������� ��� ������ � ����� ������ ������� ����� ����������, ����������� ������, �������.
�������������� �� ������� �������������� � ������� JWT-�������.

### ��������������� ����:
* python 3.7
* Django
* Django Rest Framework
* Redoc

### ��������� ������:
���������� python:
���� � ������������ ������� �� ���������� python ������ �� ���� 3.7, �� ����� ������� � �������� ��� ����������� ����������:
##### ��� Windows
�������� �� ������ � �������� ���������� ��� ����� ������������ ������� �������.

https://www.python.org/downloads/release/python-379/

##### ��� Linux
������� �������� ������:

```
sudo apt update && sudo apt upgrade
```
###### ������� �1
����� ���������� �����������:
```
sudo apt-get install wget build-essential checkinstall
sudo apt-get install libreadline-gplv2-dev libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev libffi-dev zlib1g-dev
```
������� python:
```
cd /usr/src
sudo wget https://www.python.org/ftp/python/3.7.9/Python-3.7.9.tgz
```
��������������� � ���������� �����:
```
sudo tar xzf Python-3.7.9.tgz
cd Python-3.7.9
sudo ./configure --enable-optimizations
sudo make altinstall
```
###### ������� �2 (��� Ubuntu � ��������)
��������� �� ����������� deadsnakes ppa
```
sudo apt install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt install python3.7
```
##### ��������� ������� �� �����������
����������� ����������� � ������� � ���� � ��������� ������:

```
git clone https://github.com/suslyak/api_yamdb.git
```

```
cd api_yamdb
```

C������ � ������������ ����������� ���������:

� ����������� �� ���������� ��������� � ������������ �������, ������ python3 � ��������� ����� ���� python ��� ���-�� ������.

```
python3 -m venv env
```
##### ��� Linux

```
source env/bin/activate
```

##### ��� Windows

```
source env/Scripts/activate.bat
```
�����:
```
python3 -m pip install --upgrade pip
```

���������� ����������� �� ����� requirements.txt:

```
pip install -r requirements.txt
```

�� ���������� ������� api_yamdb
```
cd .\api_yamdb\
```
��������� ��������:

```
python3 manage.py migrate
```

��������� ������:

```
python3 manage.py runserver
```

### ����������� ������:

����������� �� ������� �������������� ��� ������ JWT-�������.
#### �����������
1. ������������ ���������� POST-������ � ����������� email � username �� �������� /api/v1/auth/signup/.
2. ������ ���������� ������ � ����� ������������� �� ��������� ����� email.
3. ������������ ���������� POST-������ � ����������� username � confirmation_code � ���� ����� �� �������� /api/v1/auth/token/, � ������ �� ������ ��� �������� token (JWT-�����). � ������ �������� ������ access token (��� refresh token'a) c �������� ����� � �����, �� ��������� ��������, ������������ ���������� ����� ��������� ����� �� �������� /api/v1/auth/token/ � �������� ����� �����.

��� �� ������������ ����� ������� � �����, � ���� ������, ���� confirmation_code � ������������ ����� ������, ��� �������� POST-������� � ����������� email � username ����� ������������ �� �������� /api/v1/auth/signup/, ������ ������� ��� ������������ (confirmation_code) � ����� �������� ������ � ����� ������������� (confirmation_code) �� ��������� ����� email.

### ������� ��������:

��������� ������ ���� ������������:
GET http://127.0.0.1:8000/api/v1/titles/

��������� ������������ c id 1 � ���� ������:
GET http://127.0.0.1:8000/api/v1/titles/1/

��������� ������ ���� ������� � ������������ c id 1 � ���� ������:
GET http://127.0.0.1:8000/api/v1/titles/1/reviews/

�������� ������ � ������������ c id 1 � ���� ������:
POST http://127.0.0.1:8000/api/v1/titles/1/reviews/
� ����� ������� 
```
{
"text": "string",
"score": 1
}
```

��������� ���������� ������ c id 1 � ������������ c id 1 � ���� ������:
PATCH http://127.0.0.1:8000/api/v1/titles/1/reviews/1/
� ����� ������� 
```
{
"score": 2
}
```

�������� ������ c id 1 � ������������ c id 1 � ���� ������:
DELETE http://127.0.0.1:8000/api/v1/titles/1/reviews/1/

��������� ������ ���� ������������ � ������ c id 1 � ������������ c id 1 � ���� ������:
GET http://127.0.0.1:8000/api/v1/titles/1/reviews/comments/

�������� ����������� � ������ c id 1 � ������������ c id 1 � ���� ������:
POST http://127.0.0.1:8000/api/v1/titles/1/reviews/1/comments/
� ����� ������� 
```
{
"text": "string"
}
```

��������� ���������� ����������� c id 1 � ������ c id 1 � ������������ c id 1 � ���� ������:
PATCH http://127.0.0.1:8000/api/v1/titles/1/reviews/1/comments/1/
� ����� ������� 
```
{
"text": "string"
}
```

�������� ����������� c id 1 � ������ c id 1 � ������������ c id 1 � ���� ������:
DELETE http://127.0.0.1:8000/api/v1/titles/1/reviews/1/comments/1/

#### ��������� ������� �������� � ��������� �������� �������� � ������������ �� ����
http://127.0.0.1:8000/redoc/

#### �������� �������������
email: 
* sergey.suslyak@mail.ru
* bosacheva98@mail.ru
* maxon.nowik@yandex.ru

github: https://github.com/suslyak/
