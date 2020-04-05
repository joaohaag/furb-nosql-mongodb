Atividade Prática – MongoDB 

Exercício 1- Aquecendo com os pets 

1.Adicione outro Peixe e um Hamster com nome Frodo

Comando
> db.pets.insert({name:"Frodo",species:"Peixe"})

Resposta
WriteResult({ "nInserted" : 1 })

Comando
> db.pets.insert({name:"Frodo",species:"Hamster"})

Resposta
WriteResult({ "nInserted" : 1 })


2. Faça uma contagem dos pets na coleção 

Comando
db.pets.find().count();

Resposta
8

3. Retorne apenas um elemento o método prático possível 

Comando
> db.pets.findOne()

Resposta

{
        "_id" : ObjectId("5e8a1b135f61e90828391922"),
        "name" : "Mike",
        "species" : "Hamster"
}

4. Identifique o ID para o Gato Kilha. 

Comando
> db.pets.find({"name" : "Kilha"}, {"_id":1});

Resposta

{ "_id" : ObjectId("5e8a1b235f61e90828391924") }

5. Faça uma busca pelo ID e traga o Hamster Mike 

Comando
> db.pets.find({"name" : "Mike", species:"Hamster"}, {"_id":1});

Resposta

{ "_id" : ObjectId("5e8a1b135f61e90828391922") }

Comando
> db.pets.find({"_id" : ObjectId("5e8a1b135f61e90828391922")});

Resposta

{ "_id" : ObjectId("5e8a1b135f61e90828391922"), "name" : "Mike", "species" : "Hamster" }


6. Use o find para trazer todos os Hamster

Comando
> db.pets.find({species:"Hamster"});

Resposta

{ "_id" : ObjectId("5e8a1b135f61e90828391922"), "name" : "Mike", "species" : "Hamster" }
{ "_id" : ObjectId("5e8a1b7d5f61e90828391929"), "name" : "Frodo", "species" : "Hamster" }

7. Use o find para listar todos os pets com nome Mike

Comando
> db.pets.find({"name" : "Mike"});

Resposta

{ "_id" : ObjectId("5e8a1b135f61e90828391922"), "name" : "Mike", "species" : "Hamster" }
{ "_id" : ObjectId("5e8a1b2d5f61e90828391925"), "name" : "Mike", "species" : "Cachorro" }

8. Liste apenas o documento que é um Cachorro chamado Mike 

Comando
> db.pets.find({"name" : "Mike", species:"Cachorro"});

Resposta

{ "_id" : ObjectId("5e8a1b2d5f61e90828391925"), "name" : "Mike", "species" : "Cachorro" }


Exercício 2 – Mama mia! 

1. Liste/Conte todas as pessoas que tem exatamente 99 anos. Você pode usar um count para indicar a quantidade. 
Comando
> db.italians.find({"age" : 99}).count()

Resposta
0

2. Identifique quantas pessoas são elegíveis atendimento prioritário (pessoas com mais de 65 anos) 
Comando
> db.italians.find({"age" : {"$gt":65}}).count()

Resposta
1685

3. Identifique todos os jovens (pessoas entre 12 a 18 anos). 
Comando
> db.italians.find({"age" : {"$gte" : 12, "$lte" : 18}})

