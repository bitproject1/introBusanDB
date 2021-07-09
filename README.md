# introBusanDB

# 테이블 설계 완료

## hotspot 테이블
    
        CREATE TABLE `hotspot` (
          `id` int NOT NULL,
          `name` varchar(100) DEFAULT NULL,
          `district` varchar(50) DEFAULT NULL,
          `title` varchar(200) DEFAULT NULL,
          `subtitle` varchar(200) DEFAULT NULL,
          `address` varchar(300) DEFAULT NULL,
          `phonenum` varchar(100) DEFAULT NULL,
          `url` varchar(200) DEFAULT NULL,
          `traffic` text,
          `day` varchar(200) DEFAULT NULL,
          `holiday` varchar(200) DEFAULT NULL,
          `time` varchar(200) DEFAULT NULL,
          `fee` varchar(100) DEFAULT NULL,
          `conv` varchar(500) DEFAULT NULL,
          `img` varchar(300) DEFAULT NULL,
          `content` text,
          PRIMARY KEY (`id`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3


## restaurent 테이블

        CREATE TABLE `restaurent` (
          `id` int NOT NULL,
          `name` varchar(100) DEFAULT NULL,
          `district` varchar(50) DEFAULT NULL,
          `address` varchar(500) DEFAULT NULL,
          `phonenum` varchar(50) DEFAULT NULL,
          `url` varchar(200) DEFAULT NULL,
          `time` varchar(100) DEFAULT NULL,
          `mainmenu` varchar(100) DEFAULT NULL,
          `img` varchar(200) DEFAULT NULL,
          `content` text,
          `spot_id` int DEFAULT NULL,
          PRIMARY KEY (`id`),
          KEY `rest_spotid_idx` (`spot_id`),
          CONSTRAINT `rest_spotid` FOREIGN KEY (`spot_id`) REFERENCES `hotspot` (`id`) ON DELETE CASCADE ON UPDATE CASCADE
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3


## review 테이블

        CREATE TABLE `review` (
          `id` int NOT NULL,
          `grade` char(1) DEFAULT NULL,
          `content` text,
          `user_id` int DEFAULT NULL,
          `spot_id` int DEFAULT NULL,
          `rest_id` int DEFAULT NULL,
          PRIMARY KEY (`id`),
          KEY `review_userid_idx` (`user_id`),
          KEY `spot_id_idx` (`spot_id`),
          KEY `rest_id_idx` (`rest_id`),
          CONSTRAINT `rest_id` FOREIGN KEY (`rest_id`) REFERENCES `restaurent` (`id`),
          CONSTRAINT `spot_id` FOREIGN KEY (`spot_id`) REFERENCES `hotspot` (`id`),
          CONSTRAINT `user_id` FOREIGN KEY (`user_id`) REFERENCES `user` (`userid`) ON DELETE CASCADE ON UPDATE CASCADE
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3

## user 테이블

        CREATE TABLE `user` (
          `userid` int NOT NULL,
          `password` varchar(50) DEFAULT NULL,
          `name` varchar(30) DEFAULT NULL,
          `email` varchar(100) DEFAULT NULL,
          `age` int DEFAULT NULL,
          `gender` char(1) DEFAULT NULL,
          `auth` char(1) DEFAULT NULL,
          PRIMARY KEY (`userid`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3

## manager 테이블

        CREATE TABLE `manager` (
          `id` int NOT NULL,
          `password` varchar(50) DEFAULT NULL,
          `name` varchar(30) DEFAULT NULL,
          `email` varchar(100) DEFAULT NULL,
          `gender` char(1) DEFAULT NULL,
          `auth` char(1) DEFAULT NULL,
          PRIMARY KEY (`id`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3
