sudo -u postgres psql

Задачи 1-4

    1) создал таблицу с одной текстовой строкой и наполнил данными на 1млн строк
    2) посмотрел размер таблицы = 65mb
    3) 5 раз обновил все строчки + сразу выполнил задание со *
    4) посмотрел кол-во мертвых строчек, изначально их 5млн так как изменяли 5 раз 1млн строк

![alt text](/3/1-4.png)

Задача 5
    дождался очистки
```
SELECT relname, n_live_tup, n_dead_tup, last_autovacuum
FROM pg_stat_all_tables
WHERE relname = 'test';
```

![alt text](/3/5.png)

Убедился что строчки обновлись
![alt text](/3/check-added-a.png)

Задача 6
    снова добавил обновил все строчки 5 раз
   
    ```
    DO $$       
    BEGIN
        FOR i IN 1..5 LOOP
            UPDATE test SET name = name || 'b';
        END LOOP;
    END $$;
    ```

Задача 7
\dt+ test;
![alt text](/3/7.png)

Задачи 8-10
![alt text](/3/8-10.png)

11) Сначала мы заполнили таблицу а потом обновили и у нас появились мертвые строчки но потом они были очищены так как autovacuum == true, если отключить его то при еще одном обновлении (задача 6) они не удаляются

12) ALTER TABLE test SET (autovacuum_enabled = true);



Задача со *

    ```
    DO $$       
    BEGIN
        FOR i IN 1..10 LOOP
            UPDATE test SET name = name || 'b';
        END LOOP;
    END $$;
    ```