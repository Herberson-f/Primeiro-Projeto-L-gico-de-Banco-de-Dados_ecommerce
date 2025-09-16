## inserindo dados

```SQL
use ecommerce;


-- CLIENTES
insert into cliente(Fname, Minit, Lname, tipCliente, CPF, CNPJ, Address)
values
('Marcos', 'M', 'Finas', 'PF', '46564534511', null, 'RJ'),
('Helena', 'H', 'Guibi', 'PF', '87564763522', null, 'SP'),
('Marquin', 'M', 'peças', 'PJ', null, '98756739853', 'SP'),
('Junior', 'J', 'Pereira', 'PF', '98756734540', null, 'RJ'),
('Maria', 'M', 'Ferreira', 'PF', '67545367844', null, 'PR'),
('Enup', 'E', 'ferrangens', 'PJ', null, '98756734533', 'PR'),
('Amanda', 'A', 'Silva', 'PF', '54676563555', null, 'SP'),
('Gilberto', 'G', 'Quino', 'PF', '65748734766', null, 'SP');

-- PRODUTOS
insert into product(Fname, classification_kids, category, alavaiação, size)
values
('Celular', false, 'eletrônicos', 4.5, 'null'),
('Maçãs', false, 'Alimentos', 4.8, '1kg'),
('Macacão', true, 'Vestimenta', 3.9, 'M'),
('Carrinho', true, 'Brinquedos', 4.2, '30cm'),
('Notebook', false, 'eletrônicos', 4.7, 'null'),
('Caças', true, 'Vestimenta', 4.0, 'G');

-- PAGAMENTOS
insert into payments(idClient, typePayments, limitAvailable)
values
(1, 'Boleto', 1200.00),
(2, 'Pix', 800.00),
(3, 'Cartão', 2500.00),
(4, 'Boleto', 600.00),
(5, 'Pagamento misto', 1500.00),
(6, 'Cartão', 600.00),
(7, 'Pix', 500.00),
(8, 'Boleto', 1700.00);

-- PEDIDOS
insert into orders(idOrderCliente, orderStatus, ordeDescription, sendValue, paymentCash)
values	
(1, 'Confirmado', 'Compra de celular', 20.00, false),
(2, 'Em processamento', 'Compra de roupas', 15.00, true),
(3, 'Confirmado', 'Compra de brinquedo', 10.00, false),
(4, 'Cancelado', 'Compra cancelada', 0.00, false),
(5, 'Confirmado', 'Compra de brinquedo', 12.00, true),
(6, 'Confirmado', 'Compra de celular', 6.00, true),
(7, 'Cancelado', 'Compra cancelada', 0.00, false),
(8, 'Confirmado', 'Compra de roupas', 10.00, true);

-- FORNECEDORES
insert into supplier(SocialName, CNPJ, contact)
values
('Tech Eletrônicos LTDA', '12345678000195', '11988887777'),
('Moda Brasil SA', '98765432000188', '11977776666'),
('Alimentos Bom Sabor', '11122233000144', '21966665555');

-- VENDEDORES
insert into seller(SocialName, abstName, CNPJ, CPF, location, contact)
values
('Loja Central', 'LC', '55566677000122', null, 'SP', '11999998888'),
('Varejo Sul', 'VS', null, '123456789', 'PR', '41988887777');
 

INSERT INTO productStorage (Category, ordeLocation, quantity)
VALUES
 ('Confirmado', 'Armazém RJ', 100),
 ('Confirmado', 'Armazém SP', 200),
 ('Em processamento', 'Centro PR', 150);


INSERT INTO productSupplier (idPsSupplier, idPsProduct, Quantity)
VALUES
 (1, 1, 50),  
 (2, 2, 200),  
 (3, 3, 100),
 (1, 4, 100),  
 (1, 5, 50),  
 (3, 6, 75);   

INSERT INTO ProductOrder (idPOproduct, idPOstorage, location)
VALUES
 (1, 1, 'RJ - Lote A'), 
 (2, 2, 'SP - Lote B'),  
 (3, 3, 'PR - Lote C');  

INSERT INTO storageLocation (idLproduct, idLstorage, location)
VALUES
 (4, 1, 'RJ - Corredor 3'), 
 (5, 2, 'SP - Corredor 1'),  
 (6, 3, 'PR - Corredor 2');  

