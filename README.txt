Olá! Seja bem-vindo ao projeto isfrio desevolvido pelos alunos do 2°DS Novotec AMS:
- Lucas Pontes Soares
- Pedro Henrique Botelho
- Pedro Ramos de Lima

Primeiramente para executar o nosso projeto você deverá importar o nosso banco de dados para o phpmyadmin.
- Você pode fazer isso acessando a pasta no projeto 'bancoDados->isfrio.sql', e assim importando o aquivo .sql
- Ou você também pode colar e executar o código do sql do nosso banco.

Segue o código sql do banco de dados:

-- phpMyAdmin SQL Dump
-- version 5.1.1
-- https://www.phpmyadmin.net/
--
-- Host: 127.0.0.1
-- Tempo de geração: 01-Out-2022 às 01:21
-- Versão do servidor: 10.4.22-MariaDB
-- versão do PHP: 8.1.2

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";

CREATE DATABASE IF NOT EXISTS `isfrio` DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
USE `isfrio`;


CREATE TABLE `adicionais` (
  `id` int(11) NOT NULL,
  `nome` varchar(666) NOT NULL,
  `preco` decimal(10,2) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

INSERT INTO `adicionais` (`id`, `nome`, `preco`) VALUES
(1, 'M&M’s', '0.50'),
(2, 'Chocolates', '0.75'),
(3, 'Marshmallows', '0.40'),
(4, 'Castanha de caju', '1.05'),
(5, 'Bala fini', '0.90'),
(6, 'Paçoquinha', '1.05');

CREATE TABLE `coberturas` (
  `id` int(11) NOT NULL,
  `nome` varchar(666) NOT NULL,
  `preco` decimal(10,2) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

INSERT INTO `coberturas` (`id`, `nome`, `preco`) VALUES
(1, 'Beterraba', '1.00'),
(2, 'Churros', '1.00'),
(3, 'Kiwi', '0.75'),
(4, 'Chocolate', '1.05'),
(5, 'Cenoura', '0.75'),
(6, 'Chocolate branco', '1.00'),
(7, 'Morango', '0.90');

CREATE TABLE `massas` (
  `id` int(11) NOT NULL,
  `nome` varchar(666) NOT NULL,
  `preco` decimal(10,2) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

INSERT INTO `massas` (`id`, `nome`, `preco`) VALUES
(1, 'Beterraba', '2.00'),
(2, 'Chocolate', '2.00'),
(3, 'Banana', '2.00'),
(4, 'Abacaxi', '1.75'),
(5, 'Laranja', '1.90'),
(6, 'Limão', '1.50'),
(7, 'Jabuticaba', '1.50'),
(8, 'Uva', '1.75'),
(9, 'Whatsapp', '2.50');

CREATE TABLE `pedidos` (
  `id` int(11) NOT NULL,
  `id_usuario` int(11) NOT NULL,
  `bairro` varchar(20) NOT NULL,
  `rua` varchar(20) NOT NULL,
  `numero` int(8) NOT NULL,
  `complemento` varchar(20) DEFAULT NULL,
  `preco` varchar(20) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

INSERT INTO `pedidos` (`id`, `id_usuario`, `bairro`, `rua`, `numero`, `complemento`, `preco`) VALUES
(33, 8, 'Jardim América', 'rua abdala abujamra', 288, '', '3.25'),
(34, 6, 'Jardim América', 'rua abdala abujamra', 288, '', '4.75'),
(35, 6, 'Jardim América', 'rua abdala abujamra', 288, '', '5'),
(36, 7, 'Jardim América', 'rua abdala abujamra', 288, '', '6.4'),
(37, 7, 'Jardim América', 'rua abdala abujamra', 288, '', '6.25'),
(38, 6, 'Jardim América', 'rua abdala abujamra', 288, '', '6.3'),
(39, 9, 'vila margarida ', 'doze de outubro', 200, 'nada', '7.25'),
(40, 9, 'y', 'dasdsa', 0, '', '8'),
(41, 12, 'bozo', 'bozo', 123, '', '16.85');

CREATE TABLE `pedidos_complementos` (
  `id` int(11) NOT NULL,
  `id_produto` int(11) NOT NULL,
  `id_cobertura` varchar(11) NOT NULL,
  `id_massa` varchar(11) DEFAULT NULL,
  `id_adiconal` varchar(11) DEFAULT NULL,
  `id_pedido` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

INSERT INTO `pedidos_complementos` (`id`, `id_produto`, `id_cobertura`, `id_massa`, `id_adiconal`, `id_pedido`) VALUES
(33, 2, '3', '3', '1', 33),
(34, 2, '', '1,3', '2', 34),
(35, 1, '2', '1,2', '', 35),
(36, 2, '1,2', '2,3', '3', 36),
(37, 2, '2,3', '1,2', '1', 37),
(38, 2, '3,5', '5,7', '1,5', 38),
(39, 2, '2,5', '5,7', '4,6', 39),
(40, 2, '4,7', '8,9', '2,6', 40),
(41, 2, '1,2,3,4,5,6', '7,8,9', '1,2,3,4,5,6', 41);

CREATE TABLE `produtos` (
  `id` int(11) NOT NULL,
  `nome` varchar(666) NOT NULL,
  `img` varchar(666) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

INSERT INTO `produtos` (`id`, `nome`, `img`) VALUES
(1, 'Sorvete de litro', 'https://res.cloudinary.com/isfrio/image/upload/v1663427419/sorveteLitro_kbkzzc.png'),
(2, 'Sorvete de casquinha', 'https://res.cloudinary.com/isfrio/image/upload/v1663427419/sorveteCasca_jnevml.png');

CREATE TABLE `usuarios` (
  `id` int(11) NOT NULL,
  `email` mediumtext NOT NULL,
  `senha` mediumtext NOT NULL,
  `nome` longtext NOT NULL,
  `imagem` mediumtext NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

INSERT INTO `usuarios` (`id`, `email`, `senha`, `nome`, `imagem`) VALUES
(8, 'bozo@gmail.com', '202cb962ac59075b964b07152d234b70', 'bozo', '8.png'),
(9, 'pedro@pedro', 'c6cc8094c2dc07b700ffcc36d64e2138', 'pedro', ''),
(11, 'roberto@roberto', 'c1bfc188dba59d2681648aa0e6ca8c8e', 'roberto', ''),
(12, 'jabuti@jabuti', '202cb962ac59075b964b07152d234b70', 'jabuti', ''),
(13, 'lucao@lucao', '202cb962ac59075b964b07152d234b70', 'lucao', '13.jpeg');

ALTER TABLE `adicionais`
  ADD PRIMARY KEY (`id`);

ALTER TABLE `coberturas`
  ADD PRIMARY KEY (`id`);

ALTER TABLE `massas`
  ADD PRIMARY KEY (`id`);

ALTER TABLE `pedidos`
  ADD PRIMARY KEY (`id`);

ALTER TABLE `pedidos_complementos`
  ADD PRIMARY KEY (`id`);

ALTER TABLE `produtos`
  ADD PRIMARY KEY (`id`);

ALTER TABLE `usuarios`
  ADD PRIMARY KEY (`id`);

ALTER TABLE `adicionais`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=7;

ALTER TABLE `coberturas`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=8;

ALTER TABLE `massas`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=10;

ALTER TABLE `pedidos`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=42;

ALTER TABLE `pedidos_complementos`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=42;

ALTER TABLE `produtos`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=4;

ALTER TABLE `usuarios`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=14;
COMMIT;
