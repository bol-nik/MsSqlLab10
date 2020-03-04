Примеры:
1.	Пакеты

declare @v varchar(20);
select @v='Hello';
print @v;
print 'I packet';
GO
print @v;
print 'II packet';
GO
print 'III packet';

2.	Процедуры
a)	Вывод на экран данных из таблицы sale

create proc ex1
as
select * from sale;
çàïóñê ïðîöåäóðû:
exec ex1;

b)	Процедура для ввода в БД нового клиента:
create procedure customer_insert
@new_id int,
@new_name varchar(25),
@new_office int,
@new_address varchar(40)
As
Declare @count as smallint
Select @count=count(*) from dbo.Customer where [c_name]=@new_name;
Print @count;
If @count>0
Begin
Print 'Customer exists'
Return
End
Insert into dbo.Customer values(@new_id,@new_name,@new_office,@new_address);

Вызов процедуры:
Exec customer_insert
120, ‘Ivanov’, 7, ‘New-York’;

c)	Процедура для ввода новой страны:
create proc InsertCountry
@country varchar(25)
as
declare @id int, @dual int
select @dual= count(*) from country
where [country] = @country;
print @dual;
if @dual > 0 
begin
print 'Country exists!!!';
return;
end
select @id = max([cn_id]) + 1 from country;
insert into country(country, cn_id) values
(@country, @id);
Вызов процедуры:
exec InsertCountry 'USA'




Лабораторная работа №10

1.	Создать процедуру для ввода в БД нового сотрудника.
В качестве параметров задать: фамилию и имя сотрудника, название региона, фамилию и имя руководителя, % комиссионных.








