## 单点登录服务
### 系统sql
```sql
/*
 Navicat Premium Data Transfer

 Source Server         :  本地
 Source Server Type    : MySQL
 Source Server Version : 50721
 Source Host           : localhost:3306
 Source Schema         : sso

 Target Server Type    : MySQL
 Target Server Version : 50721
 File Encoding         : 65001

 Date: 23/05/2019 16:47:33
*/

SET NAMES utf8mb4;
SET FOREIGN_KEY_CHECKS = 0;

-- ----------------------------
-- Table structure for sso_app
-- ----------------------------
DROP TABLE IF EXISTS `sso_app`;
CREATE TABLE `sso_app`  (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `app_id` varchar(32) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT '' COMMENT 'appID',
  `app_secret` varchar(255) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL COMMENT 'app秘钥',
  `app_name` varchar(64) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL COMMENT 'app名',
  `app_url` varchar(2000) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL COMMENT 'sso链接',
  `create_time` datetime(0) NULL DEFAULT NULL,
  `update_time` datetime(0) NULL DEFAULT NULL,
  PRIMARY KEY (`id`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 1 CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;

-- ----------------------------
-- Table structure for sso_token
-- ----------------------------
DROP TABLE IF EXISTS `sso_token`;
CREATE TABLE `sso_token`  (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `token` varchar(128) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL COMMENT '登录token',
  `app_id` varchar(32) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL COMMENT '应用ID',
  `user_id` int(11) NULL DEFAULT NULL COMMENT '登录用户ID',
  `state` int(11) NULL DEFAULT NULL COMMENT '状态：1登录中  -1失效',
  `create_time` datetime(0) NULL DEFAULT NULL COMMENT '创建时间登录时间',
  `update_time` datetime(0) NULL DEFAULT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 1 CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;

-- ----------------------------
-- Table structure for sso_user
-- ----------------------------
DROP TABLE IF EXISTS `sso_user`;
CREATE TABLE `sso_user`  (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `account` varchar(32) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT '',
  `password` varchar(32) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
  `from_appid` varchar(255) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL COMMENT '来源于哪个APP,空则表示直接进入',
  `create_time` datetime(0) NULL DEFAULT NULL,
  `update_time` datetime(0) NULL DEFAULT NULL,
  PRIMARY KEY (`id`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 1 CHARACTER SET = utf8 COLLATE = utf8_general_ci ROW_FORMAT = Dynamic;

SET FOREIGN_KEY_CHECKS = 1;

```

