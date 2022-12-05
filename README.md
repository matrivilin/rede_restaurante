# rede_restaurante


DROP SCHEMA IF EXISTS rede_restaurantes;
CREATE SCHEMA rede_restaurantes;
USE rede_restaurantes;

-- Table structure for table `Lojas da Franquia`

CREATE TABLE lojas_franquia (
  id_loja INT NOT NULL,
  nome_unidade VARCHAR(20) NOT NULL,
  municipio TEXT NOT NULL,
  UF TEXT NOT NULL,
  PRIMARY KEY  (id_loja) );
 
  -- Table structure for table `Pedidos`

CREATE TABLE pedidos (
id_pedido INT NOT NULL AUTO_INCREMENT,
id_loja INT NOT NULL,
valor_pedido DECIMAL(5,2) NOT NULL,
data_pedido DATETIME NOT NULL,
forma_pagamento varchar(30) NOT NULL DEFAULT 'Cartão de Crédito',
nome_cliente VARCHAR(30),
cpf_cliente VARCHAR(20),
id_colaborador INT,
PRIMARY KEY  (id_pedido),
CONSTRAINT id_loja FOREIGN KEY (id_loja) REFERENCES lojas_franquia (id_loja) );

 -- Table structure for table `Pedidos`
 
 
 CREATE TABLE  funcionarios (
 id_loja INT NOT NULL,
 cargo VARCHAR(30) NOT NULL DEFAULT 'Atendente',
 salario DECIMAL(7,2) NOT NULL DEFAULT 3950.75 ,
 cpf_funcionario VARCHAR(20),
 id_colaborador INT NOT NULL,
 dt_admissao DATETIME,
 dt_desligamento DATETIME DEFAULT NULL,
 FOREIGN KEY (id_loja) REFERENCES lojas_franquia (id_loja) );
 
 CREATE TABLE  fornecedores (
 cnpj_f VARCHAR(20),
 id_item INT NOT NULL,
 nome_item VARCHAR(50) NOT NULL DEFAULT 'Combo Supreme',
 id_loja INT NOT NULL,
 PRIMARY KEY  (cnpj_f),
 FOREIGN KEY (id_loja) REFERENCES lojas_franquia (id_loja) );
 
 CREATE TABLE cardapio (
cnpj_f VARCHAR(20),
id_cardapio INT AUTO_INCREMENT,
id_item INT NOT NULL,
nome_item VARCHAR(50) NOT NULL,
valor_item DECIMAL (7,2) NOT NULL,
 PRIMARY KEY  (id_cardapio),
 FOREIGN KEY (cnpj_f) REFERENCES fornecedores (cnpj_f) );


-------------------------------------------------------
 
