CREATE TABLE project(
id INT(11) PRIMARY KEY AUTO_INCREMENT,
name VARCHAR(100)
);

CREATE TABLE task(
id INT(11) PRIMARY KEY AUTO_INCREMENT,
name VARCHAR(250) NOT NULL,
date_start DATETIME,
date_end DATETIME,
category_id INT(11) NOT NULL
);

CREATE TABLE users(
id INT(11) PRIMARY KEY AUTO_INCREMENT,
firstname VARCHAR(45) NOT NULL,
secondname VARCHAR(45) NOT NULL,
middlename VARCHAR(45),
birthdate DATE NOT NULL
);

CREATE TABLE category(
id INT(11) PRIMARY KEY AUTO_INCREMENT,
name VARCHAR(100),
parent_category INT(11)
);

CREATE TABLE tag(
id INT(11) PRIMARY KEY AUTO_INCREMENT,
name VARCHAR(45),
colour VARCHAR(100)
);
ALTER TABLE users ADD(
gender ENUM('male','female'),
email VARCHAR(255) UNIQUE,
company VARCHAR(100),
occupation VARCHAR(100),
street VARCHAR(45),
city VARCHAR(45),
state VARCHAR(45),
telephone DECIMAL(10) UNIQUE,
mobile DECIMAL(11) UNIQUE);

ALTER TABLE users
ADD CONSTRAINT UNIQUE (firstname, secondname, middlename, birthdate, street, city, state);

INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, state, gender, telephone, mobile) VALUES
('Elizabeth','Smith','Tillman','1979-08-27','murray1977@hotmail.com','Franklin_Simon','Registered Nurse','4375 Anmoore Road','New_York','New York','female','9174532005','7187131633'),
('Kay','Jones','Stanfill','1985-09-12','jermaine_thi@hotmail.com','Rainbow_Bay_Crafts','Radio and Television Announcer','4717 Golden Street','Miami','Florida','female','3056911864', '7722002115'),
('Ignacio','White','McGinley','1979-08-27','ben2012@yahoo.com','Shoe_Kicks','Loan Counselor','4751 Jail Drive',' Green_River','Illinois','male','3099498479','7084203660'),
('Jessie ','Wood','Harris','1989-09-27','charlene.hodkiewi@gmail.com','Ideal_Garden_Maintenance','Rock Splitter, Quarry','752 Melrose Street','Yakima','Washington','female',' 5099458744',' 5097317293'),
('Joan','Moore','Marquart','1991-08-15','ricky.flatl@yahoo.com','Wise_Solutions','Cook, Private Household','1310 Rosebud Avenue','Pine_Bluff','Arkansas','male','8704402924','8708728799'),
('Andrew','Thompson','Williams','1994-05-23','maye_kund0@yahoo.com','The_Serendipity_Dip','Textile Knitting and Weaving Machine Setter, Operator, and Tender','1956 Rosebud Avenue',' Little_Rock','Arkansas','male','7187131633','9174532005'),
('Linda','Rodriguez','Robinson','1996-07-07','jerrell_han3@yahoo.com','Netcore','Insurance Claims Clerk','Insurance Claims Clerk','Newark','New_Jersey','female','2017013461','2013033995'),
('Emily','Hernandez','Savoy','1964-04-11','gwen2002@gmail.com','Netcore','Special Education Teacher, All Other','2787 Patterson Road','New_York','New_York','female','7188738484','6462003786'),
('Richard','Powell',' Edmondson','1981-09-24','maddison1975@yahoo.com','Sounds_Great_Inc','Military Officer Special and Tactical Operations Leader, All Other','750 Walkers Ridge Way',' Burr_Ridge','Illinois','male','6302072505','8479170467'),
('Pamela','Powell',' Allen','1967-12-20','scottie1975@gmail.com','Personal_&_Corporate_Design','Artillery and Missile Officer','4096 Young Road',' Caldwell','Idaho','female','2084547202','27424'),
('Christy','Sanchez',' Barton','1973-05-23','hunter2006@hotmail.com','Standard_Sales','Print Binding and Finishing Worker','986 Stoneybrook Road','Orlando','Florida','female','3214375611','4079457208'),
('James','Sanchez','Harrison','1964-01-02','zoe2006@yahoo.com','Licorice_Pizza','Sound Engineering Technician','3143 Lindale Avenue','Oakland','California','male','5105547640','5108676194'),
('Daniel','Sanchez','Madrid','1991-02-21','jacinto2000@gmail.com','Hills_Supermarkets','Compensation, Benefit, and Job Analysis Specialist','4220 Ingram Street','Dayton','Ohio','male','9374716864','9372517085'),
('Jerry','Sanchez','Coleman','1982-08-09','kyleigh1979@gmail.com','ManPower','Industrial Engineering Technician','2748 Bungalow Road','Martinsburg','Nebraska','male','4029458735','3085937026'),
('Claretha','Sanchez','Bowman','1958-02-06','alexandro.vonrued@yahoo.com','Virgin_Megastores','Fire Inspector and Investigator','4497 Lightning Point Drive','Somerville','Tennessee','female','9014659533','4236474173');
ALTER TABLE users ADD new_post VARCHAR(25) DEFAULT " ";
ALTER TABLE users DROP COLUMN new_post;
ALTER TABLE users ALTER COLUMN city SET DEFAULT 'Tomsk';

