Поднял в виртуальной машине ubuntu 24.10 без gui

![](/1/virt.png)



Далее установил psql 17 версии

    ```$ sudo apt install curl ca-certificates
    $ sudo install -d /usr/share/postgresql-common/pgdg
    $ sudo curl -o /usr/share/postgresql-common/pgdg/apt.postgresql.org.asc --fail https://www.postgresql.org/media/keys/ACCC4CF8.asc```

    ```$ sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/postgresql-common/pgdg/apt.postgresql.org.asc] https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'```

    ```$ sudo apt update```

    ```$ sudo apt -y install postgresql-17```



![](/1/psql-version.png)


переключил роль на postgres
```sudo -i -u postgres```

залил тайские перевозки
wget https://storage.googleapis.com/thaibus/thai_small.tar.gz && tar -xf thai_small.tar.gz && psql < thai.sql


подкючился к thai командой ```\c thai```

посчитал кол-во поездок
![](/1/result.png)