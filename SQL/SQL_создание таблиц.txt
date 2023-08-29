CREATE TABLE Users (
  id INT not NULL,
  userName varchar,
  level_id int,
  skill int,
  PRIMARY KEY(id)
);

CREATE table Level (
ID int NOT NULL,
level_name VARCHAR,
primary key(ID)
);

INSERT INTO Users (id, userName, level_id, skill) 
VALUES (1,  'Anton',  1,  900000), (2,  'Denis',  3,  4000), 
(3,  'Petr',  2,  50000), (4,  'Andrey',  4,  20), (5,  'Olga',  1,  600000), 
(6,  'Anna',  1,  1600000)

INSERT INTO level (id, level_name) 
VALUES (1,  'admin'), (2,  'power_user'), 
(3,  'user'), (4, 'guest')


Задания на написание запросов к БД:								
1. Отобрать из таблицы user всех пользователей, у которых level_id=1, skill > 799000 и в имени встречается буква а								
select username from users where level_id = 1 and skill > 799000 and username like '%a%'
								
2. Удалить всех пользователей, у которых skill меньше 100000								
delete from users where skill < 100000;	
							
3. Вывести все данные из таблицы user в порядке убывания по полю skill								
select * from users order by skill desc	
							
4. Добавить в таблицу user нового пользователя по имени Oleg, с уровнем 4 и skill =10								
insert into users (id, username, level_id, skill) values (7, 'Oleg',  4, 10);	
							
5. Обновить данные в таблице user - для пользователей с level_id меньше 2 проставить skill 2000000								
update users set skill = 2000000 where level_id < 2			
					
6. Выбрать user_name всех пользователей уровня admin используя подзапрос								
select username from users WHERE
level_id in (select id from level where level_name = 'admin') 
							
7. Выбрать user_name всех пользователей уровня admin используя join								
select users.username from users 
join level on level.id = users.id
where level.level_name = 'admin'								