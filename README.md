# StrutsLibrarySystem
一个基于SSH(Struts+Spring+Hibernate）的图书馆管理系统，数据库是Mysql的，代码可正常运行
可以参考，别抄袭。

/*
Navicat MySQL Data Transfer

Source Server         : lo
Source Server Version : 50045
Source Host           : localhost:3306
Source Database       : leave

Target Server Type    : MYSQL
Target Server Version : 50045
File Encoding         : 65001

Date: 2018-03-19 20:44:05
*/

SET FOREIGN_KEY_CHECKS=0;

-- ----------------------------
-- Table structure for ask_for_leave
-- ----------------------------
DROP TABLE IF EXISTS `ask_for_leave`;
CREATE TABLE `ask_for_leave` (
  `id` int(11) NOT NULL auto_increment,
  `user_id` int(11) NOT NULL,
  `person_kind` varchar(32) default '',
  `leave_leader` varchar(255) default '',
  `leave_kind` varchar(4) default '',
  `leave_day` varchar(4) default '',
  `leave_reason` varchar(255) default '',
  `leave_start_day` varchar(32) default '',
  `leave_end_day` varchar(32) default '',
  `leave_remark` varchar(255) default '',
  `leave_cut_remark` varchar(255) default '',
  `leave_passed` tinyint(2) default '0',
  `leave_message_advance` tinyint(2) default '0',
  `leave_cut` tinyint(2) default '0',
  PRIMARY KEY  (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=159 DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of ask_for_leave
-- ----------------------------
INSERT INTO `ask_for_leave` VALUES ('157', '2670', '科办员', '无', '事假', '0', '测试', '2018-03-20', '2018-03-19', '', '无', '1', '0', '1');
INSERT INTO `ask_for_leave` VALUES ('158', '2419', '县直正科', '', '事假', '0', '回家', '2018-03-20', '2018-03-19', '', '2018.3.20', '1', '0', '1');

-- ----------------------------
-- Table structure for leave_admin
-- ----------------------------
DROP TABLE IF EXISTS `leave_admin`;
CREATE TABLE `leave_admin` (
  `id` int(32) NOT NULL auto_increment,
  `admin_id` int(32) default NULL,
  `admin_password` varchar(50) default '',
  PRIMARY KEY  (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=2 DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of leave_admin
-- ----------------------------
INSERT INTO `leave_admin` VALUES ('1', '1', 'eadc9b2f758073d4c60864891d140b7154ad2eb5');

-- ----------------------------
-- Table structure for leave_history
-- ----------------------------
DROP TABLE IF EXISTS `leave_history`;
CREATE TABLE `leave_history` (
  `id` int(11) NOT NULL auto_increment,
  `ask_for_leave_id` int(11) default NULL,
  `is_passed` int(11) default '0',
  PRIMARY KEY  (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of leave_history
-- ----------------------------

-- ----------------------------
-- Table structure for leave_related
-- ----------------------------
DROP TABLE IF EXISTS `leave_related`;
CREATE TABLE `leave_related` (
  `id` int(11) NOT NULL auto_increment,
  `leave_user_id` int(11) default '0',
  `related_leader_id` int(11) default '0',
  PRIMARY KEY  (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=39 DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of leave_related
-- ----------------------------
INSERT INTO `leave_related` VALUES ('1', '10', '11');
INSERT INTO `leave_related` VALUES ('2', '10', '9');
INSERT INTO `leave_related` VALUES ('5', '10', '2');
INSERT INTO `leave_related` VALUES ('10', '12', '15');
INSERT INTO `leave_related` VALUES ('8', '13', '14');
INSERT INTO `leave_related` VALUES ('11', '27', '25');
INSERT INTO `leave_related` VALUES ('13', '42', '27');
INSERT INTO `leave_related` VALUES ('14', '46', '48');
INSERT INTO `leave_related` VALUES ('15', '49', '46');
INSERT INTO `leave_related` VALUES ('16', '52', '53');
INSERT INTO `leave_related` VALUES ('17', '69', '68');
INSERT INTO `leave_related` VALUES ('18', '68', '69');
INSERT INTO `leave_related` VALUES ('19', '79', '78');
INSERT INTO `leave_related` VALUES ('23', '86', '87');
INSERT INTO `leave_related` VALUES ('22', '81', '80');
INSERT INTO `leave_related` VALUES ('24', '82', '80');
INSERT INTO `leave_related` VALUES ('25', '88', '88');
INSERT INTO `leave_related` VALUES ('26', '126', '115');
INSERT INTO `leave_related` VALUES ('27', '145', '146');
INSERT INTO `leave_related` VALUES ('36', '2358', '2413');
INSERT INTO `leave_related` VALUES ('35', '2358', '2370');
INSERT INTO `leave_related` VALUES ('34', '2358', '2360');
INSERT INTO `leave_related` VALUES ('32', '2419', '2413');
INSERT INTO `leave_related` VALUES ('33', '2419', '2415');
INSERT INTO `leave_related` VALUES ('37', '3089', '2449');
INSERT INTO `leave_related` VALUES ('38', '3088', '2449');

-- ----------------------------
-- Table structure for leave_rule
-- ----------------------------
DROP TABLE IF EXISTS `leave_rule`;
CREATE TABLE `leave_rule` (
  `id` int(11) NOT NULL auto_increment COMMENT 'leave_rule表舍弃，暂时不删除',
  `user_class_area` varchar(32) default '',
  `user_origin` varchar(100) default '',
  `user_position_rank` varchar(32) default '',
  `user_separated` varchar(2) default '',
  `user_max_day` varchar(2) default '',
  PRIMARY KEY  (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=9 DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of leave_rule
-- ----------------------------
INSERT INTO `leave_rule` VALUES ('8', '二类区', '西藏日喀则市谢通门县', '部级正职', '是', '10');

-- ----------------------------
-- Table structure for leave_setup
-- ----------------------------
DROP TABLE IF EXISTS `leave_setup`;
CREATE TABLE `leave_setup` (
  `id` int(11) NOT NULL auto_increment,
  `field` varchar(100) default NULL,
  `flag` tinyint(4) default NULL,
  PRIMARY KEY  (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=157 DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of leave_setup
-- ----------------------------
INSERT INTO `leave_setup` VALUES ('1', '2', '3');
INSERT INTO `leave_setup` VALUES ('2', '2018031902', '4');
INSERT INTO `leave_setup` VALUES ('3', '县委办', '0');
INSERT INTO `leave_setup` VALUES ('4', '政府办', '0');
INSERT INTO `leave_setup` VALUES ('5', '人大办', '0');
INSERT INTO `leave_setup` VALUES ('6', '政协办', '0');
INSERT INTO `leave_setup` VALUES ('7', '纪委', '0');
INSERT INTO `leave_setup` VALUES ('8', '机要局', '0');
INSERT INTO `leave_setup` VALUES ('9', '档案馆', '0');
INSERT INTO `leave_setup` VALUES ('10', '组织部（编办）', '0');
INSERT INTO `leave_setup` VALUES ('11', '老干局', '0');
INSERT INTO `leave_setup` VALUES ('12', '宣传部', '0');
INSERT INTO `leave_setup` VALUES ('13', '统战部', '0');
INSERT INTO `leave_setup` VALUES ('14', '政法委', '0');
INSERT INTO `leave_setup` VALUES ('15', '党校', '0');
INSERT INTO `leave_setup` VALUES ('16', '法院', '0');
INSERT INTO `leave_setup` VALUES ('17', '检察院', '0');
INSERT INTO `leave_setup` VALUES ('18', '发改委', '0');
INSERT INTO `leave_setup` VALUES ('19', '教育局', '0');
INSERT INTO `leave_setup` VALUES ('20', '民宗局', '0');
INSERT INTO `leave_setup` VALUES ('21', '宗组办', '0');
INSERT INTO `leave_setup` VALUES ('22', '公安局', '0');
INSERT INTO `leave_setup` VALUES ('23', '民政局', '0');
INSERT INTO `leave_setup` VALUES ('24', '司法局', '0');
INSERT INTO `leave_setup` VALUES ('25', '财政局', '0');
INSERT INTO `leave_setup` VALUES ('26', '人社局', '0');
INSERT INTO `leave_setup` VALUES ('27', '国土局', '0');
INSERT INTO `leave_setup` VALUES ('28', '环保局', '0');
INSERT INTO `leave_setup` VALUES ('29', '住建局', '0');
INSERT INTO `leave_setup` VALUES ('30', '交通局', '0');
INSERT INTO `leave_setup` VALUES ('31', '水利局', '0');
INSERT INTO `leave_setup` VALUES ('32', '农牧局', '0');
INSERT INTO `leave_setup` VALUES ('33', '商务局', '0');
INSERT INTO `leave_setup` VALUES ('34', '文广局', '0');
INSERT INTO `leave_setup` VALUES ('35', '卫计委', '0');
INSERT INTO `leave_setup` VALUES ('36', '审计局', '0');
INSERT INTO `leave_setup` VALUES ('37', '安监局', '0');
INSERT INTO `leave_setup` VALUES ('38', '食药局', '0');
INSERT INTO `leave_setup` VALUES ('39', '统计局', '0');
INSERT INTO `leave_setup` VALUES ('40', '林业局', '0');
INSERT INTO `leave_setup` VALUES ('41', '综治办', '0');
INSERT INTO `leave_setup` VALUES ('42', '扶贫办', '0');
INSERT INTO `leave_setup` VALUES ('43', '藏语委办', '0');
INSERT INTO `leave_setup` VALUES ('44', '后勤服务中心', '0');
INSERT INTO `leave_setup` VALUES ('45', '维稳办', '0');
INSERT INTO `leave_setup` VALUES ('46', '巡察办', '0');
INSERT INTO `leave_setup` VALUES ('47', '工会', '0');
INSERT INTO `leave_setup` VALUES ('48', '团县委', '0');
INSERT INTO `leave_setup` VALUES ('49', '妇联', '0');
INSERT INTO `leave_setup` VALUES ('50', '农牧综合服务中心', '0');
INSERT INTO `leave_setup` VALUES ('51', '卫生服务中心', '0');
INSERT INTO `leave_setup` VALUES ('52', '文化执法大队', '0');
INSERT INTO `leave_setup` VALUES ('53', '文化广播影视服务站', '0');
INSERT INTO `leave_setup` VALUES ('54', '社保中心', '0');
INSERT INTO `leave_setup` VALUES ('55', '五保集中供养', '0');
INSERT INTO `leave_setup` VALUES ('56', '人事争议仲裁院', '0');
INSERT INTO `leave_setup` VALUES ('57', '卡嘎镇', '0');
INSERT INTO `leave_setup` VALUES ('58', '卡嘎镇派出所', '0');
INSERT INTO `leave_setup` VALUES ('59', '通门乡', '0');
INSERT INTO `leave_setup` VALUES ('60', '通门乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('61', '塔定乡', '0');
INSERT INTO `leave_setup` VALUES ('62', '塔定乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('63', '荣玛乡', '0');
INSERT INTO `leave_setup` VALUES ('64', '荣玛乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('65', '达那答乡', '0');
INSERT INTO `leave_setup` VALUES ('66', '达那答乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('67', '仁钦则乡', '0');
INSERT INTO `leave_setup` VALUES ('68', '仁钦则乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('69', '达那普乡', '0');
INSERT INTO `leave_setup` VALUES ('70', '达那普乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('71', '孜许乡', '0');
INSERT INTO `leave_setup` VALUES ('72', '孜许乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('73', '南木切乡', '0');
INSERT INTO `leave_setup` VALUES ('74', '南木切乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('75', '查布乡', '0');
INSERT INTO `leave_setup` VALUES ('76', '查布乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('77', '春哲乡', '0');
INSERT INTO `leave_setup` VALUES ('78', '春哲乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('79', '青都乡', '0');
INSERT INTO `leave_setup` VALUES ('80', '青都乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('81', '娘热乡', '0');
INSERT INTO `leave_setup` VALUES ('82', '娘热乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('83', '纳当乡', '0');
INSERT INTO `leave_setup` VALUES ('84', '纳当乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('85', '措布西乡', '0');
INSERT INTO `leave_setup` VALUES ('86', '措布西乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('87', '达木夏乡', '0');
INSERT INTO `leave_setup` VALUES ('88', '达木夏乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('89', '列巴乡', '0');
INSERT INTO `leave_setup` VALUES ('90', '列巴乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('91', '切琼乡', '0');
INSERT INTO `leave_setup` VALUES ('92', '切琼乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('93', '美巴切勤乡', '0');
INSERT INTO `leave_setup` VALUES ('94', '美巴切勤乡派出所', '0');
INSERT INTO `leave_setup` VALUES ('95', '解放中路便民警务站', '0');
INSERT INTO `leave_setup` VALUES ('96', '吉定西路便民警务站', '0');
INSERT INTO `leave_setup` VALUES ('97', '卡嘎温泉便民警务站', '0');
INSERT INTO `leave_setup` VALUES ('98', '达那答检查站', '0');
INSERT INTO `leave_setup` VALUES ('99', '拉旺孜检查站', '0');
INSERT INTO `leave_setup` VALUES ('100', '扎西吉培寺管委会', '0');
INSERT INTO `leave_setup` VALUES ('101', '日加寺管委会', '0');
INSERT INTO `leave_setup` VALUES ('102', '林嘎寺管委会', '0');
INSERT INTO `leave_setup` VALUES ('103', '达那土登寺管委会', '0');
INSERT INTO `leave_setup` VALUES ('104', '铜布寺管委会', '0');
INSERT INTO `leave_setup` VALUES ('105', '吴坚古汝寺管委会', '0');
INSERT INTO `leave_setup` VALUES ('106', '查嘎珠德寺管委会', '0');
INSERT INTO `leave_setup` VALUES ('107', '卓列寺管委会', '0');
INSERT INTO `leave_setup` VALUES ('108', '索布寺管委会', '0');
INSERT INTO `leave_setup` VALUES ('109', '书记', '1');
INSERT INTO `leave_setup` VALUES ('110', '副书记', '1');
INSERT INTO `leave_setup` VALUES ('111', '县长', '1');
INSERT INTO `leave_setup` VALUES ('112', '副县长', '1');
INSERT INTO `leave_setup` VALUES ('113', '主任', '1');
INSERT INTO `leave_setup` VALUES ('114', '副主任', '1');
INSERT INTO `leave_setup` VALUES ('115', '主席', '1');
INSERT INTO `leave_setup` VALUES ('116', '副主席', '1');
INSERT INTO `leave_setup` VALUES ('117', '乡长', '1');
INSERT INTO `leave_setup` VALUES ('118', '副乡长', '1');
INSERT INTO `leave_setup` VALUES ('119', '纪委书记', '1');
INSERT INTO `leave_setup` VALUES ('120', '部长', '1');
INSERT INTO `leave_setup` VALUES ('121', '副部长', '1');
INSERT INTO `leave_setup` VALUES ('122', '局长', '1');
INSERT INTO `leave_setup` VALUES ('123', '副局长', '1');
INSERT INTO `leave_setup` VALUES ('124', '主任科员', '1');
INSERT INTO `leave_setup` VALUES ('125', '副主任科员', '1');
INSERT INTO `leave_setup` VALUES ('126', '副科实职', '1');
INSERT INTO `leave_setup` VALUES ('127', '科员', '1');
INSERT INTO `leave_setup` VALUES ('128', '办事员', '1');
INSERT INTO `leave_setup` VALUES ('129', '站长', '1');
INSERT INTO `leave_setup` VALUES ('130', '副站长', '1');
INSERT INTO `leave_setup` VALUES ('131', '队长', '1');
INSERT INTO `leave_setup` VALUES ('132', '副队长', '1');
INSERT INTO `leave_setup` VALUES ('133', '所长', '1');
INSERT INTO `leave_setup` VALUES ('134', '副所长', '1');
INSERT INTO `leave_setup` VALUES ('135', '员级', '1');
INSERT INTO `leave_setup` VALUES ('136', '初级', '1');
INSERT INTO `leave_setup` VALUES ('137', '中级', '1');
INSERT INTO `leave_setup` VALUES ('138', '高级', '1');
INSERT INTO `leave_setup` VALUES ('139', '检察长', '1');
INSERT INTO `leave_setup` VALUES ('140', '副检察长', '1');
INSERT INTO `leave_setup` VALUES ('141', '院长', '1');
INSERT INTO `leave_setup` VALUES ('142', '副院长', '1');
INSERT INTO `leave_setup` VALUES ('143', '校长', '1');
INSERT INTO `leave_setup` VALUES ('144', '副校长', '1');
INSERT INTO `leave_setup` VALUES ('145', '组长', '1');
INSERT INTO `leave_setup` VALUES ('146', '副组长', '1');
INSERT INTO `leave_setup` VALUES ('147', '正县', '2');
INSERT INTO `leave_setup` VALUES ('148', '副县', '2');
INSERT INTO `leave_setup` VALUES ('149', '正科', '2');
INSERT INTO `leave_setup` VALUES ('150', '副科', '2');
INSERT INTO `leave_setup` VALUES ('151', '科员', '2');
INSERT INTO `leave_setup` VALUES ('152', '办事员', '2');
INSERT INTO `leave_setup` VALUES ('153', '员级', '2');
INSERT INTO `leave_setup` VALUES ('154', '初级', '2');
INSERT INTO `leave_setup` VALUES ('155', '中级', '2');
INSERT INTO `leave_setup` VALUES ('156', '高级', '2');

-- ----------------------------
-- Table structure for leave_user
-- ----------------------------
DROP TABLE IF EXISTS `leave_user`;
CREATE TABLE `leave_user` (
  `id` int(11) NOT NULL auto_increment,
  `user_name` varchar(32) default '',
  `user_sex` varchar(2) default '',
  `user_born_time` varchar(32) default '',
  `user_work_time` varchar(32) default '',
  `user_origin` varchar(100) default '' COMMENT '籍贯',
  `user_spouse_origin` varchar(100) default '' COMMENT '配偶籍贯',
  `user_work_address` varchar(100) default '',
  `user_position` varchar(32) default '',
  `user_position_rank` varchar(32) default '',
  `user_class_area` varchar(32) default '',
  `user_separated` varchar(2) default '',
  `user_phone` bigint(20) default '0',
  `user_max_day` tinyint(4) default '0',
  PRIMARY KEY  (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=3090 DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of leave_user
-- ----------------------------
INSERT INTO `leave_user` VALUES ('1', 'xtmxzzb', '', '', '', '', '', '', '', '', '', '', '0', '0');
INSERT INTO `leave_user` VALUES ('2343', '张伟', '男', '1988-05-05', '2011-08-01', '陕西省咸阳市', '无', '措布西乡', '副乡长', '副科', '二类区', '是', '15889024310', '50');
INSERT INTO `leave_user` VALUES ('2344', '晏黎果', '男', '1986-11-12', '2013-08-01', '重庆市万州区', '无', '县委办', '科员', '科员', '二类区', '是', '17308927828', '50');
INSERT INTO `leave_user` VALUES ('2345', '司丽娟', '女', '1988-01-03', '2016-01-01', '河南省临颍县', '无', '机要局', '副主任科员', '副科', '二类区', '是', '18076925158', '50');
INSERT INTO `leave_user` VALUES ('2346', '南栋梁', '男', '1987-10-10', '2014-07-01', '甘肃省通渭县', '无', '县委办', '科员', '科员', '二类区', '是', '18708010894', '50');
INSERT INTO `leave_user` VALUES ('2347', '黄健', '女', '1990-02-16', '2016-01-01', '辽宁省庄河市', '无', '机要局', '科员', '科员', '二类区', '是', '15140648208', '50');
INSERT INTO `leave_user` VALUES ('2348', '任田颖', '女', '1988-10-11', '2012-11-01', '四川省崇州市', '无', '档案馆', '科员', '科员', '二类区', '是', '18208093096', '50');
INSERT INTO `leave_user` VALUES ('2349', '周兆峰', '男', '1975-05-14', '1998-07-01', '青海省', '无', '党校', '主任科员', '正科', '二类区', '否', '13989029775', '50');
INSERT INTO `leave_user` VALUES ('2350', '旦增南木加', '男', '1991-02-27', '2013-08-01', '西藏南木林', '无', '县委办', '科员', '科员', '二类区', '否', '18189084434', '34');
INSERT INTO `leave_user` VALUES ('2351', '仁增晋美', '男', '1992-08-08', '2014-11-01', '西藏日喀则', '无', '县委办', '科员', '科员', '二类区', '否', '13989023496', '32');
INSERT INTO `leave_user` VALUES ('2352', '扎西顿珠', '男', '1988-11-01', '2011-08-01', '西藏日喀则', '无', '机要局', '局长', '副科', '二类区', '否', '15889089891', '32');
INSERT INTO `leave_user` VALUES ('2353', '旦增卓嘎', '女', '1989-11-14', '2014-12-01', '西藏拉萨市', '西藏曲松县', '机要局', '科员', '科员', '二类区', '是', '13308982939', '46');
INSERT INTO `leave_user` VALUES ('2354', '白玛央拉', '女', '1990-10-25', '2012-11-01', '西藏谢通门县', '无', '档案馆', '科员', '科员', '二类区', '否', '18798990884', '30');
INSERT INTO `leave_user` VALUES ('2355', '旦增群培', '男', '1994-04-18', '2017-11-01', '西藏南木林', '无', '机要局', '科员', '科员', '二类区', '否', '18989087554', '34');
INSERT INTO `leave_user` VALUES ('2356', '杨倩梅', '女', '1987-12-27', '2010-08-01', '西藏江孜县', '四川安岳县', '县委办', '副主任', '副科', '二类区', '是', '15889022005', '50');
INSERT INTO `leave_user` VALUES ('2357', '边巴拉姆', '女', '1989-09-02', '2012-07-01', '青海省', '无', '县委办', '科员', '科员', '二类区', '是', '18208070771', '50');
INSERT INTO `leave_user` VALUES ('2358', '旦增更参', '男', '1979-10-12', '2001-07-01', '西藏达孜', '西藏日喀则', '县委办', '主任', '正科', '二类区', '是', '13989920011', '46');
INSERT INTO `leave_user` VALUES ('2359', '裴建军', '男', '1974-06-01', '1997-07-01', '甘肃合水县', '无', '党校', '副校长', '正科', '二类区', '是', '13518925466', '50');
INSERT INTO `leave_user` VALUES ('2360', '边巴扎西', '男', '1974-01-01', '1993-07-01', '西藏萨迦', '无', '县委办', '书记', '正县', '二类区', '是', '13908922845', '50');
INSERT INTO `leave_user` VALUES ('2361', '普布塔松', '男', '1971-11-18', '1993-07-01', '青海省', '日喀则市萨迦县', '人大办', '主任', '正县', '二类区', '是', '13648922101', '50');
INSERT INTO `leave_user` VALUES ('2362', '坚刚', '男', '1964-12-01', '1986-07-01', '谢通门县', '日喀则市谢通门县', '人大办', '副主任', '副县', '二类区', '否', '13628925665', '40');
INSERT INTO `leave_user` VALUES ('2363', '白晓明', '男', '1974-12-11', '1992-12-01', '陕西省凤县', '河南省商丘市', '人大办', '副主任', '副县', '二类区', '是', '15208097841', '60');
INSERT INTO `leave_user` VALUES ('2364', '边巴', '女', '1972-03-13', '1994-07-01', '日喀则市', '日喀则市谢通门县', '人大办', '主任', '正科', '二类区', '是', '13518921958', '42');
INSERT INTO `leave_user` VALUES ('2365', '南木加次仁', '男', '1980-11-03', '2004-07-01', '日喀则市', '日喀则市', '人大办', '副主任', '副科', '二类区', '否', '15889028559', '32');
INSERT INTO `leave_user` VALUES ('2366', '李雪娇', '女', '1989-02-07', '2011-12-01', '四川省', '河南省', '人大办', '副主任', '副科', '二类区', '是', '13908920820', '50');
INSERT INTO `leave_user` VALUES ('2367', '曹露露', '女', '1989-08-30', '2013-08-01', '河南', '日喀则市', '人大办', '科员', '科员', '二类区', '是', '18989923747', '50');
INSERT INTO `leave_user` VALUES ('2368', '王桂平', '男', '1991-07-07', '2012-11-01', '湖南省耒阳市', '湖南省衡阳县', '人大办', '科员', '科员', '二类区', '是', '18308024455', '50');
INSERT INTO `leave_user` VALUES ('2369', '马太平', '男', '1992-09-27', '2014-12-01', '河南省平顶山', '河南平顶山', '人大办', '科员', '科员', '二类区', '是', '15708081714', '50');
INSERT INTO `leave_user` VALUES ('2370', '王金铭', '男', '1973-05-01', '1993-07-01', '河南新郑', '无', '政府办', '县长', '正县', '二类区', '是', '13638925609', '60');
INSERT INTO `leave_user` VALUES ('2371', '窦沿东', '男', '1970-09-01', '1985-01-01', '黑龙江绥化', '无', '政府办', '副县长', '副县', '二类区', '是', '17889086035', '60');
INSERT INTO `leave_user` VALUES ('2372', '普琼', '男', '1976-12-01', '1999-07-01', '西藏拉孜', '无', '政府办', '副县长', '副县', '二类区', '是', '13989023999', '50');
INSERT INTO `leave_user` VALUES ('2373', '赵贵昌', '男', '1978-05-01', '1999-07-01', '黑龙江宝清', '无', '政府办', '副县长', '副县', '二类区', '是', '18189923456', '60');
INSERT INTO `leave_user` VALUES ('2374', '拉巴次仁', '男', '1975-03-01', '1994-06-01', '西藏昂仁县', '无', '政府办', '副县长', '副县', '二类区', '是', '13659565253', '50');
INSERT INTO `leave_user` VALUES ('2375', '郭利顷', '男', '1976-02-01', '2000-07-01', '河南新平', '无', '政府办', '副县长', '副县', '二类区', '是', '13908925699', '60');
INSERT INTO `leave_user` VALUES ('2376', '边巴', '男', '1979-08-01', '2002-07-01', '日喀则市桑珠孜区', '无', '政府办', '副县长', '副县', '二类区', '是', '13659578800', '50');
INSERT INTO `leave_user` VALUES ('2377', '扎珍', '女', '1975-03-01', '1996-07-01', '西藏定结', '无', '政府办', '副县长', '副县', '二类区', '是', '13989923359', '50');
INSERT INTO `leave_user` VALUES ('2378', '董竟泰', '男', '1988-05-01', '2011-08-01', '山东莱阳', '无', '政府办', '副主任', '副科', '二类区', '是', '18208087209', '50');
INSERT INTO `leave_user` VALUES ('2379', '旦增曲培', '男', '1988-06-01', '2012-07-01', '西藏南木林', '无', '政府办', '副主任', '副科', '二类区', '是', '13618921375', '34');
INSERT INTO `leave_user` VALUES ('2380', '张凯', '男', '1986-06-01', '2012-07-01', '四川仁寿', '无', '政府办', '副主任', '副科', '二类区', '是', '18208084821', '50');
INSERT INTO `leave_user` VALUES ('2381', '蒲茂林', '男', '1986-11-01', '2012-12-01', '四川阆中', '无', '政府办', '科员', '科员', '二类区', '是', '15889075957', '50');
INSERT INTO `leave_user` VALUES ('2382', '吴聚龙', '男', '1990-12-01', '2012-12-01', '湖南涟源', '无', '政府办', '科员', '科员', '二类区', '是', '18389080149', '50');
INSERT INTO `leave_user` VALUES ('2383', '张波', '男', '1985-07-01', '2015-12-01', '贵州仁怀', '无', '政府办', '科员', '科员', '二类区', '是', '15120239007', '50');
INSERT INTO `leave_user` VALUES ('2384', '赵飞龙', '男', '1991-07-01', '2015-12-01', '河南洛阳', '无', '政府办', '科员', '科员', '二类区', '是', '15139552657', '50');
INSERT INTO `leave_user` VALUES ('2385', '旦增', '男', '1988-04-01', '2014-11-01', '西藏江孜', '无', '达木夏乡', '科员', '科员', '二类区', '是', '18143877044', '34');
INSERT INTO `leave_user` VALUES ('2386', '次仁德吉', '女', '1993-02-01', '2017-01-01', '西藏山南', '无', '达那普乡', '科员', '科员', '二类区', '是', '18798916766', '36');
INSERT INTO `leave_user` VALUES ('2387', '拉巴次仁', '男', '1964-10-01', '1987-07-01', '西藏仁布县', '西藏康马县', '政协办', '主席', '正县', '二类区', '是', '18289097555', '50');
INSERT INTO `leave_user` VALUES ('2388', '万家群', '女', '1971-08-01', '1996-08-01', '四川省简阳县', '四川省渠县', '政协办', '副主席', '副县', '二类区', '是', '13628925105', '60');
INSERT INTO `leave_user` VALUES ('2389', '达娃普赤', '女', '1976-01-01', '1995-07-01', '西藏日喀则市', '西藏谢通门县', '政协办', '主任', '正科', '二类区', '否', '13989925800', '32');
INSERT INTO `leave_user` VALUES ('2390', '旦增旺姆', '女', '1984-03-01', '2007-07-01', '西藏谢通门县', '西藏乃东县', '政协办', '副主任', '副科', '二类区', '否', '13658926076', '36');
INSERT INTO `leave_user` VALUES ('2391', '陈景新', '男', '1990-02-01', '2012-07-01', '湖南省湘乡市', '陕西省富平县', '政协办', '副主任科员', '副科', '二类区', '是', '17789025123', '50');
INSERT INTO `leave_user` VALUES ('2392', '洛桑云赞', '男', '1989-07-01', '2013-08-01', '西藏林周县', '西藏昂仁县', '政协办', '科员', '科员', '二类区', '否', '18289111808', '36');
INSERT INTO `leave_user` VALUES ('2393', '巴桑', '女', '1973-05-15', '1993-07-01', '西藏日喀则市聂拉木', '西藏日喀则市聂拉木', '纪委', '书记', '副县', '二类区', '是', '13648922386', '50');
INSERT INTO `leave_user` VALUES ('2394', '巴桑普赤', '女', '1974-09-28', '1994-07-01', '西藏日喀则市', '西藏日喀则市谢通门', '纪委', '副书记', '正科', '二类区', '否', '13618923386', '32');
INSERT INTO `leave_user` VALUES ('2395', '洛桑格旦', '男', '1983-01-10', '2007-07-01', '西藏拉萨市林周县', '西藏日喀则市谢通门', '纪委', '副科实职', '副科', '二类区', '否', '13308927755', '36');
INSERT INTO `leave_user` VALUES ('2396', '张洋', '男', '1983-01-06', '2006-07-01', '陕西省扶风县', '陕西省汉中市', '纪委', '副科实职', '副科', '二类区', '是', '13638926230', '50');
INSERT INTO `leave_user` VALUES ('2397', '焦红喜', '男', '1989-09-30', '2012-11-01', '甘肃省张掖市', '甘肃省张掖市高台县', '纪委', '副科实职', '副科', '二类区', '否', '15208000405', '50');
INSERT INTO `leave_user` VALUES ('2398', '王鹏', '男', '1989-02-25', '2012-11-01', '陕西省绥德县', '无', '纪委', '副主任科员', '副科', '二类区', '是', '13989989741', '50');
INSERT INTO `leave_user` VALUES ('2399', '李鹤', '男', '1990-08-17', '2012-11-01', '江西省九江市彭泽县', '无', '纪委', '副主任科员', '副科', '二类区', '是', '13659503675', '50');
INSERT INTO `leave_user` VALUES ('2400', '索朗德吉', '女', '1987-06-13', '2011-12-01', '西藏日喀则市', '甘肃省武威县', '纪委', '科员', '副科', '二类区', '是', '18798928017', '50');
INSERT INTO `leave_user` VALUES ('2401', '次仁央金', '女', '1991-05-31', '2014-11-01', '西藏日喀则市江孜县', '无', '纪委', '科员', '科员', '二类区', '否', '18898043096', '34');
INSERT INTO `leave_user` VALUES ('2402', '旦增桑珠', '男', '1992-02-26', '2014-11-01', '西藏日喀则市', '无', '纪委', '科员', '科员', '二类区', '否', '13908928801', '32');
INSERT INTO `leave_user` VALUES ('2403', '次央', '女', '1994-12-18', '2014-11-01', '西藏日喀则市江孜县', '无', '纪委', '科员', '科员', '二类区', '否', '18489180999', '34');
INSERT INTO `leave_user` VALUES ('2404', '格桑曲扎', '男', '1991-04-21', '2014-11-01', '西藏日喀则市江孜县', '无', '纪委', '科员', '科员', '二类区', '否', '18489120685', '34');
INSERT INTO `leave_user` VALUES ('2405', '巴旦拉姆', '女', '1994-10-29', '2014-11-01', '西藏日喀则市', '四川省宣汉县', '纪委', '科员', '科员', '二类区', '是', '13989926637', '50');
INSERT INTO `leave_user` VALUES ('2406', '尼玛卓玛', '女', '1988-10-09', '2013-07-15', '西藏日喀则市聂拉木', '无', '纪委', '科员', '科员', '二类区', '否', '18408924387', '34');
INSERT INTO `leave_user` VALUES ('2407', '索朗央吉', '女', '1989-04-29', '2012-02-01', '西藏日喀则市', '无', '纪委', '科员', '科员', '二类区', '否', '18708026165', '32');
INSERT INTO `leave_user` VALUES ('2408', '周磊', '男', '1991-01-08', '2014-12-01', '四川省雅安市', '无', '纪委', '科员', '科员', '二类区', '是', '18189022767', '50');
INSERT INTO `leave_user` VALUES ('2409', '久昂拉姆', '女', '1986-02-02', '2013-07-15', '西藏拉萨市', '西藏山南市乃东县', '纪委', '科员', '科员', '二类区', '是', '15889079421', '46');
INSERT INTO `leave_user` VALUES ('2410', '扎西次仁', '男', '1992-11-10', '2013-07-15', '西藏日喀则市', '西藏日喀则市仁布县', '纪委', '科员', '科员', '二类区', '是', '18389026776', '44');
INSERT INTO `leave_user` VALUES ('2411', '扎西央拉', '女', '1990-10-09', '2013-07-15', '西藏日喀则市', '西藏日喀则市南木林', '纪委', '科员', '科员', '二类区', '否', '18898023027', '34');
INSERT INTO `leave_user` VALUES ('2412', '王山林', '男', '1986-03-24', '2011-12-01', '河南', '河南', '娘热乡', '副乡长', '副科', '二类区', '是', '13628996600', '50');
INSERT INTO `leave_user` VALUES ('2413', '冷阿海', '男', '1985-03-01', '2007-11-01', '陕西凤县', '无', '组织部（编办）', '部长', '副县', '二类区', '是', '18109178505', '60');
INSERT INTO `leave_user` VALUES ('2414', '旦木真', '男', '1983-05-01', '2006-07-01', '西藏谢通门', '西藏日喀则', '组织部（编办）', '副部长', '正科', '二类区', '否', '13638926346', '32');
INSERT INTO `leave_user` VALUES ('2415', '米玛顿珠', '男', '1985-05-01', '2009-07-01', '西藏林芝', '西藏南木林', '组织部（编办）', '主任', '正科', '二类区', '否', '13659576061', '36');
INSERT INTO `leave_user` VALUES ('2416', '张洋国', '男', '1987-09-01', '2011-08-01', '甘肃临泽', '无', '组织部（编办）', '副部长', '副科', '二类区', '是', '13549085631', '50');
INSERT INTO `leave_user` VALUES ('2417', '旺扎', '男', '1989-08-01', '2012-07-01', '西藏南木林', '无', '老干局', '副局长', '副科', '二类区', '否', '18089970757', '34');
INSERT INTO `leave_user` VALUES ('2418', '王茸', '女', '1989-10-01', '2011-08-01', '四川绵阳', '无', '组织部（编办）', '副主任科员', '副科', '二类区', '是', '18208098511', '50');
INSERT INTO `leave_user` VALUES ('2419', '王赛兵', '男', '1989-12-01', '2012-10-01', '河南郏县', '无', '组织部（编办）', '副主任科员', '副科', '二类区', '是', '13398029701', '50');
INSERT INTO `leave_user` VALUES ('2420', '唐建波', '男', '1987-09-01', '2012-10-01', '四川蓬安', '无', '组织部（编办）', '副主任科员', '副科', '二类区', '是', '13618998137', '50');
INSERT INTO `leave_user` VALUES ('2421', '格桑旺堆', '男', '1990-09-01', '2014-11-01', '西藏仲巴', '无', '组织部（编办）', '科员', '科员', '二类区', '否', '18898029098', '34');
INSERT INTO `leave_user` VALUES ('2422', '达瓦普尺', '女', '1988-04-01', '2013-08-01', '西藏拉孜', '西藏拉萨', '组织部（编办）', '科员', '科员', '二类区', '否', '18389087779', '36');
INSERT INTO `leave_user` VALUES ('2423', '拉姆央金', '女', '1989-09-01', '2013-08-01', '西藏拉萨', '西藏日喀则', '塔定乡', '科员', '科员', '二类区', '否', '18798998690', '36');
INSERT INTO `leave_user` VALUES ('2424', '杨旭', '男', '1986-04-01', '2011-12-01', '四川安岳', '无', '组织部（编办）', '科员', '科员', '二类区', '是', '15289125987', '50');
INSERT INTO `leave_user` VALUES ('2425', '符勇', '男', '1983-05-01', '2013-12-01', '黑龙江', '无', '青都乡', '科员', '科员', '二类区', '是', '17789027661', '50');
INSERT INTO `leave_user` VALUES ('2426', '张泽儒', '男', '1990-01-01', '2013-12-01', '甘肃靖远', '无', '仁钦则乡', '科员', '科员', '二类区', '是', '18008920523', '50');
INSERT INTO `leave_user` VALUES ('2427', '杨康', '男', '1991-06-01', '2013-12-01', '江苏淮安', '无', '仁钦则乡', '科员', '科员', '二类区', '是', '18189086940', '50');
INSERT INTO `leave_user` VALUES ('2428', '罗增', '女', '1992-07-01', '2015-12-01', '西藏拉萨', '无', '春哲乡', '科员', '科员', '二类区', '否', '13659517783', '36');
INSERT INTO `leave_user` VALUES ('2429', '旦增伦珠', '男', '1991-03-01', '2014-11-01', '西藏日喀则', '无', '春哲乡', '科员', '科员', '二类区', '是', '18308098809', '32');
INSERT INTO `leave_user` VALUES ('2430', '彭忠建', '男', '1987-08-01', '2014-07-01', '贵州余庆', '无', '通门乡', '科员', '科员', '二类区', '是', '13549042751', '50');
INSERT INTO `leave_user` VALUES ('2431', '普琼', '男', '1975-03-12', '1995-03-12', '西藏萨迦县', '西藏日喀则', '宣传部', '部长', '副县', '二类区', '是', '13889029117', '50');
INSERT INTO `leave_user` VALUES ('2432', '田君', '女', '1983-11-13', '2007-07-01', '山西', '云南', '措布西乡', '副主席', '正科', '二类区', '否', '18089927687', '50');
INSERT INTO `leave_user` VALUES ('2433', '张小英', '女', '1988-05-10', '2011-08-15', '四川南充', '四川南充', '宣传部', '副部长', '副科', '二类区', '否', '18208099899', '50');
INSERT INTO `leave_user` VALUES ('2434', '多吉旺堆', '男', '1988-11-29', '2011-07-01', '日喀则市', '日喀则市', '文化综合执法大队', '队长', '副科', '二类区', '否', '13518927575', '32');
INSERT INTO `leave_user` VALUES ('2435', '次旺央宗', '女', '1991-01-08', '2013-08-01', '日喀则市南木林县', '萨迦县', '宣传部', '科员', '科员', '二类区', '否', '15708082365', '34');
INSERT INTO `leave_user` VALUES ('2436', '尼玛索朗', '男', '1991-12-08', '2013-08-01', '日喀则市', '日喀则市', '宣传部', '科员', '科员', '二类区', '是', '18308021155', '42');
INSERT INTO `leave_user` VALUES ('2437', '卓玛', '女', '1989-07-25', '2011-12-15', '西藏扎囊县', '西藏江孜', '文化综合执法大队', '科员', '科员', '二类区', '否', '18289029998', '36');
INSERT INTO `leave_user` VALUES ('2438', '米吉', '女', '1987-05-04', '2012-11-14', '西藏江孜', '西藏 拉孜', '文化综合执法大队', '科员', '科员', '二类区', '否', '15289123264', '34');
INSERT INTO `leave_user` VALUES ('2439', '赵聪聪', '女', '1992-10-03', '2015-07-01', '河南', '无', '宣传部', '科员', '科员', '二类区', '是', '18089926812', '50');
INSERT INTO `leave_user` VALUES ('2440', '余仕平', '男', '1992-07-17', '2015-12-09', '湖南', '无', '塔定乡', '科员', '科员', '二类区', '否', '18898022424', '50');
INSERT INTO `leave_user` VALUES ('2441', '小普琼', '男', '1974-03-01', '1995-07-01', '日喀则市吉隆县', '日喀则市', '统战部', '正科实职', '正科', '二类区', '否', '13628920333', '34');
INSERT INTO `leave_user` VALUES ('2442', '罗布顿珠', '男', '1981-02-01', '2001-07-01', '日喀则市', '白朗县', '统战部', '正科实职', '正科', '二类区', '否', '13989925688', '34');
INSERT INTO `leave_user` VALUES ('2443', '米玛普尺', '女', '1981-05-01', '2007-07-01', '谢通门县', '江孜县', '宗组办', '主任', '副科', '二类区', '否', '13628926292', '34');
INSERT INTO `leave_user` VALUES ('2444', '其米央宗', '女', '1986-09-01', '2011-12-01', '西藏自治区林周县', '谢通门', '宗组办', '副主任', '副科', '二类区', '否', '18798924068', '36');
INSERT INTO `leave_user` VALUES ('2445', '次日卓玛', '女', '1991-08-01', '2013-08-01', '日喀则市', '无', '统战部', '科员', '科员', '二类区', '否', '18408926549', '32');
INSERT INTO `leave_user` VALUES ('2446', '雷海坤', '男', '1987-08-01', '2013-12-01', '云南省晋宁县', '云南晋宁县', '统战部', '科员', '科员', '二类区', '是', '18008922277', '50');
INSERT INTO `leave_user` VALUES ('2447', '次巴', '女', '1987-09-01', '2012-02-01', '谢通门县', '谢通门县', '统战部', '科员', '科员', '二类区', '否', '17711973031', '30');
INSERT INTO `leave_user` VALUES ('2448', '扎西平措', '男', '1973-11-01', '1995-07-01', '西藏日喀则', '无', '统战部', '部长', '副县', '二类区', '否', '13518925575', '50');
INSERT INTO `leave_user` VALUES ('2449', '次仁', '男', '1969-10-01', '1989-02-27', '西藏康玛县', '无', '政法委', '书记', '副县', '二类区', '否', '13889021778', '50');
INSERT INTO `leave_user` VALUES ('2450', '扎西平措', '男', '1985-07-20', '2007-07-01', '西藏定结县', '西藏山南琼结县', '政法委', '主任', '正科', '二类区', '是', '15289020100', '46');
INSERT INTO `leave_user` VALUES ('2451', '次仁欧珠', '男', '1986-11-30', '2011-08-01', '西藏南木林县', '西藏日喀则市桑珠孜区', '政法委', '副主任', '副科', '二类区', '否', '18208026217', '34');
INSERT INTO `leave_user` VALUES ('2452', '鲁晓彤', '男', '1989-11-17', '2012-10-01', '四川乐山', '四川乐山', '政法委', '副书记', '副科', '二类区', '是', '18184993307', '50');
INSERT INTO `leave_user` VALUES ('2453', '仁青普赤', '女', '1988-09-15', '2011-08-01', '西藏日喀则市萨迦县', '西藏拉萨', '政法委', '副主任科员', '副科', '二类区', '否', '18308027818', '36');
INSERT INTO `leave_user` VALUES ('2454', '索朗拉宗', '女', '1988-05-18', '2011-12-01', '西藏山南', '昌都', '政法委', '副主任科员', '副科', '二类区', '否', '13908929917', '38');
INSERT INTO `leave_user` VALUES ('2455', '卿持恒', '男', '1991-11-18', '2012-11-01', '四川乐山', '无', '政法委', '科员', '科员', '二类区', '是', '18289022460', '50');
INSERT INTO `leave_user` VALUES ('2456', '单祖应', '男', '1988-11-25', '2010-12-01', '云南曲靖', '云南大理', '政法委', '科员', '科员', '二类区', '是', '15208002971', '50');
INSERT INTO `leave_user` VALUES ('2457', '普布片多', '女', '1988-03-12', '2012-02-15', '西藏日喀则市桑珠孜区', '西藏日喀则市桑珠孜区', '政法委', '科员', '科员', '二类区', '是', '18898046688', '42');
INSERT INTO `leave_user` VALUES ('2458', '尼玛顿珠', '男', '1980-10-26', '2005-07-01', '西藏拉萨', '西藏拉萨', '发改委', '主任', '正科', '二类区', '是', '13908929595', '46');
INSERT INTO `leave_user` VALUES ('2459', '汪林', '男', '1967-03-09', '1984-12-01', '黑龙江哈尔滨市', '无', '发改委', '副主任', '正科', '二类区', '是', '18898026587', '50');
INSERT INTO `leave_user` VALUES ('2460', '金美旺杰', '男', '1982-07-29', '2006-07-01', '西藏昌都', '西藏山南', '发改委', '主任科员', '正科', '二类区', '否', '13989026243', '38');
INSERT INTO `leave_user` VALUES ('2461', '李文利', '男', '1980-09-20', '2012-10-01', '四川达州', '四川达州', '发改委', '副主任', '副科', '二类区', '是', '13518929598', '50');
INSERT INTO `leave_user` VALUES ('2462', '扎西顿珠', '男', '1989-05-14', '2010-07-01', '西藏桑珠孜', '日喀则桑珠孜', '发改委', '副主任', '副科', '二类区', '是', '13648920624', '42');
INSERT INTO `leave_user` VALUES ('2463', '陈南均', '男', '1987-10-09', '2011-12-01', '四川成都', '无', '南木切乡', '副乡长', '副科', '二类区', '是', '18089003787', '50');
INSERT INTO `leave_user` VALUES ('2464', '旺姆', '女', '1983-08-01', '2005-07-01', '西藏萨迦', '西藏定日', '卡嘎镇', '副主任科员', '副科', '二类区', '否', '18089026007', '34');
INSERT INTO `leave_user` VALUES ('2465', '江彪', '男', '1988-12-15', '2013-08-01', '陕西西乡', '陕西周至县', '发改委', '科员', '科员', '二类区', '是', '13659563358', '50');
INSERT INTO `leave_user` VALUES ('2466', '边仓', '女', '1990-02-06', '2013-08-02', '西藏白朗', '西藏贡嘎', '发改委', '科员', '科员', '二类区', '否', '18889090905', '36');
INSERT INTO `leave_user` VALUES ('2467', '李耀', '男', '1989-01-18', '2013-10-01', '重庆开县', '重庆开县', '发改委', '科员', '科员', '二类区', '是', '18189923091', '50');
INSERT INTO `leave_user` VALUES ('2468', '王毅', '男', '1994-03-04', '2017-08-01', '河南淮阳', '无', '发改委', '科员', '科员', '二类区', '是', '18189011395', '50');
INSERT INTO `leave_user` VALUES ('2469', '郑文凤', '女', '1994-11-08', '2017-08-01', '四川内江', '无', '发改委', '科员', '科员', '二类区', '是', '17740727882', '50');
INSERT INTO `leave_user` VALUES ('2470', '边巴次仁', '男', '1990-08-11', '2013-08-01', '西藏定日', '无', '措布西乡', '科员', '科员', '二类区', '否', '18184988188', '34');
INSERT INTO `leave_user` VALUES ('2471', '扎西坚参', '男', '1991-04-24', '2014-11-01', '西藏谢通门', '西藏普兰', '纳当乡', '科员', '科员', '二类区', '是', '18189024446', '48');
INSERT INTO `leave_user` VALUES ('2472', '罗布', '男', '1969-04-02', '1989-07-01', '谢通门县', '日喀则市', '教育局', '局长', '正科', '二类区', '否', '13638921085', '32');
INSERT INTO `leave_user` VALUES ('2473', '次旺论珠', '男', '1989-08-13', '2012-06-01', '日喀则市南木林县', '定日县', '教育局', '副局长', '副科', '二类区', '否', '18089029243', '34');
INSERT INTO `leave_user` VALUES ('2474', '德庆次旺', '女', '1990-04-21', '2011-12-05', '日喀则市', '日喀则市', '教育局', '副局长', '副科', '二类区', '否', '15889008163', '32');
INSERT INTO `leave_user` VALUES ('2475', '顿珠卓玛', '女', '1976-04-20', '1993-04-01', '谢通门县', '谢通门县', '教育局', '副主任科员', '副科', '二类区', '否', '13989022809', '30');
INSERT INTO `leave_user` VALUES ('2476', '拉顿', '男', '1970-06-04', '1993-07-01', '亚东县帕里镇', '谢通门塔定乡', '民宗局', '局长', '正科', '二类区', '否', '13659569996', '34');
INSERT INTO `leave_user` VALUES ('2477', '玉拉', '女', '1983-12-10', '2008-07-01', '谢通门县荣玛乡', '聂拉木县', '民宗局', '副局长', '正科', '二类区', '否', '13618920753', '34');
INSERT INTO `leave_user` VALUES ('2478', '德吉卓嘎', '女', '1978-10-11', '1997-07-01', '日喀则市', '谢通门县达木夏乡', '民宗局', '副主任科员', '副科', '二类区', '否', '13989924431', '32');
INSERT INTO `leave_user` VALUES ('2479', '罗杰', '男', '1990-05-12', '2013-08-01', '西藏江孜县', '山南曲松县', '民宗局', '科员', '科员', '二类区', '是', '18708092828', '46');
INSERT INTO `leave_user` VALUES ('2480', '唐茹彬', '女', '1992-05-02', '2013-08-01', '四川省达州市', '无', '民宗局', '科员', '科员', '二类区', '是', '15208090788', '50');
INSERT INTO `leave_user` VALUES ('2481', '张乘龙', '男', '1988-11-20', '2013-12-01', '陕西省汉中市', '陕西省勉县', '民宗局', '科员', '科员', '二类区', '是', '15089057121', '50');
INSERT INTO `leave_user` VALUES ('2482', '陈勇宏', '男', '1991-05-09', '2017-08-17', '四川省达州市', '无', '民宗局', '科员', '科员', '二类区', '是', '18227751360', '50');
INSERT INTO `leave_user` VALUES ('2483', '达珍', '女', '1981-10-05', '2004-07-01', '西藏定日县', '西藏桑珠孜区', '民政局', '局长', '正科', '二类区', '否', '13908929821', '34');
INSERT INTO `leave_user` VALUES ('2484', '巴桑次仁', '男', '1982-10-22', '2005-06-01', '西藏仁布县', '西藏日喀则市', '民政局', '副局长', '正科', '二类区', '否', '13908923887', '34');
INSERT INTO `leave_user` VALUES ('2485', '格桑卓玛', '女', '1990-01-10', '2013-08-01', '西藏白朗县', '西藏日喀则市', '民政局', '科员', '科员', '二类区', '否', '13658923858', '34');
INSERT INTO `leave_user` VALUES ('2486', '米玛卓嘎', '女', '1992-09-19', '2013-08-01', '西藏江孜县', '无', '民政局', '科员', '科员', '二类区', '否', '18889022481', '34');
INSERT INTO `leave_user` VALUES ('2487', '罗斌', '男', '1994-04-23', '2013-12-01', '四川绵阳市', '无', '民政局', '办事员', '办事员', '二类区', '是', '18189988789', '50');
INSERT INTO `leave_user` VALUES ('2488', '代昆', '男', '1994-12-17', '2017-08-24', '云南曲靖市', '无', '民政局', '科员', '科员', '二类区', '是', '15188016838', '50');
INSERT INTO `leave_user` VALUES ('2489', '央宗', '女', '1985-09-17', '2011-01-01', '西藏康马县', '西藏谢通门县', '五保集中供养中心', '主任', '副科', '二类区', '否', '18798992077', '34');
INSERT INTO `leave_user` VALUES ('2490', '陆林玲', '女', '1986-12-20', '2011-08-01', '重庆合川市', '无', '财政局', '副局长', '副科', '二类区', '是', '17708906895', '50');
INSERT INTO `leave_user` VALUES ('2491', '谌勇', '男', '1985-08-28', '2011-12-01', '四川射洪县', '无', '达木夏乡', '副乡长', '副科', '二类区', '是', '15208032356', '50');
INSERT INTO `leave_user` VALUES ('2492', '平措', '男', '1988-04-19', '2013-08-01', '西藏谢通门县', '西藏日喀则', '财政局', '科员', '科员', '二类区', '是', '18289023131', '42');
INSERT INTO `leave_user` VALUES ('2493', '罗多', '男', '1990-03-04', '2013-08-01', '西藏昂仁县', '无', '财政局', '科员', '科员', '二类区', '否', '18143822121', '34');
INSERT INTO `leave_user` VALUES ('2494', '马彦阳', '男', '1992-10-15', '2012-10-01', '河南内黄', '无', '财政局', '科员', '科员', '二类区', '是', '17789027727', '50');
INSERT INTO `leave_user` VALUES ('2495', '龙珍', '女', '1988-05-25', '2011-11-01', '西藏亚东县', '无', '财政局', '科员', '科员', '二类区', '否', '13618929648', '34');
INSERT INTO `leave_user` VALUES ('2496', '益西卓玛', '女', '1990-04-09', '2014-11-01', '西藏林周县', '西藏堆龙德庆县', '财政局', '科员', '科员', '二类区', '否', '18208071531', '36');
INSERT INTO `leave_user` VALUES ('2497', '曲扎', '男', '1991-11-20', '2013-08-01', '西藏达孜县', '无', '财政局', '科员', '科员', '三类区', '否', '15289124872', '36');
INSERT INTO `leave_user` VALUES ('2498', '桑珠', '男', '1991-09-02', '2014-11-01', '西藏曲松县', '无', '财政局', '科员', '科员', '二类区', '否', '13308035028', '36');
INSERT INTO `leave_user` VALUES ('2499', '王健霖', '女', '1993-06-25', '2017-07-01', '江西婺源县', '无', '财政局', '科员', '科员', '二类区', '是', '18184982085', '50');
INSERT INTO `leave_user` VALUES ('2500', '王娜', '女', '1989-11-20', '2013-08-01', '陕西勉县', '无', '财政局', '科员', '科员', '二类区', '是', '17389916826', '50');
INSERT INTO `leave_user` VALUES ('2501', '旦增旺姆', '女', '1987-11-08', '2011-12-01', '西藏拉萨', '无', '后勤服务中心', '副主任', '副科', '二类区', '否', '13638910868', '36');
INSERT INTO `leave_user` VALUES ('2502', '边巴普赤', '女', '1984-09-08', '2005-07-01', '西藏日喀则', '西藏山南', '团县委', '书记', '正科', '二类区', '否', '13638925067', '36');
INSERT INTO `leave_user` VALUES ('2503', '边巴普尺', '女', '1991-08-27', '2013-08-01', '西藏拉孜县', '西藏林芝', '团县委', '科员', '科员', '二类区', '否', '15208098223', '36');
INSERT INTO `leave_user` VALUES ('2504', '格桑玉珍', '女', '1990-12-01', '2014-11-01', '西藏日喀则', '无', '财政局', '科员', '科员', '二类区', '否', '18689023021', '32');
INSERT INTO `leave_user` VALUES ('2505', '罗布曲珍', '女', '1982-06-01', '2004-07-01', '西藏加扎县', '通门县', '人社局', '副局长', '正科', '二类区', '否', '13628922288', '36');
INSERT INTO `leave_user` VALUES ('2506', '张莉', '女', '1971-08-25', '1993-06-01', '四川省资阳市', '无', '社保中心', '副主任', '副科', '二类区', '是', '13989921130', '50');
INSERT INTO `leave_user` VALUES ('2507', '简丹丹', '女', '1988-10-09', '2011-12-01', '四川省宗州市', '陕西咸阳', '人社局', '副主任科员', '副科', '二类区', '是', '13989027287', '50');
INSERT INTO `leave_user` VALUES ('2508', '洛桑卓嘎', '女', '1978-11-11', '1998-07-01', '西藏拉萨', '谢通门县', '社保中心', '科员', '科员', '二类区', '否', '13659576166', '36');
INSERT INTO `leave_user` VALUES ('2509', '白玛曲珍', '女', '1993-01-16', '2017-12-15', '山南市洛扎县', '无', '人社局', '科员', '科员', '二类区', '否', '13321416022', '36');
INSERT INTO `leave_user` VALUES ('2510', '索朗次仁', '男', '1990-07-01', '2011-12-01', '西藏拉萨', '无', '人事争议仲裁院', '院长', '副科', '二类区', '否', '18189086021', '36');
INSERT INTO `leave_user` VALUES ('2511', '罗桑曲培', '男', '1985-08-19', '2009-07-14', '西藏谢通门县', '西藏曲水县', '国土局', '局长', '正科', '二类区', '否', '15289021037', '36');
INSERT INTO `leave_user` VALUES ('2512', '王盼盼', '女', '1989-07-18', '2011-12-14', '四川省绵阳市', '甘肃定西', '国土局', '副局长', '副科', '二类区', '否', '13908989464', '50');
INSERT INTO `leave_user` VALUES ('2513', '林红', '女', '1975-09-12', '1994-07-14', '重庆市', '青海西宁', '国土局', '主任科员', '正科', '二类区', '是', '13908989464', '50');
INSERT INTO `leave_user` VALUES ('2514', '邓增罗珠', '男', '1983-08-03', '2007-07-14', '西藏昌都', '西藏拉萨', '国土局', '主任科员', '正科', '二类区', '是', '13989922207', '48');
INSERT INTO `leave_user` VALUES ('2515', '德吉卓嘎', '女', '1990-09-13', '2013-08-10', '西藏日喀则市', '青海格尔木', '国土局', '科员', '科员', '二类区', '是', '18489181263', '50');
INSERT INTO `leave_user` VALUES ('2516', '曹益', '男', '1992-11-16', '2012-12-14', '四川南充', '无', '国土局', '科员', '科员', '二类区', '是', '18143209208', '50');
INSERT INTO `leave_user` VALUES ('2517', '索朗', '男', '1989-04-14', '2012-02-14', '西藏日喀则市', '西藏拉萨', '国土局', '科员', '科员', '二类区', '是', '17789025111', '46');
INSERT INTO `leave_user` VALUES ('2518', '旦增平措', '男', '1984-05-01', '2006-07-01', '西藏南木林县', '西藏山南市', '环保局', '副局长', '副科', '二类区', '否', '13908921395', '36');
INSERT INTO `leave_user` VALUES ('2519', '杨敬', '男', '1986-11-01', '2012-11-01', '贵州龙里', '贵州龙里', '环保局', '科员', '科员', '二类区', '是', '18184988618', '50');
INSERT INTO `leave_user` VALUES ('2520', '拉旺仁青', '男', '1982-11-01', '2009-07-01', '岗巴县', '日喀则', '住建局', '局长', '正科', '二类区', '否', '13659567877', '34');
INSERT INTO `leave_user` VALUES ('2521', '索朗吨珠', '男', '1982-06-08', '2005-07-01', '拉萨市', '无', '住建局', '副局长', '正科', '二类区', '否', '13549023611', '36');
INSERT INTO `leave_user` VALUES ('2522', '许滨', '男', '1986-07-01', '2010-08-01', '四川省乐山市', '四川成都', '列巴乡', '副乡长', '副科', '二类区', '是', '13908906244', '50');
INSERT INTO `leave_user` VALUES ('2523', '德庆卓嘎', '女', '1986-12-01', '2008-07-01', '拉萨市', '日喀则', '住建局', '主任科员', '正科', '二类区', '否', '18908920140', '36');
INSERT INTO `leave_user` VALUES ('2524', '巴桑旦增', '男', '1991-05-08', '2013-08-01', '亚东', '无', '住建局', '科员', '科员', '二类区', '否', '18408929208', '34');
INSERT INTO `leave_user` VALUES ('2525', '扎西次仁', '男', '1979-12-01', '2003-07-01', '日喀则市', '日喀则市', '交通局', '局长', '正科', '二类区', '否', '13638925556', '32');
INSERT INTO `leave_user` VALUES ('2526', '次旺多吉', '男', '1982-05-01', '2002-07-01', '谢通门县', '通门县', '交通局', '副局长', '正科', '二类区', '否', '13659566555', '30');
INSERT INTO `leave_user` VALUES ('2527', '扎西石楠', '男', '1985-01-01', '2012-07-01', '萨嘎县', '日喀则市', '交通局', '副主任科员', '副科', '二类区', '是', '1520894345', '44');
INSERT INTO `leave_user` VALUES ('2528', '何炼', '男', '1987-09-01', '2012-11-01', '广西玉林市', '广西都安', '交通局', '副主任科员', '副科', '二类区', '否', '1700118333', '50');
INSERT INTO `leave_user` VALUES ('2529', '张扬', '男', '1992-11-01', '2014-12-01', '四川省渠县', '无', '交通局', '办事员', '办事员', '二类区', '是', '18143875473', '50');
INSERT INTO `leave_user` VALUES ('2530', '普布次仁', '男', '1980-09-01', '2005-07-01', '亚东县', '日喀则市', '水利局', '局长', '正科', '二类区', '是', '13308925554', '44');
INSERT INTO `leave_user` VALUES ('2531', '达仓', '女', '1974-03-01', '1994-07-01', '日喀则市', '江孜县', '水利局', '主任科员', '正科', '二类区', '是', '18089971110', '44');
INSERT INTO `leave_user` VALUES ('2532', '边巴普赤', '女', '1976-01-01', '1997-07-01', '白朗县', '通门县', '农牧综合服务中心', '副主任', '副科', '二类区', '否', '13989929921', '34');
INSERT INTO `leave_user` VALUES ('2533', '巴贵', '男', '1990-04-01', '2013-08-01', '江孜县', '江孜县', '水利局', '科员', '科员', '二类区', '是', '18489186692', '44');
INSERT INTO `leave_user` VALUES ('2534', '确卓', '女', '1991-04-01', '2013-07-01', '谢通门县', '昌都市芒康县', '水利局', '科员', '科员', '二类区', '是', '13549021171', '48');
INSERT INTO `leave_user` VALUES ('2535', '马国全', '男', '1992-05-01', '2015-07-01', '青海省', '无', '水利局', '科员', '科员', '二类区', '否', '17789025453', '50');
INSERT INTO `leave_user` VALUES ('2536', '李伟', '男', '1992-12-01', '2015-07-01', '青海省', '无', '水利局', '科员', '科员', '二类区', '否', '14709787717', '50');
INSERT INTO `leave_user` VALUES ('2537', '赵云朋', '男', '1973-07-06', '1994-08-10', '黑龙江兰西', '黑龙江', '农牧综合服务中心', '高级', '高级', '二类区', '是', '15504554527', '50');
INSERT INTO `leave_user` VALUES ('2538', '索朗', '男', '1979-03-01', '2000-07-01', '谢通门县', '日喀则市', '农牧局', '局长', '正科', '二类区', '否', '13889080812', '32');
INSERT INTO `leave_user` VALUES ('2539', '次仁旺多', '男', '1984-07-01', '2009-07-01', '西藏江孜', '西藏昌都', '农牧局', '副局长', '副科', '二类区', '否', '13549027177', '38');
INSERT INTO `leave_user` VALUES ('2540', '代朝龙', '男', '1986-02-01', '2012-08-01', '山东', '陕西', '农牧局', '副局长', '副科', '二类区', '是', '13308920547', '50');
INSERT INTO `leave_user` VALUES ('2541', '央宗', '女', '1978-06-12', '2003-07-01', '白朗县', '亚东县', '农牧局', '主任科员', '正科', '二类区', '否', '13889020223', '34');
INSERT INTO `leave_user` VALUES ('2542', '索朗卓玛', '女', '1989-03-25', '2013-08-01', '西藏日喀则亚东县', '无', '农牧局', '科员', '科员', '二类区', '否', '18989029707', '34');
INSERT INTO `leave_user` VALUES ('2543', '多吉顿珠', '男', '1978-09-08', '2005-05-01', '日喀则市南木林县', '拉萨市', '农牧综合服务中心', '副主任', '初级', '二类区', '否', '15889029989', '36');
INSERT INTO `leave_user` VALUES ('2544', '朗加多吉', '男', '1982-03-08', '2003-07-01', '岗巴县', '谢通门县', '商务局', '局长', '正科', '二类区', '否', '18108926662', '34');
INSERT INTO `leave_user` VALUES ('2545', '普布次仁', '南', '1985-07-01', '2007-07-01', '日喀则市', '谢通门县', '商务局', '副局长', '副科', '二类区', '否', '18008925851', '32');
INSERT INTO `leave_user` VALUES ('2546', '祁梅英', '女', '1979-06-05', '2002-07-01', '陕西省\n澄城县', '云南省\n禄劝县', '商务局', '主任科员', '正科', '二类区', '是', '13989026279', '50');
INSERT INTO `leave_user` VALUES ('2547', '冯靖', '南', '1992-02-01', '2014-07-01', '安微歙县', '无', '商务局', '科员', '科员', '二类区', '是', '17711972778', '50');
INSERT INTO `leave_user` VALUES ('2548', '央宗', '女', '1992-01-01', '2014-11-01', '日喀则市', '无', '商务局', '科员', '科员', '二类区', '否', '13659577597', '32');
INSERT INTO `leave_user` VALUES ('2549', '杨超', '男', '1983-06-01', '2006-07-01', '四川省西充县', '四川省南部县', '文广局', '局长', '正科', '二类区', '是', '13518926430', '50');
INSERT INTO `leave_user` VALUES ('2550', '扎西央宗', '女', '1990-12-01', '2012-08-01', '日喀则市', '无', '文广局', '副局长', '副科', '二类区', '否', '18308098215', '32');
INSERT INTO `leave_user` VALUES ('2551', '格桑卓玛', '女', '1980-03-01', '2000-07-01', '日喀则市', '日喀则市', '文广局', '主任科员', '正科', '二类区', '否', '13518925540', '32');
INSERT INTO `leave_user` VALUES ('2552', '张翼', '男', '1993-01-01', '2015-07-01', '陕西省蓝田县', '无', '文广局', '科员', '科员', '二类区', '是', '15208013165', '50');
INSERT INTO `leave_user` VALUES ('2553', '洛桑赤烈', '男', '1985-09-25', '2008-11-01', '青海省湟中县', '西藏拉萨', '文化广播影视服务站', '副站长', '副科', '二类区', '是', '13659572725', '50');
INSERT INTO `leave_user` VALUES ('2554', '普布扎西', '男', '1980-09-03', '2005-09-01', '西藏扎囊县', '西藏桑珠孜区', '卫计委', '卫生局局长', '正科', '二类区', '否', '18798991759', '36');
INSERT INTO `leave_user` VALUES ('2555', '多吉洛旦', '男', '1985-07-25', '2008-07-01', '定日县', '林芝县', '卫生局', '卫生局副局长', '正科', '二类区', '否', '18076923338', '36');
INSERT INTO `leave_user` VALUES ('2556', '张萍', '女', '1980-10-07', '2001-07-01', '甘肃省民勤县', '山西省兴县', '卫生局', '主任科员', '正科', '二类区', '是', '13659572026', '50');
INSERT INTO `leave_user` VALUES ('2557', '央宗次仁', '女', '1985-11-05', '2012-07-01', '西藏拉孜县', '西藏拉孜县', '卫生局', '科员', '科员', '二类区', '否', '18208020989', '34');
INSERT INTO `leave_user` VALUES ('2558', '张学军', '男', '1988-10-16', '2012-11-01', '山西', '无', '卫生局', '科员', '科员', '二类区', '是', '13908941747', '50');
INSERT INTO `leave_user` VALUES ('2559', '卢茹强', '男', '1991-06-25', '2012-11-01', '山东莒南', '无', '卫生局', '科员', '科员', '二类区', '是', '15208090756', '50');
INSERT INTO `leave_user` VALUES ('2560', '旺珍', '女', '1992-05-01', '2014-11-01', '日喀则市仁布县', '无', '卫生局', '科员', '科员', '二类区', '否', '18898043437', '34');
INSERT INTO `leave_user` VALUES ('2561', '吴中阳', '男', '1986-11-01', '2012-11-01', '江苏徐州', '无', '卫生局', '科员', '科员', '二类区', '是', '17789027710', '50');
INSERT INTO `leave_user` VALUES ('2562', '旦增', '男', '1974-01-01', '1997-07-01', '西藏江孜', '无', '卫生服务中心', '主任', '正科', '二类区', '否', '13989927088', '34');
INSERT INTO `leave_user` VALUES ('2563', '索朗次旦', '男', '1979-10-01', '2000-07-01', '西藏江孜', '无', '卫生服务中心', '副主任', '副科', '二类区', '否', '13648928528', '34');
INSERT INTO `leave_user` VALUES ('2564', '格桑旺久', '男', '1975-10-01', '1999-07-01', '西藏江孜', '无', '卫生服务中心', '副主任', '副科', '二类区', '否', '18989026699', '34');
INSERT INTO `leave_user` VALUES ('2565', '扎西罗布', '男', '1977-09-01', '1997-07-01', '西藏谢通门县', '西藏拉萨', '食药局', '局长', '正科', '二类区', '否', '18108927797', '36');
INSERT INTO `leave_user` VALUES ('2566', '普布仓决', '女', '1968-10-01', '1990-07-01', '西藏桑珠孜区', '西藏谢通门', '食药局', '主任科员', '正科', '二类区', '否', '18308026995', '32');
INSERT INTO `leave_user` VALUES ('2567', '次仁旺姆', '女', '1988-09-10', '2013-08-01', '西藏谢通门县', '西藏南木林', '食药局', '科员', '科员', '二类区', '否', '18898028558', '34');
INSERT INTO `leave_user` VALUES ('2568', '陈鸣', '男', '1992-04-15', '2016-07-01', '河南内黄', '河南内黄', '食药局', '科员', '科员', '二类区', '否', '18625820888', '50');
INSERT INTO `leave_user` VALUES ('2569', '其美', '男', '1984-04-01', '2009-07-01', '西藏昌都', '西藏拉萨', '安监局', '局长', '正科', '二类区', '否', '13638922050', '38');
INSERT INTO `leave_user` VALUES ('2570', '扎西顿珠', '男', '1986-08-01', '2010-08-01', '谢通门县', '定结县', '安监局', '副局长', '副科', '二类区', '是', '13889021138', '44');
INSERT INTO `leave_user` VALUES ('2571', '拉珍', '女', '1991-09-01', '2013-08-01', '日喀则市南木林县', '无', '安监局', '科员', '科员', '二类区', '否', '15289126264', '34');
INSERT INTO `leave_user` VALUES ('2572', '鲜奇君', '男', '1989-01-01', '2013-08-01', '四川射洪', '四川射洪', '安监局', '科员', '科员', '二类区', '是', '18662230119', '50');
INSERT INTO `leave_user` VALUES ('2573', '土旦罗布', '男', '1987-03-01', '2013-08-01', '西藏林芝', '无', '安监局', '科员', '科员', '二类区', '否', '13908922829', '36');
INSERT INTO `leave_user` VALUES ('2574', '李宝翠', '女', '1980-03-28', '2002-07-01', '陕西武功县', '陕西西安', '卡嘎镇', '副主席', '副科', '二类区', '是', '13908920238', '50');
INSERT INTO `leave_user` VALUES ('2575', '边巴次仁', '男', '1981-03-15', '2002-07-01', '西藏谢通门县', '日客则市', '林业局', '局长', '正科', '二类区', '否', '13658952299', '32');
INSERT INTO `leave_user` VALUES ('2576', '巴桑欧珠', '男', '1978-05-28', '1999-06-01', '西藏江孜县', '拉萨市', '林业局', '副局长', '正科', '二类区', '否', '13638924210', '36');
INSERT INTO `leave_user` VALUES ('2577', '小平', '男', '1974-06-01', '1996-07-02', '日客则市', '谢通门县', '林业局', '主任科员', '正科', '二类区', '否', '13989920440', '32');
INSERT INTO `leave_user` VALUES ('2578', '拉巴普赤', '女', '1977-07-06', '2000-07-22', '西藏白朗县', '日客则市', '林业局', '副主任科员', '副科', '二类区', '否', '13618921770', '34');
INSERT INTO `leave_user` VALUES ('2579', '毛永生', '男', '1987-06-22', '2013-08-01', '重庆市', '重庆市', '林业局', '科员', '科员', '二类区', '是', '17708094250', '50');
INSERT INTO `leave_user` VALUES ('2580', '达娃', '男', '1973-08-01', '1997-07-01', '西藏钦则乡', '西藏白朗', '总工会', '主席', '正科', '二类区', '否', '13889022066', '34');
INSERT INTO `leave_user` VALUES ('2581', '白玛卓嘎', '女', '1974-12-01', '1997-07-01', '西藏日日喀则定结县', '无', '总工会', '副主席', '副科', '二类区', '否', '18089975557', '34');
INSERT INTO `leave_user` VALUES ('2582', '应素红', '女', '1970-02-01', '1993-06-01', '河南省郾城县', '河北省保定市', '总工会', '副主任科员', '副科', '二类区', '是', '13989920191', '50');
INSERT INTO `leave_user` VALUES ('2583', '拉姆卓玛', '女', '1990-02-01', '2012-07-01', '西藏亚东县', '西藏吉隆县', '总工会', '科员', '科员', '二类区', '否', '18908922519', '34');
INSERT INTO `leave_user` VALUES ('2584', '杨丽慧', '女', '1985-06-01', '2013-08-01', '河南省新郑市', '河南省新郑市', '总工会', '科员', '科员', '二类区', '是', '15208024467', '50');
INSERT INTO `leave_user` VALUES ('2585', '边巴卓玛', '女', '1979-09-01', '1999-07-01', '拉萨市', '无', '妇联', '主席', '正科', '二类区', '否', '13989920861', '36');
INSERT INTO `leave_user` VALUES ('2586', '次仁卓玛', '女', '1986-05-04', '2013-08-01', '谢通门县', '谢通门县', '妇联', '科员', '科员', '二类区', '是', '13618920700', '42');
INSERT INTO `leave_user` VALUES ('2587', '单增卓玛', '女', '1982-01-13', '2004-07-01', '拉萨市', '日喀则', '妇联', '副主席', '副科', '二类区', '否', '13659576610', '36');
INSERT INTO `leave_user` VALUES ('2588', '拉巴次仁', '男', '1987-01-29', '2011-12-01', '日喀则市萨迦县', '日喀则南木林', '藏语委办', '副主任', '副科', '二类区', '否', '18289028905', '34');
INSERT INTO `leave_user` VALUES ('2589', '王达娃', '男', '1981-10-16', '2005-07-01', '四川阿坝', '日喀则市', '藏语委办', '主任', '正科', '二类区', '否', '13989925501', '50');
INSERT INTO `leave_user` VALUES ('2590', '索朗顿珠', '男', '1987-12-07', '2012-07-01', '拉萨市', '江孜县', '扶贫办', '副主任科员', '副科', '二类区', '是', '13648921184', '46');
INSERT INTO `leave_user` VALUES ('2591', '拉姆', '女', '1979-09-14', '2002-07-01', '日喀则市', '拉孜县', '扶贫办', '副主任', '副科', '二类区', '否', '13989022007', '34');
INSERT INTO `leave_user` VALUES ('2592', '贾浩', '男', '1992-08-05', '2012-11-01', '四川南充', '甘肃白银', '扶贫办', '科员', '科员', '二类区', '否', '17790188770', '50');
INSERT INTO `leave_user` VALUES ('2593', '巴桑仓决', '女', '1990-10-02', '2013-08-01', '江孜县', '江孜县', '扶贫办', '科员', '科员', '二类区', '是', '17789925020', '44');
INSERT INTO `leave_user` VALUES ('2594', '杨壹栋', '男', '1992-06-08', '2012-11-01', '河南嵩县', '无', '扶贫办', '科员', '科员', '二类区', '否', '18898021010', '50');
INSERT INTO `leave_user` VALUES ('2595', '霍明', '男', '1992-03-01', '2017-08-01', '黑龙江省鸡西市', '无', '扶贫办', '科员', '科员', '二类区', '是', '17711921175', '50');
INSERT INTO `leave_user` VALUES ('2596', '普巴确', '男', '1979-07-01', '2003-06-01', '谢通门县', '山南市', '扶贫办', '主任科员', '正科', '二类区', '否', '13889029966', '36');
INSERT INTO `leave_user` VALUES ('2597', '次仁', '男', '1980-09-10', '2001-07-01', '西藏林周', '无', '扶贫办', '主任科员', '正科', '二类区', '否', '18089976661', '36');
INSERT INTO `leave_user` VALUES ('2598', '边巴次仁', '男', '1982-05-23', '2006-06-01', '拉萨市', '陕西', '扶贫办', '主任科员', '正科', '二类区', '是', '15208099992', '50');
INSERT INTO `leave_user` VALUES ('2599', '普布卓玛', '女', '1988-10-10', '2012-11-01', '日喀则市萨嘎县', '亚东县', '扶贫办', '科员', '科员', '二类区', '是', '18708021068', '44');
INSERT INTO `leave_user` VALUES ('2600', '白玛普赤', '女', '1989-01-01', '2012-11-01', '康马县', '拉孜县', '扶贫办', '科员', '科员', '二类区', '是', '18798928838', '44');
INSERT INTO `leave_user` VALUES ('2601', '次旺欧珠', '男', '1968-07-03', '1989-08-01', '西藏日喀则', '西藏昌都', '法院', '院长', '副县', '二类区', '是', '13659570900', '50');
INSERT INTO `leave_user` VALUES ('2602', '普琼', '男', '1975-02-10', '1992-01-01', '西藏日喀则', '西藏日喀则', '法院', '副院长', '正科', '二类区', '是', '13908925222', '42');
INSERT INTO `leave_user` VALUES ('2603', '扎西卓玛', '女', '1978-10-01', '2001-07-01', '西藏日喀则', '西藏日喀则', '法院', '副院长', '正科', '二类区', '是', '15289128801', '42');
INSERT INTO `leave_user` VALUES ('2604', '于海波', '男', '1978-07-27', '1997-12-01', '黑龙江安达', '黑龙江安达', '法院', '副院长', '副科', '二类区', '是', '13614640088', '50');
INSERT INTO `leave_user` VALUES ('2605', '次仁多吉', '男', '1985-07-05', '2007-07-01', '西藏日喀则', '西藏拉萨', '法院', '正科实职', '正科', '二类区', '否', '13989928787', '36');
INSERT INTO `leave_user` VALUES ('2606', '顿珠多吉', '男', '1985-10-10', '2007-07-01', '西藏谢通门', '四川甘孜', '法院', '副科实职', '副科', '二类区', '是', '13549027272', '50');
INSERT INTO `leave_user` VALUES ('2607', '普布顿珠', '男', '1983-08-03', '2008-07-01', '西藏萨嘎县', '西藏日喀则', '法院', '局长', '副科', '二类区', '是', '13549024949', '44');
INSERT INTO `leave_user` VALUES ('2608', '格桑顿珠', '男', '1987-05-25', '2008-07-01', '西藏日喀则', '无', '法院', '副主任科员', '副科', '二类区', '否', '13989029681', '32');
INSERT INTO `leave_user` VALUES ('2609', '次仁央金', '女', '1992-05-15', '2013-08-01', '西藏日喀则', '西藏聂拉木', '法院', '科员', '科员', '二类区', '是', '18408922385', '44');
INSERT INTO `leave_user` VALUES ('2610', '白玛央宗', '女', '1991-12-01', '2013-08-01', '西藏昂仁县', '西藏昂仁县', '法院', '科员', '科员', '二类区', '是', '18389088090', '44');
INSERT INTO `leave_user` VALUES ('2611', '程伟桃', '男', '1991-08-07', '2014-07-01', '四川仁寿县', '四川仁寿县', '法院', '科员', '科员', '二类区', '是', '18689028098', '50');
INSERT INTO `leave_user` VALUES ('2612', '卓嘎', '女', '1991-08-02', '2015-12-01', '西藏贡嘎县', '西藏日喀则', '法院', '科员', '科员', '二类区', '是', '13628922057', '46');
INSERT INTO `leave_user` VALUES ('2613', '德吉卓玛', '女', '1994-02-07', '2015-12-01', '西藏桑日县', '无', '法院', '科员', '科员', '二类区', '否', '18289073245', '36');
INSERT INTO `leave_user` VALUES ('2614', '仁增朗杰', '男', '1991-04-04', '2017-01-01', '西藏浪卡子县', '无', '法院', '科员', '科员', '二类区', '否', '15208093934', '36');
INSERT INTO `leave_user` VALUES ('2615', '边巴罗布', '男', '1993-06-05', '2017-01-01', '西藏日喀则', '无', '法院', '科员', '科员', '二类区', '否', '18289094029', '32');
INSERT INTO `leave_user` VALUES ('2616', '格桑曲珍', '女', '1993-08-14', '2017-01-01', '西藏萨嘎县', '无', '法院', '科员', '科员', '二类区', '否', '15728920771', '34');
INSERT INTO `leave_user` VALUES ('2617', '翁文波', '男', '1980-10-01', '2006-07-01', '四川南江', '四川南江', '司法局', '局长', '正科', '二类区', '是', '13989921202', '50');
INSERT INTO `leave_user` VALUES ('2618', '德吉卓嘎', '女', '1976-10-01', '1999-07-01', '西藏谢通门', '西藏江孜', '司法局', '主任科员', '正科', '二类区', '否', '13618929119', '34');
INSERT INTO `leave_user` VALUES ('2619', '索朗普赤', '女', '1977-11-11', '2002-07-01', '西藏日喀则', '青海民和', '司法局', '主任科员', '正科', '二类区', '是', '17708922058', '50');
INSERT INTO `leave_user` VALUES ('2620', '索朗卓玛', '女', '1983-03-21', '2007-07-01', '西藏谢通门', '西藏日喀则', '司法局', '副局长', '副科', '二类区', '否', '17808925557', '32');
INSERT INTO `leave_user` VALUES ('2621', '张国强', '男', '1979-05-27', '2012-12-01', '甘肃', '甘肃', '司法局', '科员', '科员', '二类区', '是', '15289129562', '50');
INSERT INTO `leave_user` VALUES ('2622', '次普', '女', '1994-03-06', '2014-11-01', '西藏江孜', '无', '司法局', '科员', '科员', '二类区', '否', '18308022088', '34');
INSERT INTO `leave_user` VALUES ('2623', '张富波', '男', '1991-06-30', '2015-11-01', '四川攀枝花', '无', '司法局', '科员', '科员', '二类区', '是', '18030408654', '50');
INSERT INTO `leave_user` VALUES ('2624', '拉巴普赤', '女', '1991-05-01', '2016-01-01', '西藏日喀则', '西藏日喀则', '司法局', '科员', '科员', '二类区', '否', '18708028647', '32');
INSERT INTO `leave_user` VALUES ('2625', '南珍', '女', '1989-10-18', '2016-01-01', '西藏定结', '无', '司法局', '科员', '科员', '二类区', '否', '18308098247', '34');
INSERT INTO `leave_user` VALUES ('2626', '李杰', '男', '1994-03-15', '2015-12-01', '甘肃甘谷', '无', '司法局', '科员', '科员', '二类区', '否', '13398043568', '50');
INSERT INTO `leave_user` VALUES ('2627', '德吉央宗', '女', '1993-05-15', '2015-12-01', '西藏拉萨', '无', '司法局', '科员', '科员', '二类区', '否', '18489105623', '36');
INSERT INTO `leave_user` VALUES ('2628', '李金柏', '男', '1979-10-15', '2005-07-01', '云南大理', '河北乐亭', '卡嘎镇', '书记', '正科', '二类区', '是', '18308099393', '50');
INSERT INTO `leave_user` VALUES ('2629', '巴桑欧珠', '男', '1975-05-22', '1998-07-01', '日喀则市江孜县', '谢通门县', '卡嘎镇', '副书记', '正科', '二类区', '否', '13989026272', '34');
INSERT INTO `leave_user` VALUES ('2630', '旺堆次仁', '男', '1973-10-15', '1993-07-01', '日喀则市康马县', '拉萨市', '卡嘎镇', '主席', '正科', '二类区', '否', '13549021114', '34');
INSERT INTO `leave_user` VALUES ('2631', '尼玛曲珍', '女', '1986-06-02', '2009-07-01', '拉萨市', '拉萨市', '卡嘎镇', '副书记', '正科', '二类区', '是', '18289121113', '46');
INSERT INTO `leave_user` VALUES ('2632', '尼拉', '女', '1979-11-03', '2002-07-01', '日喀则市', '谢通门县', '卡嘎镇', '主任科员', '正科', '二类区', '否', '13518921000', '32');
INSERT INTO `leave_user` VALUES ('2633', '顿珠扎西', '男', '1984-10-31', '2008-08-01', '日喀则市岗巴县', '无', '卡嘎镇', '所长', '正科', '二类区', '否', '13549022119', '34');
INSERT INTO `leave_user` VALUES ('2634', '邸亮', '男', '1985-05-08', '2009-07-01', '甘肃民勤', '甘肃民勤', '卡嘎镇', '副书记', '正科', '二类区', '是', '15889029043', '50');
INSERT INTO `leave_user` VALUES ('2635', '张娟', '女', '1987-06-15', '2011-12-01', '四川南部县', '山西临猗县', '卡嘎镇', '纪委书记', '副科', '二类区', '否', '13889099094', '50');
INSERT INTO `leave_user` VALUES ('2636', '索朗', '男', '1987-10-01', '2011-08-01', '西藏萨迦县', '西藏拉萨市', '卡嘎镇', '副乡长', '副科', '二类区', '否', '15208025929', '36');
INSERT INTO `leave_user` VALUES ('2637', '次仁措姆', '女', '1982-10-01', '2006-07-01', '拉萨市尼木县', '日喀则市', '卡嘎镇', '副乡长', '副科', '二类区', '否', '18089923566', '36');
INSERT INTO `leave_user` VALUES ('2638', '次吉', '女', '1980-06-14', '1999-07-01', '日喀则市', '日喀则市亚东县', '卡嘎镇', '副乡长', '副科', '二类区', '否', '13989923138', '34');
INSERT INTO `leave_user` VALUES ('2639', '巴桑贵吉', '男', '1975-10-08', '1995-07-01', '日喀则市谢通门县', '无', '铜布寺管委会', '主任', '正科', '二类区', '否', '15889023688', '30');
INSERT INTO `leave_user` VALUES ('2640', '白玛央金', '女', '1984-03-14', '2010-08-01', '拉萨市', '日喀则市江孜县', '铜布寺管委会', '副主任', '副科', '二类区', '否', '13908920841', '36');
INSERT INTO `leave_user` VALUES ('2641', '旺堆加布', '男', '1990-02-10', '2012-07-01', '日喀则市桑珠孜区', '日喀则市仁布县', '铜布寺管委会', '科员', '科员', '二类区', '是', '18189088955', '44');
INSERT INTO `leave_user` VALUES ('2642', '申宇涛', '男', '1991-10-19', '2014-11-01', '陕西靖边', '无', '卡嘎镇', '科员', '科员', '二类区', '是', '18189082671', '50');
INSERT INTO `leave_user` VALUES ('2643', '格桑卓玛', '女', '1990-04-08', '2013-07-01', '日喀则市南木林县', '拉萨', '卡嘎镇', '科员', '科员', '二类区', '是', '17789021023', '46');
INSERT INTO `leave_user` VALUES ('2644', '刘莉', '女', '1989-12-25', '2013-07-01', '江苏', '江苏', '卡嘎镇', '科员', '科员', '二类区', '是', '18898016267', '50');
INSERT INTO `leave_user` VALUES ('2645', '陈芬', '女', '1993-11-11', '2017-09-01', '浙江省苍南县', '无', '卡嘎镇', '科员', '科员', '二类区', '是', '15726819421', '50');
INSERT INTO `leave_user` VALUES ('2646', '贵桑群宗', '女', '1994-07-02', '2017-12-01', '日喀则市谢通门县', '无', '卡嘎镇', '科员', '科员', '二类区', '否', '15208020262', '30');
INSERT INTO `leave_user` VALUES ('2647', '白玛', '女', '1989-12-01', '2014-11-01', '日喀则市江孜县', '无', '卡嘎镇', '科员', '科员', '二类区', '否', '13618927351', '34');
INSERT INTO `leave_user` VALUES ('2648', '仓木琼', '女', '1990-07-20', '2014-11-02', '日喀则市', '无', '卡嘎镇', '科员', '科员', '二类区', '否', '13308928301', '32');
INSERT INTO `leave_user` VALUES ('2649', '王玉成', '男', '1992-01-01', '2017-08-01', '甘肃镇原', '无', '卡嘎镇', '科员', '科员', '二类区', '是', '13061983771', '50');
INSERT INTO `leave_user` VALUES ('2650', '洛丹', '男', '1994-01-10', '2017-01-01', '日喀则市', '无', '卡嘎镇', '科员', '科员', '二类区', '否', '18989022200', '32');
INSERT INTO `leave_user` VALUES ('2651', '白玛央拉', '女', '1994-10-26', '2015-12-01', '日喀则市吉隆县', '日喀则市', '卡嘎镇', '科员', '科员', '二类区', '否', '13322525050', '34');
INSERT INTO `leave_user` VALUES ('2652', '多多', '男', '1963-08-13', '2014-11-01', '日喀则市谢通门县', '日喀则市谢通门县', '卡嘎镇', '科员', '科员', '二类区', '否', '15889023958', '30');
INSERT INTO `leave_user` VALUES ('2653', '洪斌', '男', '1992-09-27', '2015-12-01', '浙江省瑞安市', '无', '卡嘎镇', '科员', '科员', '二类区', '是', '17711925543', '50');
INSERT INTO `leave_user` VALUES ('2654', '边巴顿珠', '男', '1994-05-01', '2015-12-01', '西藏萨迦县', '无', '卡嘎镇', '科员', '科员', '二类区', '否', '18143206175', '34');
INSERT INTO `leave_user` VALUES ('2655', '达瓦次仁', '男', '1977-03-01', '1999-07-01', '日喀则市', '谢通门县', '通门乡', '主席', '正科', '二类区', '否', '13628921776', '32');
INSERT INTO `leave_user` VALUES ('2656', '王原', '男', '1975-07-01', '1994-05-01', '四川遂宁', '四川遂宁', '通门乡', '乡长', '正科', '二类区', '是', '17740728999', '50');
INSERT INTO `leave_user` VALUES ('2657', '李娟', '女', '1987-08-01', '2011-07-01', '四川大邑', '四川乐山', '通门乡', '副书记', '副科', '二类区', '否', '17789025061', '50');
INSERT INTO `leave_user` VALUES ('2658', '黄金海', '男', '1990-04-01', '2012-12-01', '江西赣州', '青海互助', '通门乡', '纪委书记', '副科', '二类区', '否', '17789022450', '50');
INSERT INTO `leave_user` VALUES ('2659', '旦增桑布', '男', '1986-02-01', '2011-12-01', '林芝市察隅县', '日喀则市拉孜县', '通门乡', '副乡长', '副科', '二类区', '否', '18008927327', '36');
INSERT INTO `leave_user` VALUES ('2660', '央拉', '女', '1977-09-01', '1994-05-01', '日喀则市谢通门县', '日喀则市', '通门乡', '副乡长', '正科', '二类区', '否', '13989026857', '32');
INSERT INTO `leave_user` VALUES ('2661', '次旦卓嘎', '女', '1982-10-01', '2004-07-01', '拉萨市墨竹工卡县', '谢通门县', '通门乡', '副书记', '正科', '二类区', '否', '18076921332', '36');
INSERT INTO `leave_user` VALUES ('2662', '次旦罗布', '男', '1993-06-01', '2014-11-01', '日喀则市', '无', '通门乡', '科员', '科员', '二类区', '否', '13989922925', '32');
INSERT INTO `leave_user` VALUES ('2663', '徐金明', '男', '1992-12-01', '2015-12-01', '甘肃天祝', '无', '通门乡', '科员', '科员', '二类区', '是', '15289095697', '50');
INSERT INTO `leave_user` VALUES ('2664', '嘎措', '女', '1992-05-01', '2016-12-01', '那曲地区', '无', '通门乡', '科员', '科员', '二类区', '否', '13989997466', '38');
INSERT INTO `leave_user` VALUES ('2665', '次仁珍拉', '女', '1990-02-01', '2013-08-01', '日喀则市', '日喀则市', '通门乡', '科员', '科员', '二类区', '是', '18189065311', '42');
INSERT INTO `leave_user` VALUES ('2666', '卓玛央金（大）', '女', '1990-03-01', '2013-08-01', '山南市', '山南市', '通门乡', '科员', '科员', '二类区', '否', '18408927244', '36');
INSERT INTO `leave_user` VALUES ('2667', '德青曲珍', '女', '1992-08-01', '2015-12-01', '林芝市波密县', '日喀则市', '通门乡', '科员', '科员', '二类区', '否', '18798940841', '36');
INSERT INTO `leave_user` VALUES ('2668', '孙伟', '男', '1994-07-01', '2017-08-01', '四川万源', '无', '通门乡', '科员', '科员', '二类区', '是', '17711987809', '50');
INSERT INTO `leave_user` VALUES ('2669', '简相辉', '男', '1988-08-01', '2017-08-01', '河南信阳', '无', '通门乡', '科员', '科员', '二类区', '是', '17689529528', '50');
INSERT INTO `leave_user` VALUES ('2670', '陈天飞', '男', '1994-05-17', '2017-08-01', '四川眉山市彭山县', '请选择省份请选择城市请选择区县', '通门乡', '科员', '科员', '二类区', '否', '18089922014', '50');
INSERT INTO `leave_user` VALUES ('2671', '曲培伦珠', '男', '1955-09-01', '2013-11-05', '谢通门县', '通门乡', '通门乡', '办事员', '办事员', '二类区', '否', '18798928650', '30');
INSERT INTO `leave_user` VALUES ('2672', '伟色', '女', '1980-11-01', '2001-07-01', '西藏拉萨', '西藏日喀则', '通门乡', '书记', '科员', '二类区', '是', '15889021226', '46');
INSERT INTO `leave_user` VALUES ('2673', '次平', '男', '1983-06-01', '2007-01-01', '西藏江孜', '西藏日喀则', '通门乡派出所', '所长', '正科', '二类区', '否', '13989025230', '34');
INSERT INTO `leave_user` VALUES ('2674', '李刚', '男', '1978-07-01', '2000-07-01', '甘肃省', '四川省南充市', '通门乡派出所', '副所长', '副科', '二类区', '是', '17711926661', '50');
INSERT INTO `leave_user` VALUES ('2675', '旺堆', '男', '1988-06-01', '2011-11-01', '日喀则市萨迦县', '山南市错那县', '通门乡派出所', '副主任科员', '副主任科员', '二类区', '否', '17740735550', '36');
INSERT INTO `leave_user` VALUES ('2676', '蒋东良', '男', '1987-02-01', '2012-11-01', '四川达州', '无', '通门乡', '科员', '科员', '二类区', '是', '18308093847', '50');
INSERT INTO `leave_user` VALUES ('2677', '尼玛多吉', '男', '1990-11-01', '2011-07-01', '西藏日喀则', '西藏亚东', '通门乡', '副乡长', '副科', '二类区', '是', '18989924818', '42');
INSERT INTO `leave_user` VALUES ('2678', '其美拉宗', '女', '1990-07-01', '2013-08-01', '西藏南木林', '无', '通门乡', '副主任科员', '副科', '二类区', '否', '15208096683', '34');
INSERT INTO `leave_user` VALUES ('2679', '拉巴琼达', '女', '1981-06-01', '2004-07-01', '日喀则市', '谢通门县', '扎西吉培寺管委会', '副主任', '正科', '二类区', '否', '13638922270', '32');
INSERT INTO `leave_user` VALUES ('2680', '米玛顿珠', '男', '1979-10-01', '2001-07-01', '日喀则市', '林芝市巴宜区', '扎西吉培寺管委会', '副主任科员', '正科', '二类区', '否', '13989070966', '36');
INSERT INTO `leave_user` VALUES ('2681', '普布次仁', '男', '1976-09-01', '2006-07-01', '康马县', '康马县', '扎西吉培寺管委会', '科员', '科员', '二类区', '是', '13518928131', '32');
INSERT INTO `leave_user` VALUES ('2682', '杜伟', '男', '1987-11-01', '2012-07-01', '江苏', '日喀则市', '扎西吉培寺管委会', '副主任科员', '副科', '二类区', '是', '13989999979', '50');
INSERT INTO `leave_user` VALUES ('2683', '李秋玲', '女', '1977-08-01', '1996-12-01', '河南商丘', '四川广汉市', '扎西吉培寺管委会', '科员', '科员', '二类区', '是', '13658926262', '50');
INSERT INTO `leave_user` VALUES ('2684', '赤列', '女', '1986-01-01', '2010-07-02', '谢通门县', '山南市曲松县', '扎西吉培寺管委会', '副主任', '副科', '二类区', '是', '18708098360', '46');
INSERT INTO `leave_user` VALUES ('2685', '洛桑旦增', '男', '1987-08-01', '2008-07-03', '拉萨市', '无', '扎西吉培寺管委会', '科员', '科员', '二类区', '否', '17711978865', '36');
INSERT INTO `leave_user` VALUES ('2686', '班久', '男', '1983-05-01', '2005-07-01', '西藏江孜县', '日喀则市白朗县', '塔定乡', '书记', '正科', '二类区', '否', '13989029977', '34');
INSERT INTO `leave_user` VALUES ('2687', '蒲伟', '男', '1984-08-01', '2006-07-01', '四川南充市', '河南省', '塔定乡', '乡长', '正科', '二类区', '否', '13989026302', '50');
INSERT INTO `leave_user` VALUES ('2688', '普布曲珍', '女', '1984-01-01', '2005-07-01', '西藏山南地区', '无', '塔定乡', '主席', '正科', '二类区', '否', '17889089666', '36');
INSERT INTO `leave_user` VALUES ('2689', '巴桑普尺', '女', '1986-06-01', '2008-07-01', '西藏日喀则市', '西藏日喀则市', '塔定乡', '副书记', '正科', '二类区', '是', '13889024204', '42');
INSERT INTO `leave_user` VALUES ('2690', '边巴次仁', '男', '1982-12-01', '2005-07-01', '西藏日喀则市', '无', '塔定乡', '副书记', '副科', '二类区', '否', '15889021116', '32');
INSERT INTO `leave_user` VALUES ('2691', '白央', '女', '1991-02-01', '2012-02-01', '西藏日喀则市', '西藏日喀则市', '塔定乡', '副乡长', '副科', '二类区', '是', '18208023854', '42');
INSERT INTO `leave_user` VALUES ('2692', '次仁央吉', '女', '1991-01-01', '2013-08-01', '西藏江孜县', '西藏日喀则市', '塔定乡', '副主任科员', '副科', '二类区', '是', '17711985556', '44');
INSERT INTO `leave_user` VALUES ('2693', '群财多杰', '男', '1984-03-01', '2007-01-01', '西藏日喀则市', '无', '塔定乡派出所', '所长', '正科', '二类区', '否', '13989920079', '32');
INSERT INTO `leave_user` VALUES ('2694', '次旺拉姆', '女', '1992-11-01', '2014-11-01', '西藏仁布县', '拉萨市林周县', '塔定乡', '科员', '科员', '二类区', '否', '17789928701', '36');
INSERT INTO `leave_user` VALUES ('2695', '孙启超', '男', '1990-11-01', '2017-08-01', '山东省泰安市', '无', '塔定乡', '科员', '科员', '二类区', '是', '18143228008', '50');
INSERT INTO `leave_user` VALUES ('2696', '郑雪', '女', '1994-12-01', '2017-08-01', '浙江省温州市', '无', '塔定乡', '科员', '科员', '二类区', '是', '18395930767', '50');
INSERT INTO `leave_user` VALUES ('2697', '张欣欣', '女', '1988-04-01', '2011-08-01', '重庆', '无', '塔定乡', '副乡长', '副科', '二类区', '是', '18289094060', '50');
INSERT INTO `leave_user` VALUES ('2698', '张斌斌', '男', '1986-01-10', '2010-08-01', '河南', '无', '塔定乡派出所', '副所长', '副科', '二类区', '是', '17789027890', '50');
INSERT INTO `leave_user` VALUES ('2699', '嘎珍', '男', '1980-02-16', '2004-07-01', '西藏拉萨', '无', '塔定乡', '纪委书记', '正科', '二类区', '是', '13659565545', '46');
INSERT INTO `leave_user` VALUES ('2700', '德吉卓嘎', '女', '1900-01-01', '2014-11-01', '西藏日喀则', '西藏昌都', '塔定乡', '科员', '科员', '二类区', '是', '13908928820', '48');
INSERT INTO `leave_user` VALUES ('2701', '尼玛卓嘎', '女', '1982-04-01', '2006-07-01', '西藏日喀则', '无', '塔定乡', '主任科员', '副科', '二类区', '否', '13549025676', '32');
INSERT INTO `leave_user` VALUES ('2702', '罗布加拉', '男', '1980-04-01', '2000-07-01', '西藏谢通门', '无', '日加寺管委会', '主任', '正科', '二类区', '否', '17708926680', '30');
INSERT INTO `leave_user` VALUES ('2703', '郎杰曲珍', '女', '1984-05-01', '2009-07-01', '西藏拉萨', '西藏那曲', '日加寺管委会', '副主任', '副科', '二类区', '是', '13549062868', '48');
INSERT INTO `leave_user` VALUES ('2704', '杨绣花', '女', '1970-02-01', '1993-06-01', '甘肃', '无', '日加寺管委会', '科员', '科员', '二类区', '否', '13889023910', '50');
INSERT INTO `leave_user` VALUES ('2705', '曲珍', '女', '1991-11-01', '2013-08-01', '西藏南木林', '无', '铜布寺管委会', '科员', '科员', '二类区', '否', '12345678910', '34');
INSERT INTO `leave_user` VALUES ('2706', '顿珠', '男', '1993-05-01', '1993-07-01', '西藏谢通门', '西藏日喀则市', '日加寺管委会', '办事员', '办事员', '二类区', '是', '13659567543', '42');
INSERT INTO `leave_user` VALUES ('2707', '次穷', '男', '1979-03-20', '2002-07-01', '日喀则市', '日喀则市', '荣玛乡', '书记', '正科', '二类区', '否', '13989024746', '34');
INSERT INTO `leave_user` VALUES ('2708', '岳国宝', '男', '1982-01-20', '2006-10-01', '吉林省农安县', '四川岳池县', '荣玛乡', '乡长', '正科', '二类区', '是', '13659579192', '50');
INSERT INTO `leave_user` VALUES ('2709', '欧瓦次仁', '男', '1980-11-23', '2002-07-01', '谢通门县', '日喀则市', '荣玛乡', '主席', '正科', '二类区', '否', '13989922300', '32');
INSERT INTO `leave_user` VALUES ('2710', '莎珍', '女', '1982-11-18', '2006-07-01', '日喀则市仁布县', '江孜县', '荣玛乡', '副书记', '正科', '二类区', '是', '18989020990', '44');
INSERT INTO `leave_user` VALUES ('2711', '扎西巴珠', '男', '1987-10-04', '2011-12-01', '错那县', '米林县', '荣玛乡', '副书记', '副科', '二类区', '否', '15289026106', '36');
INSERT INTO `leave_user` VALUES ('2712', '时若男', '女', '1987-04-16', '2011-10-01', '山西省运城', '四川省遂宁', '荣玛乡', '纪委书记', '副科', '二类区', '否', '13989022901', '50');
INSERT INTO `leave_user` VALUES ('2713', '欧阳魏魏', '男', '1988-04-02', '2012-10-01', '广东省南雄县', '广东省南雄县', '荣玛乡', '副乡长', '副科', '二类区', '是', '18108924488', '50');
INSERT INTO `leave_user` VALUES ('2714', '旦增央宗', '女', '1987-01-18', '2011-08-01', '聂拉木', '谢通门县', '荣玛乡', '副乡长', '副科', '二类区', '是', '15889020729', '44');
INSERT INTO `leave_user` VALUES ('2715', '唐次仁', '男', '1987-09-05', '2011-12-01', '四川省乐至县', '四川中江县', '荣玛乡', '副乡长', '副科', '二类区', '是', '18189916381', '50');
INSERT INTO `leave_user` VALUES ('2716', '贡嘎旺久', '男', '1988-09-10', '2009-07-01', '谢通门县', '谢通门县', '荣玛乡', '副主任科员', '副科', '二类区', '否', '18189087779', '30');
INSERT INTO `leave_user` VALUES ('2717', '白玛赤列', '女', '1989-03-15', '2012-07-01', '亚东县', '山南贡嘎县', '荣玛乡', '所长', '副科', '二类区', '是', '17708917594', '46');
INSERT INTO `leave_user` VALUES ('2718', '噶旦朗加', '男', '1988-02-23', '2008-08-01', '改则县', '墨竹工卡县', '荣玛乡派出所', '所长', '正科', '二类区', '否', '13889020843', '38');
INSERT INTO `leave_user` VALUES ('2719', '旦增', '男', '1991-08-25', '2013-07-01', '江孜县', '无', '荣玛乡', '副主任科员', '副科', '二类区', '否', '18389086966', '34');
INSERT INTO `leave_user` VALUES ('2720', '索朗达娃', '男', '1995-05-08', '2017-01-01', '江孜县', '无', '荣玛乡', '科员', '科员', '二类区', '否', '13638986070', '34');
INSERT INTO `leave_user` VALUES ('2721', '益西曲珍', '女', '1994-05-28', '2017-12-01', '日喀则市萨嘎县', '无', '荣玛乡', '科员', '科员', '二类区', '否', '18889027799', '34');
INSERT INTO `leave_user` VALUES ('2722', '李军座', '男', '1989-08-01', '2015-07-01', '辽宁省岫岩县', '无', '荣玛乡', '科员', '科员', '二类区', '否', '15208008069', '50');
INSERT INTO `leave_user` VALUES ('2723', '査明鹏', '男', '1995-08-22', '2017-08-01', '安徽省安庆市', '无', '荣玛乡', '科员', '科员', '二类区', '否', '17740701174', '50');
INSERT INTO `leave_user` VALUES ('2724', '蔡亮亮', '男', '1990-10-05', '2017-08-01', '湖北荆州', '无', '荣玛乡', '科员', '科员', '二类区', '否', '17711987712', '50');
INSERT INTO `leave_user` VALUES ('2725', '普布次仁', '男', '1987-12-10', '2011-11-01', '日喀则市仁布县', '日喀则市', '荣玛乡派出所', '科员', '科员', '二类区', '是', '13989003717', '42');
INSERT INTO `leave_user` VALUES ('2726', '苗旭兵', '男', '1992-12-30', '2012-11-01', '河南省舞阳县', '河南省舞阳县', '荣玛乡派出所', '科员', '科员', '二类区', '是', '18389086506', '50');
INSERT INTO `leave_user` VALUES ('2727', '扎西平措', '男', '1993-04-15', '2013-08-01', '拉萨市', '林芝', '荣玛乡派出所', '科员', '科员', '二类区', '否', '13518907671', '36');
INSERT INTO `leave_user` VALUES ('2728', '多吉普拉', '男', '1981-05-01', '2003-07-01', '日喀则市拉孜县', '无', '达那答乡', '副主任', '副县', '三类区', '否', '13989922007', '60');
INSERT INTO `leave_user` VALUES ('2729', '黄波', '女', '1977-11-01', '2001-07-01', '四川犍为', '陕西', '达那答乡', '乡长', '正科', '三类区', '是', '13659574428', '60');
INSERT INTO `leave_user` VALUES ('2730', '南木加曲珍', '女', '1986-01-01', '2008-07-01', '日喀则市江孜县', '无', '达那答乡', '主席', '正科', '三类区', '否', '18389084774', '44');
INSERT INTO `leave_user` VALUES ('2731', '白卫小', '男', '1986-11-01', '2012-12-01', '山西吕梁', '无', '达那答乡', '副书记', '副科', '三类区', '是', '15089025607', '60');
INSERT INTO `leave_user` VALUES ('2732', '米梅', '女', '1975-11-01', '1996-07-01', '亚东县', '萨迦县', '达那答乡', '副乡长', '正科', '三类区', '是', '13989927266', '54');
INSERT INTO `leave_user` VALUES ('2733', '索朗央金', '女', '1987-07-01', '2010-10-01', '那曲巴青', '无', '达那答乡', '副书记', '副科', '三类区', '否', '17888022171', '48');
INSERT INTO `leave_user` VALUES ('2734', '阿旺白姆', '女', '1989-11-01', '2011-12-01', '拉萨市', '无', '达那答乡', '副科实职', '副科', '三类区', '否', '18708020806', '46');
INSERT INTO `leave_user` VALUES ('2735', '邓莎', '女', '1987-05-01', '2011-12-01', '贵州', '无', '达那答乡', '副科实职', '副科', '二类区', '否', '13322515657', '50');
INSERT INTO `leave_user` VALUES ('2736', '巴桑赤列', '男', '1973-06-01', '2012-09-01', '谢通门', '无', '达那答乡', '副乡长', '副科', '三类区', '否', '18889025222', '40');
INSERT INTO `leave_user` VALUES ('2737', '旦增卓嘎', '女', '1991-08-01', '2013-08-01', '日喀则市仁布县', '无', '达那答乡', '科员', '科员', '三类区', '否', '13989020925', '34');
INSERT INTO `leave_user` VALUES ('2738', '次仁玉珍', '女', '1992-04-01', '2013-08-01', '日喀则昂仁', '无', '达那答乡', '科员', '科员', '三类区', '否', '17711980003', '44');
INSERT INTO `leave_user` VALUES ('2739', '丁勇', '男', '1990-04-01', '2013-12-01', '四川威远', '无', '达那答乡', '科员', '科员', '二类区', '是', '18583285209', '50');
INSERT INTO `leave_user` VALUES ('2740', '谢晓峰', '男', '1991-05-01', '2014-07-01', '四川阆中', '无', '达那答乡', '科员', '科员', '三类区', '是', '18989043365', '60');
INSERT INTO `leave_user` VALUES ('2741', '黄奎', '男', '1982-03-01', '2015-12-01', '陕西', '无', '达那答乡', '科员', '科员', '三类区', '是', '18909166876', '60');
INSERT INTO `leave_user` VALUES ('2742', '胡然', '男', '1995-01-01', '2016-07-01', '四川南充', '无', '达那答乡', '科员', '科员', '二类区', '是', '18380462712', '50');
INSERT INTO `leave_user` VALUES ('2743', '唐波', '男', '1991-01-01', '2016-07-01', '四川德阳', '无', '达那答乡', '科员', '科员', '三类区', '否', '17308927621', '60');
INSERT INTO `leave_user` VALUES ('2744', '吴义', '男', '1993-03-01', '2016-07-01', '四川南充', '无', '达那答乡', '科员', '科员', '三类区', '否', '18380458723', '50');
INSERT INTO `leave_user` VALUES ('2745', '郑辉', '男', '1992-11-01', '2016-07-01', '四川南充', '无', '达那答乡', '科员', '科员', '二类区', '否', '18189028913', '50');
INSERT INTO `leave_user` VALUES ('2746', '格桑加措', '男', '1992-12-01', '2017-01-01', '西藏拉孜县', '无', '达那答乡', '科员', '科员', '三类区', '否', '18798922244', '44');
INSERT INTO `leave_user` VALUES ('2747', '王国贵', '男', '1992-03-01', '2017-08-01', '云南宜良', '无', '达那答乡', '科员', '科员', '三类区', '否', '13661564662', '60');
INSERT INTO `leave_user` VALUES ('2748', '常磊', '男', '1993-09-01', '2017-08-01', '云南镇雄县', '无', '达那答乡', '科员', '科员', '三类区', '否', '15002156970', '60');
INSERT INTO `leave_user` VALUES ('2749', '卓玛', '女', '1993-10-01', '2017-01-01', '西藏日喀则', '无', '达那答乡', '科员', '科员', '三类区', '否', '13889029089', '42');
INSERT INTO `leave_user` VALUES ('2750', '李森', '男', '1994-01-01', '2017-08-01', '四川广元', '无', '达那答乡', '科员', '科员', '三类区', '否', '13659597482', '60');
INSERT INTO `leave_user` VALUES ('2751', '黄建丰', '男', '1984-01-01', '2012-11-01', '四川广安', '无', '达那答乡', '科员', '科员', '二类区', '否', '13989023536', '50');
INSERT INTO `leave_user` VALUES ('2752', '格桑顿珠', '男', '1989-10-01', '2011-08-01', '西藏日喀则', '西藏拉萨', '达那答乡', '科员', '科员', '二类区', '是', '18708028833', '46');
INSERT INTO `leave_user` VALUES ('2753', '石曲普赤', '女', '1990-08-01', '2013-08-01', '西藏谢通门县', '无', '达那答乡', '科员', '科员', '三类区', '否', '18408921854', '40');
INSERT INTO `leave_user` VALUES ('2754', '索朗', '女', '1976-03-01', '1999-07-01', '西藏日喀则', '无', '达那土登寺管委会', '主任科员', '正科', '三类区', '否', '13638925915', '42');
INSERT INTO `leave_user` VALUES ('2755', '次多', '男', '1980-06-01', '2001-07-01', '日喀则', '白朗县', '达那答乡派出所', '所长', '正科', '三类区', '是', '13989026969', '44');
INSERT INTO `leave_user` VALUES ('2756', '普琼', '男', '1993-03-01', '2013-08-01', '江孜', '无', '达那答乡派出所', '科员', '科员', '三类区', '否', '18289101105', '44');
INSERT INTO `leave_user` VALUES ('2757', '晋美', '男', '1993-09-01', '2014-11-01', '日喀则', '无', '达那答乡派出所', '科员', '科员', '三类区', '否', '18208091521', '42');
INSERT INTO `leave_user` VALUES ('2758', '旦增次旺', '男', '1986-07-01', '2012-07-01', '拉萨市', '无', '达那答乡派出所', '科员', '科员', '三类区', '否', '18389089922', '46');
INSERT INTO `leave_user` VALUES ('2759', '达瓦普赤', '女', '1900-01-01', '1900-01-01', '西藏日喀则', '西藏萨迦', '达那答乡', '科员', '科员', '三类区', '是', '15208009199', '42');
INSERT INTO `leave_user` VALUES ('2760', '尼玛平措', '男', '1968-10-01', '1991-07-01', '日喀则市江孜县', '日喀则市桑珠孜区', '仁钦则乡', '书记', '副县', '三类区', '是', '13658926065', '50');
INSERT INTO `leave_user` VALUES ('2761', '赤列旺堆', '男', '1970-06-01', '1991-12-01', '日喀则市', '日喀则市拉孜县', '仁钦则乡', '主席', '正科', '三类区', '否', '15289027926', '42');
INSERT INTO `leave_user` VALUES ('2762', '杨朝文', '男', '1980-04-01', '2007-07-01', '四川仁寿', '重庆', '仁钦则乡', '乡长', '正科', '三类区', '是', '13628922790', '60');
INSERT INTO `leave_user` VALUES ('2763', '次仁顿珠', '男', '1988-03-01', '2011-08-01', '日喀则市', '日喀则市', '仁钦则乡', '副乡长', '副科', '三类区', '是', '18708025248', '52');
INSERT INTO `leave_user` VALUES ('2764', '袁东', '男', '1989-05-01', '2014-11-01', '四川德阳', '无', '仁钦则乡', '科员', '科员', '三类区', '是', '18208091467', '60');
INSERT INTO `leave_user` VALUES ('2765', '梁斌', '男', '1990-03-01', '2013-08-01', '甘肃', '无', '仁钦则乡', '科员', '科员', '三类区', '是', '13889006420', '60');
INSERT INTO `leave_user` VALUES ('2766', '德吉', '女', '1985-03-01', '2009-07-01', '日喀则市萨迦县', '日喀则市通门县', '仁钦则乡', '副书记', '副科', '三类区', '否', '13989027373', '44');
INSERT INTO `leave_user` VALUES ('2767', '段淑兰', '女', '1972-06-01', '1992-07-01', '四川', '甘肃', '仁钦则乡', '副乡长', '正科', '三类区', '是', '13628926696', '60');
INSERT INTO `leave_user` VALUES ('2768', '巴桑罗布', '男', '1987-04-01', '2010-08-01', '拉萨市', '拉萨', '仁钦则乡', '所长', '副科', '三类区', '是', '13648994261', '56');
INSERT INTO `leave_user` VALUES ('2769', '格桑拉姆', '女', '1989-09-01', '2011-08-01', '谢通门', '无', '仁钦则乡', '副乡长', '副科', '三类区', '否', '17789027694', '40');
INSERT INTO `leave_user` VALUES ('2770', '尼玛参', '女', '1982-01-01', '2003-07-01', '日喀则市', '日喀则市', '仁钦则乡', '科员', '科员', '三类区', '是', '15348921234', '52');
INSERT INTO `leave_user` VALUES ('2771', '杨云', '女', '1989-09-01', '2014-11-01', '陕西渭南', '无', '仁钦则乡', '科员', '科员', '三类区', '是', '15889071691', '60');
INSERT INTO `leave_user` VALUES ('2772', '仁增多吉', '男', '1982-03-01', '2005-07-01', '西藏墨脱', '无', '仁钦则乡', '主任科员', '正科', '三类区', '否', '13628925627', '46');
INSERT INTO `leave_user` VALUES ('2773', '米玛索朗', '女', '1987-03-01', '2012-02-01', '拉萨市', '日喀则市定结县', '仁钦则乡', '副主任科员', '副科', '三类区', '是', '13322590276', '56');
INSERT INTO `leave_user` VALUES ('2774', '彭顺顺', '男', '1988-01-01', '2012-11-01', '重庆渝武', '无', '仁钦则乡派出所', '科员', '科员', '三类区', '是', '13398021207', '60');
INSERT INTO `leave_user` VALUES ('2775', '郭林芳', '女', '1991-09-01', '2014-11-01', '山东省', '谢通门县', '仁钦则乡派出所', '科员', '科员', '三类区', '是', '18989085459', '60');
INSERT INTO `leave_user` VALUES ('2776', '落桑旦增', '男', '1991-09-01', '2013-08-01', '日喀则市仁布县', '日喀则市南木林县', '仁钦则乡派出所', '科员', '科员', '三类区', '是', '13549047723', '54');
INSERT INTO `leave_user` VALUES ('2777', '拉巴', '男', '1984-05-01', '2007-01-01', '日喀则市谢通门县', '江孜', '仁钦则乡派出所', '副所长', '副科', '三类区', '否', '13908922112', '44');
INSERT INTO `leave_user` VALUES ('2778', '边巴次仁', '男', '1983-04-01', '2007-01-01', '西藏昂仁', '无', '达那土登寺管委会', '副主任', '副科', '三类区', '是', '13648922224', '44');
INSERT INTO `leave_user` VALUES ('2779', '次旦', '女', '1986-10-01', '2000-07-01', '西藏日喀则', '无', '仁钦则乡', '副书记', '正科', '三类区', '否', '13989020552', '42');
INSERT INTO `leave_user` VALUES ('2780', '王鑫', '男', '1988-08-01', '2012-11-01', '山东临沭', '无', '仁钦则乡', '乡纪委书记', '副科', '三类区', '是', '18143203110', '60');
INSERT INTO `leave_user` VALUES ('2781', '杨维成', '男', '1995-09-01', '2017-08-01', '安徽', '无', '仁钦则乡', '科员', '科员', '三类区', '是', '17711987656', '60');
INSERT INTO `leave_user` VALUES ('2782', '许小倩', '女', '1993-07-01', '2017-12-01', '四川彭州', '无', '仁钦则乡', '科员', '科员', '三类区', '是', '18215544315', '60');
INSERT INTO `leave_user` VALUES ('2783', '格顿', '男', '1991-07-01', '2017-01-01', '西藏江孜', '无', '仁钦则乡', '科员', '科员', '三类区', '否', '18143899911', '42');
INSERT INTO `leave_user` VALUES ('2784', '德吉措姆', '女', '1982-05-01', '2004-07-01', '西藏山南', '无', '达那土登寺管委会', '副主任科员', '副科', '三类区', '否', '13989924173', '46');
INSERT INTO `leave_user` VALUES ('2785', '达娃扎西', '男', '1983-10-01', '2003-07-01', '谢通门县', '谢通门县', '达那普乡', '书记', '正科', '三类区', '否', '18076921320', '40');
INSERT INTO `leave_user` VALUES ('2786', '琼拉', '女', '1978-08-15', '1999-07-01', '谢通门县', '萨迦县', '达那普乡', '主席', '正科', '三类区', '否', '18908929680', '44');
INSERT INTO `leave_user` VALUES ('2787', '陈税涛', '男', '1986-10-30', '2008-07-01', '四川射洪', '山西县', '达那普乡', '乡长', '正科', '三类区', '否', '18908929900', '60');
INSERT INTO `leave_user` VALUES ('2788', '顿珠旺姆', '男', '1982-04-07', '2011-10-01', '谢通门县', '仁布县', '达那普乡', '副书记', '副科', '三类区', '否', '15208020303', '44');
INSERT INTO `leave_user` VALUES ('2789', '边央', '女', '1988-06-11', '2010-11-01', '拉萨推龙德庆', '无', '达那普乡', '纪委书记', '副科', '三类区', '否', '13648991286', '46');
INSERT INTO `leave_user` VALUES ('2790', '普布旦增', '男', '1984-10-21', '2008-07-01', '日喀则市', '日喀则', '达那普乡', '副乡长', '副科', '三类区', '是', '13638924460', '52');
INSERT INTO `leave_user` VALUES ('2791', '旦增措姆', '女', '1983-12-31', '2011-07-01', '拉萨推龙德庆', '青海', '达那普乡', '副乡长', '副科', '三类区', '否', '15208092277', '60');
INSERT INTO `leave_user` VALUES ('2792', '才俊伟', '男', '1979-11-25', '2009-07-01', '辽宁省', '无', '达那普乡', '副乡长', '副科', '三类区', '否', '18089973555', '60');
INSERT INTO `leave_user` VALUES ('2793', '次仁卓嘎', '女', '1987-03-23', '2009-07-01', '日喀则市', '无', '达那普乡', '副主任科员', '副科', '三类区', '否', '17708906850', '42');
INSERT INTO `leave_user` VALUES ('2794', '仓觉', '女', '1989-05-24', '2012-07-10', '白朗县', '白朗县', '达那普乡', '副主任科员', '副科', '三类区', '是', '17789028883', '54');
INSERT INTO `leave_user` VALUES ('2795', '巴桑桑珠', '男', '1991-07-06', '2013-08-01', '拉萨市', '无', '达那普乡', '副主任科员', '副科', '三类区', '否', '15889007152', '46');
INSERT INTO `leave_user` VALUES ('2796', '陈祥顺', '男', '1988-04-23', '2013-12-01', '贵州威宁', '贵州威宁', '达那普乡', '科员', '科员', '三类区', '是', '18208022020', '60');
INSERT INTO `leave_user` VALUES ('2797', '邱洪春', '男', '1984-12-10', '2015-12-01', '四川南充', '四川南充', '达那普乡', '科员', '科员', '三类区', '是', '19184888618', '60');
INSERT INTO `leave_user` VALUES ('2798', '扎西普赤', '女', '1993-02-21', '2015-12-01', '日喀则市', '无', '达那普乡', '科员', '科员', '三类区', '否', '17711980251', '42');
INSERT INTO `leave_user` VALUES ('2799', '边巴次仁', '男', '1973-09-14', '1995-07-01', '日喀则市', '谢通门县', '查嘎珠德寺管委会', '主任', '正科', '三类区', '否', '13989928493', '42');
INSERT INTO `leave_user` VALUES ('2800', '尼玛次仁', '男', '1989-02-10', '2011-11-01', '日喀则市仁布县', '无', '查嘎珠德寺管委会', '副主任科员', '副科', '三类区', '否', '18289126667', '44');
INSERT INTO `leave_user` VALUES ('2801', '普布次仁', '男', '1983-11-10', '2012-07-10', '日喀则市', '拉孜县', '达那普乡派出所', '副所长', '副科', '三类区', '是', '13518929130', '54');
INSERT INTO `leave_user` VALUES ('2802', '邹堂权', '男', '1974-06-23', '1999-07-01', '四川荣县', '重庆渝北区', '孜许乡', '书记', '正科', '四类区', '否', '18798929119', '70');
INSERT INTO `leave_user` VALUES ('2803', '巴吉', '女', '1971-12-06', '1992-07-01', '西藏日喀则市', '西藏亚东', '孜许乡', '主席', '正科', '四类区', '否', '13908925335', '54');
INSERT INTO `leave_user` VALUES ('2804', '多吉伦珠', '男', '1981-03-20', '2006-07-01', '西藏谢通门', '西藏拉萨市', '孜许乡', '乡长', '正科', '四类区', '是', '18889026777', '66');
INSERT INTO `leave_user` VALUES ('2805', '张洪', '男', '1988-08-08', '2012-11-01', '重庆垫江', '重庆垫江', '孜许乡', '副书记', '副科', '四类区', '是', '18289121708', '70');
INSERT INTO `leave_user` VALUES ('2806', '平措白珍', '女', '1987-09-12', '2011-12-01', '西藏山南市', '四川甘孜', '孜许乡', '纪委书记', '副科', '四类区', '是', '13549027709', '70');
INSERT INTO `leave_user` VALUES ('2807', '何广', '男', '1984-11-01', '2010-11-01', '四川仪陇', '四川仪陇', '孜许乡', '副乡长', '副科', '四类区', '是', '18798998290', '70');
INSERT INTO `leave_user` VALUES ('2808', '次珍', '女', '1985-03-28', '2009-12-01', '西藏拉萨市', '西藏萨迦县', '孜许乡', '副乡长', '副科', '四类区', '否', '15208020077', '56');
INSERT INTO `leave_user` VALUES ('2809', '晁增彬', '男', '1988-08-23', '2013-12-01', '四川宜宾', '四川宜宾', '孜许乡', '科员', '科员', '四类区', '是', '18189929776', '70');
INSERT INTO `leave_user` VALUES ('2810', '索朗拉珍', '女', '1993-03-11', '2015-12-01', '西藏错那', '无', '孜许乡', '科员', '科员', '四类区', '否', '18889024215', '56');
INSERT INTO `leave_user` VALUES ('2811', '次旦央拉', '女', '1993-04-29', '2017-12-15', '西藏南木林', '无', '孜许乡', '科员', '科员', '四类区', '否', '13628924729', '54');
INSERT INTO `leave_user` VALUES ('2812', '贡嘎次仁', '男', '1966-01-18', '1993-10-01', '西藏谢通门', '西藏谢通门', '孜许乡', '办事员', '办事员', '四类区', '否', '18189922249', '54');
INSERT INTO `leave_user` VALUES ('2813', '拉巴次仁', '男', '1984-08-08', '2005-11-01', '西藏日喀则市', '西藏日喀则市', '孜许乡派出所', '副所长', '副科', '四类区', '否', '15289129991', '54');
INSERT INTO `leave_user` VALUES ('2814', '黄亚东', '男', '1993-01-16', '2012-11-01', '云南曲靖', '无', '孜许乡派出所', '科员', '科员', '四类区', '否', '17888085678', '70');
INSERT INTO `leave_user` VALUES ('2815', '次仁旺久', '男', '1982-02-04', '2005-12-01', '西藏日喀则市', '西藏日喀则市', '索布寺管委会', '主任', '正科', '四类区', '是', '13398021991', '62');
INSERT INTO `leave_user` VALUES ('2816', '尼玛顿珠', '男', '1989-04-21', '2012-12-01', '西藏谢通门', '西藏白朗', '索布寺管委会', '科员', '科员', '四类区', '是', '13889016726', '64');
INSERT INTO `leave_user` VALUES ('2817', '洛桑朗加', '男', '1993-02-08', '2013-07-01', '西藏浪卡子', '西藏日喀则市', '索布寺管委会', '科员', '科员', '四类区', '否', '15289129191', '56');
INSERT INTO `leave_user` VALUES ('2818', '卢仕华', '男', '1989-04-12', '2015-12-01', '云南广南', '西藏谢通门', '孜许乡', '科员', '科员', '四类区', '否', '18189081382', '70');
INSERT INTO `leave_user` VALUES ('2819', '粗真', '男', '1970-08-01', '1994-07-01', '日喀则市谢通门县', '日喀则市', '南木切乡', '书记', '正科', '四类区', '否', '18143200008', '52');
INSERT INTO `leave_user` VALUES ('2820', '扎西郎加', '男', '1980-01-01', '2003-07-01', '日喀则市康马县', '拉萨市', '南木切乡', '主席', '正科', '四类区', '是', '13989026294', '66');
INSERT INTO `leave_user` VALUES ('2821', '兰贤洲', ' 男', '1982-06-01', '2004-07-01', '江西省', '四川', '南木切乡', '乡长', '正科', '四类区', '是', '13989926115', '70');
INSERT INTO `leave_user` VALUES ('2822', '边巴普赤', '女', '1983-04-01', '2005-07-01', '西藏谢通门县', '西藏仁布县', '南木切乡', '副书记', '正科', '四类区', '否', '13989920637', '54');
INSERT INTO `leave_user` VALUES ('2823', '李兴明', '男', '1976-07-01', '2005-07-01', '甘肃省天水县', '山西大同', '南木切乡', '所长', '正科', '四类区', '否', '13638926339', '70');
INSERT INTO `leave_user` VALUES ('2824', '次单曲珍', '女', '1985-11-01', '2009-01-01', '山南市扎囊县', '无', '南木切乡', '纪委书记', '副科', '四类区', '否', '18076921323', '56');
INSERT INTO `leave_user` VALUES ('2825', '扎西次仁', '男', '1979-01-01', '1997-12-01', '西藏通门县', '谢通门', '南木切乡', '副乡长', '副科', '四类区', '否', '15208022224', '50');
INSERT INTO `leave_user` VALUES ('2826', '次仁央金', '女', '1989-02-01', '2012-07-01', '日喀则市', '山南市贡嘎县', '南木切乡', '副乡长', '副科', '四类区', '否', '18889021710', '56');
INSERT INTO `leave_user` VALUES ('2827', '旺堆次仁', '男', '1990-06-01', '2012-07-01', '西藏谢通门县', '西藏浪卡子县', '南木切乡派出所', '科员', '科员', '四类区', '是', '18408929997', '66');
INSERT INTO `leave_user` VALUES ('2828', '边巴伦珠', '男', '1992-01-01', '2017-01-01', '日喀则市江孜县', '无', '南木切乡派出所', '科员', '科员', '四类区', '否', '15289128408', '54');
INSERT INTO `leave_user` VALUES ('2829', '拉琼', '男', '1982-05-01', '2006-09-01', '西藏日喀则市', '西藏日喀则市', '查布乡', '书记', '正科', '四类区', '是', '18189923330', '62');
INSERT INTO `leave_user` VALUES ('2830', '巴桑次仁', '男', '1977-05-01', '1998-07-01', '西藏桑珠孜区', '西藏南木林', '查布乡', '主席', '正科', '四类区', '否', '13518923329', '52');
INSERT INTO `leave_user` VALUES ('2831', '苏治国', '男', '1980-08-01', '2007-07-01', '吉林长春', '四川南部', '查布乡', '乡长', '正科', '四类区', '是', '13989023740', '70');
INSERT INTO `leave_user` VALUES ('2832', '扎西旺堆', '男', '1969-08-01', '1993-07-01', '西藏日喀则市', '西藏日喀则市', '查布乡', '副乡长', '主任科员', '四类区', '是', '13989029348', '62');
INSERT INTO `leave_user` VALUES ('2833', '贡嘎', '女', '1986-10-01', '2012-07-01', '西藏谢通门', '西藏谢通门', '查布乡', '副书记', '副科', '四类区', '否', '13908923797', '50');
INSERT INTO `leave_user` VALUES ('2834', '尼玛片多', '女', '1971-02-01', '1993-04-01', '西藏日喀则市', '西藏江孜', '查布乡', '纪委书记', '副科', '四类区', '否', '13638926248', '54');
INSERT INTO `leave_user` VALUES ('2835', '罗兴文', '男', '1976-11-01', '1999-07-01', '四川苍溪', '西藏谢通门', '查布乡', '副乡长', '副科', '四类区', '否', '13628926548', '70');
INSERT INTO `leave_user` VALUES ('2836', '次仁德吉', '女', '1986-09-01', '2012-07-01', '西藏谢通门', '无', '查布乡', '副乡长', '副科', '四类区', '否', '15208024560', '50');
INSERT INTO `leave_user` VALUES ('2837', '陈宏', '男', '1990-07-01', '2013-12-01', '甘肃民乐', '无', '查布乡', '科员', '科员', '四类区', '是', '13648929955', '70');
INSERT INTO `leave_user` VALUES ('2838', '向红飞', '男', '1990-12-01', '2013-12-01', '重庆万州', '重庆万州', '查布乡', '科员', '科员', '四类区', '是', '18143205460', '70');
INSERT INTO `leave_user` VALUES ('2839', '次旦卓玛', '女', '1990-10-01', '2014-11-01', '西藏浪卡子', '西藏扎囊', '查布乡', '科员', '科员', '四类区', '否', '18143822146', '56');
INSERT INTO `leave_user` VALUES ('2840', '杜少冬', '男', '1993-12-01', '2012-12-01', '四川营山', '无', '查布乡', '科员', '科员', '四类区', '是', '18708022864', '70');
INSERT INTO `leave_user` VALUES ('2841', '旦桑', '女', '1988-11-01', '2011-11-01', '西藏谢通门', '西藏谢通门', '查布乡', '科员', '科员', '四类区', '否', '13659567899', '50');
INSERT INTO `leave_user` VALUES ('2842', '巴桑扎西', '男', '1993-02-01', '2017-01-01', '西藏日喀则市', '无', '查布乡', '科员', '科员', '四类区', '否', '18143203335', '52');
INSERT INTO `leave_user` VALUES ('2843', '罗桑扎西', '男', '1991-07-01', '2015-12-01', '西藏谢通门', '无', '查布乡', '科员', '科员', '四类区', '否', '15208028725', '50');
INSERT INTO `leave_user` VALUES ('2844', '贺娜', '女', '1991-09-01', '2017-01-01', '陕西延安', '山东临沂', '查布乡', '科员', '科员', '四类区', '否', '17708907083', '70');
INSERT INTO `leave_user` VALUES ('2845', '王中国', '男', '1990-03-01', '2017-07-01', '山东泰安', '无', '查布乡', '科员', '科员', '四类区', '是', '18089090385', '70');
INSERT INTO `leave_user` VALUES ('2846', '格桑顿珠', '男', '1985-09-01', '2011-12-01', '西藏日喀则市', '西藏江孜', '查布乡派出所', '副所长', '副科', '四类区', '否', '18184993334', '52');
INSERT INTO `leave_user` VALUES ('2847', '普欧珠', '男', '1990-06-01', '2013-08-01', '西藏江孜', '西藏南木林', '查布乡派出所', '科员', '科员', '四类区', '否', '13648929706', '54');
INSERT INTO `leave_user` VALUES ('2848', '格扎', '男', '1900-01-01', '1900-01-01', '西藏谢通门', '西藏谢通门', '查布乡', '办事员', '办事员', '四类区', '否', '12345678910', '0');
INSERT INTO `leave_user` VALUES ('2849', '边巴奴布', '男', '1981-10-01', '2005-07-01', '山南', '日喀则', '青都乡', '书记', '正科', '四类区', '否', '13989024771', '56');
INSERT INTO `leave_user` VALUES ('2850', '张军社', '男', '1972-06-01', '1998-07-01', '陕西省', '陕西省', '青都乡', '乡长', '正科', '四类区', '是', '18189085788', '70');
INSERT INTO `leave_user` VALUES ('2851', '米玛次仁', '男', '1972-01-01', '1994-06-01', '江孜县', '通门县', '青都乡', '副书记', '正科', '四类区', '否', '13658926016', '54');
INSERT INTO `leave_user` VALUES ('2852', '琼吉', '女', '1985-08-01', '2011-12-01', '林周县', '南木林县', '青都乡', '纪委书记', '副科', '四类区', '是', '13989008707', '66');
INSERT INTO `leave_user` VALUES ('2853', '唐沛君', '女', '1976-02-01', '1999-07-01', '重庆渝北', '无', '青都乡', '副乡长', '副科', '四类区', '是', '13618929176', '50');
INSERT INTO `leave_user` VALUES ('2854', '白玛曲珍', '女', '1974-11-01', '1994-05-01', '谢通门县', '日喀则', '青都乡', '主任科员', '正科', '四类区', '否', '13658926009', '52');
INSERT INTO `leave_user` VALUES ('2855', '次仁顿珠', '男', '1988-05-01', '2011-12-01', '谢通门县', '林周县', '青都乡', '副乡长', '副科', '四类区', '否', '18289094234', '56');
INSERT INTO `leave_user` VALUES ('2856', '徐茂林', '男', '1991-06-01', '2012-11-01', '四川广安', '四川广安', '青都乡', '副科', '副科', '四类区', '是', '17708924545', '70');
INSERT INTO `leave_user` VALUES ('2857', '夏国庆', '男', '1982-11-22', '2005-07-01', '通门县', '无', '春哲乡', '书记', '正科', '四类区', '是', '13659576181', '70');
INSERT INTO `leave_user` VALUES ('2858', '玉珠拉姆', '女', '1985-10-08', '2003-07-01', '日喀则市', '日喀则市', '春哲乡', '乡长', '正科', '四类区', '否', '18708096369', '52');
INSERT INTO `leave_user` VALUES ('2859', '旦增平措', '男', '1983-07-01', '2005-07-01', '西藏拉萨', '无', '春哲乡', '主席', '正科', '四类区', '否', '13638927000', '56');
INSERT INTO `leave_user` VALUES ('2860', '石确南木加', '女', '1986-09-08', '2009-07-01', '拉萨市', '山南扎囊', '春哲乡', '副书记', '副科', '四类区', '否', '15889025306', '56');
INSERT INTO `leave_user` VALUES ('2861', '扎拉旦增', '男', '1987-06-01', '2011-12-01', '山南乃东', '无', '春哲乡', '副乡长', '副科', '四类区', '否', '18089972223', '56');
INSERT INTO `leave_user` VALUES ('2862', '索朗次仁', '男', '1988-08-09', '2011-12-01', '日喀则市', '拉萨', '春哲乡', '纪委书记', '副科', '四类区', '是', '17789027775', '66');
INSERT INTO `leave_user` VALUES ('2863', '顿珠旺庆', '男', '1988-09-24', '2009-11-01', '日喀则市', '昌都市', '春哲乡派出所', '所长', '科员', '四类区', '是', '15208091347', '68');
INSERT INTO `leave_user` VALUES ('2864', '米玛穷拉', '女', '1991-07-17', '2014-11-01', '通门县', '无', '春哲乡', '科员', '科员', '四类区', '否', '13618920319', '50');
INSERT INTO `leave_user` VALUES ('2865', '扎西多吉', '男', '1985-01-05', '2008-07-01', '通门县', '日喀则市', '春哲乡', '副主任科员', '副科', '四类区', '否', '13518920984', '52');
INSERT INTO `leave_user` VALUES ('2866', '李娇', '女', '1995-03-06', '2017-01-01', '四川省达州市', '无', '春哲乡', '科员', '科员', '四类区', '是', '18291000520', '70');
INSERT INTO `leave_user` VALUES ('2867', '边巴扎西', '男', '1993-04-01', '2013-07-01', '山南贡嘎县', '山南市桑日县', '春哲乡派出所', '科员', '科员', '四类区', '否', '18308034147', '66');
INSERT INTO `leave_user` VALUES ('2868', '琼片多', '女', '1994-04-24', '2018-01-01', '通门县', '无', '春哲乡', '科员', '科员', '四类区', '否', '18205156673', '50');
INSERT INTO `leave_user` VALUES ('2869', '次多', '男', '1989-11-01', '2013-08-01', '西藏日喀则', '无', '春哲乡', '副主任科员', '副科', '四类区', '是', '18289025893', '52');
INSERT INTO `leave_user` VALUES ('2870', '次旺罗布', '男', '1983-06-04', '2003-07-01', '西藏江孜县', '西藏日喀则市', '娘热乡', '书记', '正科', '四类区', '否', '13989925855', '54');
INSERT INTO `leave_user` VALUES ('2871', '朱歆玮', '男', '1983-09-16', '2007-07-01', '山西运城', '四川南充', '娘热乡', '乡长', '正科', '四类区', '是', '17889029218', '70');
INSERT INTO `leave_user` VALUES ('2872', '罗布扎西', '男', '1982-12-01', '2005-07-01', '西藏拉孜县', '日喀则拉孜', '娘热乡', '主席', '正科', '四类区', '否', '13989021465', '54');
INSERT INTO `leave_user` VALUES ('2873', '旦增平措', '男', '1987-08-19', '2011-08-01', '西藏拉萨', '西藏拉萨', '娘热乡', '副书记', '副科', '四类区', '否', '18989990805', '56');
INSERT INTO `leave_user` VALUES ('2874', '达瓦旺拉', '男', '1973-06-01', '1991-12-01', '西藏谢通门', '西藏谢通门县', '娘热乡', '副书记', '正科', '四类区', '否', '13989024471', '50');
INSERT INTO `leave_user` VALUES ('2875', '格桑旦增', '男', '1986-03-09', '2007-07-01', '西藏日喀则', '西藏日喀则市', '娘热乡', '副乡长', '副科', '四类区', '是', '13549021118', '64');
INSERT INTO `leave_user` VALUES ('2876', '加央', '男', '1984-10-24', '2009-08-01', '西藏日喀则', '西藏拉萨', '娘热乡', '副科实职', '副科', '四类区', '否', '17708906835', '56');
INSERT INTO `leave_user` VALUES ('2877', '郝祥', '男', '1987-11-23', '2013-12-01', '湖南汉寿', '湖南汉寿', '娘热乡', '科员', '科员', '四类区', '是', '15208023871', '70');
INSERT INTO `leave_user` VALUES ('2878', '洛桑平措', '男', '1993-05-04', '2014-11-01', '西藏曲松', '无', '娘热乡', '科员', '科员', '四类区', '否', '18898040302', '56');
INSERT INTO `leave_user` VALUES ('2879', '琼达', '女', '1993-04-05', '2017-12-15', '西藏桑珠孜区', '无', '娘热乡', '科员', '科员', '四类区', '否', '18798918213', '52');
INSERT INTO `leave_user` VALUES ('2880', '古桑仁增', '男', '1985-07-08', '2009-11-03', '西藏山南', '西藏日喀则桑珠孜', '娘热乡派出所', '所长', '正科', '四类区', '否', '15289122992', '56');
INSERT INTO `leave_user` VALUES ('2881', '李俊', '男', '1993-01-07', '2012-11-01', '四川达州', '西藏日喀则桑珠孜', '娘热乡派出所', '科员', '科员', '四类区', '否', '14789021371', '70');
INSERT INTO `leave_user` VALUES ('2882', '边巴吉律', '男', '1992-05-17', '2014-11-17', '西藏康马', '西藏江孜', '娘热乡派出所', '科员', '科员', '四类区', '否', '15289026017', '54');
INSERT INTO `leave_user` VALUES ('2883', '次仁顿珠', '男', '1985-08-15', '2013-02-01', '日喀则吉隆', '西藏江孜', '娘热乡派出所', '科员', '科员', '四类区', '是', '13989923531', '64');
INSERT INTO `leave_user` VALUES ('2884', '秦彬', '男', '1994-08-03', '2013-12-01', '四川仁寿', '无', '娘热乡', '科员', '科员', '四类区', '是', '18289021965', '70');
INSERT INTO `leave_user` VALUES ('2885', '陈天荣', '男', '1981-10-01', '2005-07-01', '云南宣威', '山西临汾', '纳当乡', '书记', '正科', '三类区', '否', '13518926470', '60');
INSERT INTO `leave_user` VALUES ('2886', '伊比热', '男', '1976-11-01', '2000-07-01', '拉萨市', '无', '纳当乡', '乡长', '正科', '三类区', '否', '18989025778', '46');
INSERT INTO `leave_user` VALUES ('2887', '德吉卓嘎', '女', '1972-08-01', '1993-07-01', '日喀则市亚东县', '日喀则市南木林县', '纳当乡', '主席', '正科', '三类区', '是', '13518921887', '54');
INSERT INTO `leave_user` VALUES ('2888', '曲吉', '女', '1982-07-01', '2005-07-01', '山南市错那县', '无', '纳当乡', '纪委书记', '正科', '三类区', '否', '13658935155', '46');
INSERT INTO `leave_user` VALUES ('2889', '罗珍', '女', '1987-06-01', '2010-08-01', '日喀则市谢通门县', '四川省甘孜州色达县', '纳当乡', '副书记', '副科', '三类区', '否', '13989903216', '60');
INSERT INTO `leave_user` VALUES ('2890', '扎桑', '女', '1985-06-01', '2010-08-01', '林芝市', '拉萨市', '纳当乡', '副乡长', '副科', '三类区', '是', '13549097766', '56');
INSERT INTO `leave_user` VALUES ('2891', '索朗多吉', '男', '1975-08-01', '1993-12-01', '日喀则市', '昂仁县', '纳当乡', '副主任科员', '副科', '三类区', '是', '18089025666', '54');
INSERT INTO `leave_user` VALUES ('2892', '杨永清', '女', '1973-10-01', '1994-07-01', '重庆合川', '江苏泗阳', '纳当乡', '副乡长', '副科', '三类区', '否', '13989025555', '60');
INSERT INTO `leave_user` VALUES ('2893', '潘多', '女', '1984-06-01', '2008-07-01', '日喀则市桑珠孜区', '日喀则市江孜县', '纳当乡', '科员', '科员', '三类区', '否', '18089029469', '44');
INSERT INTO `leave_user` VALUES ('2894', '嘎桑曲珍', '女', '1986-01-01', '2009-12-01', '日喀则市谢通门县', '山南市扎囊县', '纳当乡', '科员', '科员', '三类区', '是', '15889026750', '56');
INSERT INTO `leave_user` VALUES ('2895', '许锦伟', '男', '1991-10-01', '2015-12-01', '甘肃省', '无', '纳当乡', '科员', '科员', '三类区', '否', '18908991520', '60');
INSERT INTO `leave_user` VALUES ('2896', '贡嘎', '男', '1970-10-01', '1993-07-01', '日喀则市', '日喀则市', '纳当乡派出所', '所长', '正科', '三类区', '是', '18089023486', '52');
INSERT INTO `leave_user` VALUES ('2897', '次旺', '男', '1986-11-01', '2011-11-01', '日喀则市', '日喀则市', '纳当乡派出所', '副所长', '副科', '三类区', '是', '18708098123', '52');
INSERT INTO `leave_user` VALUES ('2898', '杜汶芯', '男', '1979-01-01', '2005-07-01', '四川剑阁', '四川仪陇县', '措布西乡', '书记', '正科', '三类区', '是', '18189981111', '60');
INSERT INTO `leave_user` VALUES ('2899', '旺久', '男', '1982-09-01', '2005-07-01', '山南乃东县', '谢通门县', '措布西乡', '乡长', '正科', '三类区', '否', '13618929965', '46');
INSERT INTO `leave_user` VALUES ('2900', '卫东', '女', '1967-11-01', '1990-07-01', '日喀则市', '无', '措布西乡', '主席', '正科', '三类区', '否', '13989024758', '42');
INSERT INTO `leave_user` VALUES ('2901', '边巴罗布', '男', '1986-06-01', '2008-07-01', '日喀则市', '谢通门县', '措布西乡', '副书记', '副科', '三类区', '否', '18908925585', '42');
INSERT INTO `leave_user` VALUES ('2902', '次旦卓拉', '女', '1988-11-01', '2010-07-01', '谢通门县', '萨迦县', '措布西乡', '纪委书记', '副科', '三类区', '否', '18708095588', '44');
INSERT INTO `leave_user` VALUES ('2903', '边巴旺堆', '男', '1990-09-01', '2011-12-01', '拉萨市', '谢通门县', '措布西乡', '副乡长', '副科', '三类区', '否', '13989925415', '46');
INSERT INTO `leave_user` VALUES ('2904', '西热次仁', '男', '1984-05-01', '2013-07-01', '那曲申扎', '那曲申扎县', '措布西派出所', '所长', '科员', '三类区', '否', '13889068754', '48');
INSERT INTO `leave_user` VALUES ('2905', '侯勇', '男', '1992-03-01', '2013-12-01', '重庆', '重庆市开州区', '措布西派出所', '干警', '员级', '三类区', '是', '18089088751', '60');
INSERT INTO `leave_user` VALUES ('2906', '桂中原', '男', '1992-09-01', '2012-11-01', '河南西川', '无', '措布西乡', '科员', '科员', '三类区', '否', '17789027676', '60');
INSERT INTO `leave_user` VALUES ('2907', '王晶晶', '女', '1992-01-01', '2017-12-01', '河南省内黄县', '谢通门县', '措布西乡', '科员', '科员', '三类区', '否', '17711989012', '60');
INSERT INTO `leave_user` VALUES ('2908', '次旺多吉', '男', '1993-02-01', '2017-12-01', '日喀则市南木林县', '无', '措布西乡', '科员', '科员', '三类区', '否', '13638920637', '44');
INSERT INTO `leave_user` VALUES ('2909', '旦巴扎西', '男', '1966-05-01', '2016-07-01', '谢通门县', '谢通门县', '措布西乡', '办事员', '办事员', '三类区', '否', '15208000559', '40');
INSERT INTO `leave_user` VALUES ('2910', '王立新', '男', '1981-06-11', '2005-07-01', '天津蓟县', '无', '达木夏乡', '书记', '正科', '三类区', '否', '13618929151', '60');
INSERT INTO `leave_user` VALUES ('2911', '尼玛顿珠', '男', '1983-01-01', '2005-07-01', '山南', '桑珠孜区', '达木夏乡', '乡长', '正科', '三类区', '是', '17711980004', '56');
INSERT INTO `leave_user` VALUES ('2912', '次旦普赤', '女', '1979-01-01', '2005-07-01', '日喀则市', '谢通门县', '达木夏乡', '主席', '正科', '三类区', '否', '13658926255', '42');
INSERT INTO `leave_user` VALUES ('2913', '达瓦次仁', '男', '1986-05-01', '2011-12-01', '白朗县', '日喀则市', '达木夏乡', '纪委书记', '副科', '三类区', '是', '18208095800', '54');
INSERT INTO `leave_user` VALUES ('2914', '扎西卓嘎', '女', '1988-09-01', '2010-08-01', '拉萨市', '无', '达木夏乡', '副书记', '副科', '三类区', '否', '18389022556', '46');
INSERT INTO `leave_user` VALUES ('2915', '扎旺', '女', '1984-08-01', '2008-09-01', '白朗县', '江孜县', '达木夏乡', '副乡长', '副科', '三类区', '否', '18076921325', '44');
INSERT INTO `leave_user` VALUES ('2916', '次珍', '女', '1985-09-01', '2008-09-01', '江孜县', '谢通门县', '达木夏乡', '副乡长', '副科', '三类区', '否', '15289128683', '44');
INSERT INTO `leave_user` VALUES ('2917', '旦增群培', '男', '1985-08-01', '2011-11-01', '拉萨市', '无', '达木夏乡', '副书记', '副科', '三类区', '否', '18289000502', '46');
INSERT INTO `leave_user` VALUES ('2918', '袁健', '男', '1990-07-14', '2015-12-01', '重庆江津', '贵州都匀', '达木夏乡', '科员', '科员', '三类区', '否', '15823430011', '60');
INSERT INTO `leave_user` VALUES ('2919', '其美卓嘎', '女', '1989-11-01', '2013-08-01', '拉萨市', '卡嘎镇', '达木夏乡', '科员', '科员', '三类区', '否', '18389020578', '46');
INSERT INTO `leave_user` VALUES ('2920', '德庆', '女', '1986-02-01', '2012-11-01', '江孜县', '南木林县', '达木夏乡', '主任', '副科', '三类区', '否', '18189022229', '44');
INSERT INTO `leave_user` VALUES ('2921', '袁超', '男', '1992-10-01', '2013-12-01', '湖北武汉', '无', '达木夏乡', '科员', '科员', '三类区', '否', '17789025204', '60');
INSERT INTO `leave_user` VALUES ('2922', '仁增多吉', '男', '1992-04-01', '2013-12-01', '日喀则市南木林县', '山南', '达木夏乡', '科员', '科员', '三类区', '否', '18184923733', '46');
INSERT INTO `leave_user` VALUES ('2923', '旺拉', '男', '1986-03-01', '2013-08-01', '谢通门县', '南木林 ', '达木夏乡', '副主任科员', '副科', '三类区', '否', '18008925995', '44');
INSERT INTO `leave_user` VALUES ('2924', '巴桑仓决', '女', '1994-07-01', '2017-12-01', '康玛县', '无', '达木夏乡', '科员', '科员', '三类区', '否', '13696953291', '44');
INSERT INTO `leave_user` VALUES ('2925', '索平', '男', '1983-08-01', '1999-12-01', '江孜县', '拉萨', '达木夏乡派出所', '副所长', '副科', '三类区', '否', '13308929551', '46');
INSERT INTO `leave_user` VALUES ('2926', '欧珠', '男', '1986-01-01', '2015-02-01', '日喀则市', '拉萨', '达木夏乡派出所', '科员', '科员', '三类区', '否', '17808921119', '46');
INSERT INTO `leave_user` VALUES ('2927', '次仁伦珠', '男', '1994-01-01', '2014-11-01', '日喀则市桑珠孜区', '林芝市波密县', '达木夏乡派出所', '科员', '科员', '三类区', '否', '18184997616', '46');
INSERT INTO `leave_user` VALUES ('2928', '次仁加布', '男', '1989-05-01', '2013-08-01', '那曲地区', '那曲', '达木夏乡派出所', '科员', '科员', '三类区', '是', '13659561210', '58');
INSERT INTO `leave_user` VALUES ('2929', '拉巴次仁', '男', '1991-01-01', '2017-01-01', '林芝市', '无', '达木夏乡派出所', '科员', '科员', '三类区', '否', '15348996334', '46');
INSERT INTO `leave_user` VALUES ('2930', '拉旦', '男', '1989-01-01', '2012-07-01', '江孜县', '谢通门县', '林嘎寺管委会', '副主任', '副科', '三类区', '是', '13659565807', '54');
INSERT INTO `leave_user` VALUES ('2931', '达瓦次仁', '男', '1990-05-01', '2011-11-01', '江孜县', '山南扎朗县', '林嘎寺管委会', '副主任科员', '副科', '三类区', '否', '13659565774', '46');
INSERT INTO `leave_user` VALUES ('2932', '平措扎西', '男', '1992-06-01', '2014-11-01', '山南浪卡子县', '无', '林嘎寺管委会', '科员', '科员', '三类区', '否', '17789029721', '46');
INSERT INTO `leave_user` VALUES ('2933', '米玛群宗', '女', '1985-10-01', '2010-08-01', '西藏日喀则', '无', '达木夏乡', '副乡长', '副科', '三类区', '否', '13518922488', '42');
INSERT INTO `leave_user` VALUES ('2934', '归桑卓嘎', '女', '1988-09-27', '2011-11-01', '西藏浪卡子县', '西藏日喀则市', '美巴切勤乡', '纪委书记', '副科', '四类区', '否', '18289026042', '56');
INSERT INTO `leave_user` VALUES ('2935', '庄明芳', '男', '1985-12-04', '2012-11-01', '福建省惠安县', '福建省惠安县', '美巴切勤乡', '副乡长', '副科', '四类区', '是', '18989927758', '70');
INSERT INTO `leave_user` VALUES ('2936', '卓玛', '女', '1986-04-04', '2004-09-01', '西藏日喀则市', '西藏谢通门县', '美巴切勤乡', '主席', '正科', '四类区', '是', '13618923221', '62');
INSERT INTO `leave_user` VALUES ('2937', '周丹', '男', '1993-11-18', '2017-12-15', '四川省营山县', '无', '美巴切勤乡', '科员', '科员', '四类区', '是', '17740708624', '70');
INSERT INTO `leave_user` VALUES ('2938', '白玛拉姆', '女', '1988-12-03', '2010-11-01', '西藏日喀则市', '西藏日喀则市', '美巴切勤乡', '副乡长', '副科', '四类区', '是', '13518925000', '62');
INSERT INTO `leave_user` VALUES ('2939', '白玛旺久', '男', '1989-07-20', '2011-12-01', '西藏日喀则市', '无', '美巴切勤乡', '副乡长', '副科', '四类区', '否', '18989925567', '52');
INSERT INTO `leave_user` VALUES ('2940', '刘加祥', '男', '1985-07-20', '2011-08-15', '四川省苍溪县', '四川省苍溪县', '美巴切勤乡', '乡长', '正科', '四类区', '是', '18289093584', '70');
INSERT INTO `leave_user` VALUES ('2941', '强巴热旦', '男', '1981-02-27', '2002-07-01', '西藏仁布县', '西藏仁布县', '美巴切勤乡', '书记', '正科', '四类区', '是', '13518927717', '64');
INSERT INTO `leave_user` VALUES ('2942', '格桑达瓦', '男', '1986-03-01', '2011-12-01', '西藏尼木县', '西藏尼木县', '美巴切勤乡', '副书记', '副科', '四类区', '否', '13658924455', '56');
INSERT INTO `leave_user` VALUES ('2943', '多吉伦珠', '男', '1981-06-19', '2002-12-01', '西藏聂拉木县', '西藏谢通门县', '美巴切勤乡派出所', '科员', '科员', '四类区', '否', '15289028682', '54');
INSERT INTO `leave_user` VALUES ('2944', '江白多吉', '男', '1989-10-15', '2013-08-15', '西藏日喀则市', '无', '美巴切勤乡派出所', '科员', '科员', '四类区', '否', '18208078207', '52');
INSERT INTO `leave_user` VALUES ('2945', '张永占', '男', '1986-06-01', '2012-11-01', '山东滕州', '无', '美巴切勤乡', '科员', '科员', '四类区', '是', '17708923344', '70');
INSERT INTO `leave_user` VALUES ('2946', '马江', '男', '1982-12-01', '2006-07-01', '重庆万州', '日喀则市', '切琼乡', '书记', '正科', '四类区', '否', '13638920881', '70');
INSERT INTO `leave_user` VALUES ('2947', '次仁顿珠', '男', '1984-11-01', '2007-07-01', '日喀则市白郎县', '日喀则亚东县', '切琼乡', '主席', '正科', '四类区', '是', '13659576228', '64');
INSERT INTO `leave_user` VALUES ('2948', '益西格桑', '男', '1981-10-01', '2005-07-01', '日喀则市江孜县', '日喀则市', '切琼乡', '乡长', '正科', '四类区', '否', '13989929278', '54');
INSERT INTO `leave_user` VALUES ('2949', '次旺仁增', '男', '1981-09-01', '2004-07-01', '日喀则市', '拉萨', '切琼乡', '主任科员', '正科', '四类区', '否', '13659573610', '56');
INSERT INTO `leave_user` VALUES ('2950', '张家林', '男', '1974-08-01', '1999-07-01', '四川乐山', '无', '切琼乡', '主任科员', '正科', '四类区', '否', '18982257505', '70');
INSERT INTO `leave_user` VALUES ('2951', '张丁水', '男', '1986-04-01', '2010-08-01', '四川巴中', '通门县卡嘎镇', '切琼乡', '纪委书记', '副科', '四类区', '是', '18008925066', '70');
INSERT INTO `leave_user` VALUES ('2952', '索朗普尺', '女', '1987-07-01', '2010-11-01', '日喀则市江孜县', '日喀则市', '切琼乡', '副乡长', '副科', '四类区', '是', '15208096031', '64');
INSERT INTO `leave_user` VALUES ('2953', '王琳', '男', '1992-09-01', '2015-12-01', '河南洛阳', '无', '切琼乡', '科员', '科员', '四类区', '否', '17337937820', '70');
INSERT INTO `leave_user` VALUES ('2954', '瞿云陶', '男', '1994-12-01', '2013-12-01', '云南玉溪', '无', '切琼乡', '科员', '科员', '四类区', '否', '18187736429', '70');
INSERT INTO `leave_user` VALUES ('2955', '多吉次旦', '男', '1967-07-01', '2014-11-01', '西藏谢通门', '无', '切琼乡', '科员', '科员', '四类区', '否', '13638925307', '50');
INSERT INTO `leave_user` VALUES ('2956', '尼玛扎西', '男', '1990-04-01', '2012-07-01', '西藏谢通门', '无', '切琼乡派出所', '民警', '科员', '四类区', '否', '18389029996', '50');
INSERT INTO `leave_user` VALUES ('2957', '刘磊峰', '男', '1991-01-01', '2012-10-01', '湖南湘潭', '无', '切琼乡派出所', '民警', '科员', '四类区', '否', '18076921354', '70');
INSERT INTO `leave_user` VALUES ('2958', '游本国', '男', '1992-02-01', '2012-10-01', '云南镇雄', '福建泉州', '切琼乡派出所', '民警', '科员', '四类区', '是', '17711987545', '70');
INSERT INTO `leave_user` VALUES ('2959', '白马央金', '女', '1985-06-01', '2008-07-01', '西藏南木林县', '西藏谢通门县', '吴坚古汝寺管会', '主任', '正科', '三类区', '否', '15208097965', '44');
INSERT INTO `leave_user` VALUES ('2960', '洛桑桑珠', '男', '1988-07-01', '2013-08-01', '西藏山南曲松县', '西藏日喀则市桑珠孜区', '吴坚古汝寺管会', '科员', '科员', '三类区', '否', '18898020460', '46');
INSERT INTO `leave_user` VALUES ('2961', '尹文明', '男', '1977-12-16', '1998-07-15', '四川省宣汉县', '四川省达州市', '列巴乡', '书记', '正科', '三类区', '是', '13518921902', '70');
INSERT INTO `leave_user` VALUES ('2962', '普布顿珠', '男', '1982-06-17', '2005-07-15', '日喀则市南木林县', '日喀则市昂仁县', '列巴乡', '乡长', '正科', '三类区', '是', '13989929060', '64');
INSERT INTO `leave_user` VALUES ('2963', '次仁顿珠', '男', '1987-08-09', '2008-07-15', '西藏日喀则市', '昌都市卡若区', '列巴乡', '主席', '正科', '三类区', '是', '18089929990', '68');
INSERT INTO `leave_user` VALUES ('2964', '多珍', '女', '1985-08-01', '2009-11-25', '日喀则市白朗县', '日喀则市白朗县', '列巴乡', '副书记', '副科', '三类区', '是', '18189083886', '64');
INSERT INTO `leave_user` VALUES ('2965', '次旦央吉', '女', '1987-05-17', '2011-11-25', '日喀则市南木林县', '日喀则市南木林县', '列巴乡', '纪委书记', '副科', '三类区', '是', '18708023333', '64');
INSERT INTO `leave_user` VALUES ('2966', '顿堆多吉', '男', '1989-10-20', '2009-11-01', '日喀则市江孜县', '日喀则市仁布县', '列巴乡派出所', '所长', '正科', '三类区', '是', '15289126061', '64');
INSERT INTO `leave_user` VALUES ('2967', '泽必', '女', '1984-12-24', '2006-08-15', '拉萨市城关区', '西藏日喀则市', '列巴乡', '副乡长', '副科', '三类区', '否', '17708906825', '56');
INSERT INTO `leave_user` VALUES ('2968', '杜刚', '男', '1984-12-29', '2012-10-01', '四川省绵阳', '四川省绵阳市', '列巴乡', '主任', '副科', '三类区', '是', '15889025826', '70');
INSERT INTO `leave_user` VALUES ('2969', '次仁旺拉', '男', '1991-08-23', '2013-08-01', '西藏日喀则市', '日喀则市白朗县', '列巴乡', '副主任科员', '副科', '三类区', '否', '15208029699', '54');
INSERT INTO `leave_user` VALUES ('2970', '旦增欧珠', '男', '1989-03-26', '2013-08-10', '西藏日喀则市', '无', '列巴乡', '副主任科员', '副科', '三类区', '是', '13989977811', '52');
INSERT INTO `leave_user` VALUES ('2971', '吕德鑫', '男', '1993-05-15', '2017-07-15', '云南省曲靖', '江西上饶市婺源县', '列巴乡', '科员', '科员', '三类区', '是', '18184982690', '70');
INSERT INTO `leave_user` VALUES ('2972', '次旦卓玛', '女', '1993-05-12', '2017-12-15', '拉萨市城关区', '无', '列巴乡', '科员', '科员', '三类区', '否', '13658996336', '56');
INSERT INTO `leave_user` VALUES ('2973', '次仁扎西', '男', '1991-10-26', '2013-08-15', '拉萨市城关区', '无', '列巴乡派出所', '科员', '科员', '三类区', '否', '15208098172', '56');
INSERT INTO `leave_user` VALUES ('2974', '王梦梦', '男', '1992-09-21', '2013-12-01', '湖北省天门市', '重庆市壁山县', '列巴乡派出所', '科员', '科员', '三类区', '是', '18108922711', '70');
INSERT INTO `leave_user` VALUES ('2975', '多拉', '男', '1971-03-25', '1995-03-15', '日喀则市谢通门县', '日喀则市谢通门县', '卓列寺管委会', '科员', '科员', '三类区', '否', '13989920553', '50');
INSERT INTO `leave_user` VALUES ('2976', '顿珠', '男', '1961-03-14', '1988-07-01', '西藏谢通门', '无', '卓列寺管委会', '主任', '正科', '三类区', '否', '13989922059', '50');
INSERT INTO `leave_user` VALUES ('2977', '占堆', '男', '1984-12-02', '2012-07-01', '那曲地区尼玛县', '日喀则市拉孜县', '卓列寺管委会', '科员', '科员', '三类区', '是', '13628915930', '68');
INSERT INTO `leave_user` VALUES ('2978', '旺久', '男', '1962-12-01', '1983-07-01', '西藏日喀则', '西藏亚东', '检察院', '检察长', '副县', '二类区', '是', '13658920088', '50');
INSERT INTO `leave_user` VALUES ('2979', '拉巴次仁', '男', '1981-02-01', '2004-09-01', '西藏江孜', '西藏日喀则', '检察院', '副检察长', '正科', '二类区', '是', '13549020100', '44');
INSERT INTO `leave_user` VALUES ('2980', '胡辅平', '男', '1981-09-01', '2005-07-01', '湖南娄底', '湖南娄底', '检察院', '副检察长', '正科', '二类区', '是', '15208098108', '50');
INSERT INTO `leave_user` VALUES ('2981', '旦格', '男', '1986-02-01', '2009-07-01', '西藏江孜', '西藏日喀则', '检察院', '副检察长', '副科', '二类区', '否', '13989927197', '34');
INSERT INTO `leave_user` VALUES ('2982', '索朗卓嘎', '女', '1986-07-01', '2008-07-01', '西藏拉萨', '西藏昌都', '检察院', '副科实职', '副科', '二类区', '否', '13638929018', '38');
INSERT INTO `leave_user` VALUES ('2983', '闫利云', '女', '1986-08-01', '2009-07-01', '河南鹤壁', '四川南充', '检察院', '副科实职', '副科', '二类区', '否', '13989925639', '50');
INSERT INTO `leave_user` VALUES ('2984', '平措朗吉', '男', '1985-01-01', '2009-07-01', '西藏仁布', '西藏谢通门县', '检察院', '副科实职', '副科', '二类区', '否', '15889023023', '34');
INSERT INTO `leave_user` VALUES ('2985', '平措顿珠', '男', '1989-01-01', '2012-02-01', '西藏山南', '西藏日喀则', '检察院', '副科实职', '副科', '二类区', '是', '18908999505', '44');
INSERT INTO `leave_user` VALUES ('2986', '曲尼措姆', '女', '1986-01-01', '2008-07-01', '西藏拉萨', '西藏谢通门县', '检察院', '副科实职', '副科', '二类区', '是', '18008973616', '46');
INSERT INTO `leave_user` VALUES ('2987', '次仁德吉', '女', '1991-12-01', '2014-11-01', '西藏日喀则', '未婚', '检察院', '科员', '科员', '二类区', '否', '18708020627', '32');
INSERT INTO `leave_user` VALUES ('2988', '拉珍', '女', '1993-04-01', '2015-12-01', '西藏日喀则', '未婚', '检察院', '科员', '科员', '二类区', '否', '15208028238', '32');
INSERT INTO `leave_user` VALUES ('2989', '赵苏长', '男', '1989-09-01', '2016-02-01', '四川射洪', '未婚', '检察院', '科员', '科员', '二类区', '否', '15089046443', '50');
INSERT INTO `leave_user` VALUES ('2990', '焦文龙', '男', '1990-08-01', '2015-12-01', '陕西咸阳', '未婚', '检察院', '科员', '科员', '二类区', '否', '18898024556', '50');
INSERT INTO `leave_user` VALUES ('2991', '王小晶', '女', '1989-07-01', '2016-02-01', '河南许昌', '未婚', '检察院', '科员', '科员', '二类区', '否', '18889080651', '50');
INSERT INTO `leave_user` VALUES ('2992', '丹增白珍', '女', '1991-12-01', '2015-12-01', '贵州兴义', '未婚', '检察院', '科员', '科员', '二类区', '否', '15608980561', '50');
INSERT INTO `leave_user` VALUES ('2993', '格桑卓玛', '女', '1986-07-01', '2015-12-01', '西藏聂拉木', '西藏聂拉木', '检察院', '科员', '科员', '二类区', '否', '13659572538', '34');
INSERT INTO `leave_user` VALUES ('2994', '李建浩', '男', '1987-11-01', '2004-12-01', '河南叶县', '四川', '措布西乡派出所', '副所长', '副科', '二类区', '是', '13628921777', '50');
INSERT INTO `leave_user` VALUES ('2995', '桑杰曲扎', '男', '1989-04-04', '2013-08-01', '西藏山南浪卡子县', '西藏日喀则市', '公安局', '科员', '科员', '二类区', '是', '17711973444', '46');
INSERT INTO `leave_user` VALUES ('2996', '边巴扎西', '男', '1991-06-22', '2012-07-15', '西藏拉萨市', '西藏日喀则市', '公安局', '科员', '副科', '二类区', '否', '18076900077', '36');
INSERT INTO `leave_user` VALUES ('2997', '阿陪', '男', '1987-09-16', '2012-07-15', '西藏谢通门县', '西藏山南错那县', '公安局', '科员', '科员', '二类区', '是', '18008922555', '46');
INSERT INTO `leave_user` VALUES ('2998', '马琳', '女', '1984-06-19', '2007-01-01', '河南省临颍县', '无', '孜许乡派出所', '副所长', '副科', '三类区', '是', '13618920305', '50');
INSERT INTO `leave_user` VALUES ('2999', '杨志国', '男', '1995-12-11', '2017-12-15', '山西省岚县', '无', '公安局', '科员', '科员', '二类区', '是', '13353435237', '50');
INSERT INTO `leave_user` VALUES ('3000', '次仁扎西', '男', '1988-11-03', '2012-07-01', '西藏昂仁县', '西藏日喀则市', '公安局', '科员', '科员', '二类区', '是', '18898026626', '34');
INSERT INTO `leave_user` VALUES ('3001', '李晨', '男', '1989-01-02', '2011-08-01', '甘肃通渭县', '无', '公安局', '副主任科员', '副科', '二类区', '是', '18708023901', '50');
INSERT INTO `leave_user` VALUES ('3002', '蒋丽强', '男', '1993-05-04', '2012-10-01', '云南保山市', '无', '公安局', '科员', '科员', '二类区', '是', '13658921273', '50');
INSERT INTO `leave_user` VALUES ('3003', '格桑旺姆', '女', '1989-05-10', '2011-08-01', '西藏南木林县', '无', '公安局', '副主任科员', '副科', '二类区', '否', '13989021942', '34');
INSERT INTO `leave_user` VALUES ('3004', '拉片', '女', '1988-01-30', '2013-08-01', '西藏江孜县', '无', '公安局', '科员', '科员', '二类区', '否', '18289097813', '34');
INSERT INTO `leave_user` VALUES ('3005', '索朗旺杰', '男', '1990-01-02', '2013-08-01', '西藏墨竹工卡县', '无', '公安局', '科员', '科员', '二类区', '否', '18289100993', '36');
INSERT INTO `leave_user` VALUES ('3006', '普布次仁', '男', '1990-12-14', '2013-08-01', '西藏康玛县', '无', '公安局', '科员', '科员', '二类区', '否', '18489184557', '34');
INSERT INTO `leave_user` VALUES ('3007', '次仁占堆', '男', '1990-08-05', '2013-08-01', '西藏南木林县', '无', '公安局', '科员', '科员', '二类区', '否', '18184984332', '34');
INSERT INTO `leave_user` VALUES ('3008', '索朗扎西', '男', '1989-08-11', '2013-08-01', '西藏墨竹工卡县', '无', '公安局', '科员', '科员', '二类区', '否', '18143203007', '36');
INSERT INTO `leave_user` VALUES ('3009', '云旦平措', '男', '1989-06-21', '2011-08-01', '西藏南木林县', '无', '公安局', '队长', '副科', '二类区', '否', '18798927722', '34');
INSERT INTO `leave_user` VALUES ('3010', '侯博星', '男', '1995-12-27', '2017-12-15', '西安市周至县', '陕西省商县', '公安局', '科员', '科员', '二类区', '是', '17629200043', '50');
INSERT INTO `leave_user` VALUES ('3011', '张飞', '男', '1984-06-10', '2013-12-01', '四川省南充市', '无', '公安局', '科员', '科员', '二类区', '是', '18889029708', '50');
INSERT INTO `leave_user` VALUES ('3012', '洛绒加挖', '男', '1988-08-08', '2011-11-01', '四川省色达县', '西藏谢通门县', '公安局', '队长', '副科', '二类区', '是', '13628923492', '50');
INSERT INTO `leave_user` VALUES ('3013', '刘正天', '男', '1985-09-14', '2013-02-01', '甘肃省武威市', '甘肃省武威市京州区', '公安局', '科员', '科员', '二类区', '是', '18289097787', '50');
INSERT INTO `leave_user` VALUES ('3014', '索朗普赤', '女', '1989-06-21', '2009-10-01', '西藏日喀则市', '西藏山南浪卡子县', '公安局', '副主任科员', '副科', '二类区', '否', '15289125395', '36');
INSERT INTO `leave_user` VALUES ('3015', '洛桑朗加', '男', '1993-02-08', '2013-08-01', '西藏浪卡子县', '西藏日喀则市', '公安局', '科员', '科员', '四类区', '否', '15289129191', '36');
INSERT INTO `leave_user` VALUES ('3016', '索朗卓嘎', '女', '1997-04-16', '2017-12-15', '西藏山南贡嘎县', '无', '公安局', '科员', '科员', '二类区', '否', '13618912442', '36');
INSERT INTO `leave_user` VALUES ('3017', '时生强', '男', '1995-10-08', '2017-12-15', '青海省乐都县', '无', '公安局', '科员', '科员', '二类区', '是', '15500542581', '50');
INSERT INTO `leave_user` VALUES ('3018', '边俊录', '男', '1990-05-23', '2017-12-15', '山西省朔州市', '无', '公安局', '科员', '科员', '二类区', '是', '13994225043', '50');
INSERT INTO `leave_user` VALUES ('3019', '德吉卓嘎', '女', '1990-05-20', '2012-07-15', '西藏日喀则市', '无', '公安局', '科员', '科员', '二类区', '否', '18308098221', '32');
INSERT INTO `leave_user` VALUES ('3020', '次仁拉姆', '女', '1984-05-15', '2007-08-01', '西藏日喀则市', '西藏日喀则市', '公安局', '副主任科员', '副科', '二类区', '否', '13648928985', '32');
INSERT INTO `leave_user` VALUES ('3021', '次多', '男', '1980-06-24', '2001-07-01', '西藏日喀则市', '西藏日喀则市', '达那答乡派出所', '所长', '正科', '三类区', '否', '13989026969', '32');
INSERT INTO `leave_user` VALUES ('3022', '蒋敏', '女', '1989-10-25', '2012-07-15', '河北省大名县', '无', '公安局', '科员', '科员', '二类区', '否', '18143874555', '50');
INSERT INTO `leave_user` VALUES ('3023', '穷拉', '女', '1993-07-14', '2015-12-01', '西藏谢通门县', '西藏江孜县', '公安局', '科员', '科员', '二类区', '否', '18289026426', '34');
INSERT INTO `leave_user` VALUES ('3024', '普琼', '男', '1993-03-18', '2013-08-01', '西藏江孜县', '西藏谢通门县', '达那答乡派出所', '科员', '科员', '二类区', '否', '15289101105', '34');
INSERT INTO `leave_user` VALUES ('3025', '白央', '女', '1974-08-18', '1991-12-01', '西藏谢通门县', '无', '卡嘎镇派出所', '副所长', '副科', '二类区', '否', '13889029146', '50');
INSERT INTO `leave_user` VALUES ('3026', '韦威华', '男', '1990-08-03', '2012-10-01', '广西壮族来宾市', '无', '公安局', '科员', '科员', '二类区', '是', '18289129668', '50');
INSERT INTO `leave_user` VALUES ('3027', '张怀', '男', '1989-12-01', '2013-12-01', '四川省仪陇县', '无', '公安局', '科员', '科员', '二类区', '是', '15208095400', '50');
INSERT INTO `leave_user` VALUES ('3028', '阿旺多吉', '男', '1992-07-09', '2013-08-01', '西藏日喀则市', '无', '公安局', '科员', '科员', '二类区', '否', '13989027913', '32');
INSERT INTO `leave_user` VALUES ('3029', '罗布', '男', '1993-07-31', '2011-12-01', '西藏日喀则市', '无', '公安局', '科员', '科员', '二类区', '否', '18089926302', '32');
INSERT INTO `leave_user` VALUES ('3030', '雷石', '男', '1991-10-16', '2013-12-01', '四川省阆中市', '无', '公安局', '科员', '科员', '二类区', '是', '17789020631', '50');
INSERT INTO `leave_user` VALUES ('3031', '巴桑扎西', '男', '1989-02-18', '2012-07-15', '西藏吉隆县', '无', '公安局', '队长', '副科', '二类区', '否', '18143205955', '34');
INSERT INTO `leave_user` VALUES ('3032', '格桑塔杰', '男', '1989-03-04', '2011-12-01', '西藏昂仁县', '无', '公安局', '科员', '科员', '二类区', '否', '18208096066', '34');
INSERT INTO `leave_user` VALUES ('3033', '塔杰', '男', '1983-02-21', '2005-07-01', '西藏日喀则市', '西藏江孜县', '公安局', '主任科员', '正科', '二类区', '是', '13618928887', '44');
INSERT INTO `leave_user` VALUES ('3034', '拉巴顿珠', '男', '1989-11-06', '2013-08-01', '西藏日喀则市', '西藏南木林县', '公安局', '主任科员', '正科', '二类区', '是', '18184981110', '44');
INSERT INTO `leave_user` VALUES ('3035', '何忠凯', '男', '1992-11-21', '2011-12-01', '四川省眉山市', '无', '公安局', '科员', '科员', '二类区', '是', '18798998263', '50');
INSERT INTO `leave_user` VALUES ('3036', '杨丹', '男', '1996-02-08', '2017-12-15', '陕西省城固县', '无', '公安局', '科员', '科员', '二类区', '是', '18329469803', '50');
INSERT INTO `leave_user` VALUES ('3037', '拉巴次仁', '男', '1991-01-15', '2013-08-01', '西藏亚东县', '西藏南木林县', '公安局', '科员', '科员', '二类区', '是', '18184999899', '44');
INSERT INTO `leave_user` VALUES ('3038', '史明', '男', '1986-01-30', '2009-07-01', '河北省普中地区', '河北省大康县', '公安局', '队长', '副科', '二类区', '是', '13653410505', '50');
INSERT INTO `leave_user` VALUES ('3039', '顿珠朗杰', '男', '1992-06-01', '2013-08-01', '西藏山南洛扎县', '无', '公安局', '科员', '科员', '二类区', '否', '18189080086', '36');
INSERT INTO `leave_user` VALUES ('3040', '赵一凡', '女', '1994-10-05', '2017-12-15', '甘肃省陇南市', '无', '公安局', '科员', '科员', '二类区', '是', '17693622135', '50');
INSERT INTO `leave_user` VALUES ('3041', '孙晨', '男', '1993-02-11', '2012-10-01', '山东省枣庄市', '山东省枣庄市', '达那答检查站', '科员', '科员', '三类区', '是', '18389083482', '50');
INSERT INTO `leave_user` VALUES ('3042', '顿珠', '男', '1994-08-05', '2015-12-01', '西藏谢通门县', '无', '达那答检查站', '科员', '科员', '三类区', '否', '15208012653', '30');
INSERT INTO `leave_user` VALUES ('3043', '郑洪燕', '男', '1986-03-17', '2011-11-01', '山东省单县', '无', '达那答检查站', '副主任科员', '副科', '三类区', '是', '13618921262', '50');
INSERT INTO `leave_user` VALUES ('3044', '米玛桑珠', '男', '1990-02-25', '2013-08-01', '西藏亚东县', '西藏山南乃东县', '达那答检查站', '科员', '科员', '三类区', '否', '13549047038', '36');
INSERT INTO `leave_user` VALUES ('3045', '扎西次仁', '男', '1990-04-30', '2013-08-01', '西藏达子县', '西藏南木林县', '达那答检查站', '科员', '科员', '三类区', '否', '13659537612', '36');
INSERT INTO `leave_user` VALUES ('3046', '周正', '男', '1988-12-26', '2013-12-01', '山东省嘉祥县', '无', '达那答检查站', '科员', '科员', '三类区', '是', '18108923456', '50');
INSERT INTO `leave_user` VALUES ('3047', '加央旦增', '男', '1983-05-04', '2007-10-31', '西藏萨迦县', '西藏日喀则市', '达那答检查站', '副站长', '副科', '三类区', '否', '13989928103', '34');
INSERT INTO `leave_user` VALUES ('3048', '仁青措姆', '女', '1989-03-05', '2010-10-01', '西藏芒康县', '无', '公安局', '副主任科员', '副科', '二类区', '是', '18798998987', '48');
INSERT INTO `leave_user` VALUES ('3049', '格桑旦增', '男', '1987-05-16', '2010-08-01', '西藏山南措美县', '西藏日喀则市', '公安局', '队长', '副科', '二类区', '否', '15889076669', '36');
INSERT INTO `leave_user` VALUES ('3050', '付永青', '男', '1990-03-06', '2012-10-01', '云南省保山市', '无', '公安局', '科员', '科员', '二类区', '是', '18798924608', '50');
INSERT INTO `leave_user` VALUES ('3051', '达央', '女', '1991-10-21', '2013-08-01', '西藏江孜县', '无', '公安局', '科员', '科员', '二类区', '否', '17711926663', '34');
INSERT INTO `leave_user` VALUES ('3052', '旦增格桑', '男', '1986-06-20', '2013-08-01', '西藏拉孜县', '无', '公安局', '科员', '科员', '二类区', '否', '18489188882', '34');
INSERT INTO `leave_user` VALUES ('3053', '洛桑曲达', '男', '1989-12-05', '2012-07-15', '西藏萨嘎县', '西藏林周县', '公安局', '科员', '科员', '二类区', '否', '13889022992', '36');
INSERT INTO `leave_user` VALUES ('3054', '武凯', '男', '1995-04-22', '2017-12-01', '甘肃天水市秦城区', '无', '公安局', '科员', '科员', '二类区', '是', '15699052828', '50');
INSERT INTO `leave_user` VALUES ('3055', '白玛旦增', '男', '1989-05-19', '2011-11-01', '西藏江孜县', '无', '公安局', '队长', '副科', '二类区', '否', '17789027779', '34');
INSERT INTO `leave_user` VALUES ('3056', '晋巴', '男', '1990-09-21', '2013-08-01', '西藏南木林县', '西藏谢通门县', '公安局', '科员', '科员', '二类区', '是', '17711926777', '44');
INSERT INTO `leave_user` VALUES ('3057', '李江', '男', '1995-03-07', '2017-12-15', '四川省达县', '无', '公安局', '科员', '科员', '二类区', '是', '18982813149', '50');
INSERT INTO `leave_user` VALUES ('3058', '罗旦', '男', '1990-06-08', '2012-07-15', '西藏萨迦县', '西藏谢通门县', '公安局', '科员', '科员', '二类区', '否', '15708023454', '34');
INSERT INTO `leave_user` VALUES ('3059', '欧阳文明', '男', '1989-01-09', '2012-10-01', '湖南省宁远县', '无', '解放中路便民警务站', '科员', '科员', '二类区', '是', '18143229530', '50');
INSERT INTO `leave_user` VALUES ('3060', '张海飞', '男', '1987-11-09', '2012-10-01', '河南省汤阴县', '无', '解放中路便民警务站', '科员', '科员', '二类区', '是', '13628994922', '50');
INSERT INTO `leave_user` VALUES ('3061', '张青福', '男', '1990-04-16', '2012-10-01', '湖南省麻阳县', '无', '解放中路便民警务站', '科员', '科员', '二类区', '是', '13989024601', '50');
INSERT INTO `leave_user` VALUES ('3062', '庄德志', '男', '1990-05-21', '2013-12-01', '山东省青州市', '无', '解放中路便民警务站', '科员', '科员', '二类区', '是', '17011171060', '50');
INSERT INTO `leave_user` VALUES ('3063', '益西旺久', '男', '1991-05-20', '2013-08-01', '西藏日喀则市', '无', '解放中路便民警务站', '科员', '科员', '二类区', '否', '13648923773', '32');
INSERT INTO `leave_user` VALUES ('3064', '强巴达娃', '男', '1989-10-05', '2013-02-01', '西藏山南琼结县', '无', '解放中路便民警务站', '科员', '科员', '二类区', '否', '18143822111', '36');
INSERT INTO `leave_user` VALUES ('3065', '普布旦增', '男', '1989-11-25', '2012-07-15', '西藏日喀则市', '西藏定日县', '解放中路便民警务站', '科员', '科员', '二类区', '是', '18008926030', '44');
INSERT INTO `leave_user` VALUES ('3066', '索朗多布杰', '男', '1990-11-24', '2013-08-01', '西藏山南扎囊县', '西藏白朗县', '解放中路便民警务站', '科员', '科员', '二类区', '是', '18389027827', '46');
INSERT INTO `leave_user` VALUES ('3067', '勤次平措', '男', '1992-01-17', '2013-08-01', '西藏日喀则市', '无', '解放中路便民警务站', '科员', '科员', '二类区', '否', '18708028147', '32');
INSERT INTO `leave_user` VALUES ('3068', '穷巴', '男', '1989-03-07', '2012-07-15', '西藏南木林县', '无', '解放中路便民警务站', '站长', '副科', '二类区', '否', '13659578283', '34');
INSERT INTO `leave_user` VALUES ('3069', '张雨', '男', '1985-12-11', '2010-07-01', '四川省仁寿县', '无', '卡嘎温泉便民警务站', '站长', '副科', '二类区', '是', '13518922509', '50');
INSERT INTO `leave_user` VALUES ('3070', '加央多吉', '男', '1991-03-23', '2013-08-01', '西藏谢通门县', '无', '卡嘎温泉便民警务站', '科员', '科员', '二类区', '否', '18389085051', '30');
INSERT INTO `leave_user` VALUES ('3071', '嘎玛加参', '男', '1989-08-09', '2013-08-01', '西藏亚东县', '无', '卡嘎温泉便民警务站', '科员', '科员', '二类区', '否', '13518994798', '34');
INSERT INTO `leave_user` VALUES ('3072', '李洪才', '男', '1984-04-15', '2011-12-01', '贵州省安顺市', '云南省绥江县', '卡嘎温泉便民警务站', '科员', '科员', '二类区', '是', '13688535334', '50');
INSERT INTO `leave_user` VALUES ('3073', '彭建波', '男', '1990-09-05', '2013-08-01', '青海格尔木', '无', '卡嘎温泉便民警务站', '科员', '科员', '二类区', '是', '17708906831', '50');
INSERT INTO `leave_user` VALUES ('3074', '齐玉章', '男', '1993-06-01', '2013-12-01', '黑龙江省肇州县', '无', '卡嘎温泉便民警务站', '科员', '科员', '二类区', '是', '18184928987', '50');
INSERT INTO `leave_user` VALUES ('3075', '杨军洪', '男', '1985-07-05', '2011-12-01', '贵州省剑河县', '无', '吉定西路便民警务站', '站长', '副科', '二类区', '是', '13648923071', '50');
INSERT INTO `leave_user` VALUES ('3076', '黄大正', '男', '1993-03-20', '2012-10-01', '湖南省津市市', '无', '吉定西路便民警务站', '科员', '科员', '二类区', '是', '18289121513', '50');
INSERT INTO `leave_user` VALUES ('3077', '郑奥', '男', '1993-08-05', '2013-12-01', '四川省自贡市', '无', '吉定西路便民警务站', '科员', '科员', '二类区', '是', '18008144441', '50');
INSERT INTO `leave_user` VALUES ('3078', '旦巴措赤', '男', '1987-05-03', '2013-08-01', '西藏江孜县', '西藏江孜县', '吉定西路便民警务站', '科员', '科员', '二类区', '是', '18189929469', '44');
INSERT INTO `leave_user` VALUES ('3079', '李全杰', '男', '1993-04-01', '2017-12-15', '甘肃省临夏县', '无', '公安局', '科员', '科员', '二类区', '是', '18394511391', '50');
INSERT INTO `leave_user` VALUES ('3080', '扎西顿珠', '男', '1992-05-15', '2013-08-01', '西藏康玛县', '西藏江孜县', '公安局', '科员', '科员', '二类区', '是', '18089975717', '44');
INSERT INTO `leave_user` VALUES ('3081', '扎西努布', '男', '1990-04-16', '2013-08-01', '西藏谢通门县', '无', '拉旺孜检查站', '科员', '科员', '二类区', '否', '15728923454', '30');
INSERT INTO `leave_user` VALUES ('3082', '边巴旺堆', '男', '1992-01-02', '2015-12-01', '西藏白朗县', '西藏日喀则市', '拉旺孜检查站', '科员', '科员', '二类区', '是', '18383098175', '44');
INSERT INTO `leave_user` VALUES ('3083', '李超', '男', '1990-11-23', '2011-12-01', '山西省岐山县', '无', '拉旺孜检查站', '科员', '科员', '二类区', '是', '18108985199', '50');
INSERT INTO `leave_user` VALUES ('3084', '格桑群培', '男', '1988-08-07', '2013-08-01', '西藏山南扎囊县', '西藏山南浪卡子县', '公安局', '科员', '科员', '二类区', '是', '13628945692', '46');
INSERT INTO `leave_user` VALUES ('3085', '陈思', '男', '1992-11-12', '2017-12-15', '云南凤庆县', '无', '公安局', '科员', '科员', '二类区', '是', '14787452414', '50');
INSERT INTO `leave_user` VALUES ('3086', '落桑', '男', '1993-12-26', '2016-08-01', '西藏南木林县', '西藏日喀则市', '公安局', '科员', '科员', '二类区', '是', '15358920170', '44');
INSERT INTO `leave_user` VALUES ('3087', '扎西次仁', '男', '1992-05-18', '2008-12-01', '西藏日喀则市', '无', '公安局', '科员', '科员', '二类区', '否', '18143828055', '32');
INSERT INTO `leave_user` VALUES ('3088', '格桑多吉', '男', '1992-08-08', '2013-08-01', '西藏南木林县', '西藏山南浪卡子县', '公安局', '科员', '科员', '二类区', '否', '17711927771', '36');
INSERT INTO `leave_user` VALUES ('3089', '葛德', '男', '1986-11-29', '2007-01-01', '四川省巴塘县', '无', '公安局', '政委', '正科', '二类区', '是', '13628929000', '50');

-- ----------------------------
-- Table structure for temporary_leave
-- ----------------------------
DROP TABLE IF EXISTS `temporary_leave`;
CREATE TABLE `temporary_leave` (
  `id` int(11) NOT NULL auto_increment,
  `user_id` int(11) default NULL,
  `content` varchar(255) default NULL,
  `message_date` varchar(32) default NULL,
  PRIMARY KEY  (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=52 DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of temporary_leave
-- ----------------------------
INSERT INTO `temporary_leave` VALUES ('1', '14', '测试', '2017-12-01');
INSERT INTO `temporary_leave` VALUES ('2', '14', '测试', '2017-12-02');
INSERT INTO `temporary_leave` VALUES ('3', '14', '测试', '2017-12-02');
INSERT INTO `temporary_leave` VALUES ('4', '24', '我临时有事', '2017-12-02');
INSERT INTO `temporary_leave` VALUES ('5', '10', '临时有事', '2017-12-02');
INSERT INTO `temporary_leave` VALUES ('6', '25', '哈哈哈哈', '2017-12-02');
INSERT INTO `temporary_leave` VALUES ('7', '10', '巨幕口苦骷髅精灵', '2017-12-02');
INSERT INTO `temporary_leave` VALUES ('8', '10', '朱世财请假去洗澡', '2017-12-02');
INSERT INTO `temporary_leave` VALUES ('9', '27', '嗯', '2017-12-03');
INSERT INTO `temporary_leave` VALUES ('10', '44', '来咯好哦', '2017-12-09');
INSERT INTO `temporary_leave` VALUES ('11', '46', '两路口困特特', '2017-12-11');
INSERT INTO `temporary_leave` VALUES ('12', '46', '自由自我教育', '2017-12-11');
INSERT INTO `temporary_leave` VALUES ('13', '48', '我想去买菜', '2017-12-11');
INSERT INTO `temporary_leave` VALUES ('14', '48', '我在组织部', '2017-12-11');
INSERT INTO `temporary_leave` VALUES ('15', '48', '我要去洗个澡', '2017-12-11');
INSERT INTO `temporary_leave` VALUES ('16', '46', '哈哈好的', '2017-12-12');
INSERT INTO `temporary_leave` VALUES ('17', '46', '没意义', '2017-12-14');
INSERT INTO `temporary_leave` VALUES ('18', '46', '墨迹咯啦咯', '2017-12-16');
INSERT INTO `temporary_leave` VALUES ('19', '50', '嘻嘻嘻WWI', '2017-12-17');
INSERT INTO `temporary_leave` VALUES ('20', '52', '有事出去', '2017-12-17');
INSERT INTO `temporary_leave` VALUES ('21', '53', 'ing', '2017-12-18');
INSERT INTO `temporary_leave` VALUES ('22', '53', '呵呵哒', '2017-12-18');
INSERT INTO `temporary_leave` VALUES ('23', '53', '呵呵哒', '2017-12-18');
INSERT INTO `temporary_leave` VALUES ('24', '53', '哎', '2017-12-18');
INSERT INTO `temporary_leave` VALUES ('25', '53', '为什么', '2017-12-18');
INSERT INTO `temporary_leave` VALUES ('26', '53', '和', '2017-12-18');
INSERT INTO `temporary_leave` VALUES ('27', '52', '完美', '2017-12-18');
INSERT INTO `temporary_leave` VALUES ('28', '52', '完美哈哈', '2017-12-18');
INSERT INTO `temporary_leave` VALUES ('29', '53', '什么鬼', '2017-12-18');
INSERT INTO `temporary_leave` VALUES ('30', '53', '测试', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('31', '65', '测试', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('32', '65', '不好', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('33', '65', '呵呵', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('34', '67', '完美', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('35', '67', '再测试', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('36', '67', '测试测试', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('37', '67', '请假', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('38', '71', '请假', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('39', '72', '测试', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('40', '73', '请假', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('41', '72', '测试', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('42', '75', '测试', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('43', '72', '请假', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('44', '76', '哦扣扣', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('45', '76', '洪荒', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('46', '76', '狗狗', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('47', '77', '哈来', '2017-12-19');
INSERT INTO `temporary_leave` VALUES ('48', '88', '临时请假测试', '2018-02-13');
INSERT INTO `temporary_leave` VALUES ('49', '88', '临时请假测试', '2018-02-13');
INSERT INTO `temporary_leave` VALUES ('50', '88', '临时请假测试', '2018-02-13');
INSERT INTO `temporary_leave` VALUES ('51', '88', '测试请假', '2018-02-13');

-- ----------------------------
-- Table structure for temporary_leave_info
-- ----------------------------
DROP TABLE IF EXISTS `temporary_leave_info`;
CREATE TABLE `temporary_leave_info` (
  `id` int(11) NOT NULL auto_increment,
  `user_id` int(11) default NULL,
  `leave_reason` varchar(255) default NULL,
  `leave_date` varchar(32) default NULL,
  `leave_hours` varchar(32) default NULL,
  PRIMARY KEY  (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=8 DEFAULT CHARSET=utf8;

-- ----------------------------
-- Records of temporary_leave_info
-- ----------------------------
INSERT INTO `temporary_leave_info` VALUES ('1', '25', '啊手动阀手动阀', '2017-12-03', '3');
INSERT INTO `temporary_leave_info` VALUES ('2', '27', '洗澡', '2017-12-07', '2个小时');
INSERT INTO `temporary_leave_info` VALUES ('3', '44', '个v发的', '2017-12-13', '2');
INSERT INTO `temporary_leave_info` VALUES ('4', '48', '我在组织部', '2017-12-11', '10');
INSERT INTO `temporary_leave_info` VALUES ('5', '48', '我要洗个澡', '2017-12-11', '5');
INSERT INTO `temporary_leave_info` VALUES ('6', '67', '请假', '2017-12-01', '2');
INSERT INTO `temporary_leave_info` VALUES ('7', '65', '请假', '2017-12-02', '3');
