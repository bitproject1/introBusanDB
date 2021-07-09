# introBusanDB

# 테이블 설계 완료

## hotspot 테이블
    
    CREATE TABLE `hotspot` (
      `spot_id` int NOT NULL,
      `spot_name` varchar(100) DEFAULT NULL,
      `spot_district` varchar(50) DEFAULT NULL,
      `spot_title` varchar(200) DEFAULT NULL,
      `spot_subtitle` varchar(200) DEFAULT NULL,
      `spot_address` varchar(300) DEFAULT NULL,
      `spot_phonenum` varchar(100) DEFAULT NULL,
      `spot_url` varchar(200) DEFAULT NULL,
      `spot_traffic` text,
      `spot_day` varchar(200) DEFAULT NULL,
      `spot_holiday` varchar(200) DEFAULT NULL,
      `spot_time` varchar(200) DEFAULT NULL,
      `spot_fee` varchar(100) DEFAULT NULL,
      `spot_conv` varchar(500) DEFAULT NULL,
      `spot_img` varchar(300) DEFAULT NULL,
      `spot_content` text,
      PRIMARY KEY (`spot_id`)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3


## restaurent 테이블

    CREATE TABLE `restaurent` (
      `rest_id` int NOT NULL,
      `rest_name` varchar(100) DEFAULT NULL,
      `rest_district` varchar(50) DEFAULT NULL,
      `rest_address` varchar(500) DEFAULT NULL,
      `rest_phonenum` varchar(50) DEFAULT NULL,
      `rest_url` varchar(200) DEFAULT NULL,
      `rest_time` varchar(100) DEFAULT NULL,
      `rest_mainmenu` varchar(100) DEFAULT NULL,
      `rest_img` varchar(200) DEFAULT NULL,
      `rest_content` text,
      `rest_spotid` int DEFAULT NULL,
      PRIMARY KEY (`rest_id`),
      KEY `rest_spotid_idx` (`rest_spotid`),
      CONSTRAINT `rest_spotid` FOREIGN KEY (`rest_spotid`) REFERENCES `hotspot` (`spot_id`) ON DELETE CASCADE ON UPDATE CASCADE
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3


## review 테이블

    CREATE TABLE `review` (
      `review_userid` int DEFAULT NULL,
      `reviewid` varchar(45) NOT NULL,
      `grade` char(1) DEFAULT NULL,
      `content` text,
      PRIMARY KEY (`reviewid`),
      KEY `review_userid_idx` (`review_userid`),
      CONSTRAINT `review_userid` FOREIGN KEY (`review_userid`) REFERENCES `user` (`userid`) ON DELETE CASCADE ON UPDATE CASCADE
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
      `managerid` int NOT NULL,
      `password` varchar(50) DEFAULT NULL,
      `name` varchar(30) DEFAULT NULL,
      `email` varchar(100) DEFAULT NULL,
      `gender` char(1) DEFAULT NULL,
      `auth` char(1) DEFAULT NULL,
      PRIMARY KEY (`managerid`)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb3