Resposta
{ "_id" : ObjectId("5e8a31712c71b99c0f203e51"), "firstname" : "Giusy", "surname" : "Moretti", "username" : "user129", "age" : 17, "email" : "Giusy.Moretti@gmail.com", "bloodType" : "AB+", "id_num" : "117846875072", "registerDate" : ISODate("2007-03-21T10:31:37.348Z"), "ticketNumber" : 4160, "jobs" : [ "Música", "Oceanografia" ], "favFruits" : [ "Pêssego" ], "movies" : [ { "title" : "A Felicidade Não se Compra (1946)", "rating" : 2.43 } ], "cat" : { "name" : "Laura", "age" : 16 } }
{ "_id" : ObjectId("5e8a31712c71b99c0f203e53"), "firstname" : "Veronica", "surname" : "Barone", "username" : "user131", "age" : 12, "email" : "Veronica.Barone@uol.com.br", "bloodType" : "A+", "id_num" : "768470232510", "registerDate" : ISODate("2012-11-10T00:00:58.587Z"), "ticketNumber" : 657, "jobs" : [ "Química", "Rádio, TV e Internet" ], "favFruits" : [ "Banana", "Goiaba" ], "movies" : [ { "title" : "A Vida é Bela (1997)", "rating" : 2.02 }, { "title" : "Forrest Gump: O Contador de Histórias (1994)", "rating" : 2.37 }, { "title" : "À Espera de um Milagre (1999)", "rating" : 0.93 } ], "cat" : { "name" : "Claudia", "age" : 6 } }
{ "_id" : ObjectId("5e8a31712c71b99c0f203e56"), "firstname" : "Elisabetta", "surname" : "Palumbo", "username" : "user134", "age" : 17, "email" : "Elisabetta.Palumbo@gmail.com", "bloodType" : "B-", "id_num" : "561202382714", "registerDate" : ISODate("2007-05-26T21:12:45.947Z"), "ticketNumber" : 2260, "jobs" : [ "Engenharia Florestal" ], "favFruits" : [ "Pêssego", "Melancia", "Mamão" ], "movies" : [ { "title" : "Seven: Os Sete Crimes Capitais (1995)", "rating" : 1.06 } ] }
{ "_id" : ObjectId("5e8a31712c71b99c0f203e5f"), "firstname" : "Valentina", "surname" : "D’Amico", "username" : "user143", "age" : 17, "email" : "Valentina.D’Amico@hotmail.com", "bloodType" : "O-", "id_num" : "406056052041", "registerDate" : ISODate("2008-10-27T08:41:34.745Z"), "ticketNumber" : 5282, "jobs" : [ "Conservação e Restauro", "Animação" ], "favFruits" : [ "Goiaba", "Tangerina" ], "movies" : [ { "title" : "O Poderoso Chefão II (1974)", "rating" : 4.01 }, { "title" : "Os Sete Samurais (1954)", "rating" : 4.42 }, { "title" : "Cidade de Deus (2002)", "rating" : 4.18 }, { "title" : "O Silêncio dos Inocentes (1991)", "rating" : 0.73 }, { "title" : "1917 (2019)", "rating" : 3.54 } ], "father" : { "firstname" : "Emanuela", "surname" : "D’Amico", "age" : 53 } }
{ "_id" : ObjectId("5e8a31712c71b99c0f203e64"), "firstname" : "Mattia", "surname" : "Moretti", "username" : "user148", "age" : 12, "email" : "Mattia.Moretti@yahoo.com", "bloodType" : "O+", "id_num" : "167617274765", "registerDate" : ISODate("2016-08-18T04:17:58.108Z"), "ticketNumber" : 2432, "jobs" : [ "Alimentos" ], "favFruits" : [ "Melancia" ], "movies" : [ { "title" : "Matrix (1999)", "rating" : 3.04 }, { "title" : "O Poderoso Chefão (1972)", "rating" : 2.85 }, { "title" : "O Poderoso Chefão (1972)", "rating" : 2.34 }, { "title" : "O Poderoso Chefão (1972)", "rating" : 1.29 } ], "cat" : { "name" : "Federico", "age" : 11 } }
{ "_id" : ObjectId("5e8a31712c71b99c0f203e6c"), "firstname" : "Silvia", "surname" : "Bernardi", "username" : "user156", "age" : 13, "email" : "Silvia.Bernardi@yahoo.com", "bloodType" : "A+", "id_num" : "060332202012", "registerDate" : ISODate("2019-01-21T14:03:39.551Z"), "ticketNumber" : 8645, "jobs" : [ "Comunicação das Artes do Corpo", "Psicologia" ], "favFruits" : [ "Pêssego", "Pêssego", "Banana" ], "movies" : [ { "title" : "Forrest Gump: O Contador de Histórias (1994)", "rating" : 1.73 }, { "title" : "Matrix (1999)", "rating" : 2.3 }, { "title" : "O Poderoso Chefão (1972)", "rating" : 2.48 } ], "cat" : { "name" : "Pasquale", "age" : 4 } }
{ "_id" : ObjectId("5e8a31712c71b99c0f203e71"), "firstname" : "Gabiele", "surname" : "Silvestri", "username" : "user161", "age" : 14, "email" : "Gabiele.Silvestri@yahoo.com", "bloodType" : "AB-", "id_num" : "177688448421", "registerDate" : ISODate("2013-10-27T03:37:24.887Z"), "ticketNumber" : 3252, "jobs" : [ "Processos Gerenciais", "Produção de Bebidas" ], "favFruits" : [ "Maçã" ], "movies" : [ { "title" : "À Espera de um Milagre (1999)", "rating" : 1.39 } ] }
{ "_id" : ObjectId("5e8a31712c71b99c0f203e79"), "firstname" : "Ilaria", "surname" : "Lombardi", "username" : "user169", "age" : 14, "email" : "Ilaria.Lombardi@outlook.com", "bloodType" : "AB+", "id_num" : "061177310255", "registerDate" : ISODate("2015-04-20T07:39:30.825Z"), "ticketNumber" : 840, "jobs" : [ "Ciências Naturais e Exatas" ], "favFruits" : [ "Goiaba", "Kiwi", "Kiwi" ], "movies" : [ { "title" : "Pulp Fiction: Tempo de Violência (1994)", "rating" : 2.61 }, { "title" : "12 Homens e uma Sentença (1957)", "rating" : 0.01 }, { "title" : "Batman: O Cavaleiro das Trevas (2008)", "rating" : 0.02 }, { "title" : "Parasita (2019)", "rating" : 2.08 }, { "title" : "O Resgate do Soldado Ryan (1998)", "rating" : 0.99 } ], "mother" : { "firstname" : "Mattia", "surname" : "Lombardi", "age" : 32 }, "dog" : { "name" : "Federico", "age" : 2 } }
{ "_id" : ObjectId("5e8a31712c71b99c0f203e7b"), "firstname" : "Vincenzo", "surname" : "Marino", "username" : "user171", "age" : 13, "email" : "Vincenzo.Marino@yahoo.com", "bloodType" : "AB-", "id_num" : "812503158768", "registerDate" : ISODate("2020-01-08T00:11:42.354Z"), "ticketNumber" : 3898, "jobs" : [ "Engenharia de Telecomunicações", "Nutrição" ], "favFruits" : [ "Kiwi" ], "movies" : [ { "title" : "A Origem (2010)", "rating" : 1.64 }, { "title" : "Parasita (2019)", "rating" : 4.37 } ], "cat" : { "name" : "Enzo ", "age" : 17 }, "dog" : { "name" : "Cinzia", "age" : 10 } }
{ "_id" : ObjectId("5e8a31712c71b99c0f203e8d"), "firstname" : "Alberto", "surname" : "De Rosa", "username" : "user189", "age" : 16, "email" : "Alberto.De Rosa@gmail.com", "bloodType" : "B-", "id_num" : "884324284581", "registerDate" : ISODate("2014-12-09T02:18:29.787Z"), "ticketNumber" : 5943, "jobs" : [ "Fabricação Mecânica", "Odontologia" ], "favFruits" : [ "Uva", "Laranja" ], "movies" : [ { "title" : "12 Homens e uma Sentença (1957)", "rating" : 0.19 }, { "title" : "Três Homens em Conflito (1966)", "rating" : 0.59 }, { "title" : "Forrest Gump: O Contador de Histórias (1994)", "rating" : 0.8 }, { "title" : "Cidade de Deus (2002)", "rating" : 0.53 }, { "title" : "Coringa (2019)", "rating" : 0.66 } ], "cat" : { "name" : "Paola", "age" : 8 }, "dog" : { "name" : "Davide", "age" : 1 } }
{ "_id" : ObjectId("5e8a31712c71b99c0f203ea1"), "firstname" : "Veronica", "surname" : "Villa", "username" : "user209", "age" : 12, "email" : "Veronica.Villa@outlook.com", "bloodType" : "O-", "id_num" : "704647070516", "registerDate" : ISODate("2014-01-12T10:46:16.399Z"), "ticketNumber" : 4387, "jobs" : [ "Engenharia de Minas", "Estética e Cosmética" ], "favFruits" : [ "Kiwi", "Kiwi", "Banana" ], "movies" : [ { "title" : "Pulp Fiction: Tempo de Violência (1994)", "rating" : 4.87 }, { "title" : "A Lista de Schindler (1993)", "rating" : 2.12 }, { "title" : "Vingadores: Ultimato (2019)", "rating" : 4.2 }, { "title" : "Guerra nas Estrelas (1977)", "rating" : 4.09 } ], "father" : { "firstname" : "Daniele", "surname" : "Villa", "age" : 35 } }
{ "_id" : ObjectId("5e8a31712c71b99c0f203ead"), "firstname" : "Dario", "surname" : "Longo", "username" : "user221", "age" : 13, "email" : "Dario.Longo@uol.com.br", "bloodType" : "B-", "id_num" : "501717314724", "registerDate" : ISODate("2009-11-28T01:27:36.306Z"), "ticketNumber" : 9653, "jobs" : [ "Arquitetura e Urbanismo" ], "favFruits" : [ "Melancia" ], "movies" : [ { "title" : "A Felicidade Não se Compra (1946)", "rating" : 1.26 } ], "father" : { "firstname" : "Silvia", "surname" : "Longo", "age" : 44 }, "cat" : { "name" : "Rosa", "age" : 10 }, "dog" : { "name" : "Michele", "age" : 1 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203ec8"), "firstname" : "Marta", "surname" : "Lombardo", "username" : "user248", "age" : 17, "email" : "Marta.Lombardo@uol.com.br", "bloodType" : "A-", "id_num" : "076643131565", "registerDate" : ISODate("2018-08-02T22:26:10.059Z"), "ticketNumber" : 6766, "jobs" : [ "Ciências Contábeis" ], "favFruits" : [ "Tangerina", "Banana" ], "movies" : [ { "title" : "O Senhor dos Anéis: A Sociedade do Anel (2001)", "rating" : 1.23 }, { "title" : "Interestelar (2014)", "rating" : 1.45 }, { "title" : "Cidade de Deus (2002)", "rating" : 0.83 } ], "cat" : { "name" : "Alessandra", "age" : 16 }, "dog" : { "name" : "Eleonora", "age" : 15 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203ed2"), "firstname" : "Emanuele", "surname" : "Battaglia", "username" : "user258", "age" : 14, "email" : "Emanuele.Battaglia@uol.com.br", "bloodType" : "O+", "id_num" : "330068714336", "registerDate" : ISODate("2007-10-02T12:26:10.864Z"), "ticketNumber" : 9406, "jobs" : [ "Animação" ], "favFruits" : [ "Kiwi", "Laranja", "Pêssego" ], "movies" : [ { "title" : "Forrest Gump: O Contador de Histórias (1994)", "rating" : 1.52 }, { "title" : "Vingadores: Ultimato (2019)", "rating" : 4.84 }, { "title" : "O Poderoso Chefão (1972)", "rating" : 2.66 }, { "title" : "A Origem (2010)", "rating" : 3.4 }, { "title" : "Gladiador (2000)", "rating" : 2.8 } ], "dog" : { "name" : "Marta", "age" : 13 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203ef5"), "firstname" : "Giorgia", "surname" : "Grassi", "username" : "user293", "age" : 17, "email" : "Giorgia.Grassi@yahoo.com", "bloodType" : "B+", "id_num" : "337002648082", "registerDate" : ISODate("2013-10-06T03:29:50.083Z"), "ticketNumber" : 1097, "jobs" : [ "Comunicação e Informação", "Gestão da Qualidade" ], "favFruits" : [ "Uva" ], "movies" : [ { "title" : "Forrest Gump: O Contador de Histórias (1994)", "rating" : 0.01 }, { "title" : "Cidade de Deus (2002)", "rating" : 3.19 }, { "title" : "A Origem (2010)", "rating" : 4.06 } ], "cat" : { "name" : "Cristian", "age" : 9 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f03"), "firstname" : "Veronica", "surname" : "De Angelis", "username" : "user307", "age" : 18, "email" : "Veronica.De Angelis@yahoo.com", "bloodType" : "B-", "id_num" : "710375500775", "registerDate" : ISODate("2019-07-27T00:19:03.435Z"), "ticketNumber" : 5582, "jobs" : [ "Gestão de Segurança Privada" ], "favFruits" : [ "Tangerina", "Uva" ], "movies" : [ { "title" : "Um Estranho no Ninho (1975)", "rating" : 4.98 }, { "title" : "A Lista de Schindler (1993)", "rating" : 1.26 }, { "title" : "12 Homens e uma Sentença (1957)", "rating" : 0.6 }, { "title" : "A Vida é Bela (1997)", "rating" : 2.17 }, { "title" : "12 Homens e uma Sentença (1957)", "rating" : 0.72 } ], "father" : { "firstname" : "Marta", "surname" : "De Angelis", "age" : 53 }, "cat" : { "name" : "Veronica", "age" : 6 }, "dog" : { "name" : "Carlo", "age" : 9 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f05"), "firstname" : "Ilaria", "surname" : "Battaglia", "username" : "user309", "age" : 15, "email" : "Ilaria.Battaglia@yahoo.com", "bloodType" : "O-", "id_num" : "888838608135", "registerDate" : ISODate("2014-10-06T11:38:44.490Z"), "ticketNumber" : 7131, "jobs" : [ "Educação Física" ], "favFruits" : [ "Pêssego", "Pêssego" ], "movies" : [ { "title" : "Três Homens em Conflito (1966)", "rating" : 2.38 } ], "cat" : { "name" : "Anna", "age" : 2 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f13"), "firstname" : "Giovanna", "surname" : "Ricci", "username" : "user323", "age" : 17, "email" : "Giovanna.Ricci@hotmail.com", "bloodType" : "B+", "id_num" : "576234013587", "registerDate" : ISODate("2012-05-07T22:03:26.444Z"), "ticketNumber" : 9267, "jobs" : [ "Produção Cênica", "Mecatrônica Industrial" ], "favFruits" : [ "Kiwi" ], "movies" : [ { "title" : "Clube da Luta (1999)", "rating" : 0.22 }, { "title" : "Clube da Luta (1999)", "rating" : 3.36 }, { "title" : "Clube da Luta (1999)", "rating" : 4.09 } ], "cat" : { "name" : "Sonia", "age" : 17 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f23"), "firstname" : "Marco", "surname" : "Galli", "username" : "user339", "age" : 16, "email" : "Marco.Galli@uol.com.br", "bloodType" : "A-", "id_num" : "631868652576", "registerDate" : ISODate("2010-01-20T03:41:56.764Z"), "ticketNumber" : 7321, "jobs" : [ "Administração Pública", "História" ], "favFruits" : [ "Mamão", "Uva", "Goiaba" ], "movies" : [ { "title" : "Os Sete Samurais (1954)", "rating" : 2.53 }, { "title" : "Matrix (1999)", "rating" : 4.24 }, { "title" : "O Senhor dos Anéis: O Retorno do Rei (2003)", "rating" : 4.41 } ], "father" : { "firstname" : "Paolo", "surname" : "Galli", "age" : 41 }, "cat" : { "name" : "Valeira", "age" : 14 }, "dog" : { "name" : "Anna", "age" : 10 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f27"), "firstname" : "Enzo ", "surname" : "Lombardo", "username" : "user343", "age" : 15, "email" : "Enzo .Lombardo@hotmail.com", "bloodType" : "AB+", "id_num" : "256448186835", "registerDate" : ISODate("2007-03-21T15:30:59.759Z"), "ticketNumber" : 6475, "jobs" : [ "Engenharia Física" ], "favFruits" : [ "Maçã" ], "movies" : [ { "title" : "O Senhor dos Anéis: A Sociedade do Anel (2001)", "rating" : 0.73 } ] }
Type "it" for more

