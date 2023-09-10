CREATE DATABASE IF NOT EXISTS `ergasiadb`;

USE `ergasiadb`;
SET SQL_SAFE_UPDATES = 0;
DROP TABLE IF EXISTS `users`;
CREATE TABLE `users` (
`id` BIGINT AUTO_INCREMENT,
`username` varchar(45) NOT NULL,
`email` varchar(45) NOT NULL,
`firstname` varchar(45) NOT NULL,
`lastname` varchar(45) NOT NULL,
`afm` varchar(45) NOT NULL,
`password` varchar(100) DEFAULT NULL,
PRIMARY KEY (`id`),
UNIQUE KEY `id_uk1` (`username`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
LOCK TABLES `users` WRITE;
INSERT INTO `users` (`id`, `username`, `email`, `firstname`, `lastname`, `afm`, `password`)
VALUES
(1, 'admin', 'a@a.gr', 'Admin',
'Administrator', '1222345', '$2a$12$l0n6rBUNJi5Brmm9SLBy4eWM2n5gcvnUXgu7KotScJ65Q/6PzDYma'),
(2, 'agtest', 'b@b.gr', 'testuser',
'agorastis', '2343345', '$2a$12$l0n6rBUNJi5Brmm9SLBy4eWM2n5gcvnUXgu7KotScJ65Q/6PzDYma'),
(3, 'poltest', 'b@b.gr', 'testuser',
'politis', '354654213','$2a$12$l0n6rBUNJi5Brmm9SLBy4eWM2n5gcvnUXgu7KotScJ65Q/6PzDYma'),
(4, 'buyertest1', 'b1@b.gr', 'testuser1',
'buyer1', '35164651321','$2a$12$l0n6rBUNJi5Brmm9SLBy4eWM2n5gcvnUXgu7KotScJ65Q/6PzDYma'),
(5, 'buyertest5', 'b5@b.gr', 'testuser5',
'buyer5', '354684352168','$2a$12$l0n6rBUNJi5Brmm9SLBy4eWM2n5gcvnUXgu7KotScJ65Q/6PzDYma'),
(6, 'buyertest6', 'b6@b.gr', 'testuser6',
'buyer6', '351684689','$2a$12$l0n6rBUNJi5Brmm9SLBy4eWM2n5gcvnUXgu7KotScJ65Q/6PzDYma'),
(7, 'buyertest7', 'b7@b.gr', 'testuser7',
'buyer7', '99554845','$2a$12$l0n6rBUNJi5Brmm9SLBy4eWM2n5gcvnUXgu7KotScJ65Q/6PzDYma'),
(8, 'buyertest8', 'b8@b.gr', 'testuser8',
'buyer8', '9687987465465489','$2a$12$l0n6rBUNJi5Brmm9SLBy4eWM2n5gcvnUXgu7KotScJ65Q/6PzDYma'),
(9, 'buyertest9', 'b9@b.gr', 'testuser9',
'buyer9', '234845616854','$2a$12$l0n6rBUNJi5Brmm9SLBy4eWM2n5gcvnUXgu7KotScJ65Q/6PzDYma'),
(10, 'buyertest10', 'b10@b.gr', 'testuser10',
'buyer10', '35485165845','$2a$12$l0n6rBUNJi5Brmm9SLBy4eWM2n5gcvnUXgu7KotScJ65Q/6PzDYma'),
(11, 'buyertest11', 'b11@b.gr', 'testuser11',
'buyer11', '35168456132','$2a$12$l0n6rBUNJi5Brmm9SLBy4eWM2n5gcvnUXgu7KotScJ65Q/6PzDYma'),
(12, 'buyertest12', 'b12@b.gr', 'testuser12',
'buyer12', '879878456','$2a$12$l0n6rBUNJi5Brmm9SLBy4eWM2n5gcvnUXgu7KotScJ65Q/6PzDYma'),
(13, 'sellecttest13', 's13@s.gr', 'testuser13',
'seller13', '987894521','$2a$12$l0n6rBUNJi5Brmm9SLBy4eWM2n5gcvnUXgu7KotScJ65Q/6PzDYma'),
(14, 'sellertest14', 's14@s.gr', 'testuser14',
'seller14', '9878945168','$2a$12$l0n6rBUNJi5Brmm9SLBy4eWM2n5gcvnUXgu7KotScJ65Q/6PzDYma');
/*!40000 ALTER TABLE `users` ENABLE KEYS */;
UNLOCK TABLES;
DROP TABLE IF EXISTS `roles`;
CREATE TABLE `roles` (
`id` BIGINT AUTO_INCREMENT,
`name` varchar(20) NOT NULL,
PRIMARY KEY (`id`),
UNIQUE KEY `id_uk1` (`name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
LOCK TABLES `roles` WRITE;
INSERT INTO `roles` (`id`, `name`)
VALUES
(1, 'ROLE_ADMIN'), 
(2, 'ROLE_AGORASTIS'),
(3, 'ROLE_POLITIS');
/*!40000 ALTER TABLE `roles` ENABLE KEYS */;
UNLOCK TABLES;
DROP TABLE IF EXISTS `user_roles`;
CREATE TABLE `user_roles` (
  `user_id` BIGINT NOT NULL,
  `role_id` BIGINT NOT NULL,
  PRIMARY KEY (user_id, role_id),
  FOREIGN KEY  (user_id) REFERENCES users(id),
  FOREIGN KEY  (role_id) REFERENCES roles(id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
LOCK TABLES `user_roles` WRITE;
INSERT INTO `user_roles` (`user_id`, `role_id`)
VALUES
(1, 1), 
(2,2), 
(3,3), 
(4,2), 
(5,2), 
(6,2), 
(7,2), 
(8,2), 
(9,2), 
(10,2), 
(11,2), 
(12,2), 
(13,3), 
(14,3);
/*!40000 ALTER TABLE `user_roles` ENABLE KEYS */;
UNLOCK TABLES;
DROP TABLE IF EXISTS `oxima`;
CREATE TABLE `oxima` (
`id` BIGINT AUTO_INCREMENT,
`pinakida` varchar(45) NOT NULL,
`user_id` BIGINT NOT NULL,
PRIMARY KEY (`id`),
UNIQUE KEY `id_uk1` (`pinakida`),
FOREIGN KEY  (user_id) REFERENCES users(id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
LOCK TABLES `oxima` WRITE;
INSERT INTO `oxima` (`id`, `pinakida`, `user_id`)
VALUES
(1, 'ixe0001', 3),
(2, 'ixe0002', 3),
(3, 'ixe0003', 3),
(4, 'ixe0004', 3),
(5, 'ixe0005', 3),
(6, 'ixe0006', 3),
(7, 'ixe0007', 3),
(8, 'ixe0008', 13);
/*!40000 ALTER TABLE `oxima` ENABLE KEYS */;
UNLOCK TABLES;
DROP TABLE IF EXISTS `sinalagi`;
CREATE TABLE `sinalagi` (
`id` int unsigned NOT NULL AUTO_INCREMENT,
`seller_id` BIGINT NOT NULL,
`buyer_id` BIGINT NOT NULL,
`oxima_id` BIGINT NOT NULL,
  `status` varchar(45) NOT NULL,
  `periferia` varchar(45) NOT NULL,
  FOREIGN KEY  (seller_id) REFERENCES users(id),
  FOREIGN KEY  (buyer_id) REFERENCES users(id),
    FOREIGN KEY  (oxima_id) REFERENCES oxima(id),
PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
LOCK TABLES `sinalagi` WRITE;
INSERT INTO `sinalagi` (`id`, `seller_id`, `buyer_id`,`oxima_id`,`status`,`periferia` )
VALUES
(1, 3, 5, 6, 'PENDING', 'DM Thessaloniki'),
(2, 3, 13, 8, 'COMPLETED', 'DM Athina'),
(3, 3, 7, 7, 'PENDING','DM Athina' );
/*!40000 ALTER TABLE `sinalagi` ENABLE KEYS */;
UNLOCK TABLES;
