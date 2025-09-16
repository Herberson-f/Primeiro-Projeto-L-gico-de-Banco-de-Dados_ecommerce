## estrura do banco de dados

```SQL 
-- criando database
create database ecommerce; 
use ecommerce;

-- criando tebela cliente
create table cliente(
	idCliente int  primary key auto_increment,
    Fname varchar(10),
    Minit char(2),
    Lname varchar(20), 
    tipCliente enum ('PF', 'PJ') not null default 'PF',
    CPF char(11) null,
    CNPJ char(12) null,
    Address varchar(20),
    constraint check_pf_pj check (
		(tipCliente = 'PF' and CPF is not null and CNPJ is null)
        or
        (tipCliente = 'PJ' and CNPJ is not null and CPF is null)
    ),
    constraint unique_cpf_cliente unique(CPF),
	constraint unique_cnpj_cliente unique (CNPJ)
);

desc cliente;
alter table cliente auto_increment =1;
ALTER TABLE cliente MODIFY COLUMN idCliente INT AUTO_INCREMENT;

-- criando tabela produto
-- size = dimensão
create table product(
	idProduct int auto_increment primary key,
    Fname varchar(10) not null,
    classification_kids bool,
    category enum('eletrônicos','Vestimenta','Brinquedos','Alimentos'),
    alavaiação float default 0,
    size varchar(10)
);
alter table product auto_increment =1;
alter table product drop column CPF;
-- criar tabela pagamento
-- terminar tabela, conexoes e constraints

create table payments(
	id_payments int auto_increment,
	idClient int,
    typePayments enum ('Boleto','cartão','pix','pagamento misto') not null,
    limitAvailable float,
    primary key (id_payments, idClient),
    constraint pay_idCient foreign key(idClient) references cliente(idCliente)
);
alter table payments auto_increment =1;
-- drop table orders;
-- criando tabela pedido
-- order = pedido
create table orders( 
	idOrder int auto_increment primary key,
    idOrderCliente int,
    orderStatus enum ('Cancelado','Confirmado','Em processamento') default "Em processamento",
    ordeDescription varchar(250),
    sendValue float default 10,
    paymentCash bool default false,
    constraint fk_order_client foreign key (idOrderCliente) references cliente(idCliente)
);
alter table orders auto_increment =1;

create table delivery (
    idDelivery INT AUTO_INCREMENT PRIMARY KEY,
    idOrder INT NOT NULL,
    deliveryAddress VARCHAR(255) NOT NULL,
    deliveryStatus ENUM('Pendente','Enviado','Saiu para entrega','Entregue','Cancelado') DEFAULT 'Pendente',
    deliveryDate DATE,
    constraint fk_delivery_order FOREIGN KEY (idOrder) REFERENCES orders(idOrder)
);

-- criando tabela estoque 
create table productStorage(
	idProdStorage int auto_increment primary key,
    Category enum ('Canelado','Confirmado','Em processamento') default "Em processamento",
    ordeLocation varchar(250),
    quantity int default 0
);
alter table productStorage auto_increment =1;


-- criando tabela fornecedor
create table supplier(
	idSupplier int auto_increment primary key,
    SocialName varchar(40) not null,
    CNPJ char(15) not null,
    contact char(11) not null,
    constraint unique_supplier unique (CNPJ)
);
alter table supplier auto_increment =1;

-- criando tabela vendedor
create table seller(
	idSeller int auto_increment primary key,
    SocialName varchar(40) not null,
    abstName varchar(40),
    CNPJ char(15),
    CPF char(9),
    location varchar(40),
    contact char(11) not null,
    constraint unique_cnpj_seller unique (CNPJ),
    constraint unique_cpf_seller unique (CPF)
    
);
alter table seller auto_increment =1;


-- criando tabela
create table productseller(
	idSeller int,
    idProduct int,
    prodQuantity int default 1,
    primary key (idseller, idProduct),
    constraint fk_product_seller foreign key(idSeller) references Seller(idseller),
    constraint fk_product_product foreign key (idProduct) references product(idProduct)
);

create table ProductOrder(
	idPOproduct int,
    idPOstorage int,
    location varchar(40) not null,
    primary key (idPOproduct, idPOstorage),
    constraint fk_productorder_seller foreign key(idPOproduct) references product(idProduct),
    constraint fk_productorder_product foreign key(idPOstorage) references productStorage (idProdStorage)
);

create table storageLocation(
	idLproduct int,
    idLstorage int,
    location varchar(40) not null,
    primary key (idLproduct, idLstorage),
    constraint fk_storage_Location_product foreign key(idLProduct) references product(idproduct),
    constraint fk_storage_Location_storege foreign key(idLstorage) references productStorage(idProdStorage  )
);

create table productSupplier(
	idPsSupplier int,
    idPsProduct int,
    Quantity int not null,
    primary key (idPsSupplier, idPsProduct),
    constraint fk_supplier_seller foreign key(idPsSupplier) references supplier(idSupplier),
    constraint fk_supplier_product foreign key (idPsProduct) references product(idProduct)
);