4. Identifique quantas pessoas tem gatos, quantas tem cachorro e quantas não tem nenhum dos dois 

Gatos
> db.italians.find({cat: {$exists: true}}).count()
5976

Cachorros
> db.italians.find({dog: {$exists: true}}).count()
3949

Nem cachorro nem gato
> db.italians.find({$and:[{dog: {$exists: false}},{cat: {$exists: false}}]}).count()
2409

5. Liste/Conte todas as pessoas acima de 60 anos que tenham gato 
> db.italians.find({$and:[{cat: {$exists: true}},{"age" : {"$gt":65}}]}).count()
1018

6. Liste/Conte todos os jovens com cachorro 
> db.italians.find({$and:[{dog: {$exists: true}},{"age" : {"$gte" : 12, "$lte" : 18}}]}).count()
345

7. Utilizando o $where, liste todas as pessoas que tem gato e cachorro 


8. Liste todas as pessoas mais novas que seus respectivos gatos. 

> db.italians.find({ $and: [ { cat: { $exists: true }}, { $where: "this.age < this.cat.age" } ] },{"firstname":1,"age": 1, "cat.age":1})
{ "_id" : ObjectId("5e8a31712c71b99c0f203e3c"), "firstname" : "Andrea", "age" : 5, "cat" : { "age" : 7 } }
{ "_id" : ObjectId("5e8a31712c71b99c0f203e3f"), "firstname" : "Alessandra", "age" : 1, "cat" : { "age" : 7 } }
{ "_id" : ObjectId("5e8a31712c71b99c0f203e6d"), "firstname" : "Patrizia", "age" : 3, "cat" : { "age" : 10 } }
{ "_id" : ObjectId("5e8a31712c71b99c0f203e7b"), "firstname" : "Vincenzo", "age" : 13, "cat" : { "age" : 17 } }
{ "_id" : ObjectId("5e8a31712c71b99c0f203e88"), "firstname" : "Barbara", "age" : 8, "cat" : { "age" : 11 } }
{ "_id" : ObjectId("5e8a31712c71b99c0f203ea0"), "firstname" : "Daniela", "age" : 5, "cat" : { "age" : 12 } }
{ "_id" : ObjectId("5e8a31712c71b99c0f203ea7"), "firstname" : "Pasquale", "age" : 4, "cat" : { "age" : 12 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203eb6"), "firstname" : "Maria", "age" : 4, "cat" : { "age" : 9 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203eb7"), "firstname" : "Emanuele", "age" : 8, "cat" : { "age" : 15 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203ec6"), "firstname" : "Manuela", "age" : 1, "cat" : { "age" : 6 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203ef8"), "firstname" : "Cristina", "age" : 2, "cat" : { "age" : 6 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f02"), "firstname" : "Filipo", "age" : 8, "cat" : { "age" : 11 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f0a"), "firstname" : "Lorenzo", "age" : 2, "cat" : { "age" : 13 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f11"), "firstname" : "Simone", "age" : 2, "cat" : { "age" : 10 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f34"), "firstname" : "Nicola", "age" : 1, "cat" : { "age" : 3 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f3d"), "firstname" : "Luca", "age" : 3, "cat" : { "age" : 17 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f41"), "firstname" : "Michele", "age" : 1, "cat" : { "age" : 8 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f50"), "firstname" : "Alberto", "age" : 2, "cat" : { "age" : 5 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f56"), "firstname" : "Giuseppe", "age" : 0, "cat" : { "age" : 3 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f66"), "firstname" : "Paola", "age" : 8, "cat" : { "age" : 13 } }

9. Liste as pessoas que tem o mesmo nome que seu bichano (gatou ou cachorro) 


10. Projete apenas o nome e sobrenome das pessoas com tipo de sangue de fator RH negativo

> db.italians.find({"bloodType" : /-/}, {"firstname": 1, "surname": 1, "bloodType" : 1, "_id":0})

{ "firstname" : "Lucia", "surname" : "Caputo", "bloodType" : "A-" }
{ "firstname" : "Emanuele", "surname" : "Barone", "bloodType" : "AB-" }
{ "firstname" : "Dario", "surname" : "Costatini", "bloodType" : "A-" }
{ "firstname" : "Alessandro", "surname" : "Montanari", "bloodType" : "AB-" }
{ "firstname" : "Michela", "surname" : "Farina", "bloodType" : "A-" }
{ "firstname" : "Valeira", "surname" : "Giuliani", "bloodType" : "A-" }
{ "firstname" : "Gianluca", "surname" : "Marchetti", "bloodType" : "AB-" }
{ "firstname" : "Fabio", "surname" : "Galli", "bloodType" : "B-" }
{ "firstname" : "Silvia", "surname" : "Gatti", "bloodType" : "AB-" }
{ "firstname" : "Fabrizio", "surname" : "Morelli", "bloodType" : "AB-" }
{ "firstname" : "Gianni", "surname" : "Longo", "bloodType" : "AB-" }
{ "firstname" : "Emanuela", "surname" : "Montanari", "bloodType" : "AB-" }
{ "firstname" : "Simona", "surname" : "De Angelis", "bloodType" : "A-" }
{ "firstname" : "Andrea", "surname" : "Orlando", "bloodType" : "A-" }
{ "firstname" : "Alex", "surname" : "Testa", "bloodType" : "O-" }
{ "firstname" : "Carlo", "surname" : "Battaglia", "bloodType" : "AB-" }
{ "firstname" : "Enzo ", "surname" : "Testa", "bloodType" : "O-" }
{ "firstname" : "Elisabetta", "surname" : "Palumbo", "bloodType" : "B-" }
{ "firstname" : "Andrea", "surname" : "Conti", "bloodType" : "B-" }
{ "firstname" : "Giuseppe", "surname" : "Montanari", "bloodType" : "O-" }

11. Projete apenas os animais dos italianos. Devem ser listados os animais com nome e idade. Não mostre o identificado do mongo (ObjectId) 


12. Quais são as 5 pessoas mais velhas com sobrenome Rossi? 


13. Crie um italiano que tenha um leão como animal de estimação. Associe um nome e idade ao bichano 


14. Infelizmente o Leão comeu o italiano. Remova essa pessoa usando o Id. 


15. Passou um ano. Atualize a idade de todos os italianos e dos bichanos em 1. 


16. O Corona Vírus chegou na Itália e misteriosamente atingiu pessoas somente com gatos e de 66 anos. Remova esses italianos. 


17. Utilizando o framework agregate, liste apenas as pessoas com nomes iguais a sua respectiva mãe e que tenha gato ou cachorro. 


18. Utilizando aggregate framework, faça uma lista de nomes única de nomes. Faça isso usando apenas o primeiro nome 


19. Agora faça a mesma lista do item acima, considerando nome completo. 


20. Procure pessoas que gosta de Banana ou Maçã, tenham cachorro ou gato, mais de 20 e  menos de 60 anos. 

Exercício 3 - Stockbrokers

1. Liste as ações com profit acima de 0.5 (limite a 10 o resultado)
2. Liste as ações com perdas (limite a 10 novamente)
3. Liste as 10 ações mais rentáveis
4. Qual foi o setor mais rentável?
5. Ordene as ações pelo profit e usando um cursor, liste as ações.
6. Renomeie o campo “Profit Margin” para apenas “profit”.
7. Agora liste apenas a empresa e seu respectivo resultado
8. Analise as ações. É uma bola de cristal na sua mão... Quais as três ações
você investiria?
9. Liste as ações agrupadas por setor
