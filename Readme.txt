�������:
1.	������
declare @v varchar(20);
select @v='Hello';
print @v;
print 'I packet';
GO
print @v;
print 'II packet';
GO
print 'III packet';

2.	���������
a)	����� �� ����� ������ �� ������� sale
create proc ex1
as
select * from sale;
������ ���������:
exec ex1;

b)	��������� ��� ����� � �� ������ �������:
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

����� ���������:
Exec customer_insert
120, �Ivanov�, 7, �New-York�;

c)	��������� ��� ����� ����� ������:
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
����� ���������:
exec InsertCountry 'USA'




������������ ������ �10

1.	������� ��������� ��� ����� � �� ������ ����������.
� �������� ���������� ������: ������� � ��� ����������, �������� �������, ������� � ��� ������������, % ������������.