ALTER TABLE users MODIFY COLUMN gender TINYINT(1) NOT NULL;
ALTER TABLE users ALTER COLUMN gender SET DEFAULT 1;

CREATE TABLE gender (
id TINYINT(1) PRIMARY KEY AUTO_INCREMENT,
rus VARCHAR(10) NOT NULL,
eng VARCHAR(10) NOT NULL
);

INSERT INTO gender (rus, eng) values
('Муж', 'male'),
('Жен', 'female');

CREATE TABLE company (
id INT(11) PRIMARY KEY AUTO_INCREMENT, 
name VARCHAR(60),
director VARCHAR(60),
TIN VARCHAR(30) UNIQUE,
PSRN VARCHAR(20) UNIQUE,
adress VARCHAR(100)
);

CREATE TABLE city (
id INT(11) PRIMARY KEY AUTO_INCREMENT,
name VARCHAR(20)
);

INSERT INTO company (name) VALUES 
('Franklin_Simon'), ('Rainbow_Bay_Crafts'), ('Shoe_Kicks'), ('Ideal_Garden_Maintenance'), ('Wise_Solutions'), ('The_Serendipity_Dip'),
('Netcore'), ('Sounds_Great_Inc'), ('Personal_&_Corporate_Design'), ('Standard_Sales'), ('Licorice_Pizza'), ('Hills_Supermarkets'),
('ManPower'), ('Virgin_Megastores');
INSERT INTO city (name) VALUES
('Tomsk'), ('Novosibirsk'), ('New_York'), ('Miami'), ('Yakima'), ('Pine_Bluss'), ('Little_Rock'), ('Newark'),
('Burr_Ridge'), ('Caldwell'), ('Orlando'), ('Oakland'), ('Dayton'), ('Martinsburg'), ('Somerville');
UPDATE users SET gender = 1;
UPDATE users set gender = 2 WHERE id IN (1,2,4,7,8,10,11,12);
ALTER TABLE users ADD FOREIGN key (gender) REFERENCES gender(id);

UPDATE users SET company = (SELECT id FROM company WHERE company.name = users.company)
WHERE EXISTS (SELECT id FROM company WHERE company.name = users.company);

ALTER TABLE users MODIFY COLUMN company INT(11);
ALTER TABLE users ADD CONSTRAINT user_company FOREIGN KEY (company) REFERENCES company(id);
UPDATE users SET city = 6 WHERE id IN (1,3,7,15);
UPDATE users SET city = 5 WHERE id IN (2,5,8);
UPDATE users SET city = 1 WHERE id IN (4,6,9);
UPDATE users SET city = 2 WHERE id IN (10,14,12);
UPDATE users SET city = 5 WHERE id IN (11,13);

ALTER TABLE users ADD COLUMN age TINYINT(3);
UPDATE users SET age = (YEAR(CURRENT_DATE)-YEAR(birthdate))-(RIGHT(CURRENT_DATE,5)<RIGHT(birthdate,5));

INSERT INTO company (name) VALUES ('Fresh Start'),('Elbrus'),('d.e.m.o.');

INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Альбина','Закруткина','Валерьевна',"1984-05-13",'albina13051984@gmail.com',1,'Interactive Quality Technician','Чапаева ул.','г. Улан-Удэ',2,7003282215,79446457489,37) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Георгий','Гулин','Давидович',"1985-11-09",'georgiy09111985@hotmail.com',1,'Product Data Facilitator','Рабочая ул.','г. Новомосковск',1,8060585720,79925562920,36) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Степан','Поличев','Гаврннлович',"1989-01-05",'stepan41@hotmail.com',1,'Senior Response Developer','Совхозная ул.','г. Сочи',1,7877624292,79536222968,33) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Кира','Малкина','Герасимовна',"1963-09-02",'kira02091963@yandex.ru',1,'Forward Research Liason','Заводская ул.','г. Долгопрудный',2,9568889458,79426849567,58) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Марк','Кондратенко','Филиппович',"1977-06-21",'mark5897@ya.ru',1,'Internal Branding Manager','Радужная ул.','г. Петропавловск-Камчатский',1,1890373490,79903332934,44) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Степан','Нардин','Филиппович',"1984-01-16",'stepan1984@gmail.com',2,'Product Markets Associate','Рабочая ул.','г. Екатеринбург',1,7799128458,79884489342,38) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Аркадий','Лероев','Евгениевич',"1973-07-16",'arkadiy1973@hotmail.com',2,'Direct Integration Technician','Заводская ул.','г. Стерлитамак',1,1780725567,79502446018,48) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Василий','Апраксин','Макарович',"1987-09-02",'vasiliy02091987@hotmail.com',2,'Human Data Representative','Садовая ул.','г. Ульяновск',1,6883132169,79419073171,34) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Гавриил','Агапов','Павлович',"1967-01-04",'gavriil04011967@mail.ru',7,'Relational Security Associate','Лесная ул.','г. Одинцово',1,6908844746,79576815631,55) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Ярослава','Минаева','Ивановна',"1981-02-05",'yaroslava05021981@outlook.com',7,'Construction Manager','Новоселов ул.','г. Кисловодск',2,2614271027,79768525028,41) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Марк','Домышев','Елизарович',"1967-12-07",'mark07121967@gmail.com',7,'Interactive Marketing Architect','Строителей ул.','г. Новочеркасск',1,193410307,79871635443,54) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Валентин','Справцев','Юрьевич',"1970-09-03",'valentin1592@ya.ru',7,'Dynamic Impact Associate','Чапаева ул.','г. Реутов',1,615090632,79799869866,51) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Юрий','Снегирёв','Евгениевич',"1979-06-09",'yuriy1872@outlook.com',7,'National Directives Technician','Спортивная ул.','г. Тамбов',1,5762965655,79647108985,42) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Давид','Сагадиев','Маркович',"1969-04-06",'david19@yandex.ru',7,'Internal Assurance Synergist','3 Марта ул.','г. Кострома',1,5916056797,79982666889,53) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Алиса','Яшвили','Семеновна',"1977-05-05",'alisa.yashvili@outlook.com',7,'Product Factors Planner','ЯнкиКупалы ул.','г. Благовещенск',2,339303649,79227923864,44) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Юрий','Рашет','Феодосивич',"1987-01-08",'yuriy9435@mail.ru',7,'Product Tactics Technician','Луговой пер.','г. Майкоп',1,237702287,79883212295,35) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Клара','Мирова','Ефимовна',"1981-08-09",'klara27@ya.ru',7,'Lawyer','Луговая ул.','г. Чебоксары',2,425194825,79643651199,40) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Валерий','Ясин','Наумович',"1996-06-25",'valeriy34@mail.ru',7,'Customer Mobility Administrator','Первомайская ул.','г. Невинномысск',1,6557921861,79386722756,25) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Савва','Железкин','Всеволодович',"1974-12-13",'savva6126@yandex.ru',10,'Dynamic Team Strategist','Октябрьский пер.','г. Новокузнецк',1,870108928,79657104189,47) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Юлиана','Шульгина','Валерьевна',"1991-04-25",'yuliana.ulgina@hotmail.com',10,'Relational Data Consultant','Минская ул.','г. Уфа',2,4444937453,79379893413,30) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Георгий','Таганцев','Романович',"1982-02-20",'georgiy20021982@ya.ru',10,'Internal Identity Orchestrator','Комсомольская ул.','г. Армавир',1,1193280480,79538804122,40) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Оксана','Мяукина','Юрьевна',"1970-12-09",'oksana1970@gmail.com',11,'Regional Creative Consultant','Белорусская ул.','г. Орёл',2,5146938872,79709301045,51) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Ульяна','Дрокова','Ефимовна',"1994-12-20",'ulyana8209@gmail.com',11,'Human Communications Analyst','Советская ул.','г. Ярославль',2,1714469871,79583641242,27) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Нина','Губанова','Захаровна',"1996-11-01",'nina.gubanova@ya.ru',11,'Human Brand Developer','Вокзальная ул.','г. Хасавюрт',2,7415563599,79751457349,25) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Марина','Лебединская','Игнатьевна',"1969-02-27",'marina1969@yandex.ru',11,'Human Web Producer','Молодежный пер.','г. Уфа',2,4568445677,79564539081,53) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Никита','Блантер','Игнатьевич',"1982-01-11",'nikita1982@hotmail.com',11,'Product Configuration Agent','Восточная ул.','г. Пятигорск',1,8185162259,79837986767,40) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Михаил','Кидирбаев','Васильевич',"1967-08-18",'mihail1967@yandex.ru',6,'Legacy Quality Developer','Советский пер.','г. Батайск',1,7423883858,79928584537,54) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Игнатий','Грибалев','Игнатьевич',"1994-03-06",'ignatiy1994@rambler.ru',6,'Customer Implementation Producer','Сельская ул.','г. Артем',1,2677244982,79222625934,28) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Максим','Бехтерев','Витальевич',"1990-07-23",'maksim31@hotmail.com',6,'Dynamic Web Developer','Заслонова ул.','г. Сургут',1,7733068936,79721205361,31) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Василий','Шабанов','Ипполитович',"1993-02-16",'vasiliy5369@ya.ru',6,'Principal Tactics Associate','Дзержинского ул.','г. Октябрьский',1,6025401243,79464774458,29) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Кирилл','Яфаев','Кириллович',"1965-05-10",'kirill10051965@yandex.ru',6,'National Solutions Consultant','Лесная ул.','г. Энгельс',1,1126515832,79172306833,56) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Александра','Яковленко','Герасимовна',"1980-08-07",'aleksandra.yakovlenko@outlook.com',6,'Senior Usability Producer','Песчаная ул.','г. Рыбинск',2,6563456193,79956848030,41) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Ефим','Шеломов','Кириллович',"1992-06-16",'efim.elomov@mail.ru',3,'International Security Manager','Западная ул.','г. Каменск - Уральский',1,2852076378,79753038724,29) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Юрий','Трухин','Егорович',"1962-09-23",'yuriy1291@mail.ru',3,'Relational Marketing Strategist','Спортивная ул.','г. Волгоград',1,9401084241,79644893333,59) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Алиса','Каипова','Максимовна',"1964-04-04",'alisa.kaipova@mail.ru',9,'Dynamic Impact Administrator','Молодежный пер.','г. Белгород',2,436146568,79457768944,58) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Алексей','Головнин','Герасимович',"1980-04-24",'aleksey24@yandex.ru',9,'Legacy Quality Representative','Калинина ул.','г. Нижний Новгород',1,1139776526,79797329160,41) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Серафима','Китаева','Прохоровна',"1978-10-09",'serafima53@hotmail.com',9,'Dynamic Factors Planner','Ленинская ул.','г. Прокопьевск',2,2710135325,79173273842,43) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Трофим','Плюхин','Феоктистович',"1983-04-02",'trofim74@hotmail.com',9,'Direct Assurance VP','Полевая ул.','г. Пенза',1,5299845787,79684835799,39) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Полина','Полотенцева','Наумовна',"1985-11-06",'polina.polotenceva@mail.ru',9,'Chief Mobility Assistant','Полесская ул.','г. Шахты',2,2750312025,79696078021,36) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Александра','Чеснокова','Ипполитовна',"1992-02-27",'aleksandra70@hotmail.com',9,'Principal Operations Coordinator','Социалистическая ул.','г. Новосибирск',2,3597129614,79358529312,30) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Афанасий','Максимушкин','Порфирьевич',"1968-07-08",'afanasiy7860@gmail.com',9,'Internal Interactions Specialist','Лесная ул.','г. Севастополь',1,485053836,79166947928,53) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Елена','Лапаева','Леонтьевна',"1962-04-22",'elena36@hotmail.com',9,'Future Integration Planner','Совхозная ул.','г. Мурманск',2,9691993467,79093572971,60) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Мила','Ясаманова','Никифоровна',"1987-09-03",'mila1987@rambler.ru',9,'Interactive Markets Designer','Дорожная ул.','г. Реутов',2,6419480870,79622154989,34) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Филипп','Лебедков','Давидович',"1995-09-12",'filipp8844@rambler.ru',9,'Customer Accountability Engineer','Сельская ул.','г. Екатеринбург',1,5530924674,79528857030,26) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Зинаида','Клим','Игнатьевна',"1963-12-11",'zinaida11121963@mail.ru',9,'Direct Data Strategist','Пушкина ул.','г. Раменское',2,6525962668,79367056428,58) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Павел','Фролов','Филиппович',"1986-04-22",'pavel1986@ya.ru',9,'Legacy Mobility Associate','Полесская ул.','г. Красноярск',1,7756743779,79738626541,35) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Федот','Борисюк','Иванович',"1980-07-26",'fedot6289@ya.ru',12,'Internal Team Supervisor','Садовая ул.','г. Назрань',1,1934401837,79332427314,41) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Марьяна','Степашина','Максимовна',"1992-02-03",'maryana51@ya.ru',12,'Lead Response Synergist','17 Сентября ул.','г. Ростов-на-Дону',2,5231408316,79989272957,30) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Альбина','Поливанова','Константиновна',"1976-09-27",'albina.polivanova@outlook.com',12,'Dynamic Intranet Producer','Дружбы ул.','г. Каспийск',2,7271659591,79496975498,45) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Людмила','Гаголина','Прокловна',"1986-02-26",'lyudmila16@yandex.ru',12,'Regional Tactics Executive','Железнодорожная ул.','г. Волжский',2,3593786422,79742842363,36) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Емельян','Богачёв','Викторович',"1987-11-07",'emelyan20@ya.ru',12,'Lead Infrastructure Producer','Майская ул.','г. Ставрополь',1,5425257964,79402965033,34) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Тимофей','Мышелов','Федорович',"1972-12-20",'timofey1972@gmail.com',12,'Chief Tactics Developer','Дачная ул.','г. Люберцы',1,3679638881,79909033018,49) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Адам','Ивкин','Севастьянович',"1978-07-04",'adam93@hotmail.com',15,'Regional Response Liason','Мирная ул.','г. Тула',1,7515168443,79429179825,43) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Ксения','Верещагина','Филипповна',"1966-06-10",'kseniya10061966@outlook.com',15,'Human Group Director','Вишневая ул.','г. Арзамас',2,6902608112,79104291993,55) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Зинаида','Николюк','Дмитриевна',"1965-06-15",'zinaida15061965@yandex.ru',15,'International Solutions Director','Песчаная ул.','г. Уссурийск',2,9152930188,79808736821,56) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Давид','Долгов','Валерианович',"1977-02-05",'david05021977@gmail.com',15,'National Branding Representative','Песчаная ул.','г. Миасс',1,496231518,79402527398,45) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Раиса','Кондюрина','Себастьяновна',"1972-03-07",'raisa1972@ya.ru',16,'District Factors Liason','Западная ул.','г. Тольятти',2,1011933113,79371829519,50) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Клавдия','Батищева','Афанасьевна',"1990-08-22",'klavdiya3903@outlook.com',16,'Dynamic Security Executive','Сельская ул.','г. Обнинск',2,6630758629,79287301394,31) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Татьяна','Евстигнеева','Михаиловна',"1983-11-08",'tatyana1983@yandex.ru',16,'International Usability Director','Солнечный пер.','г. Комсомольск-на-Амуре',2,1624785537,79765658667,38) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Зоя','Леонтьева','Саввановна',"1976-08-10",'zoya1976@hotmail.com',16,'Relational Data Architect','Заслонова ул.','г. Владимир',2,5959370707,79868654595,45) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Елизавета','Янкова','Романовна',"1978-10-02",'elizaveta02101978@hotmail.com',16,'Customer Program Technician','Южная ул.','г. Балашиха',2,3818670682,79996551677,43) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Елена','Караулина','Герасимовна',"1996-11-15",'elena2599@ya.ru',16,'Dynamic Resonance Coordinator','Октябрьская ул.','г. Раменское',2,699243009,79867701347,25) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Егор','Капп','Васильевич',"1980-07-19",'egor.kapp@gmail.com',17,'Dynamic Web Architect','Дружная ул.','г. Воронеж',1,5833903646,79537645113,41) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Мария','Францева','Марковна',"1980-01-18",'mariya2315@ya.ru',17,'Forward Assurance VP','Новый пер.','г. Москва',2,6513672802,79274013675,42) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Инна','Яшина','Вениаминовна',"1980-04-02",'inna2953@gmail.com',17,'Lead Optimization Manager','Белорусская ул.','г. Оренбург',2,9273674570,79155473369,42) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Варвара','Дарбиняна','Петровна',"1964-11-21",'varvara.darbinyana@ya.ru',14,'Product Factors Facilitator','Трудовая ул.','г. Кисловодск',2,331605351,79671506398,57) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Яков','Зуйков','Игнатьевич',"1989-09-10",'yakov10091989@mail.ru',14,'Chief Accounts Associate','Советская ул.','г. Томск',1,7555735084,79146621837,32) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Федор','Панькив','Ипполитович',"1977-06-28",'fedor.pankiv@ya.ru',14,'Future Quality Associate','Октябрьская ул.','г. Белгород',1,5793240281,79828692484,44) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Роман','Набойщиков','Давидович',"1982-06-24",'roman24061982@ya.ru',14,'Regional Assurance Producer','Совхозная ул.','г. Калуга',1,1212857944,79489461420,39) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Ника','Рытова','Кирилловна',"1993-02-19",'nika7885@rambler.ru',14,'Internal Group Liason','Западная ул.','г. Уфа',2,9932431867,79073668269,29) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Константин','Кондюрин','Ефремович',"1976-08-15",'konstantin1976@outlook.com',14,'International Communications Officer','Сосновая ул.','г. Кемерово',1,6080119261,79311485472,45) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Александр','Янечко','Юринович',"1961-03-06",'aleksandr06031961@gmail.com',14,'Dynamic Creative Technician','Шоссейная ул.','г. Смоленск',1,7333037486,79786005678,61) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Кирилл','Брежнев','Даниилович',"1966-10-10",'kirill1966@rambler.ru',13,'Central Ideation Associate','Ленинская ул.','г. Орск',1,1985072748,79912932732,55) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Альбина','Терёшина','Лукьяновна',"1969-04-05",'albina9908@yandex.ru',13,'Legacy Interactions Developer','Полесская ул.','г. Нижний Новгород',2,2894820978,79543674435,53) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Тарас','Яндарбиев','Николаевич',"1977-04-01",'taras1977@outlook.com',13,'Internal Configuration Manager','Социалистическая ул.','г. Северск',1,1134872414,79771497126,45) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Марфа','Седельникова','Трофимовна',"1994-12-20",'marfa20121994@mail.ru',13,'Interactive Optimization Representative','Трудовая ул.','г. Новомосковск',2,937112094,79588113441,27) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Антонина','Державина','Денисовна',"1975-08-13",'antonina2892@gmail.com',13,'Internal Infrastructure Assistant','Калинина ул.','г. Санкт-Петербург',2,9972960791,79155103221,46) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Евгения','Снегирева','Сергеевна',"1985-01-11",'evgeniya48@rambler.ru',13,'Legacy Operations Designer','Чапаева ул.','г. Таганрог',2,2570812252,79385328536,37) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Михаил','Яхненко','Емельянович',"1967-01-26",'mihail26011967@hotmail.com',13,'Customer Research Developer','Якуба Коласа ул.','г. Петропавловск-Камчатский',1,9040240730,79144966867,55) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Артем','Ядыкин','Панкратович',"1973-04-03",'artem5697@ya.ru',5,'Corporate Tactics VP','Речная ул.','г. Волжский',1,1257237319,79275086922,49) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Ульяна','Дудкина','Саввановна',"1960-09-24",'ulyana24091960@mail.ru',5,'District Research Designer','Речная ул.','г. Самара',2,9970206435,79414568580,61) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Георгий','Бабанов','Лаврентиич',"1977-10-24",'georgiy24101977@mail.ru',5,'Human Intranet Representative','Первомайский пер.','г. Новокуйбышевск',1,7672656617,79632916827,44) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Виктория','Прокашева','Викторовна',"1974-08-01",'viktoriya5534@hotmail.com',5,'National Implementation Associate','Победы ул.','г. Саратов',2,7510252241,79497588742,47) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('София','Ишутина','Васильевна',"1963-07-04",'sofiya3067@mail.ru',5,'Global Identity Specialist','Полесская ул.','г. Калининград',2,2242895343,79706394713,58) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Максим','Мордвинов','Кириллович',"1980-03-11",'maksim11031980@mail.ru',5,'Future Mobility Administrator','Калинина ул.','г. Хасавюрт',1,1676238025,79255048494,42) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Ника','Толбанова','Себастьяновна',"1986-05-15",'nika85@rambler.ru',5,'Dynamic Ideation Developer','Радужная ул.','г. Балаково',2,4689903025,79285147234,35) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Ника','Пелевина','Никандровна',"1986-10-21",'nika.pelevina@ya.ru',5,'Regional Optimization Vice President','Солнечный пер.','г. Владивосток',2,7816450752,79572049660,35) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Мила','Ибрагимова','Тимофеевна',"1995-09-23",'mila.ibragimova@outlook.com',5,'Regional Creative VP','Ленинская ул.','г. Элиста',2,2966869423,79911481837,26) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Лаврентий','Щепетинников','Феоктистович',"1990-06-22",'lavrentiy65@gmail.com',5,'Legacy Ideation Strategist','Цветочная ул.','г. Липецк',1,290603221,79477179921,31) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Николай','Чечин','Иванович',"1965-11-09",'nikolay5441@rambler.ru',8,'District Group Technician','Вокзальная ул.','г. Саратов',1,4749824066,79414683243,56) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Давид','Латушкин','Аркадьевич',"1970-07-04",'david1970@rambler.ru',8,'Senior Program Planner','Молодежная ул.','г. Рыбинск',1,3280122522,79359254676,51) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Виктория','Стиплина','Нифонтовна',"1975-02-17",'viktoriya17021975@hotmail.com',8,'International Identity Analyst','Зеленая ул.','г. Кызыл',2,2342765869,79438905588,47) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Николай','Цур-Милен','Антонович',"1970-07-24",'nikolay7370@mail.ru',8,'International Infrastructure Coordinator','Луговой пер.','г. Омск',1,1843250953,79925706947,51) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Нина','Кокоткина','Васильевна',"1960-10-14",'nina14@yandex.ru',8,'Lead Resonance Designer','Строителей ул.','г. Казань',2,3436688961,79399167680,61) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Ксения','Яблонская','Лльвона',"1996-02-04",'kseniya43@mail.ru',8,'Lead Brand Liason','Речной пер.','г. Сергиев Посад',2,307993855,79741485352,26) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Арсений','Минкин','Александрович',"1961-12-12",'arseniy.minkin@hotmail.com',4,'Dynamic Program Developer','Вокзальная ул.','г. Октябрьский',1,895990314,79339464454,60) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Надежда','Карандашова','Васильевна',"1972-11-20",'nadejda20111972@yandex.ru',4,'Interactive Directives Associate','Ленина ул.','г. Улан-Удэ',2,4033929050,79446739726,49) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Николай','Бодров','Геннадьевич',"1964-10-04",'nikolay04101964@yandex.ru',4,'Lead Branding Architect','Советский пер.','г. Реутов',1,6735121691,79214067048,57) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Венедикт','Железкин','Кириллович',"1969-06-14",'venedikt1969@yandex.ru',4,'Product Ideation Engineer','Сельская ул.','г. Сергиев Посад',1,9648779143,79854088792,52) ;
INSERT INTO users (firstname, secondname, middlename, birthdate, email, company, occupation, street, city, gender, telephone, mobile, age) VALUES ('Лана','Смелоч','Николаевна',"1989-06-02",'lana02061989@hotmail.com',4,'International Resonance Executive','Комсомольская ул.','г. Альметьевск',2,8711726763,79844662840,32) ;
