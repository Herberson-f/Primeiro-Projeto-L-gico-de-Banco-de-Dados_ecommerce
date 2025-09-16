## consultas feitas 

```SQL
use ecommerce;

-- 1 Total de clientes cadastrados
select count(*) as clientes
from cliente ;

-- 2 Liste os nomes e CPFs de todos os clientes do estado de São Paulo
select Fname as nome, CPF, Address as endereço
from cliente
where Address = 'SP';

-- 3 Liste todos os pedidos com status Confirmado.
select idOrder as ID, orderStatus as 'status'
from orders
where orderStatus = 'confirmado';

-- 4 Quais produtos são classificados como infantis
select Fname as nome, 
	case 
		when classification_kids = 1 then 'produto infantil' 
        else ' ' end as classificação 
from product
where classification_kids = true;

-- 5 Quantos pedidos foram feitos por cada cliente?
select idCliente as ID, Fname as nome, count(idOrder) as quantidade
from cliente c join orders o on o.idOrderCliente = c.idCliente 
group by idOrder;

-- 6 Liste todos os fornecedores e os produtos que cada um fornece.
select Fname, Quantity, SocialName, CNPJ
from product p 
left join Quantity ps on p.idProduct = ps.idPsProduct
left join supplier s on ps.idPsSupplier = s.idSupplier;

-- 7 Qual o estoque total disponível por categoria de produto
select category, sum(Quantity)
from product p join productSupplier ps on p.idProduct = ps.idPsProduct
group by category;

-- 8 Qual foi o valor médio de frete para pedidos confirmados?
select avg(sendValue)
from orders 
where orderStatus = 'confirmado';

-- 9 nomes dos clientes junto com os nomes dos produtos que eles compraram.
select Fname, ordeDescription
from cliente c join orders o on c.idCliente = o.idOrderCliente;

-- 10 quantidade de ccompra por status
select orderStatus as 'status', count(orderStatus) as quantidade
from orders
group by orderStatus;
