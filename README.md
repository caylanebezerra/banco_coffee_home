# Banco de Dados Coffee Home


Pequeno desenho ilustrando a relação das tabelas dos produtos da Cafeteria Home:
    <a data-flickr-embed="true" href="https://www.flickr.com/photos/198233475@N03/52866371656/in/dateposted-public/" title="Captura da Web_3-5-2023_03352_github.com"><img src="https://live.staticflickr.com/65535/52866371656_f1a1068dee_z.jpg" width="640" height="487" alt="Captura da Web_3-5-2023_03352_github.com"/></a><script async src="//embedr.flickr.com/assets/client-code.js" charset="utf-8"></script>

# Para criar as tabelas, utilizei os seguintes comandos:
-- Criando a tabela "produto"
CREATE TABLE produto (
  id_produto SERIAL PRIMARY KEY,
  nome_produto VARCHAR(100) NOT NULL,
  descricao TEXT,
  preco NUMERIC(10,2)
);

-- Criando a tabela "comidas" com chave estrangeira para a tabela "produto"
CREATE TABLE comidas (
  id_produto INT PRIMARY KEY REFERENCES produto(id_produto),
  tipo VARCHAR(10) NOT NULL
);

-- Criando a tabela "salgados" com chave estrangeira para a tabela "comidas"
CREATE TABLE salgados (
  id_salgado SERIAL PRIMARY KEY,
  nome_salgado VARCHAR(100) NOT NULL,
  id_comida INT NOT NULL REFERENCES comidas(id_produto),
  descricao_salgado TEXT,
  preco_salgado NUMERIC(10,2)
);

-- Criando a tabela "doces" com chave estrangeira para a tabela "comidas"
CREATE TABLE doces (
  id_doce SERIAL PRIMARY KEY,
  nome_doce VARCHAR(100) NOT NULL,
  id_comida INT NOT NULL REFERENCES comidas(id_produto),
  descricao_doce TEXT,
  preco_doce NUMERIC(10,2)
);

#Inserindo Valores nas tabelas:
INSERT INTO produto (id_produto,nome_produto,preco) VALUES
(1, 'Bolo', '20'),
(2, 'Esfirra', '8'),
(3, 'Croissant', '8');

INSERT INTO comidas (id_produto, tipo) VALUES (1, 'doce');
INSERT INTO comidas (id_produto, tipo) VALUES (2, 'salgado');
INSERT INTO comidas (id_produto, tipo) VALUES (3, 'salgado');

INSERT INTO doces(id_doce,nome_doce,id_comida) VALUES (1,'Bolo de Banana',1); --mesmo id_comida pois ambos sao bolos
INSERT INTO doces(id_doce,nome_doce,id_comida) VALUES (2,'Bolo de Cenoura',1);

INSERT INTO salgados(id_salgado,nome_salgado,id_comida) VALUES (1,'Esfirra de Queijo',2);
INSERT INTO salgados(id_salgado,nome_salgado,id_comida) VALUES (2,'Esfirra de Frango',2);

INSERT INTO salgados(id_salgado,nome_salgado,id_comida) VALUES (3,'Croissant de Carne do Sol',3);
INSERT INTO salgados(id_salgado,nome_salgado,id_comida) VALUES (4,'Croissant de Queijo',3);

# Explicando as inserções de valores:
- O produto é o mais geral
- A tabela comidas é relacionada com a tabela produto, a principal, através da chave estrangeira id_produto, ja a variável "tipo" que existe na tabela comidas poderá aceitar valores como doce ou salgado, e assim se relacionará com as tabelas filhas doces e salgados.
- As tabelas doces e salgados receem a variavel "id_comida" que se relacionará com a tabela comidas.

# Resultado da criação e dos inserts:
<a data-flickr-embed="true" href="https://www.flickr.com/photos/198233475@N03/52866760285/in/dateposted-public/" title="Captura de tela 2023-05-03 004436"><img src="https://live.staticflickr.com/65535/52866760285_9765ce0cbd_z.jpg" width="640" height="247" alt="Captura de tela 2023-05-03 004436"/></a><script async src="//embedr.flickr.com/assets/client-code.js" charset="utf-8"></script>

<a data-flickr-embed="true" href="https://www.flickr.com/photos/198233475@N03/52866760355/in/dateposted-public/" title="Captura de tela 2023-05-03 004535"><img src="https://live.staticflickr.com/65535/52866760355_861eff4aab_w.jpg" width="400" height="258" alt="Captura de tela 2023-05-03 004535"/></a><script async src="//embedr.flickr.com/assets/client-code.js" charset="utf-8"></script>

<a data-flickr-embed="true" href="https://www.flickr.com/photos/198233475@N03/52866371516/in/dateposted-public/" title="Captura de tela 2023-05-03 004623"><img src="https://live.staticflickr.com/65535/52866371516_92aedccc1c_w.jpg" width="400" height="118" alt="Captura de tela 2023-05-03 004623"/></a><script async src="//embedr.flickr.com/assets/client-code.js" charset="utf-8"></script>

<a data-flickr-embed="true" href="https://www.flickr.com/photos/198233475@N03/52866371466/in/dateposted-public/" title="Captura de tela 2023-05-03 004603"><img src="https://live.staticflickr.com/65535/52866371466_b5d9a34fa6_w.jpg" width="400" height="116" alt="Captura de tela 2023-05-03 004603"/></a><script async src="//embedr.flickr.com/assets/client-code.js" charset="utf-8"></script>



