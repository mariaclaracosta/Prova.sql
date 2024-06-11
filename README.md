<h1>Torneio de Super-Heróis </h1>
<h1>1- CENÁRIO</h1>
<p>Um torneio de super-heróis que será feito em duplas de uma escola que deverá ter:

Participantes, seu nome, nome de herói, poder, data de nascimento, turma, e um número identificador de estudante.

Partida, qual equipe participará, suas fases, seu identificador e classificações.

Juiz, seu nome, telefone e identificador.

Dupla, seu nome, seus participantes, e seu identidicador.

Patrocinador, nome, identificador, nome de herói, aluno patrocinado.</p>

<h1>2- MODELO CONCEITUAL</h1>

![image](https://github.com/mariaclaracosta/Prova.sql/assets/106972816/f6438058-53ce-46d0-9dd4-f76225057b5e)

![image](https://github.com/mariaclaracosta/Prova.sql/assets/106972816/e9d98995-7714-43fb-bfb6-bf303d3c6bec)



<h1>3- MODELO LÓGICO</h1>

![image](https://github.com/mariaclaracosta/Prova.sql/assets/106972816/7a994657-63b0-49e1-9c27-48280e477d08)

![image](https://github.com/mariaclaracosta/Prova.sql/assets/106972816/1f0e24cd-d00c-4233-8f5f-5f2dc73ba122)



<p>Nota:Para as cardinalidades que possuem (n,n), são criadas novas tabelas pra conter e agrupar informações das suas respectivas entidades, atributos compostos são "dissolvidos" e multivalorados se transformam em tabelas.</p>


<h1>4- TABELAS</h1>

<h2>Criando Database</h2>

```sql
CREATE DATABASE ProvaBD;
USE ProvaBD;
```

<h2>Criando as tabelas</h2>


```sql
CREATE TABLE Patrocinador (
Id_patrocinador	INT PRIMARY KEY IDENTITY,
Nome VARCHAR(60),
Nome_de_heroi VARCHAR(60),
Aluno VARCHAR(60)
);
```

```sql
CREATE TABLE Participante (
Id_participantes INT PRIMARY KEY IDENTITY,
Nome VARCHAR(60),
Nome_de_heroi VARCHAR(60),
Data_nasc DATE,
Poder VARCHAR(40),
Turma VARCHAR(5)
);
```
```sql
CREATE TABLE Duplas (
Id_dupla INT PRIMARY KEY IDENTITY,
Nome VARCHAR(30),
);
```


```sql
CREATE TABLE Partidas (
Id_partida INT PRIMARY KEY IDENTITY,
Dupla VARCHAR(30),
Classificacao	VARCHAR(20),
Fase1 VARCHAR(60),
Fase2 VARCHAR(60),
Fase3 VARCHAR(60),
Fase4 VARCHAR(60),
);
```

```sql
CREATE TABLE Juiz (
Id_juiz INT	PRIMARY KEY IDENTITY,
Nome	VARCHAR(60),
);
```
<h3>"Tabelas-ponte"</h3>

```sql
CREATE TABLE Telefone(
Id_telefone		INT		PRIMARY KEY		IDENTITY,
Telefone		VARCHAR(15),
Id_juiz			INT,
FOREIGN KEY	(Id_juiz) REFERENCES Juiz(Id_juiz)
);
```
```sql
CREATE TABLE Participantes(
Id_participantes	INT		PRIMARY KEY		IDENTITY,
Id_participante			INT,
Id_dupla				INT,
FOREIGN KEY	(Id_dupla) REFERENCES Duplas(Id_dupla),
FOREIGN KEY	(Id_participante) REFERENCES Participante(Id_participantes)
);
```

<h1>5- INSERÇÃO DE DADOS</h1>

```sql

INSERT INTO Participante (Nome, Data_nasc, Nome_de_heroi, Poder, Turma)
VALUES
('Izuku Midoriya', '2006-04-20', 'Deku', 'One For All', '1-A'),
('Katsuki Bakugo', '2006-04-20', 'Kacchan', 'Explosão', '1-A'),
('Ochaco Uraraka', '2006-12-27', 'Uravity', 'Zero Gravity', '1-A'),
('Shoto Todoroki', '2006-01-11', 'Shoto', 'Half-Cold Half-Hot', '1-A'),
('Tenya Iida', '2006-08-22', 'Iida', 'Engine', '1-A'),
('Eijiro Kirishima', '2006-10-16', 'Red Riot', 'Hardening', '1-A'),
('Tsuyu Asui', '2006-02-12', 'Froppy', 'Frog', '1-A'),
('Momo Yaoyorozu', '2006-09-23', 'Creati', 'Creation', '1-A'),
('Denki Kaminari', '2006-06-29', 'Chargebolt', 'Electrification', '1-A'),
('Kyoka Jiro', '2006-08-01', 'Earphone Jack', 'Earphone Jack', '1-A'),
('Fumikage Tokoyami', '2006-10-30', 'Tsukuyomi', 'Dark Shadow', '1-A'),
('Minoru Mineta', '2006-10-08', 'Grape Juice', 'Pop Off', '1-A'),
('Mashirao Ojiro', '2006-05-28', 'Tailman', 'Tail', '1-A'),
('Toru Hagakure', '2006-06-16', 'Invisible Girl', 'Transparency', '1-A'),
('Yuga Aoyama', '2006-05-30', 'Can''t Stop Twinkling', 'Navel Laser', '1-A'),
('Mezo Shoji', '2006-02-05', 'Tentacole', 'Dupli-Arms', '1-A'),
('Hanta Sero', '2006-07-28', 'Cellophane', 'Tape', '1-A'),
('Rikido Sato', '2006-10-30', 'Sugarman', 'Sugar Rush', '1-A'),
('Koji Koda', '2006-12-01', 'Anima', 'Anivoice', '1-A'),
('Tooru Hagakure', '2006-06-16', 'Invisible Girl', 'Transparency', '1-A'),
('Itsuka Kendo', '2006-08-08', 'Battle Fist', 'Big Fist', '1-B'),
('Tetsutetsu Tetsutetsu', '2006-09-09', 'Real Steel', 'Steel', '1-B'),
('Neito Monoma', '2006-06-06', 'Phantom Thief', 'Copy', '1-B'),
('Yosetsu Awase', '2006-02-02', 'Welder', 'Welding', '1-B'),
('Sen Kaibara', '2006-01-01', 'Slicing Wind', 'Slicing', '1-B'),
('Juzo Honenuki', '2006-07-07', 'Mud Man', 'Mud Manipulation', '1-B'),
('Pony Tsunotori', '2006-03-03', 'Horn Cannon', 'Horn Cannon', '1-B'),
('Reiko Yanagi', '2006-11-11', 'Poltergeist', 'Telekinesis', '1-B'),
('Kinoko Komori', '2006-04-04', 'Shemage', 'Mushroom', '1-B'),
('Togaru Kamakiri', '2006-05-05', 'Jack Mantis', 'Mantis Arms', '1-B'),
('Setsuna Tokage', '2006-10-10', 'Lizardy', 'Lizard Tail Splitter', '1-B'),
('Manga Fukidashi', '2006-12-12', 'Comicman', 'Comic Creation', '1-B'),
('Nirengeki Shoda', '2006-09-19', 'Twin Impact', 'Double Impact', '1-B'),
('Yui Kodai', '2006-01-23', 'Rulebook', 'Size Manipulation', '1-B'),
('Kosei Tsuburaba', '2006-02-15', 'Solid Air', 'Solid Air', '1-B'),
('Jurota Shishida', '2006-06-26', 'Gevaudan', 'Beast Transformation', '1-B'),
('Pony Tsunotori', '2006-03-03', 'Horn Cannon', 'Horn Cannon', '1-B'),
('Ibara Shiozaki', '2006-05-05', 'Vine', 'Vine', '1-B'),
('Nirengeki Shoda', '2006-09-19', 'Twin Impact', 'Double Impact', '1-B'),
('Tetsutetsu Tetsutetsu', '2006-09-09', 'Real Steel', 'Steel', '1-B');



INSERT INTO Participantes (Id_participante, Id_dupla)
VALUES
(1, 1),
(2, 1),
(3, 2),
(4, 2),
(5, 3),
(6, 3),
(7, 4),
(8, 4),
(9, 5),
(10,5),
(11,6),
(12,6),
(13,7),
(14,7),
(15,8),
(16,8),
(17,9),
(18,9),
(19,10),
(20,10);



INSERT INTO Duplas (Nome)
	VALUES 
('Fire-Ice'),
('ThunderLightning'),
('Shadow-Light'),
('Blaze-Frost'),
('Phoenix-Dragon'),
('Moon-Sun'),
('Night-Day'),
('Star-Comet'),
('Ocean-Sky'),
('Earth-Wind'),
('Sapphire-Ruby'),
('Emerald-Topaz'),
('Silver-Gold'),
('Titan-Atlas'),
('Luna-Sol'),
('Aurora-Borealis'),
('Cosmos-Galaxy'),
('Arrow-Bow'),
('Shield-Sword'),
('Harmony-Discord');
 
INSERT INTO Juiz (Nome)
VALUES
('All Might'),
('Endeavor'),
('Gran Torino'),
('Eraserhead'),
('Present Mic'),
('Midnight'),
('Recovery Girl'),
('Cementoss'),
('Mt. Lady'),
('Kamui Woods'),
('Best Jeanist'),
('Hawks'),
('Fat Gum'),
('Mirko'),
('Burnin'),
('Manual'),
('Nighteye'),
('Bubble Girl'),
('Centipeder'),
('Gang Orca');
 
INSERT INTO Telefone (Telefone, Id_juiz)
VALUES
('555-1234',1),
('555-5678',2),
('555-9876',3),
('555-4321',4),
('555-8765',5),
('555-2109',6),
('555-6789',7),
('555-5432',8),
('555-8901',9),
('555-3456',10),
('555-6780',11),
('555-1230',12),
('555-5670',13),
('555-9012',14),
('555-2345',15),
('555-6781',16),
('555-3451',17),
('555-8902',18),
('555-2101',19),
('555-5679',20);
 
INSERT INTO Partidas (Dupla, Fase1, Classificacao)
VALUES
('Fire-Ice','Fire-Ice','Vitória'),
('ThunderLightning','ThunderLightning','Vitória'),
('Shadow-Light','Shadow-Light','Vitória'),
('Blaze-Frost','Blaze-Frost','Vitória'),
('Phoenix-Dragon','Phoenix-Dragon','Vitória'),
('Moon-Sun','Moon-Sun','Vitória'),
('Night-Day','Night-Day','Vitória'),
('Star-Comet','Star-Comet','Vitória'),
('Ocean-Sky','Ocean-Sky','Vitória'),
('Earth-Wind','Earth-Wind','Vitória'),
('Sapphire-Ruby','Sapphire-Ruby','Derrota'),
('Emerald-Topaz','Emerald-Topaz','Derrota'),
('Silver-Gold','Silver-Gold','Derrota'),
('Titan-Atlas','Titan-Atlas','Derrota'),
('Luna-Sol','Luna-Sol','Derrota'),
('Aurora-Borealis','Aurora-Borealis','Derrota'),
('Cosmos-Galaxy','Cosmos-Galaxy','Derrota'),
('Arrow-Bow','Arrow-Bow','Derrota'),
('Shield-Sword','Shield-Sword','Derrota'),
('Harmony-Discord','Harmony-Discord','Derrota');
 
INSERT INTO Partidas (Fase2, Classificacao)
VALUES
('Fire-Ice','Vitória'),
('ThunderLightning','Vitória'),
('Shadow-Light','Vitória'),
('Blaze-Frost','Vitória'),
('Phoenix-Dragon','Vitória'),
('Moon-Sun','Derrota'),
('Night-Day','Derrota'),
('Star-Comet','Derrota'),
('Ocean-Sky','Derrota'),
('Earth-Wind','Derrota');
 
INSERT INTO Partidas (Fase3, Classificacao)
VALUES
('Fire-Ice','Vitória'),
('ThunderLightning','Vitória'),
('Shadow-Light','Derrota'),
('Blaze-Frost','Derrota'),
('Phoenix-Dragon','Derrota');
 
INSERT INTO Partidas (Fase4, Classificacao)
VALUES
('Fire-Ice','Vitória'),
('ThunderLightning','Derrota');
```
<h1>6- CRUD (Create, Read, Update, Delete)</h1>

<h4>Criar</h4>

```sql
INSERT INTO Participante (Nome, Data_nasc, Nome_de_heroi, Poder, Turma)
VALUES
('Izuku Midoriya', '2006-04-20', 'Deku', 'One For All', '1-A'),
```

![image](https://github.com/mariaclaracosta/Prova.sql/assets/106972816/5d1e4aeb-e0cf-4468-adbd-83bf31f1e6e5)

<h4>Ler</h4>

```sql
INSERT INTO Participante (Nome, Data_nasc, Nome_de_heroi, Poder, Turma)
VALUES
('Izuku Midoriya', '2006-04-20', 'Deku', 'One For All', '1-A'),
```

![image](https://github.com/mariaclaracosta/Prova.sql/assets/106972816/7a99f839-3b2e-408e-872c-15fec21ad736)


<h4>Atualizar</h4>

```sql
UPDATE Participante
SET Poder = 'Sapo'
WHERE Nome = 'Tsuyu Asui'
```
<h5>Antes</h5>

![image](https://github.com/mariaclaracosta/Prova.sql/assets/106972816/cf250071-7ed1-42b3-866c-bbd15b411e56)

<h5>Depois</h5>

![image](https://github.com/mariaclaracosta/Prova.sql/assets/106972816/7b68f2a6-edba-4cd5-9d5d-7e94ca60298c)


<h4>Deletar</h4>

```sql
DELETE FROM Participante
WHERE Nome = 'Minoru Mineta'
```

<h5>Antes</h5>

![image](https://github.com/mariaclaracosta/Prova.sql/assets/106972816/d55bf924-aaf1-428a-a9f1-909dc08c49c7)

<h5>Depois</h5>

![image](https://github.com/mariaclaracosta/Prova.sql/assets/106972816/27194556-a0bf-4963-8cc0-c04c56f4fdf7)

<h1>7- Relatórios</h1>

```sql
SELECT * FROM Participante WHERE Turma = '1-A';
```
![image](https://github.com/mariaclaracosta/Prova.sql/assets/106972816/fd7ff102-1f1f-4278-8b07-c801acad03b3)
