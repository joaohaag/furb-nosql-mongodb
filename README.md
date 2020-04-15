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

db.italians.find({ $or: [{ $and: [ { dog: { $exists: true}}, { $where: "this.firstname== this.dog.name" } ] },{ $and: [ { cat: { $exists: true}}, { $where: "this.firstname== this.cat.name" } ] }]})

{ "_id" : ObjectId("5e8a31712c71b99c0f203e63"), "firstname" : "Giusy", "surname" : "Gatti", "username" : "user147", "age" : 63, "email" : "Giusy.Gatti@yahoo.com", "bloodType" : "O+", "id_num" : "246444570530", "registerDate" : ISODate("2013-02-11T16:57:08.973Z"), "ticketNumber" : 9186, "jobs" : [ "Gestão de Cooperativas" ], "favFruits" : [ "Laranja", "Mamão" ], "movies" : [ { "title" : "Clube da Luta (1999)", "rating" : 1.53 }, { "title" : "Cidade de Deus (2002)", "rating" : 1.99 }, { "title" : "Gladiador (2000)", "rating" : 3.53 }, { "title" : "À Espera de um Milagre (1999)", "rating" : 1.03 } ], "cat" : { "name" : "Giusy", "age" : 2 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203eed"), "firstname" : "Patrizia", "surname" : "Cattaneo", "username" : "user285", "age" : 10, "email" : "Patrizia.Cattaneo@live.com", "bloodType" : "B-", "id_num" : "640180245356", "registerDate" : ISODate("2008-01-05T13:22:00.559Z"), "ticketNumber" : 7197, "jobs" : [ "Engenharia Mecânica", "Engenharia Agrícola" ], "favFruits" : [ "Maçã" ], "movies" : [ { "title" : "Vingadores: Ultimato (2019)", "rating" : 3.58 }, { "title" : "O Senhor dos Anéis: As Duas Torres (2002)", "rating" : 2.99 } ], "cat" : { "name" : "Claudia", "age" : 4 }, "dog" : { "name" : "Patrizia", "age" : 11 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f03"), "firstname" : "Veronica", "surname" : "De Angelis", "username" : "user307", "age" : 18, "email" : "Veronica.De Angelis@yahoo.com", "bloodType" : "B-", "id_num" : "710375500775", "registerDate" : ISODate("2019-07-27T00:19:03.435Z"), "ticketNumber" : 5582, "jobs" : [ "Gestão de Segurança Privada" ], "favFruits" : [ "Tangerina", "Uva" ], "movies" : [ { "title" : "Um Estranho no Ninho (1975)", "rating" : 4.98 }, { "title" : "A Lista de Schindler (1993)", "rating" : 1.26 }, { "title" : "12 Homens e uma Sentença (1957)", "rating" : 0.6 }, { "title" : "A Vida é Bela (1997)", "rating" : 2.17 }, { "title" : "12 Homens e uma Sentença (1957)", "rating" : 0.72 } ], "father" : { "firstname" : "Marta", "surname" : "De Angelis", "age" : 53 }, "cat" : { "name" : "Veronica", "age" : 6 }, "dog" : { "name" : "Carlo", "age" : 9 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f0f"), "firstname" : "Alessandro", "surname" : "Costa", "username" : "user319", "age" : 58, "email" : "Alessandro.Costa@hotmail.com", "bloodType" : "AB-", "id_num" : "407877877285", "registerDate" : ISODate("2014-09-09T07:58:15.154Z"), "ticketNumber" : 4687, "jobs" : [ "Cooperativismo", "Sistemas para Internet" ], "favFruits" : [ "Melancia" ], "movies" : [ { "title" : "Harakiri (1962)", "rating" : 4.23 }, { "title" : "O Resgate do Soldado Ryan (1998)", "rating" : 0.9 }, { "title" : "A Origem (2010)", "rating" : 2.17 }, { "title" : "Intocáveis (2011)", "rating" : 0.35 } ], "cat" : { "name" : "Alessandro", "age" : 3 }, "dog" : { "name" : "Gianni", "age" : 12 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f3c"), "firstname" : "Giuseppe", "surname" : "Milani", "username" : "user364", "age" : 20, "email" : "Giuseppe.Milani@gmail.com", "bloodType" : "O+", "id_num" : "611533311616", "registerDate" : ISODate("2012-08-17T11:45:53.276Z"), "ticketNumber" : 4521, "jobs" : [ "Filosofia", "Agronegócios e Agropecuária" ], "favFruits" : [ "Maçã" ], "movies" : [ { "title" : "Cidade de Deus (2002)", "rating" : 2.89 }, { "title" : "Interestelar (2014)", "rating" : 0.92 }, { "title" : "Interestelar (2014)", "rating" : 3.37 }, { "title" : "Clube da Luta (1999)", "rating" : 1.24 } ], "cat" : { "name" : "Giuseppe", "age" : 2 }, "dog" : { "name" : "Michela", "age" : 17 } }
{ "_id" : ObjectId("5e8a31722c71b99c0f203f49"), "firstname" : "Massimiliano", "surname" : "Martino", "username" : "user377", "age" : 38, "email" : "Massimiliano.Martino@hotmail.com", "bloodType" : "O+", "id_num" : "066283365575", "registerDate" : ISODate("2016-12-04T18:17:28.767Z"), "ticketNumber" : 4922, "jobs" : [ "Fotografia" ], "favFruits" : [ "Melancia", "Uva", "Melancia" ], "movies" : [ { "title" : "Vingadores: Ultimato (2019)", "rating" : 4.16 }, { "title" : "12 Homens e uma Sentença (1957)", "rating" : 0.24 } ], "mother" : { "firstname" : "Claudia", "surname" : "Martino", "age" : 70 }, "cat" : { "name" : "Massimiliano", "age" : 9 } }
{ "_id" : ObjectId("5e8a31732c71b99c0f20402a"), "firstname" : "Alberto", "surname" : "Grassi", "username" : "user602", "age" : 2, "email" : "Alberto.Grassi@outlook.com", "bloodType" : "AB+", "id_num" : "160236032728", "registerDate" : ISODate("2019-09-15T04:32:10.616Z"), "ticketNumber" : 2586, "jobs" : [ "Engenharia Hídrica", "Gestão da Informação" ], "favFruits" : [ "Pêssego", "Mamão" ], "movies" : [ { "title" : "Um Sonho de Liberdade (1994)", "rating" : 3.97 }, { "title" : "Vingadores: Ultimato (2019)", "rating" : 3.01 } ], "cat" : { "name" : "Roberta", "age" : 10 }, "dog" : { "name" : "Alberto", "age" : 1 } }
{ "_id" : ObjectId("5e8a31732c71b99c0f20402f"), "firstname" : "Valentina", "surname" : "Barbieri", "username" : "user607", "age" : 33, "email" : "Valentina.Barbieri@gmail.com", "bloodType" : "B-", "id_num" : "417647515841", "registerDate" : ISODate("2016-12-23T15:16:49.670Z"), "ticketNumber" : 2732, "jobs" : [ "Hotelaria", "Papel e Celulose" ], "favFruits" : [ "Pêssego", "Uva", "Uva" ], "movies" : [ { "title" : "Gladiador (2000)", "rating" : 0.66 }, { "title" : "O Senhor dos Anéis: As Duas Torres (2002)", "rating" : 3.87 } ], "cat" : { "name" : "Valentina", "age" : 15 } }
{ "_id" : ObjectId("5e8a31732c71b99c0f2040e5"), "firstname" : "Elisa", "surname" : "Caruso", "username" : "user789", "age" : 12, "email" : "Elisa.Caruso@yahoo.com", "bloodType" : "AB-", "id_num" : "866726402465", "registerDate" : ISODate("2009-08-02T14:49:32.982Z"), "ticketNumber" : 8530, "jobs" : [ "Análise e Desenvolvimento de Sistemas", "Geografia" ], "favFruits" : [ "Tangerina", "Tangerina" ], "movies" : [ { "title" : "A Origem (2010)", "rating" : 0.08 }, { "title" : "Um Estranho no Ninho (1975)", "rating" : 3.07 }, { "title" : "12 Homens e uma Sentença (1957)", "rating" : 0.29 } ], "dog" : { "name" : "Elisa", "age" : 16 } }
{ "_id" : ObjectId("5e8a31742c71b99c0f204207"), "firstname" : "Alberto", "surname" : "Mazza", "username" : "user1079", "age" : 37, "email" : "Alberto.Mazza@hotmail.com", "bloodType" : "B-", "id_num" : "351562276807", "registerDate" : ISODate("2008-12-02T23:32:02.529Z"), "ticketNumber" : 7814, "jobs" : [ "Artes e Design" ], "favFruits" : [ "Kiwi", "Melancia", "Goiaba" ], "movies" : [ { "title" : "Parasita (2019)", "rating" : 4.9 } ], "cat" : { "name" : "Alberto", "age" : 12 }, "dog" : { "name" : "Sonia", "age" : 14 } }
{ "_id" : ObjectId("5e8a31762c71b99c0f20437f"), "firstname" : "Sara", "surname" : "Lombardi", "username" : "user1455", "age" : 79, "email" : "Sara.Lombardi@live.com", "bloodType" : "A-", "id_num" : "345346612647", "registerDate" : ISODate("2017-06-22T06:01:38.395Z"), "ticketNumber" : 5684, "jobs" : [ "Arqueologia" ], "favFruits" : [ "Mamão" ], "movies" : [ { "title" : "A Felicidade Não se Compra (1946)", "rating" : 1.19 }, { "title" : "Batman: O Cavaleiro das Trevas (2008)", "rating" : 2.04 }, { "title" : "Clube da Luta (1999)", "rating" : 3.31 }, { "title" : "O Senhor dos Anéis: A Sociedade do Anel (2001)", "rating" : 0.65 } ], "cat" : { "name" : "Sara", "age" : 17 } }
{ "_id" : ObjectId("5e8a31762c71b99c0f2043e8"), "firstname" : "Giulia", "surname" : "D’Angelo", "username" : "user1560", "age" : 45, "email" : "Giulia.D’Angelo@yahoo.com", "bloodType" : "A-", "id_num" : "403465523657", "registerDate" : ISODate("2012-02-17T21:36:32.230Z"), "ticketNumber" : 6272, "jobs" : [ "Biocombustíveis", "Gestão da Produção Industrial" ], "favFruits" : [ "Uva", "Tangerina" ], "movies" : [ { "title" : "Três Homens em Conflito (1966)", "rating" : 2.96 }, { "title" : "Guerra nas Estrelas (1977)", "rating" : 0.64 }, { "title" : "Forrest Gump: O Contador de Histórias (1994)", "rating" : 4.7 }, { "title" : "Gladiador (2000)", "rating" : 0.92 } ], "cat" : { "name" : "Giulia", "age" : 13 }, "dog" : { "name" : "Antonella", "age" : 11 } }
{ "_id" : ObjectId("5e8a31762c71b99c0f204427"), "firstname" : "Fabio", "surname" : "Conte", "username" : "user1623", "age" : 44, "email" : "Fabio.Conte@hotmail.com", "bloodType" : "O-", "id_num" : "253666610427", "registerDate" : ISODate("2011-09-21T01:13:28.601Z"), "ticketNumber" : 4643, "jobs" : [ "Engenharia de Energia", "Engenharia Elétrica" ], "favFruits" : [ "Banana", "Mamão", "Kiwi" ], "movies" : [ { "title" : "Cidade de Deus (2002)", "rating" : 2.97 }, { "title" : "1917 (2019)", "rating" : 0.81 }, { "title" : "À Espera de um Milagre (1999)", "rating" : 1.89 }, { "title" : "Intocáveis (2011)", "rating" : 0.13 }, { "title" : "1917 (2019)", "rating" : 2 } ], "cat" : { "name" : "Federico", "age" : 10 }, "dog" : { "name" : "Fabio", "age" : 11 } }
{ "_id" : ObjectId("5e8a31762c71b99c0f204431"), "firstname" : "Andrea", "surname" : "Conte", "username" : "user1633", "age" : 29, "email" : "Andrea.Conte@yahoo.com", "bloodType" : "B-", "id_num" : "457703828678", "registerDate" : ISODate("2015-08-03T03:25:03.278Z"), "ticketNumber" : 4467, "jobs" : [ "Rochas Ornamentais", "Engenharia Física" ], "favFruits" : [ "Melancia" ], "movies" : [ { "title" : "Matrix (1999)", "rating" : 1.72 }, { "title" : "Matrix (1999)", "rating" : 1.28 }, { "title" : "Parasita (2019)", "rating" : 4.52 }, { "title" : "À Espera de um Milagre (1999)", "rating" : 0.22 }, { "title" : "O Senhor dos Anéis: O Retorno do Rei (2003)", "rating" : 0.74 } ], "father" : { "firstname" : "Salvatore", "surname" : "Conte", "age" : 67 }, "cat" : { "name" : "Andrea", "age" : 3 } }
{ "_id" : ObjectId("5e8a31762c71b99c0f204439"), "firstname" : "Antonio", "surname" : "Sala", "username" : "user1641", "age" : 17, "email" : "Antonio.Sala@live.com", "bloodType" : "AB+", "id_num" : "844848817513", "registerDate" : ISODate("2014-09-29T11:36:39.865Z"), "ticketNumber" : 1347, "jobs" : [ "Materiais" ], "favFruits" : [ "Laranja" ], "movies" : [ { "title" : "Cidade de Deus (2002)", "rating" : 3.52 } ], "cat" : { "name" : "Antonio", "age" : 9 } }
{ "_id" : ObjectId("5e8a31762c71b99c0f20445b"), "firstname" : "Simone", "surname" : "Caruso", "username" : "user1675", "age" : 27, "email" : "Simone.Caruso@yahoo.com", "bloodType" : "A+", "id_num" : "227674232715", "registerDate" : ISODate("2016-09-09T06:47:51.140Z"), "ticketNumber" : 6873, "jobs" : [ "Geoprocessamento", "Design de Interiores" ], "favFruits" : [ "Tangerina", "Kiwi", "Uva" ], "movies" : [ { "title" : "Um Sonho de Liberdade (1994)", "rating" : 2.82 }, { "title" : "Batman: O Cavaleiro das Trevas (2008)", "rating" : 0.65 }, { "title" : "Matrix (1999)", "rating" : 2.83 } ], "cat" : { "name" : "Simone", "age" : 0 }, "dog" : { "name" : "Simona", "age" : 16 } }
{ "_id" : ObjectId("5e8a31772c71b99c0f20449c"), "firstname" : "Manuela", "surname" : "Lombardi", "username" : "user1740", "age" : 20, "email" : "Manuela.Lombardi@gmail.com", "bloodType" : "B-", "id_num" : "376328642341", "registerDate" : ISODate("2015-12-03T14:51:38.208Z"), "ticketNumber" : 1141, "jobs" : [ "Artes e Design", "Engenharia Industrial Madeireira" ], "favFruits" : [ "Kiwi", "Banana", "Mamão" ], "movies" : [ { "title" : "12 Homens e uma Sentença (1957)", "rating" : 4.06 }, { "title" : "Cidade de Deus (2002)", "rating" : 3.69 }, { "title" : "O Senhor dos Anéis: As Duas Torres (2002)", "rating" : 2.32 }, { "title" : "Clube da Luta (1999)", "rating" : 1.95 }, { "title" : "O Silêncio dos Inocentes (1991)", "rating" : 4.22 } ], "mother" : { "firstname" : "Raffaele", "surname" : "Lombardi", "age" : 35 }, "cat" : { "name" : "Manuela", "age" : 11 } }
{ "_id" : ObjectId("5e8a31782c71b99c0f20460e"), "firstname" : "Tiziana", "surname" : "Gallo", "username" : "user2110", "age" : 49, "email" : "Tiziana.Gallo@gmail.com", "bloodType" : "AB-", "id_num" : "688180587516", "registerDate" : ISODate("2015-12-28T12:02:25.918Z"), "ticketNumber" : 2412, "jobs" : [ "Direito", "Agrimensura" ], "favFruits" : [ "Goiaba", "Maçã" ], "movies" : [ { "title" : "Gladiador (2000)", "rating" : 0.9 } ], "cat" : { "name" : "Tiziana", "age" : 3 } }
{ "_id" : ObjectId("5e8a31782c71b99c0f204669"), "firstname" : "Simona", "surname" : "Orlando", "username" : "user2201", "age" : 23, "email" : "Simona.Orlando@uol.com.br", "bloodType" : "AB-", "id_num" : "541664006078", "registerDate" : ISODate("2017-06-15T12:35:29.633Z"), "ticketNumber" : 3236, "jobs" : [ "Engenharia Civil" ], "favFruits" : [ "Uva", "Goiaba", "Kiwi" ], "movies" : [ { "title" : "Três Homens em Conflito (1966)", "rating" : 2.51 }, { "title" : "Coringa (2019)", "rating" : 1 }, { "title" : "Vingadores: Ultimato (2019)", "rating" : 4.13 }, { "title" : "A Origem (2010)", "rating" : 4.76 } ], "cat" : { "name" : "Luigi", "age" : 13 }, "dog" : { "name" : "Simona", "age" : 3 } }
{ "_id" : ObjectId("5e8a31782c71b99c0f204689"), "firstname" : "Mattia", "surname" : "Gatti", "username" : "user2233", "age" : 47, "email" : "Mattia.Gatti@hotmail.com", "bloodType" : "B+", "id_num" : "504015057528", "registerDate" : ISODate("2014-04-24T22:27:14.122Z"), "ticketNumber" : 5742, "jobs" : [ "Processos Químicos", "Ciências Contábeis" ], "favFruits" : [ "Pêssego", "Mamão", "Tangerina" ], "movies" : [ { "title" : "Interestelar (2014)", "rating" : 4.39 } ], "cat" : { "name" : "Elisabetta", "age" : 14 }, "dog" : { "name" : "Mattia", "age" : 9 } }

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

> db.italians.find({},{"dog.name":1, "dog.age": 1, "cat.name":1, "cat.age" : 1, "_id" : 0})


{ "cat" : { "name" : "Emanuele", "age" : 14 } }
{ "cat" : { "name" : "Enzo ", "age" : 1 }, "dog" : { "name" : "Cristina", "age" : 10 } }
{ "dog" : { "name" : "Elisabetta", "age" : 13 } }
{  }
{ "cat" : { "name" : "Elisabetta", "age" : 16 } }
{ "dog" : { "name" : "Michela", "age" : 14 } }
{  }
{ "cat" : { "name" : "Enrico", "age" : 0 } }
{ "cat" : { "name" : "Giacomo", "age" : 7 } }
{  }
{ "cat" : { "name" : "Enrico", "age" : 10 }, "dog" : { "name" : "Lucia", "age" : 12 } }
{ "cat" : { "name" : "Barbara", "age" : 7 }, "dog" : { "name" : "Chiara", "age" : 5 } }
{ "cat" : { "name" : "Valeira", "age" : 15 } }
{ "cat" : { "name" : "Mario", "age" : 3 } }
{  }
{  }
{ "cat" : { "name" : "Angelo", "age" : 1 }, "dog" : { "name" : "Gianluca", "age" : 7 } }
{ "cat" : { "name" : "Raffaele", "age" : 11 } }
{  }
{  }

12. Quais são as 5 pessoas mais velhas com sobrenome Rossi? 

> db.italians.find({"surname": "Rossi"}).pretty().limit(5).sort({age : -1})


{
        "_id" : ObjectId("5e8a31892c71b99c0f205c31"),
        "firstname" : "Mauro",
        "surname" : "Rossi",
        "username" : "user7777",
        "age" : 78,
        "email" : "Mauro.Rossi@uol.com.br",
        "bloodType" : "AB-",
        "id_num" : "045151846632",
        "registerDate" : ISODate("2019-01-23T18:41:21.547Z"),
        "ticketNumber" : 4509,
        "jobs" : [
                "Sistemas de Informação"
        ],
        "favFruits" : [
                "Maçã",
                "Kiwi",
                "Maçã"
        ],
        "movies" : [
                {
                        "title" : "Forrest Gump: O Contador de Histórias (1994)",
                        "rating" : 1.77
                }
        ],
        "father" : {
                "firstname" : "Elisabetta",
                "surname" : "Rossi",
                "age" : 113
        },
        "cat" : {
                "name" : "Vincenzo",
                "age" : 5
        }
}
{
        "_id" : ObjectId("5e8a317a2c71b99c0f2048d4"),
        "firstname" : "Pietro",
        "surname" : "Rossi",
        "username" : "user2820",
        "age" : 77,
        "email" : "Pietro.Rossi@outlook.com",
        "bloodType" : "AB+",
        "id_num" : "882642868270",
        "registerDate" : ISODate("2015-02-25T16:01:11.942Z"),
        "ticketNumber" : 4781,
        "jobs" : [
                "Engenharia Mecatrônica"
        ],
        "favFruits" : [
                "Uva",
                "Uva"
        ],
        "movies" : [
                {
                        "title" : "Interestelar (2014)",
                        "rating" : 4.8
                }
        ],
        "father" : {
                "firstname" : "Manuela",
                "surname" : "Rossi",
                "age" : 101
        }
}
{
        "_id" : ObjectId("5e8a317d2c71b99c0f204d04"),
        "firstname" : "Salvatore",
        "surname" : "Rossi",
        "username" : "user3892",
        "age" : 75,
        "email" : "Salvatore.Rossi@hotmail.com",
        "bloodType" : "AB+",
        "id_num" : "672535567063",
        "registerDate" : ISODate("2008-03-30T08:26:25.997Z"),
        "ticketNumber" : 5744,
        "jobs" : [
                "Educação Física",
                "Engenharia Têxtil"
        ],
        "favFruits" : [
                "Melancia"
        ],
        "movies" : [
                {
                        "title" : "1917 (2019)",
                        "rating" : 2.7
                },
                {
                        "title" : "Pulp Fiction: Tempo de Violência (1994)",
                        "rating" : 2.55
                },
                {
                        "title" : "A Lista de Schindler (1993)",
                        "rating" : 4.41
                },
                {
                        "title" : "Forrest Gump: O Contador de Histórias (1994)",
                        "rating" : 1.01
                },
                {
                        "title" : "Um Sonho de Liberdade (1994)",
                        "rating" : 1.07
                }
        ],
        "cat" : {
                "name" : "Teresa",
                "age" : 10
        },
        "dog" : {
                "name" : "Carlo",
                "age" : 9
        }
}
{
        "_id" : ObjectId("5e8a31752c71b99c0f20431e"),
        "firstname" : "Giovanni",
        "surname" : "Rossi",
        "username" : "user1358",
        "age" : 74,
        "email" : "Giovanni.Rossi@uol.com.br",
        "bloodType" : "A+",
        "id_num" : "841557081662",
        "registerDate" : ISODate("2018-02-09T18:16:57.302Z"),
        "ticketNumber" : 4823,
        "jobs" : [
                "Animação"
        ],
        "favFruits" : [
                "Laranja",
                "Melancia"
        ],
        "movies" : [
                {
                        "title" : "Guerra nas Estrelas (1977)",
                        "rating" : 0.63
                },
                {
                        "title" : "Clube da Luta (1999)",
                        "rating" : 3.24
                }
        ],
        "cat" : {
                "name" : "Elisa",
                "age" : 1
        }
}
{
        "_id" : ObjectId("5e8a31752c71b99c0f204276"),
        "firstname" : "Daniele",
        "surname" : "Rossi",
        "username" : "user1190",
        "age" : 73,
        "email" : "Daniele.Rossi@yahoo.com",
        "bloodType" : "A-",
        "id_num" : "161010323347",
        "registerDate" : ISODate("2009-07-20T20:39:48.765Z"),
        "ticketNumber" : 8845,
        "jobs" : [
                "Serviço Social",
                "Engenharia Civil"
        ],
        "favFruits" : [
                "Maçã",
                "Laranja",
                "Pêssego"
        ],
        "movies" : [
                {
                        "title" : "Os Bons Companheiros (1990)",
                        "rating" : 3.92
                }
        ],
        "cat" : {
                "name" : "Emanuela",
                "age" : 4
        }
}

13. Crie um italiano que tenha um leão como animal de estimação. Associe um nome e idade ao bichano 

> db.italians.insert({
...         "firstname" : "João",
...         "surname" : "Haag",
...         "username" : "joaohaag",
...         "age" : 27,
...         "email" : "joaohaag@hotmail.com",
...         "bloodType" : "B+",
...         "id_num" : "014505207505",
...         "registerDate" : ISODate("2014-12-06T13:32:47.898Z"),
...         "ticketNumber" : 3500,
...         "jobs" : [
...                 "Analista"
...         ],
...         "favFruits" : [
...                 "Manga"
...         ],
...         "movies" : [
...                 {
...                         "title" : "A Lista de Schindler (1993)",
...                         "rating" : 4.92
...                 },
...                 {
...                         "title" : "Parasita (2019)",
...                         "rating" : 3.06
...                 }
...         ],
...         "lion" : {
...                 "name" : "jack",
...                 "age" : 2
...         }
... })
WriteResult({ "nInserted" : 1 })

14. Infelizmente o Leão comeu o italiano. Remova essa pessoa usando o Id. 

> db.italians.remove({"_id": ObjectId("5e9501fbe0d1aa424e9f53df")});
WriteResult({ "nRemoved" : 1 })

15. Passou um ano. Atualize a idade de todos os italianos e dos bichanos em 1. 

Atualiza idade dos Italianos
db.italians.update({}, {$inc :{"age" : 1}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

Atualiza idade dos gatos
> db.italians.update({cat: { $exists: true}}, {$inc :{"cat.age" : 1}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

Atualiza idade dos cachorros
> db.italians.update({dog: { $exists: true}}, {$inc :{"dog.age" : 1}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

16. O Corona Vírus chegou na Itália e misteriosamente atingiu pessoas somente com gatos e de 66 anos. Remova esses italianos. 

> db.italians.remove({cat: { $exists: true}, "age" : 66});
WriteResult({ "nRemoved" : 87 })

17. Utilizando o framework agregate, liste apenas as pessoas com nomes iguais a sua respectiva mãe e que tenha gato ou cachorro. 

> db.italians.aggregate([
... {$match: { $or: [ {cat: { $exists: 1}}, {dog: { $exists: 1}} ] }},
... {$match: {mother: { $exists: 1}}},
... {$project: {firstname: 1, mother: 1, isEqual: { $cmp: ["$firstname","$mother.firstname"]}}},
... {$match: {isEqual : 0}}
... ])


{ "_id" : ObjectId("5e8a31722c71b99c0f203f6e"), "firstname" : "Daniele", "mother" : { "firstname" : "Daniele", "surname" : "Coppola", "age" : 104 }, "isEqual" : 0 }
{ "_id" : ObjectId("5e8a31762c71b99c0f20439c"), "firstname" : "Dario", "mother" : { "firstname" : "Dario", "surname" : "Amato", "age" : 98 }, "isEqual" : 0 }
{ "_id" : ObjectId("5e8a317a2c71b99c0f204871"), "firstname" : "Alessia", "mother" : { "firstname" : "Alessia", "surname" : "Cattaneo", "age" : 100 }, "isEqual" : 0 }
{ "_id" : ObjectId("5e8a317b2c71b99c0f204a08"), "firstname" : "Domenico", "mother" : { "firstname" : "Domenico", "surname" : "Pellegrini", "age" : 52 }, "isEqual" : 0 }
{ "_id" : ObjectId("5e8a317c2c71b99c0f204b04"), "firstname" : "Claudio", "mother" : { "firstname" : "Claudio", "surname" : "Costatini", "age" : 49 }, "isEqual" : 0 }
{ "_id" : ObjectId("5e8a31892c71b99c0f205c10"), "firstname" : "Serena", "mother" : { "firstname" : "Serena", "surname" : "Serra", "age" : 32 }, "isEqual" : 0 }


18. Utilizando aggregate framework, faça uma lista de nomes única de nomes. Faça isso usando apenas o primeiro nome 
> db.italians.aggregate({ $project: { Nome: "$firstname", "_id" : 0} } )

{ "Nome" : "Antonio" }
{ "Nome" : "Roberto" }
{ "Nome" : "Lucia" }
{ "Nome" : "Emanuele" }
{ "Nome" : "Dario" }
{ "Nome" : "Alessandro" }
{ "Nome" : "Roberta" }
{ "Nome" : "Michela" }
{ "Nome" : "Andrea" }
{ "Nome" : "Valeira" }
{ "Nome" : "Gianluca" }
{ "Nome" : "Alessandra" }
{ "Nome" : "Teresa" }
{ "Nome" : "Fabio" }
{ "Nome" : "Silvia" }
{ "Nome" : "Alessandro" }
{ "Nome" : "Giuseppe" }
{ "Nome" : "Michele" }
{ "Nome" : "Fabrizio" }
{ "Nome" : "Laura" }

19. Agora faça a mesma lista do item acima, considerando nome completo. 

> db.italians.aggregate([{ $project: { Nome_Completo: { $concat: [ "$firstname", " ", "$surname" ] }, "_id" : 0} } ] )
{ "Nome_Completo" : "Antonio Longo" }
{ "Nome_Completo" : "Roberto De Angelis" }
{ "Nome_Completo" : "Lucia Caputo" }
{ "Nome_Completo" : "Emanuele Barone" }
{ "Nome_Completo" : "Dario Costatini" }
{ "Nome_Completo" : "Alessandro Montanari" }
{ "Nome_Completo" : "Roberta Lombardi" }
{ "Nome_Completo" : "Michela Farina" }
{ "Nome_Completo" : "Andrea Carbone" }
{ "Nome_Completo" : "Valeira Giuliani" }
{ "Nome_Completo" : "Gianluca Marchetti" }
{ "Nome_Completo" : "Alessandra Gatti" }
{ "Nome_Completo" : "Teresa Costa" }
{ "Nome_Completo" : "Fabio Galli" }
{ "Nome_Completo" : "Silvia Gatti" }
{ "Nome_Completo" : "Alessandro Milani" }
{ "Nome_Completo" : "Giuseppe Sanna" }
{ "Nome_Completo" : "Michele Damico" }
{ "Nome_Completo" : "Fabrizio Morelli" }
{ "Nome_Completo" : "Laura Barbieri" }

20. Procure pessoas que gosta de Banana ou Maçã, tenham cachorro ou gato, mais de 20 e menos de 60 anos. 

> db.italians.find({$and: [{$or: [{"favFruits" : "Banana"}, {"favFruits" : "Maçã"}]}, {$or: [{dog: {$exists: true}}, {cat:{ $exists: true}} ]}, {"age" : {"$gt" : 20, "$lt" : 60}}]}).pretty()
{
        "_id" : ObjectId("5e8a31712c71b99c0f203e40"),
        "firstname" : "Teresa",
        "surname" : "Costa",
        "username" : "user112",
        "age" : 38,
        "email" : "Teresa.Costa@live.com",
        "bloodType" : "O+",
        "id_num" : "243708624026",
        "registerDate" : ISODate("2015-03-22T17:31:02.095Z"),
        "ticketNumber" : 9771,
        "jobs" : [
                "Meteorologia"
        ],
        "favFruits" : [
                "Maçã"
        ],
        "movies" : [
                {
                        "title" : "Clube da Luta (1999)",
                        "rating" : 3.72
                },
                {
                        "title" : "Star Wars, Episódio V: O Império Contra-Ataca (1980)",
                        "rating" : 1.53
                },
                {
                        "title" : "A Lista de Schindler (1993)",
                        "rating" : 0.93
                },
                {
                        "title" : "1917 (2019)",
                        "rating" : 3.7
                },
                {
                        "title" : "Os Bons Companheiros (1990)",
                        "rating" : 2.96
                }
        ],
        "cat" : {
                "name" : "Valeira",
                "age" : 15
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203e4e"),
        "firstname" : "Simona",
        "surname" : "De Angelis",
        "username" : "user126",
        "age" : 46,
        "email" : "Simona.De Angelis@gmail.com",
        "bloodType" : "A-",
        "id_num" : "250872176351",
        "registerDate" : ISODate("2012-10-09T03:10:42.359Z"),
        "ticketNumber" : 9461,
        "jobs" : [
                "Comunicação das Artes do Corpo",
                "Engenharia de Petróleo"
        ],
        "favFruits" : [
                "Melancia",
                "Banana",
                "Uva"
        ],
        "movies" : [
                {
                        "title" : "Guerra nas Estrelas (1977)",
                        "rating" : 4.01
                },
                {
                        "title" : "O Poderoso Chefão II (1974)",
                        "rating" : 4.74
                },
                {
                        "title" : "Clube da Luta (1999)",
                        "rating" : 2.1
                }
        ],
        "mother" : {
                "firstname" : "Giovanna",
                "surname" : "De Angelis",
                "age" : 72
        },
        "cat" : {
                "name" : "Alessia",
                "age" : 13
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203e50"),
        "firstname" : "Alex",
        "surname" : "Testa",
        "username" : "user128",
        "age" : 53,
        "email" : "Alex.Testa@live.com",
        "bloodType" : "O-",
        "id_num" : "667000548108",
        "registerDate" : ISODate("2008-04-29T14:32:40.817Z"),
        "ticketNumber" : 5924,
        "jobs" : [
                "Ciências Aeronáuticas"
        ],
        "favFruits" : [
                "Maçã",
                "Tangerina"
        ],
        "movies" : [
                {
                        "title" : "O Resgate do Soldado Ryan (1998)",
                        "rating" : 3.68
                },
                {
                        "title" : "Os Bons Companheiros (1990)",
                        "rating" : 3.19
                }
        ],
        "father" : {
                "firstname" : "Sonia",
                "surname" : "Testa",
                "age" : 73
        },
        "cat" : {
                "name" : "Pasquale",
                "age" : 15
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203e62"),
        "firstname" : "Lucia",
        "surname" : "Sala",
        "username" : "user146",
        "age" : 29,
        "email" : "Lucia.Sala@uol.com.br",
        "bloodType" : "O-",
        "id_num" : "035460836585",
        "registerDate" : ISODate("2016-05-13T16:36:08.484Z"),
        "ticketNumber" : 7025,
        "jobs" : [
                "Negócios Imobiliários"
        ],
        "favFruits" : [
                "Banana"
        ],
        "movies" : [
                {
                        "title" : "Batman: O Cavaleiro das Trevas (2008)",
                        "rating" : 0.01
                },
                {
                        "title" : "A Viagem de Chihiro (2001)",
                        "rating" : 0.41
                },
                {
                        "title" : "Interestelar (2014)",
                        "rating" : 3.61
                }
        ],
        "cat" : {
                "name" : "Simona",
                "age" : 10
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203e67"),
        "firstname" : "Giuseppe",
        "surname" : "Gallo",
        "username" : "user151",
        "age" : 59,
        "email" : "Giuseppe.Gallo@gmail.com",
        "bloodType" : "B-",
        "id_num" : "768584821033",
        "registerDate" : ISODate("2019-09-13T19:35:55.688Z"),
        "ticketNumber" : 3846,
        "jobs" : [
                "Administração Pública",
                "Gestão em Saúde"
        ],
        "favFruits" : [
                "Banana",
                "Maçã"
        ],
        "movies" : [
                {
                        "title" : "Intocáveis (2011)",
                        "rating" : 0.31
                },
                {
                        "title" : "Harakiri (1962)",
                        "rating" : 3.23
                }
        ],
        "cat" : {
                "name" : "Daniela",
                "age" : 6
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203e75"),
        "firstname" : "Anna",
        "surname" : "Lombardi",
        "username" : "user165",
        "age" : 29,
        "email" : "Anna.Lombardi@outlook.com",
        "bloodType" : "A-",
        "id_num" : "861164082438",
        "registerDate" : ISODate("2014-02-23T15:44:48.631Z"),
        "ticketNumber" : 3026,
        "jobs" : [
                "Informática Biomédica"
        ],
        "favFruits" : [
                "Maçã"
        ],
        "movies" : [
                {
                        "title" : "O Poderoso Chefão II (1974)",
                        "rating" : 3.93
                },
                {
                        "title" : "O Senhor dos Anéis: As Duas Torres (2002)",
                        "rating" : 2.55
                },
                {
                        "title" : "O Silêncio dos Inocentes (1991)",
                        "rating" : 1.08
                },
                {
                        "title" : "À Espera de um Milagre (1999)",
                        "rating" : 1.17
                },
                {
                        "title" : "Intocáveis (2011)",
                        "rating" : 0.33
                }
        ],
        "cat" : {
                "name" : "Angela",
                "age" : 10
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203e77"),
        "firstname" : "Marco",
        "surname" : "Farina",
        "username" : "user167",
        "age" : 58,
        "email" : "Marco.Farina@gmail.com",
        "bloodType" : "B+",
        "id_num" : "820814447208",
        "registerDate" : ISODate("2011-07-08T08:05:30.544Z"),
        "ticketNumber" : 5625,
        "jobs" : [
                "Ciência e Tecnologia de Alimentos",
                "Logística"
        ],
        "favFruits" : [
                "Melancia",
                "Kiwi",
                "Banana"
        ],
        "movies" : [
                {
                        "title" : "Um Sonho de Liberdade (1994)",
                        "rating" : 2.62
                },
                {
                        "title" : "O Resgate do Soldado Ryan (1998)",
                        "rating" : 1.1
                }
        ],
        "cat" : {
                "name" : "Mario",
                "age" : 0
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203e7d"),
        "firstname" : "Veronica",
        "surname" : "Caputo",
        "username" : "user173",
        "age" : 34,
        "email" : "Veronica.Caputo@gmail.com",
        "bloodType" : "A-",
        "id_num" : "488130148137",
        "registerDate" : ISODate("2012-08-28T08:34:08.047Z"),
        "ticketNumber" : 3985,
        "jobs" : [
                "Artes Visuais",
                "Gestão Financeira"
        ],
        "favFruits" : [
                "Laranja",
                "Banana"
        ],
        "movies" : [
                {
                        "title" : "O Poderoso Chefão (1972)",
                        "rating" : 0.11
                },
                {
                        "title" : "Pulp Fiction: Tempo de Violência (1994)",
                        "rating" : 0.79
                },
                {
                        "title" : "Harakiri (1962)",
                        "rating" : 4.75
                },
                {
                        "title" : "Forrest Gump: O Contador de Histórias (1994)",
                        "rating" : 2.25
                }
        ],
        "cat" : {
                "name" : "Sabrina",
                "age" : 16
        },
        "dog" : {
                "name" : "Angela",
                "age" : 3
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203e7e"),
        "firstname" : "Alex",
        "surname" : "Rizzi",
        "username" : "user174",
        "age" : 27,
        "email" : "Alex.Rizzi@yahoo.com",
        "bloodType" : "A+",
        "id_num" : "108213700015",
        "registerDate" : ISODate("2009-08-11T01:24:22.407Z"),
        "ticketNumber" : 2145,
        "jobs" : [
                "Design",
                "Construção Naval"
        ],
        "favFruits" : [
                "Laranja",
                "Banana",
                "Melancia"
        ],
        "movies" : [
                {
                        "title" : "O Poderoso Chefão II (1974)",
                        "rating" : 1.56
                }
        ],
        "dog" : {
                "name" : "Paolo",
                "age" : 13
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203e8c"),
        "firstname" : "Angela",
        "surname" : "Rizzo",
        "username" : "user188",
        "age" : 56,
        "email" : "Angela.Rizzo@yahoo.com",
        "bloodType" : "A+",
        "id_num" : "411036300188",
        "registerDate" : ISODate("2008-07-15T00:35:37.036Z"),
        "ticketNumber" : 7480,
        "jobs" : [
                "Odontologia",
                "Ciência e Tecnologia de Alimentos"
        ],
        "favFruits" : [
                "Melancia",
                "Banana",
                "Goiaba"
        ],
        "movies" : [
                {
                        "title" : "A Lista de Schindler (1993)",
                        "rating" : 4.07
                },
                {
                        "title" : "Vingadores: Ultimato (2019)",
                        "rating" : 4.85
                },
                {
                        "title" : "1917 (2019)",
                        "rating" : 3.12
                },
                {
                        "title" : "12 Homens e uma Sentença (1957)",
                        "rating" : 2.49
                }
        ],
        "dog" : {
                "name" : "Giuseppe",
                "age" : 13
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203e90"),
        "firstname" : "Alberto",
        "surname" : "De Santis",
        "username" : "user192",
        "age" : 43,
        "email" : "Alberto.De Santis@live.com",
        "bloodType" : "B+",
        "id_num" : "443204820234",
        "registerDate" : ISODate("2008-06-28T22:19:26.054Z"),
        "ticketNumber" : 4258,
        "jobs" : [
                "Ciências Naturais e Exatas",
                "Luteria"
        ],
        "favFruits" : [
                "Kiwi",
                "Mamão",
                "Banana"
        ],
        "movies" : [
                {
                        "title" : "Interestelar (2014)",
                        "rating" : 0.19
                },
                {
                        "title" : "Seven: Os Sete Crimes Capitais (1995)",
                        "rating" : 0.43
                },
                {
                        "title" : "Três Homens em Conflito (1966)",
                        "rating" : 1.48
                }
        ],
        "father" : {
                "firstname" : "Cinzia",
                "surname" : "De Santis",
                "age" : 66
        },
        "cat" : {
                "name" : "Stefano",
                "age" : 17
        },
        "dog" : {
                "name" : "Giovanni",
                "age" : 3
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203e97"),
        "firstname" : "Simona",
        "surname" : "Greco",
        "username" : "user199",
        "age" : 21,
        "email" : "Simona.Greco@outlook.com",
        "bloodType" : "AB+",
        "id_num" : "211154540663",
        "registerDate" : ISODate("2014-09-08T01:09:00.089Z"),
        "ticketNumber" : 432,
        "jobs" : [
                "Análise e Desenvolvimento de Sistemas"
        ],
        "favFruits" : [
                "Banana"
        ],
        "movies" : [
                {
                        "title" : "Os Sete Samurais (1954)",
                        "rating" : 3.54
                },
                {
                        "title" : "Coringa (2019)",
                        "rating" : 1.04
                },
                {
                        "title" : "Batman: O Cavaleiro das Trevas (2008)",
                        "rating" : 3.49
                }
        ],
        "cat" : {
                "name" : "Luigi",
                "age" : 15
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203ea3"),
        "firstname" : "Lorenzo",
        "surname" : "Rossetti",
        "username" : "user211",
        "age" : 32,
        "email" : "Lorenzo.Rossetti@outlook.com",
        "bloodType" : "B+",
        "id_num" : "705555303170",
        "registerDate" : ISODate("2011-04-12T12:06:52.434Z"),
        "ticketNumber" : 6070,
        "jobs" : [
                "Engenharia Industrial Madeireira",
                "Informática Biomédica"
        ],
        "favFruits" : [
                "Maçã",
                "Banana",
                "Banana"
        ],
        "movies" : [
                {
                        "title" : "A Viagem de Chihiro (2001)",
                        "rating" : 0.01
                },
                {
                        "title" : "Os Bons Companheiros (1990)",
                        "rating" : 3.58
                },
                {
                        "title" : "O Poderoso Chefão (1972)",
                        "rating" : 1.16
                },
                {
                        "title" : "Vingadores: Ultimato (2019)",
                        "rating" : 2.16
                }
        ],
        "father" : {
                "firstname" : "Ilaria",
                "surname" : "Rossetti",
                "age" : 52
        },
        "cat" : {
                "name" : "Filipo",
                "age" : 5
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203ea4"),
        "firstname" : "Ilaria",
        "surname" : "Milani",
        "username" : "user212",
        "age" : 34,
        "email" : "Ilaria.Milani@live.com",
        "bloodType" : "B-",
        "id_num" : "657162335837",
        "registerDate" : ISODate("2012-04-06T00:09:02.815Z"),
        "ticketNumber" : 6568,
        "jobs" : [
                "Música",
                "Secretariado Executivo"
        ],
        "favFruits" : [
                "Maçã",
                "Tangerina",
                "Uva"
        ],
        "movies" : [
                {
                        "title" : "O Silêncio dos Inocentes (1991)",
                        "rating" : 0.74
                },
                {
                        "title" : "Cidade de Deus (2002)",
                        "rating" : 1.03
                },
                {
                        "title" : "Star Wars, Episódio V: O Império Contra-Ataca (1980)",
                        "rating" : 1.03
                },
                {
                        "title" : "A Vida é Bela (1997)",
                        "rating" : 2.08
                }
        ],
        "cat" : {
                "name" : "Luca",
                "age" : 1
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203eaa"),
        "firstname" : "Antonio",
        "surname" : "Fiore",
        "username" : "user218",
        "age" : 43,
        "email" : "Antonio.Fiore@uol.com.br",
        "bloodType" : "O-",
        "id_num" : "877380201471",
        "registerDate" : ISODate("2016-05-21T13:04:38.939Z"),
        "ticketNumber" : 4569,
        "jobs" : [
                "Secretariado",
                "Gestão Pública"
        ],
        "favFruits" : [
                "Laranja",
                "Banana"
        ],
        "movies" : [
                {
                        "title" : "À Espera de um Milagre (1999)",
                        "rating" : 3.63
                },
                {
                        "title" : "Um Estranho no Ninho (1975)",
                        "rating" : 2.53
                }
        ],
        "cat" : {
                "name" : "Valentina",
                "age" : 6
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203eab"),
        "firstname" : "Monica",
        "surname" : "Ferretti",
        "username" : "user219",
        "age" : 58,
        "email" : "Monica.Ferretti@hotmail.com",
        "bloodType" : "O-",
        "id_num" : "486317062337",
        "registerDate" : ISODate("2018-04-10T00:10:16.994Z"),
        "ticketNumber" : 3606,
        "jobs" : [
                "Engenharia Ambiental e Sanitária"
        ],
        "favFruits" : [
                "Mamão",
                "Maçã"
        ],
        "movies" : [
                {
                        "title" : "O Senhor dos Anéis: A Sociedade do Anel (2001)",
                        "rating" : 3.24
                },
                {
                        "title" : "Star Wars, Episódio V: O Império Contra-Ataca (1980)",
                        "rating" : 1.12
                },
                {
                        "title" : "Coringa (2019)",
                        "rating" : 3
                },
                {
                        "title" : "Pulp Fiction: Tempo de Violência (1994)",
                        "rating" : 2.9
                },
                {
                        "title" : "Forrest Gump: O Contador de Histórias (1994)",
                        "rating" : 1.6
                }
        ],
        "cat" : {
                "name" : "Alessia",
                "age" : 10
        }
}
{
        "_id" : ObjectId("5e8a31712c71b99c0f203eb0"),
        "firstname" : "Daniele",
        "surname" : "Giuliani",
        "username" : "user224",
        "age" : 52,
        "email" : "Daniele.Giuliani@gmail.com",
        "bloodType" : "A-",
        "id_num" : "815466641050",
        "registerDate" : ISODate("2008-08-18T15:11:54.533Z"),
        "ticketNumber" : 7454,
        "jobs" : [
                "Música"
        ],
        "favFruits" : [
                "Pêssego",
                "Banana",
                "Banana"
        ],
        "movies" : [
                {
                        "title" : "Interestelar (2014)",
                        "rating" : 1
                },
                {
                        "title" : "12 Homens e uma Sentença (1957)",
                        "rating" : 3.94
                },
                {
                        "title" : "O Poderoso Chefão II (1974)",
                        "rating" : 2.47
                }
        ],
        "mother" : {
                "firstname" : "Elisa",
                "surname" : "Giuliani",
                "age" : 78
        },
        "dog" : {
                "name" : "Paola",
                "age" : 12
        }
}
{
        "_id" : ObjectId("5e8a31722c71b99c0f203ebe"),
        "firstname" : "Eleonora",
        "surname" : "Lombardo",
        "username" : "user238",
        "age" : 56,
        "email" : "Eleonora.Lombardo@hotmail.com",
        "bloodType" : "AB+",
        "id_num" : "065001746574",
        "registerDate" : ISODate("2012-08-06T00:14:33.059Z"),
        "ticketNumber" : 798,
        "jobs" : [
                "Gestão da Qualidade"
        ],
        "favFruits" : [
                "Maçã",
                "Goiaba",
                "Banana"
        ],
        "movies" : [
                {
                        "title" : "Parasita (2019)",
                        "rating" : 1.98
                }
        ],
        "dog" : {
                "name" : "Tiziana",
                "age" : 13
        }
}
{
        "_id" : ObjectId("5e8a31722c71b99c0f203ec0"),
        "firstname" : "Cristina",
        "surname" : "Greco",
        "username" : "user240",
        "age" : 44,
        "email" : "Cristina.Greco@live.com",
        "bloodType" : "AB+",
        "id_num" : "187784377386",
        "registerDate" : ISODate("2011-06-21T04:00:57.586Z"),
        "ticketNumber" : 4882,
        "jobs" : [
                "Produção Multimídia"
        ],
        "favFruits" : [
                "Maçã",
                "Tangerina",
                "Banana"
        ],
        "movies" : [
                {
                        "title" : "12 Homens e uma Sentença (1957)",
                        "rating" : 1.68
                },
                {
                        "title" : "Os Bons Companheiros (1990)",
                        "rating" : 2.03
                },
                {
                        "title" : "Seven: Os Sete Crimes Capitais (1995)",
                        "rating" : 3.24
                }
        ],
        "cat" : {
                "name" : "Monica",
                "age" : 0
        }
}
{
        "_id" : ObjectId("5e8a31722c71b99c0f203ec7"),
        "firstname" : "Elena",
        "surname" : "Ruggiero",
        "username" : "user247",
        "age" : 34,
        "email" : "Elena.Ruggiero@hotmail.com",
        "bloodType" : "B-",
        "id_num" : "554605780383",
        "registerDate" : ISODate("2013-08-19T06:14:33.470Z"),
        "ticketNumber" : 8074,
        "jobs" : [
                "Radiologia",
                "Agroecologia"
        ],
        "favFruits" : [
                "Melancia",
                "Mamão",
                "Maçã"
        ],
        "movies" : [
                {
                        "title" : "Três Homens em Conflito (1966)",
                        "rating" : 3.42
                },
                {
                        "title" : "O Resgate do Soldado Ryan (1998)",
                        "rating" : 1.7
                }
        ],
        "mother" : {
                "firstname" : "Carlo",
                "surname" : "Ruggiero",
                "age" : 66
        },
        "father" : {
                "firstname" : "Pietro",
                "surname" : "Ruggiero",
                "age" : 62
        },
        "cat" : {
                "name" : "Filipo",
                "age" : 0
        },
        "dog" : {
                "name" : "Valentina",
                "age" : 13
        }
}


Exercício 3 - Stockbrokers

1. Liste as ações com profit acima de 0.5 (limite a 10 o resultado)

> db.stocks.find({"Profit Margin" : { $gt: 0.5 }}).limit(10).pretty()

{
        "_id" : ObjectId("52853800bb1177ca391c180f"),
        "Ticker" : "AB",
        "Profit Margin" : 0.896,
        "Institutional Ownership" : 0.368,
        "EPS growth past 5 years" : -0.348,
        "Total Debt/Equity" : 0,
        "Return on Assets" : 0.086,
        "Sector" : "Financial",
        "P/S" : 13.25,
        "Change from Open" : 0.0047,
        "Performance (YTD)" : 0.3227,
        "Performance (Week)" : -0.0302,
        "Insider Transactions" : 0.5973,
        "P/B" : 1.4,
        "EPS growth quarter over quarter" : 2.391,
        "Payout Ratio" : 1.75,
        "Performance (Quarter)" : 0.0929,
        "Forward P/E" : 12.58,
        "P/E" : 15.82,
        "200-Day Simple Moving Average" : 0.0159,
        "Shares Outstanding" : 92.26,
        "Earnings Date" : ISODate("2013-10-24T12:30:00Z"),
        "52-Week High" : -0.1859,
        "Change" : -0.0009,
        "Analyst Recom" : 3,
        "Volatility (Week)" : 0.0264,
        "Country" : "USA",
        "Return on Equity" : 0.087,
        "50-Day Low" : 0.123,
        "Price" : 21.5,
        "50-Day High" : -0.0574,
        "Return on Investment" : 0.033,
        "Shares Float" : 86.66,
        "Dividend Yield" : 0.0743,
        "EPS growth next 5 years" : 0.08,
        "Industry" : "Asset Management",
        "Beta" : 1.63,
        "Operating Margin" : 1,
        "EPS (ttm)" : 1.36,
        "PEG" : 1.98,
        "Float Short" : 0.0253,
        "52-Week Low" : 0.4687,
        "Average True Range" : 0.59,
        "EPS growth next year" : 0.0654,
        "Sales growth past 5 years" : -0.298,
        "Company" : "AllianceBernstein Holding L.P.",
        "Gap" : -0.0056,
        "Relative Volume" : 0.63,
        "Volatility (Month)" : 0.0298,
        "Market Cap" : 1985.39,
        "Volume" : 199677,
        "Short Ratio" : 6.3,
        "Performance (Half Year)" : -0.1159,
        "Relative Strength Index (14)" : 50.05,
        "Insider Ownership" : 0.002,
        "20-Day Simple Moving Average" : -0.007,
        "Performance (Month)" : 0.0847,
        "P/Free Cash Flow" : 93.21,
        "Institutional Transactions" : 0.0818,
        "Performance (Year)" : 0.3884,
        "LT Debt/Equity" : 0,
        "Average Volume" : 348.08,
        "EPS growth this year" : 1.567,
        "50-Day Simple Moving Average" : 0.0458
}
{
        "_id" : ObjectId("52853801bb1177ca391c1895"),
        "Ticker" : "AGNC",
        "Profit Margin" : 0.972,
        "Institutional Ownership" : 0.481,
        "EPS growth past 5 years" : -0.0107,
        "Total Debt/Equity" : 8.56,
        "Return on Assets" : 0.022,
        "Sector" : "Financial",
        "P/S" : 3.77,
        "Change from Open" : 0.0102,
        "Performance (YTD)" : -0.1652,
        "Performance (Week)" : -0.017,
        "Insider Transactions" : 0.4931,
        "P/B" : 0.86,
        "EPS growth quarter over quarter" : -8.2,
        "Payout Ratio" : 0.79,
        "Performance (Quarter)" : -0.0083,
        "Forward P/E" : 7.64,
        "P/E" : 3.68,
        "200-Day Simple Moving Average" : -0.1282,
        "Shares Outstanding" : 390.6,
        "Earnings Date" : ISODate("2013-10-28T20:30:00Z"),
        "52-Week High" : -0.2938,
        "P/Cash" : 3.93,
        "Change" : 0.0131,
        "Analyst Recom" : 2.6,
        "Volatility (Week)" : 0.0268,
        "Country" : "USA",
        "Return on Equity" : 0.205,
        "50-Day Low" : 0.0695,
        "Price" : 21.71,
        "50-Day High" : -0.1066,
        "Return on Investment" : 0.015,
        "Shares Float" : 383.97,
        "Dividend Yield" : 0.1493,
        "EPS growth next 5 years" : 0.035,
        "Industry" : "REIT - Residential",
        "Beta" : 0.51,
        "Sales growth quarter over quarter" : 0.073,
        "Operating Margin" : 0.67,
        "EPS (ttm)" : 5.82,
        "PEG" : 1.05,
        "Float Short" : 0.0311,
        "52-Week Low" : 0.1117,
        "Average True Range" : 0.52,
        "EPS growth next year" : -0.3603,
        "Company" : "American Capital Agency Corp.",
        "Gap" : 0.0028,
        "Relative Volume" : 0.71,
        "Volatility (Month)" : 0.02,
        "Market Cap" : 8370.56,
        "Volume" : 4576064,
        "Gross Margin" : 0.746,
        "Short Ratio" : 1.69,
        "Performance (Half Year)" : -0.2136,
        "Relative Strength Index (14)" : 43.53,
        "Insider Ownership" : 0.003,
        "20-Day Simple Moving Average" : -0.0318,
        "Performance (Month)" : -0.042,
        "Institutional Transactions" : 0.0077,
        "Performance (Year)" : -0.1503,
        "LT Debt/Equity" : 0,
        "Average Volume" : 7072.83,
        "EPS growth this year" : -0.169,
        "50-Day Simple Moving Average" : -0.0376
}
{
        "_id" : ObjectId("52853801bb1177ca391c1950"),
        "Ticker" : "ARCC",
        "Profit Margin" : 0.654,
        "Institutional Ownership" : 0.513,
        "EPS growth past 5 years" : 0.105,
        "Total Debt/Equity" : 0.59,
        "Return on Assets" : 0.08,
        "Sector" : "Financial",
        "P/S" : 5.87,
        "Change from Open" : 0.0105,
        "Performance (YTD)" : 0.0805,
        "Performance (Week)" : 0.0023,
        "P/B" : 1.08,
        "EPS growth quarter over quarter" : 0.22,
        "Payout Ratio" : 0.714,
        "Performance (Quarter)" : 0.0548,
        "Forward P/E" : 10.69,
        "P/E" : 8.32,
        "200-Day Simple Moving Average" : 0.046,
        "Shares Outstanding" : 266.17,
        "Earnings Date" : ISODate("2013-11-05T13:30:00Z"),
        "52-Week High" : -0.0014,
        "P/Cash" : 46.93,
        "Change" : 0.0082,
        "Analyst Recom" : 2,
        "Volatility (Week)" : 0.0129,
        "Country" : "USA",
        "Return on Equity" : 0.13,
        "50-Day Low" : 0.0527,
        "Price" : 17.86,
        "50-Day High" : -0.0014,
        "Return on Investment" : 0.056,
        "Shares Float" : 279.11,
        "Dividend Yield" : 0.0858,
        "EPS growth next 5 years" : 0.08,
        "Industry" : "Diversified Investments",
        "Beta" : 1.62,
        "Sales growth quarter over quarter" : 0.16,
        "Operating Margin" : 0.485,
        "EPS (ttm)" : 2.13,
        "PEG" : 1.04,
        "Float Short" : 0.0146,
        "52-Week Low" : 0.2192,
        "Average True Range" : 0.21,
        "EPS growth next year" : 0.0209,
        "Sales growth past 5 years" : 0.317,
        "Company" : "Ares Capital Corporation",
        "Gap" : -0.0023,
        "Relative Volume" : 0.68,
        "Volatility (Month)" : 0.0109,
        "Market Cap" : 4716.6,
        "Volume" : 938330,
        "Gross Margin" : 0.528,
        "Short Ratio" : 2.68,
        "Performance (Half Year)" : 0.0267,
        "Relative Strength Index (14)" : 61.2,
        "20-Day Simple Moving Average" : 0.0211,
        "Performance (Month)" : 0.0381,
        "Institutional Transactions" : 0.0183,
        "Performance (Year)" : 0.1574,
        "LT Debt/Equity" : 0,
        "Average Volume" : 1522.64,
        "EPS growth this year" : 0.417,
        "50-Day Simple Moving Average" : 0.0272
}
{
        "_id" : ObjectId("52853801bb1177ca391c195a"),
        "Ticker" : "ARI",
        "Profit Margin" : 0.576,
        "Institutional Ownership" : 0.631,
        "EPS growth past 5 years" : 0.1829,
        "Total Debt/Equity" : 0.28,
        "Return on Assets" : 0.046,
        "Sector" : "Financial",
        "P/S" : 9.35,
        "Change from Open" : 0.0214,
        "Performance (YTD)" : 0.0803,
        "Performance (Week)" : -0.0055,
        "Insider Transactions" : -0.0353,
        "P/B" : 0.89,
        "EPS growth quarter over quarter" : -0.413,
        "Payout Ratio" : 1.159,
        "Performance (Quarter)" : 0.0861,
        "Forward P/E" : 9.57,
        "P/E" : 11.88,
        "200-Day Simple Moving Average" : 0.0497,
        "Shares Outstanding" : 37.37,
        "Earnings Date" : ISODate("2013-11-04T21:30:00Z"),
        "52-Week High" : -0.0404,
        "P/Cash" : 3.88,
        "Change" : 0.024,
        "Analyst Recom" : 2.1,
        "Volatility (Week)" : 0.0135,
        "Country" : "USA",
        "Return on Equity" : 0.064,
        "50-Day Low" : 0.1598,
        "Price" : 16.67,
        "50-Day High" : 0.0109,
        "Return on Investment" : 0.044,
        "Shares Float" : 36.7,
        "Dividend Yield" : 0.0983,
        "EPS growth next 5 years" : 0.025,
        "Industry" : "REIT - Diversified",
        "Beta" : 0.55,
        "Sales growth quarter over quarter" : 0.309,
        "Operating Margin" : 0.682,
        "EPS (ttm)" : 1.37,
        "PEG" : 4.75,
        "Float Short" : 0.0182,
        "52-Week Low" : 0.2179,
        "Average True Range" : 0.24,
        "EPS growth next year" : 0.1739,
        "Company" : "Apollo Commercial Real Estate Finance, Inc.",
        "Gap" : 0.0025,
        "Relative Volume" : 1.48,
        "Volatility (Month)" : 0.0152,
        "Market Cap" : 608.45,
        "Volume" : 299352,
        "Gross Margin" : 0.919,
        "Short Ratio" : 3.01,
        "Performance (Half Year)" : -0.0502,
        "Relative Strength Index (14)" : 68.71,
        "Insider Ownership" : 0.004,
        "20-Day Simple Moving Average" : 0.0331,
        "Performance (Month)" : 0.0376,
        "P/Free Cash Flow" : 126.76,
        "Institutional Transactions" : 0.0318,
        "Performance (Year)" : 0.1259,
        "LT Debt/Equity" : 0.28,
        "Average Volume" : 222.35,
        "EPS growth this year" : 0.193,
        "50-Day Simple Moving Average" : 0.0673
}
{
        "_id" : ObjectId("52853801bb1177ca391c1968"),
        "Ticker" : "ARR",
        "Profit Margin" : 0.848,
        "Institutional Ownership" : 0.318,
        "EPS growth past 5 years" : 0.813,
        "Total Debt/Equity" : 8.92,
        "Return on Assets" : 0.031,
        "Sector" : "Financial",
        "P/S" : 1.7,
        "Change from Open" : 0.0223,
        "Performance (YTD)" : -0.2821,
        "Performance (Week)" : -0.0025,
        "Insider Transactions" : 0.2313,
        "P/B" : 0.68,
        "Payout Ratio" : 0.474,
        "Performance (Quarter)" : -0.0195,
        "Forward P/E" : 6.79,
        "P/E" : 1.88,
        "200-Day Simple Moving Average" : -0.1454,
        "Shares Outstanding" : 372.59,
        "Earnings Date" : ISODate("2013-10-28T04:00:00Z"),
        "52-Week High" : -0.3453,
        "P/Cash" : 1.87,
        "Change" : 0.0249,
        "Analyst Recom" : 2.6,
        "Volatility (Week)" : 0.024,
        "Country" : "USA",
        "Return on Equity" : 0.308,
        "50-Day Low" : 0.0728,
        "Price" : 4.12,
        "50-Day High" : -0.0678,
        "Return on Investment" : 0.011,
        "Shares Float" : 366.32,
        "Dividend Yield" : 0.1493,
        "EPS growth next 5 years" : -0.049,
        "Industry" : "REIT - Residential",
        "Beta" : 0.3,
        "Operating Margin" : 0.858,
        "EPS (ttm)" : 2.14,
        "Float Short" : 0.0415,
        "52-Week Low" : 0.1495,
        "Average True Range" : 0.09,
        "EPS growth next year" : -0.0878,
        "Company" : "ARMOUR Residential REIT, Inc.",
        "Gap" : 0.0025,
        "Relative Volume" : 1.37,
        "Volatility (Month)" : 0.0218,
        "Market Cap" : 1497.82,
        "Volume" : 6608855,
        "Short Ratio" : 2.87,
        "Performance (Half Year)" : -0.2651,
        "Relative Strength Index (14)" : 51.26,
        "Insider Ownership" : 0.002,
        "20-Day Simple Moving Average" : -0.0024,
        "Performance (Month)" : -0.0099,
        "P/Free Cash Flow" : 10.46,
        "Institutional Transactions" : 0.0016,
        "Performance (Year)" : -0.286,
        "LT Debt/Equity" : 0,
        "Average Volume" : 5299,
        "EPS growth this year" : 7.533,
        "50-Day Simple Moving Average" : 0.0048
}
{
        "_id" : ObjectId("52853801bb1177ca391c1998"),
        "Ticker" : "ATHL",
        "Profit Margin" : 0.732,
        "Institutional Ownership" : 0.753,
        "EPS growth past 5 years" : 0,
        "Total Debt/Equity" : 1.81,
        "Current Ratio" : 0.5,
        "Return on Assets" : 0.218,
        "Sector" : "Basic Materials",
        "P/S" : 10.42,
        "Change from Open" : 0.0088,
        "Performance (YTD)" : 0.1851,
        "Performance (Week)" : 0.1049,
        "Quick Ratio" : 0.5,
        "Insider Transactions" : -0.2682,
        "P/B" : 7.24,
        "EPS growth quarter over quarter" : -0.566,
        "Payout Ratio" : 0,
        "Performance (Quarter)" : 0.2007,
        "Forward P/E" : 27.38,
        "P/E" : 28.16,
        "200-Day Simple Moving Average" : 0.0877,
        "Shares Outstanding" : 66.34,
        "Earnings Date" : ISODate("2013-11-11T21:30:00Z"),
        "52-Week High" : -0.0439,
        "P/Cash" : 866.67,
        "Change" : 0.0126,
        "Analyst Recom" : 2.3,
        "Volatility (Week)" : 0.0678,
        "Country" : "USA",
        "Return on Equity" : 0.528,
        "50-Day Low" : 0.2479,
        "Price" : 33.07,
        "50-Day High" : -0.0439,
        "Return on Investment" : 0.08,
        "Shares Float" : 76.13,
        "EPS growth next 5 years" : 0.5,
        "Industry" : "Independent Oil & Gas",
        "Sales growth quarter over quarter" : 0.964,
        "Operating Margin" : 0.394,
        "EPS (ttm)" : 1.16,
        "PEG" : 0.56,
        "Float Short" : 0.0046,
        "52-Week Low" : 0.3097,
        "Average True Range" : 1.53,
        "EPS growth next year" : 0.6013,
        "Company" : "Athlon Energy Inc.",
        "Gap" : 0.0037,
        "Relative Volume" : 0.59,
        "Volatility (Month)" : 0.0464,
        "Market Cap" : 2166.66,
        "Volume" : 177265,
        "Gross Margin" : 0.791,
        "Short Ratio" : 1.07,
        "Relative Strength Index (14)" : 56.58,
        "Insider Ownership" : 0.09,
        "20-Day Simple Moving Average" : 0.0373,
        "Performance (Month)" : 0.0102,
        "LT Debt/Equity" : 1.81,
        "Average Volume" : 330.36,
        "EPS growth this year" : 0,
        "50-Day Simple Moving Average" : 0.0476
}
{
        "_id" : ObjectId("52853801bb1177ca391c19f6"),
        "Ticker" : "AYR",
        "Profit Margin" : 0.548,
        "Institutional Ownership" : 0.745,
        "EPS growth past 5 years" : -0.228,
        "Total Debt/Equity" : 2.08,
        "Return on Assets" : 0.066,
        "Sector" : "Services",
        "P/S" : 1.92,
        "Change from Open" : 0.0058,
        "Performance (YTD)" : 0.5577,
        "Performance (Week)" : -0.0032,
        "Insider Transactions" : -0.0052,
        "P/B" : 0.83,
        "EPS growth quarter over quarter" : -0.656,
        "Payout Ratio" : 0.123,
        "Performance (Quarter)" : 0.1566,
        "Forward P/E" : 10.45,
        "P/E" : 126.07,
        "200-Day Simple Moving Average" : 0.2063,
        "Shares Outstanding" : 70.35,
        "Earnings Date" : ISODate("2013-10-31T12:30:00Z"),
        "52-Week High" : -0.0257,
        "P/Cash" : 5.58,
        "Change" : 0.0042,
        "Analyst Recom" : 2.6,
        "Volatility (Week)" : 0.0202,
        "Country" : "USA",
        "Return on Equity" : 0.257,
        "50-Day Low" : 0.1304,
        "Price" : 18.99,
        "50-Day High" : -0.0257,
        "Return on Investment" : 0.007,
        "Shares Float" : 64.67,
        "Dividend Yield" : 0.0349,
        "EPS growth next 5 years" : 0.292,
        "Industry" : "Rental & Leasing Services",
        "Beta" : 2.07,
        "Sales growth quarter over quarter" : -0.016,
        "Operating Margin" : 0.457,
        "EPS (ttm)" : 0.15,
        "PEG" : 4.32,
        "Float Short" : 0.0327,
        "52-Week Low" : 0.8106,
        "Average True Range" : 0.37,
        "EPS growth next year" : 0.4873,
        "Sales growth past 5 years" : 0.125,
        "Company" : "Aircastle LTD",
        "Gap" : -0.0016,
        "Relative Volume" : 0.39,
        "Volatility (Month)" : 0.0193,
        "Market Cap" : 1330.3,
        "Volume" : 200382,
        "Short Ratio" : 3.78,
        "Performance (Half Year)" : 0.2295,
        "Relative Strength Index (14)" : 58.67,
        "Insider Ownership" : 0.008,
        "20-Day Simple Moving Average" : 0.0054,
        "Performance (Month)" : 0.0849,
        "P/Free Cash Flow" : 3.39,
        "Institutional Transactions" : -0.0268,
        "Performance (Year)" : 0.7493,
        "LT Debt/Equity" : 2.08,
        "Average Volume" : 559.42,
        "EPS growth this year" : -0.72,
        "50-Day Simple Moving Average" : 0.0545
}
{
        "_id" : ObjectId("52853801bb1177ca391c1a97"),
        "Ticker" : "BK",
        "Profit Margin" : 0.63,
        "Institutional Ownership" : 0.826,
        "EPS growth past 5 years" : -0.03,
        "Total Debt/Equity" : 0.53,
        "Return on Assets" : 0.006,
        "Sector" : "Financial",
        "P/S" : 11.32,
        "Change from Open" : -0.0015,
        "Performance (YTD)" : 0.3095,
        "Performance (Week)" : 0.0195,
        "Insider Transactions" : -0.1546,
        "P/B" : 1.07,
        "EPS growth quarter over quarter" : 0.344,
        "Payout Ratio" : 0.304,
        "Performance (Quarter)" : 0.0898,
        "Forward P/E" : 13.19,
        "P/E" : 18.03,
        "200-Day Simple Moving Average" : 0.127,
        "Shares Outstanding" : 1148.72,
        "Earnings Date" : ISODate("2013-10-16T12:30:00Z"),
        "52-Week High" : -0.0069,
        "P/Cash" : 0.22,
        "Change" : 0.003,
        "Analyst Recom" : 2.7,
        "Volatility (Week)" : 0.0216,
        "Country" : "USA",
        "Return on Equity" : 0.06,
        "50-Day Low" : 0.1255,
        "Price" : 33.1,
        "50-Day High" : -0.0069,
        "Return on Investment" : 0.042,
        "Shares Float" : 1146.23,
        "Dividend Yield" : 0.0182,
        "EPS growth next 5 years" : 0.066,
        "Industry" : "Asset Management",
        "Beta" : 1.16,
        "Sales growth quarter over quarter" : -0.025,
        "EPS (ttm)" : 1.83,
        "PEG" : 2.73,
        "Float Short" : 0.0125,
        "52-Week Low" : 0.4512,
        "Average True Range" : 0.54,
        "EPS growth next year" : 0.096,
        "Sales growth past 5 years" : -0.092,
        "Company" : "The Bank of New York Mellon Corporation",
        "Gap" : 0.0045,
        "Relative Volume" : 0.61,
        "Volatility (Month)" : 0.0155,
        "Market Cap" : 37907.89,
        "Volume" : 2578576,
        "Short Ratio" : 3.1,
        "Performance (Half Year)" : 0.1156,
        "Relative Strength Index (14)" : 63.27,
        "Insider Ownership" : 0.001,
        "20-Day Simple Moving Average" : 0.032,
        "Performance (Month)" : 0.0749,
        "Institutional Transactions" : 0.0015,
        "Performance (Year)" : 0.4019,
        "LT Debt/Equity" : 0.53,
        "Average Volume" : 4611.68,
        "EPS growth this year" : 0,
        "50-Day Simple Moving Average" : 0.0626
}
{
        "_id" : ObjectId("52853801bb1177ca391c1abd"),
        "Ticker" : "BLX",
        "Profit Margin" : 0.588,
        "Institutional Ownership" : 0.281,
        "EPS growth past 5 years" : 0.045,
        "Total Debt/Equity" : 3.73,
        "Return on Assets" : 0.017,
        "Sector" : "Financial",
        "P/S" : 5.22,
        "Change from Open" : 0.0103,
        "Performance (YTD)" : 0.2812,
        "Performance (Week)" : -0.0131,
        "P/B" : 1.19,
        "EPS growth quarter over quarter" : -0.506,
        "Payout Ratio" : 0.372,
        "Performance (Quarter)" : 0.0597,
        "Forward P/E" : 9.32,
        "P/E" : 13.01,
        "200-Day Simple Moving Average" : 0.1134,
        "Shares Outstanding" : 38.22,
        "Earnings Date" : ISODate("2013-10-16T12:30:00Z"),
        "52-Week High" : -0.0161,
        "P/Cash" : 1.71,
        "Change" : 0.0095,
        "Analyst Recom" : 1.7,
        "Volatility (Week)" : 0.023,
        "Country" : "Panama",
        "Return on Equity" : 0.137,
        "50-Day Low" : 0.1075,
        "Price" : 26.54,
        "50-Day High" : -0.0161,
        "Return on Investment" : 0.027,
        "Shares Float" : 29.25,
        "Dividend Yield" : 0.0456,
        "EPS growth next 5 years" : 0.0698,
        "Industry" : "Foreign Money Center Banks",
        "Beta" : 1.19,
        "Sales growth quarter over quarter" : 0,
        "Operating Margin" : 0.809,
        "EPS (ttm)" : 2.02,
        "PEG" : 1.86,
        "Float Short" : 0.0296,
        "52-Week Low" : 0.366,
        "Average True Range" : 0.49,
        "EPS growth next year" : 0.2192,
        "Sales growth past 5 years" : -0.062,
        "Company" : "Banco Latinoamericano de Comercio Exterior, S.A",
        "Gap" : -0.0008,
        "Relative Volume" : 1.05,
        "Volatility (Month)" : 0.0205,
        "Market Cap" : 1004.75,
        "Volume" : 102478,
        "Short Ratio" : 8.07,
        "Performance (Half Year)" : 0.1597,
        "Relative Strength Index (14)" : 60.34,
        "Insider Ownership" : 0.0706,
        "20-Day Simple Moving Average" : 0.0098,
        "Performance (Month)" : 0.0554,
        "P/Free Cash Flow" : 56.77,
        "Institutional Transactions" : 0.0149,
        "Performance (Year)" : 0.2983,
        "LT Debt/Equity" : 1.91,
        "Average Volume" : 107.45,
        "EPS growth this year" : 0.098,
        "50-Day Simple Moving Average" : 0.0498
}
{
        "_id" : ObjectId("52853801bb1177ca391c1af0"),
        "Ticker" : "BPO",
        "Profit Margin" : 0.503,
        "Institutional Ownership" : 0.958,
        "EPS growth past 5 years" : 0.354,
        "Total Debt/Equity" : 1.15,
        "Current Ratio" : 1,
        "Return on Assets" : 0.043,
        "Sector" : "Financial",
        "P/S" : 4.04,
        "Change from Open" : 0.001,
        "Performance (YTD)" : 0.1519,
        "Performance (Week)" : -0.0052,
        "Quick Ratio" : 1,
        "P/B" : 0.9,
        "EPS growth quarter over quarter" : -0.415,
        "Payout Ratio" : 0.235,
        "Performance (Quarter)" : 0.1825,
        "Forward P/E" : 18.74,
        "P/E" : 8.65,
        "200-Day Simple Moving Average" : 0.1124,
        "Shares Outstanding" : 505,
        "Earnings Date" : ISODate("2011-02-11T13:30:00Z"),
        "52-Week High" : -0.022,
        "P/Cash" : 22.13,
        "Change" : 0.0021,
        "Analyst Recom" : 3.1,
        "Volatility (Week)" : 0.0127,
        "Country" : "USA",
        "Return on Equity" : 0.115,
        "50-Day Low" : 0.1976,
        "Price" : 19.15,
        "50-Day High" : -0.022,
        "Return on Investment" : 0.015,
        "Shares Float" : 504.86,
        "Dividend Yield" : 0.0293,
        "EPS growth next 5 years" : 0.0735,
        "Industry" : "Property Management",
        "Beta" : 1.64,
        "Sales growth quarter over quarter" : 0.01,
        "Operating Margin" : 0.552,
        "EPS (ttm)" : 2.21,
        "PEG" : 1.18,
        "Float Short" : 0.0062,
        "52-Week Low" : 0.2728,
        "Average True Range" : 0.23,
        "EPS growth next year" : -0.105,
        "Sales growth past 5 years" : -0.043,
        "Company" : "Brookfield Properties Corporation",
        "Gap" : 0.001,
        "Relative Volume" : 0.17,
        "Volatility (Month)" : 0.0112,
        "Market Cap" : 9650.55,
        "Volume" : 249482,
        "Gross Margin" : 0.621,
        "Short Ratio" : 1.9,
        "Performance (Half Year)" : 0.0269,
        "Relative Strength Index (14)" : 62.08,
        "Insider Ownership" : 0.4972,
        "20-Day Simple Moving Average" : 0.012,
        "Performance (Month)" : 0.0154,
        "Institutional Transactions" : -0.004,
        "Performance (Year)" : 0.2482,
        "LT Debt/Equity" : 1.15,
        "Average Volume" : 1650.73,
        "EPS growth this year" : -0.212,
        "50-Day Simple Moving Average" : 0.0538
}

2. Liste as ações com perdas (limite a 10 novamente)

> db.stocks.find({"Profit Margin" : { $lt: 0}}).limit(10).pretty()


{
        "_id" : ObjectId("52853800bb1177ca391c1806"),
        "Ticker" : "AAOI",
        "Profit Margin" : -0.023,
        "Institutional Ownership" : 0.114,
        "EPS growth past 5 years" : 0,
        "Current Ratio" : 1.5,
        "Return on Assets" : -0.048,
        "Sector" : "Technology",
        "P/S" : 2.3,
        "Change from Open" : -0.0215,
        "Performance (YTD)" : 0.2671,
        "Performance (Week)" : -0.0381,
        "Quick Ratio" : 0.9,
        "EPS growth quarter over quarter" : -1,
        "Forward P/E" : 12.77,
        "200-Day Simple Moving Average" : 0.0654,
        "Shares Outstanding" : 12.6,
        "52-Week High" : -0.0904,
        "P/Cash" : 16.23,
        "Change" : -0.0269,
        "Analyst Recom" : 1.8,
        "Volatility (Week)" : 0.0377,
        "Country" : "USA",
        "Return on Equity" : 0.043,
        "50-Day Low" : 0.3539,
        "Price" : 12.28,
        "50-Day High" : -0.0904,
        "Return on Investment" : -0.004,
        "Shares Float" : 11.46,
        "Industry" : "Semiconductor - Integrated Circuits",
        "Sales growth quarter over quarter" : 0.256,
        "Operating Margin" : -0.007,
        "EPS (ttm)" : -0.13,
        "Float Short" : 0.0011,
        "52-Week Low" : 0.3539,
        "Average True Range" : 0.63,
        "EPS growth next year" : 38.52,
        "Company" : "Applied Optoelectronics, Inc.",
        "Gap" : -0.0055,
        "Relative Volume" : 0.12,
        "Volatility (Month)" : 0.0608,
        "Market Cap" : 159.06,
        "Volume" : 12203,
        "Gross Margin" : 0.292,
        "Short Ratio" : 0.12,
        "Insider Ownership" : 0.021,
        "20-Day Simple Moving Average" : -0.0251,
        "Performance (Month)" : 0.2397,
        "Average Volume" : 110.95,
        "EPS growth this year" : 0.833,
        "50-Day Simple Moving Average" : 0.0654
}
{
        "_id" : ObjectId("52853800bb1177ca391c180c"),
        "Ticker" : "AAV",
        "Profit Margin" : -0.232,
        "Institutional Ownership" : 0.58,
        "EPS growth past 5 years" : -0.265,
        "Total Debt/Equity" : 0.32,
        "Current Ratio" : 0.8,
        "Return on Assets" : -0.032,
        "Sector" : "Basic Materials",
        "P/S" : 2.64,
        "Change from Open" : 0.0286,
        "Performance (YTD)" : 0.1914,
        "Performance (Week)" : 0.0158,
        "Quick Ratio" : 0.8,
        "P/B" : 0.63,
        "EPS growth quarter over quarter" : 1.556,
        "Performance (Quarter)" : 0.0349,
        "200-Day Simple Moving Average" : 0.0569,
        "Shares Outstanding" : 168.38,
        "Earnings Date" : ISODate("2011-03-16T04:00:00Z"),
        "52-Week High" : -0.1242,
        "Change" : 0.0233,
        "Analyst Recom" : 2.7,
        "Volatility (Week)" : 0.0381,
        "Country" : "Canada",
        "Return on Equity" : -0.055,
        "50-Day Low" : 0.1127,
        "Price" : 3.95,
        "50-Day High" : -0.0436,
        "Return on Investment" : -0.068,
        "Shares Float" : 167.07,
        "Industry" : "Oil & Gas Drilling & Exploration",
        "Beta" : 2.05,
        "Sales growth quarter over quarter" : 0.399,
        "Operating Margin" : 0.102,
        "EPS (ttm)" : -0.34,
        "Float Short" : 0.0008,
        "52-Week Low" : 0.4158,
        "Average True Range" : 0.12,
        "EPS growth next year" : -0.667,
        "Sales growth past 5 years" : -0.121,
        "Company" : "Advantage Oil & Gas Ltd.",
        "Gap" : -0.0052,
        "Relative Volume" : 0.85,
        "Volatility (Month)" : 0.0303,
        "Market Cap" : 649.96,
        "Volume" : 116750,
        "Gross Margin" : 0.682,
        "Short Ratio" : 0.89,
        "Performance (Half Year)" : 0.0078,
        "Relative Strength Index (14)" : 52.62,
        "Insider Ownership" : 0.0025,
        "20-Day Simple Moving Average" : -0.0001,
        "Performance (Month)" : 0.0158,
        "Institutional Transactions" : 0.0402,
        "Performance (Year)" : 0.1386,
        "LT Debt/Equity" : 0.32,
        "Average Volume" : 149.81,
        "EPS growth this year" : 0.42,
        "50-Day Simple Moving Average" : 0.023
}
{
        "_id" : ObjectId("52853800bb1177ca391c1817"),
        "Ticker" : "ABFS",
        "Profit Margin" : -0.005,
        "Institutional Ownership" : 0.921,
        "EPS growth past 5 years" : -0.164,
        "Total Debt/Equity" : 0.31,
        "Current Ratio" : 1.3,
        "Return on Assets" : -0.01,
        "Sector" : "Services",
        "P/S" : 0.37,
        "Change from Open" : -0.006,
        "Performance (YTD)" : 2.3474,
        "Performance (Week)" : 0.1949,
        "Quick Ratio" : 1.3,
        "Insider Transactions" : 0.1293,
        "P/B" : 1.69,
        "EPS growth quarter over quarter" : -0.591,
        "Performance (Quarter)" : 0.3813,
        "Forward P/E" : 18.66,
        "200-Day Simple Moving Average" : 0.6449,
        "Shares Outstanding" : 25.69,
        "Earnings Date" : ISODate("2013-11-11T13:30:00Z"),
        "52-Week High" : -0.0166,
        "P/Cash" : 6.87,
        "Change" : -0.0082,
        "Analyst Recom" : 2.8,
        "Volatility (Week)" : 0.0625,
        "Country" : "USA",
        "Return on Equity" : -0.022,
        "50-Day Low" : 0.474,
        "Price" : 31.44,
        "50-Day High" : -0.0166,
        "Return on Investment" : -0.008,
        "Shares Float" : 24.3,
        "Dividend Yield" : 0.0038,
        "EPS growth next 5 years" : 0.1,
        "Industry" : "Trucking",
        "Beta" : 1.91,
        "Sales growth quarter over quarter" : 0.13,
        "Operating Margin" : -0.006,
        "EPS (ttm)" : -0.4,
        "Float Short" : 0.1176,
        "52-Week Low" : 3.9271,
        "Average True Range" : 1.58,
        "EPS growth next year" : 7.0142,
        "Sales growth past 5 years" : 0.024,
        "Company" : "Arkansas Best Corporation",
        "Gap" : -0.0022,
        "Relative Volume" : 0.73,
        "Volatility (Month)" : 0.0537,
        "Market Cap" : 814.5,
        "Volume" : 351906,
        "Gross Margin" : 0.212,
        "Short Ratio" : 5.44,
        "Performance (Half Year)" : 0.8592,
        "Relative Strength Index (14)" : 67.77,
        "Insider Ownership" : 0.034,
        "20-Day Simple Moving Average" : 0.1304,
        "Performance (Month)" : 0.3319,
        "P/Free Cash Flow" : 13.67,
        "Institutional Transactions" : 0.0328,
        "Performance (Year)" : 3.4336,
        "LT Debt/Equity" : 0.2,
        "Average Volume" : 525.42,
        "EPS growth this year" : -2.348,
        "50-Day Simple Moving Average" : 0.1974
}
{
        "_id" : ObjectId("52853800bb1177ca391c1815"),
        "Ticker" : "ABCD",
        "Profit Margin" : -0.645,
        "Institutional Ownership" : 0.186,
        "EPS growth past 5 years" : -0.195,
        "Current Ratio" : 1.4,
        "Return on Assets" : -0.416,
        "Sector" : "Services",
        "P/S" : 0.41,
        "Change from Open" : 0,
        "Performance (YTD)" : 0.2072,
        "Performance (Week)" : 0.0229,
        "Quick Ratio" : 1.2,
        "Insider Transactions" : -0.0267,
        "EPS growth quarter over quarter" : 1.022,
        "Performance (Quarter)" : -0.0496,
        "200-Day Simple Moving Average" : 0.0446,
        "Shares Outstanding" : 47.36,
        "Earnings Date" : ISODate("2013-11-07T21:30:00Z"),
        "52-Week High" : -0.2757,
        "P/Cash" : 1.37,
        "Change" : 0,
        "Analyst Recom" : 2,
        "Volatility (Week)" : 0.0737,
        "Country" : "USA",
        "Return on Equity" : 3.596,
        "50-Day Low" : 0.072,
        "Price" : 1.34,
        "50-Day High" : -0.2299,
        "Return on Investment" : -0.876,
        "Shares Float" : 15.11,
        "Industry" : "Education & Training Services",
        "Beta" : 1.7,
        "Sales growth quarter over quarter" : 0.059,
        "Operating Margin" : 0.048,
        "EPS (ttm)" : -2.06,
        "Float Short" : 0.0007,
        "52-Week Low" : 0.5952,
        "Average True Range" : 0.09,
        "Sales growth past 5 years" : 0.084,
        "Company" : "Cambium Learning Group, Inc.",
        "Gap" : 0,
        "Relative Volume" : 0.04,
        "Volatility (Month)" : 0.0584,
        "Market Cap" : 63.46,
        "Volume" : 1600,
        "Gross Margin" : 0.552,
        "Short Ratio" : 0.21,
        "Performance (Half Year)" : 0.1356,
        "Relative Strength Index (14)" : 48.07,
        "Insider Ownership" : 0.003,
        "20-Day Simple Moving Average" : 0.0037,
        "Performance (Month)" : -0.0074,
        "P/Free Cash Flow" : 2.47,
        "Institutional Transactions" : -0.095,
        "Performance (Year)" : 0.6543,
        "Average Volume" : 48.58,
        "EPS growth this year" : -1.533,
        "50-Day Simple Moving Average" : -0.064
}
{
        "_id" : ObjectId("52853800bb1177ca391c181b"),
        "Ticker" : "ABMC",
        "Profit Margin" : -0.0966,
        "Institutional Ownership" : 0.12,
        "EPS growth past 5 years" : 0,
        "Total Debt/Equity" : 0.63,
        "Current Ratio" : 1.74,
        "Return on Assets" : -0.1194,
        "Sector" : "Healthcare",
        "P/S" : 0.34,
        "Change from Open" : 0,
        "Performance (YTD)" : 0.3077,
        "Performance (Week)" : 0.1333,
        "Quick Ratio" : 0.57,
        "P/B" : 1,
        "EPS growth quarter over quarter" : -2.4252,
        "Performance (Quarter)" : 0,
        "200-Day Simple Moving Average" : 0.0413,
        "Shares Outstanding" : 21.74,
        "Earnings Date" : ISODate("2013-11-11T05:00:00Z"),
        "52-Week High" : -0.3929,
        "P/Cash" : 6.26,
        "Change" : 0,
        "Volatility (Week)" : 0.0695,
        "Country" : "USA",
        "Return on Equity" : -0.2455,
        "50-Day Low" : 1.4286,
        "Price" : 0.17,
        "50-Day High" : -0.0556,
        "Return on Investment" : -0.1961,
        "Shares Float" : 18.7,
        "Industry" : "Diagnostic Substances",
        "Beta" : 1.71,
        "Sales growth quarter over quarter" : -0.1896,
        "Operating Margin" : -0.0734,
        "EPS (ttm)" : -0.05,
        "Float Short" : 0.0003,
        "52-Week Low" : 1.4286,
        "Average True Range" : 0.02,
        "Sales growth past 5 years" : 0.0028,
        "Company" : "American Bio Medica Corp.",
        "Gap" : 0,
        "Relative Volume" : 0.04,
        "Volatility (Month)" : 0.0517,
        "Market Cap" : 3.7,
        "Volume" : 0,
        "Gross Margin" : 0.3916,
        "Short Ratio" : 0.43,
        "Performance (Half Year)" : 0.0625,
        "Relative Strength Index (14)" : 56.93,
        "Insider Ownership" : 0.14,
        "20-Day Simple Moving Average" : 0.1039,
        "Performance (Month)" : 0.2143,
        "Institutional Transactions" : -0.1183,
        "Performance (Year)" : -0.0556,
        "LT Debt/Equity" : 0.2,
        "Average Volume" : 13.73,
        "EPS growth this year" : 0.1416,
        "50-Day Simple Moving Average" : 0.1502
}
{
        "_id" : ObjectId("52853800bb1177ca391c1821"),
        "Ticker" : "ABX",
        "Profit Margin" : -0.769,
        "Institutional Ownership" : 0.739,
        "EPS growth past 5 years" : -0.206,
        "Total Debt/Equity" : 1.13,
        "Current Ratio" : 1.8,
        "Return on Assets" : -0.241,
        "Sector" : "Basic Materials",
        "P/S" : 1.32,
        "Change from Open" : -0.0019,
        "Performance (YTD)" : -0.4728,
        "Performance (Week)" : -0.0131,
        "Quick Ratio" : 1,
        "P/B" : 1.33,
        "EPS growth quarter over quarter" : -0.727,
        "Performance (Quarter)" : -0.084,
        "Forward P/E" : 8.19,
        "200-Day Simple Moving Average" : -0.1368,
        "Shares Outstanding" : 1001,
        "Earnings Date" : ISODate("2011-02-17T13:30:00Z"),
        "52-Week High" : -0.4877,
        "P/Cash" : 7.94,
        "Change" : 0.0014,
        "Analyst Recom" : 2.6,
        "Volatility (Week)" : 0.0202,
        "Country" : "Canada",
        "Return on Equity" : -0.592,
        "50-Day Low" : 0.0581,
        "Price" : 18.13,
        "50-Day High" : -0.121,
        "Return on Investment" : -0.017,
        "Shares Float" : 997.93,
        "Dividend Yield" : 0.011,
        "EPS growth next 5 years" : 0.02,
        "Industry" : "Gold",
        "Beta" : 0.46,
        "Sales growth quarter over quarter" : -0.122,
        "Operating Margin" : 0.366,
        "EPS (ttm)" : -10.08,
        "Float Short" : 0.0118,
        "52-Week Low" : 0.3525,
        "Average True Range" : 0.57,
        "EPS growth next year" : -0.16,
        "Sales growth past 5 years" : 0.193,
        "Company" : "Barrick Gold Corporation",
        "Gap" : 0.0033,
        "Relative Volume" : 1.09,
        "Volatility (Month)" : 0.0277,
        "Market Cap" : 18118.1,
        "Volume" : 17478164,
        "Gross Margin" : 0.444,
        "Short Ratio" : 0.67,
        "Performance (Half Year)" : -0.0479,
        "Relative Strength Index (14)" : 41.96,
        "20-Day Simple Moving Average" : -0.0436,
        "Performance (Month)" : 0.018,
        "Institutional Transactions" : 0.0315,
        "Performance (Year)" : -0.474,
        "LT Debt/Equity" : 1.07,
        "Average Volume" : 17602.98,
        "EPS growth this year" : -1.147,
        "50-Day Simple Moving Average" : -0.0239
}
{
        "_id" : ObjectId("52853800bb1177ca391c1826"),
        "Ticker" : "ACCL",
        "Profit Margin" : -0.014,
        "Institutional Ownership" : 0.911,
        "EPS growth past 5 years" : -0.421,
        "Total Debt/Equity" : 0,
        "Current Ratio" : 1.4,
        "Return on Assets" : -0.006,
        "Sector" : "Technology",
        "P/S" : 3.13,
        "Change from Open" : 0.0011,
        "Performance (YTD)" : 0.0331,
        "Performance (Week)" : 0.0108,
        "Quick Ratio" : 1.4,
        "Insider Transactions" : -0.1768,
        "P/B" : 2.1,
        "Performance (Quarter)" : 0.0331,
        "Forward P/E" : 24.35,
        "200-Day Simple Moving Average" : 0.0112,
        "Shares Outstanding" : 55.66,
        "Earnings Date" : ISODate("2013-10-30T20:30:00Z"),
        "52-Week High" : -0.071,
        "P/Cash" : 4.14,
        "Change" : -0.0064,
        "Analyst Recom" : 2.3,
        "Volatility (Week)" : 0.0189,
        "Country" : "USA",
        "Return on Equity" : -0.01,
        "50-Day Low" : 0.0322,
        "Price" : 9.29,
        "50-Day High" : -0.071,
        "Return on Investment" : -0.086,
        "Shares Float" : 55.4,
        "EPS growth next 5 years" : 0.2,
        "Industry" : "Application Software",
        "Beta" : 0.84,
        "Sales growth quarter over quarter" : 0.01,
        "Operating Margin" : -0.091,
        "EPS (ttm)" : -0.05,
        "Float Short" : 0.0179,
        "52-Week Low" : 0.1987,
        "Average True Range" : 0.21,
        "EPS growth next year" : 0.1294,
        "Sales growth past 5 years" : 0.153,
        "Company" : "Accelrys Inc.",
        "Gap" : -0.0075,
        "Relative Volume" : 0.31,
        "Volatility (Month)" : 0.0236,
        "Market Cap" : 520.42,
        "Volume" : 33912,
        "Gross Margin" : 0.679,
        "Short Ratio" : 8.32,
        "Performance (Half Year)" : 0.0872,
        "Relative Strength Index (14)" : 45.52,
        "Insider Ownership" : 0.0092,
        "20-Day Simple Moving Average" : -0.018,
        "Performance (Month)" : -0.0032,
        "Institutional Transactions" : 0.0133,
        "Performance (Year)" : 0.0747,
        "LT Debt/Equity" : 0,
        "Average Volume" : 118.95,
        "EPS growth this year" : -7.333,
        "50-Day Simple Moving Average" : -0.0226
}
{
        "_id" : ObjectId("52853800bb1177ca391c182b"),
        "Ticker" : "ACFC",
        "Profit Margin" : -0.18,
        "Institutional Ownership" : 0.079,
        "EPS growth past 5 years" : -0.524,
        "Total Debt/Equity" : 0,
        "Return on Assets" : -0.007,
        "Sector" : "Financial",
        "P/S" : 0.27,
        "Change from Open" : 0,
        "Performance (YTD)" : 0.6667,
        "Performance (Week)" : -0.1184,
        "P/B" : 0.27,
        "EPS growth quarter over quarter" : 0.483,
        "Performance (Quarter)" : -0.1321,
        "200-Day Simple Moving Average" : -0.2118,
        "Shares Outstanding" : 2.5,
        "Earnings Date" : ISODate("2013-11-04T05:00:00Z"),
        "52-Week High" : -0.4956,
        "P/Cash" : 0.1,
        "Change" : 0.0358,
        "Analyst Recom" : 3,
        "Volatility (Week)" : 0.0508,
        "Country" : "USA",
        "Return on Equity" : -0.147,
        "50-Day Low" : 0.081,
        "Price" : 3.47,
        "50-Day High" : -0.2078,
        "Return on Investment" : 0.161,
        "Shares Float" : 1.72,
        "Industry" : "Regional - Southeast Banks",
        "Beta" : 0.83,
        "Sales growth quarter over quarter" : -0.14,
        "Operating Margin" : -0.18,
        "EPS (ttm)" : -2.22,
        "Float Short" : 0.0085,
        "52-Week Low" : 1.3767,
        "Average True Range" : 0.12,
        "Sales growth past 5 years" : -0.096,
        "Company" : "Atlantic Coast Financial Corporation",
        "Gap" : 0.0358,
        "Relative Volume" : 0,
        "Volatility (Month)" : 0.0228,
        "Market Cap" : 8.39,
        "Volume" : 0,
        "Short Ratio" : 6.07,
        "Performance (Half Year)" : -0.3667,
        "Relative Strength Index (14)" : 40.71,
        "Insider Ownership" : 0.001,
        "20-Day Simple Moving Average" : -0.0742,
        "Performance (Month)" : -0.1138,
        "Institutional Transactions" : -4.3825,
        "Performance (Year)" : 0.7539,
        "LT Debt/Equity" : 0,
        "Average Volume" : 2.41,
        "EPS growth this year" : 0.354,
        "50-Day Simple Moving Average" : -0.0993
}
{
        "_id" : ObjectId("52853800bb1177ca391c182f"),
        "Ticker" : "ACH",
        "Profit Margin" : -0.051,
        "Institutional Ownership" : 0.02,
        "EPS growth past 5 years" : -0.227,
        "Total Debt/Equity" : 2.84,
        "Current Ratio" : 0.7,
        "Return on Assets" : -0.039,
        "Sector" : "Basic Materials",
        "P/S" : 0.19,
        "Change from Open" : -0.0032,
        "Performance (YTD)" : -0.2645,
        "Performance (Week)" : -0.0437,
        "Quick Ratio" : 0.7,
        "P/B" : 0.67,
        "EPS growth quarter over quarter" : 0.711,
        "Performance (Quarter)" : 0.0057,
        "200-Day Simple Moving Average" : -0.0544,
        "Shares Outstanding" : 540.98,
        "Earnings Date" : ISODate("2011-03-02T05:00:00Z"),
        "52-Week High" : -0.3369,
        "P/Cash" : 2.77,
        "Change" : 0.0059,
        "Analyst Recom" : 5,
        "Volatility (Week)" : 0.015,
        "Country" : "China",
        "Return on Equity" : -0.172,
        "50-Day Low" : 0.0176,
        "Price" : 8.81,
        "50-Day High" : -0.1117,
        "Return on Investment" : -0.029,
        "Shares Float" : 156.18,
        "Industry" : "Aluminum",
        "Beta" : 1.9,
        "Sales growth quarter over quarter" : 0.065,
        "Operating Margin" : -0.021,
        "EPS (ttm)" : -1.76,
        "Float Short" : 0.02,
        "52-Week Low" : 0.2154,
        "Average True Range" : 0.2,
        "EPS growth next year" : 0.487,
        "Sales growth past 5 years" : 0.119,
        "Company" : "Aluminum Corporation Of China Limited",
        "Gap" : 0.0091,
        "Relative Volume" : 1.05,
        "Volatility (Month)" : 0.0183,
        "Market Cap" : 4738.98,
        "Volume" : 78010,
        "Gross Margin" : 0.005,
        "Short Ratio" : 38.23,
        "Performance (Half Year)" : -0.124,
        "Relative Strength Index (14)" : 38.92,
        "20-Day Simple Moving Average" : -0.0477,
        "Performance (Month)" : -0.0405,
        "Institutional Transactions" : -0.0063,
        "Performance (Year)" : -0.1577,
        "LT Debt/Equity" : 1.19,
        "Average Volume" : 81.57,
        "EPS growth this year" : 0.839,
        "50-Day Simple Moving Average" : -0.0421
}
{
        "_id" : ObjectId("52853800bb1177ca391c1832"),
        "Ticker" : "ACI",
        "Profit Margin" : -0.173,
        "Institutional Ownership" : 0.662,
        "EPS growth past 5 years" : -0.361,
        "Total Debt/Equity" : 1.97,
        "Current Ratio" : 3.5,
        "Return on Assets" : -0.058,
        "Sector" : "Basic Materials",
        "P/S" : 0.28,
        "Change from Open" : -0.0372,
        "Performance (YTD)" : -0.4019,
        "Performance (Week)" : -0.0183,
        "Quick Ratio" : 3,
        "Insider Transactions" : 0.0178,
        "P/B" : 0.35,
        "EPS growth quarter over quarter" : -5.455,
        "Performance (Quarter)" : -0.0549,
        "200-Day Simple Moving Average" : -0.1177,
        "Shares Outstanding" : 212.11,
        "Earnings Date" : ISODate("2013-10-29T12:30:00Z"),
        "52-Week High" : -0.4702,
        "P/Cash" : 0.66,
        "Change" : -0.0372,
        "Analyst Recom" : 2.8,
        "Volatility (Week)" : 0.0516,
        "Country" : "USA",
        "Return on Equity" : -0.207,
        "50-Day Low" : 0.104,
        "Price" : 4.14,
        "50-Day High" : -0.2114,
        "Return on Investment" : -0.047,
        "Shares Float" : 209.56,
        "Dividend Yield" : 0.0279,
        "EPS growth next 5 years" : 0.05,
        "Industry" : "Industrial Metals & Minerals",
        "Beta" : 1.61,
        "Sales growth quarter over quarter" : -0.272,
        "Operating Margin" : -0.04,
        "EPS (ttm)" : -3.16,
        "Float Short" : 0.1772,
        "52-Week Low" : 0.1997,
        "Average True Range" : 0.23,
        "EPS growth next year" : 0.143,
        "Sales growth past 5 years" : 0.115,
        "Company" : "Arch Coal Inc.",
        "Gap" : 0,
        "Relative Volume" : 0.66,
        "Volatility (Month)" : 0.0546,
        "Market Cap" : 912.08,
        "Volume" : 5417562,
        "Gross Margin" : 0.141,
        "Short Ratio" : 4.12,
        "Performance (Half Year)" : -0.1224,
        "Relative Strength Index (14)" : 43.64,
        "Insider Ownership" : 0.0054,
        "20-Day Simple Moving Average" : -0.0171,
        "Performance (Month)" : 0.0437,
        "Institutional Transactions" : 0.0024,
        "Performance (Year)" : -0.3741,
        "LT Debt/Equity" : 1.97,
        "Average Volume" : 9000.5,
        "EPS growth this year" : -5.378,
        "50-Day Simple Moving Average" : -0.0482
}

3. Liste as 10 ações mais rentáveis

> db.stocks.find({"Profit Margin": { $exists: 1}}, {"Ticker" : 1, "Profit Margin" : 1}).sort( { "Profit Margin" : -1 } ).limit(10).pretty()

{
        "_id" : ObjectId("52853801bb1177ca391c1af3"),
        "Ticker" : "BPT",
        "Profit Margin" : 0.994
}
{
        "_id" : ObjectId("52853802bb1177ca391c1b69"),
        "Ticker" : "CACB",
        "Profit Margin" : 0.994
}
{
        "_id" : ObjectId("5285380bbb1177ca391c2c3c"),
        "Ticker" : "ROYT",
        "Profit Margin" : 0.99
}
{
        "_id" : ObjectId("52853808bb1177ca391c281b"),
        "Ticker" : "NDRO",
        "Profit Margin" : 0.986
}
{
        "_id" : ObjectId("5285380fbb1177ca391c318e"),
        "Ticker" : "WHZ",
        "Profit Margin" : 0.982
}
{
        "_id" : ObjectId("52853808bb1177ca391c27bd"),
        "Ticker" : "MVO",
        "Profit Margin" : 0.976
}
{
        "_id" : ObjectId("52853801bb1177ca391c1895"),
        "Ticker" : "AGNC",
        "Profit Margin" : 0.972
}
{
        "_id" : ObjectId("5285380ebb1177ca391c3101"),
        "Ticker" : "VOC",
        "Profit Margin" : 0.971
}
{
        "_id" : ObjectId("52853807bb1177ca391c279a"),
        "Ticker" : "MTR",
        "Profit Margin" : 0.97
}
{
        "_id" : ObjectId("52853809bb1177ca391c2946"),
        "Ticker" : "OLP",
        "Profit Margin" : 0.97
}

4. Qual foi o setor mais rentável?
> db.stocks.aggregate([ {$group: {_id: "$Sector", Média: {$avg: "$Profit Margin"}}}, {$sort: {Média: -1}}, {$limit: 1} ])

{ "_id" : "Financial", "Média" : 0.16467639311043566 }

5. Ordene as ações pelo profit e usando um cursor, liste as ações.
> var cursor = db.stocks.find({"Profit Margin": { $exists: 1}}, {"Ticker" : 1, "Profit Margin" : 1}).sort( { "Profit Margin" : -1 } )

> cursor
{ "_id" : ObjectId("52853801bb1177ca391c1af3"), "Ticker" : "BPT", "Profit Margin" : 0.994 }
{ "_id" : ObjectId("52853802bb1177ca391c1b69"), "Ticker" : "CACB", "Profit Margin" : 0.994 }
{ "_id" : ObjectId("5285380bbb1177ca391c2c3c"), "Ticker" : "ROYT", "Profit Margin" : 0.99 }
{ "_id" : ObjectId("52853808bb1177ca391c281b"), "Ticker" : "NDRO", "Profit Margin" : 0.986 }
{ "_id" : ObjectId("5285380fbb1177ca391c318e"), "Ticker" : "WHZ", "Profit Margin" : 0.982 }
{ "_id" : ObjectId("52853808bb1177ca391c27bd"), "Ticker" : "MVO", "Profit Margin" : 0.976 }
{ "_id" : ObjectId("52853801bb1177ca391c1895"), "Ticker" : "AGNC", "Profit Margin" : 0.972 }
{ "_id" : ObjectId("5285380ebb1177ca391c3101"), "Ticker" : "VOC", "Profit Margin" : 0.971 }
{ "_id" : ObjectId("52853807bb1177ca391c279a"), "Ticker" : "MTR", "Profit Margin" : 0.97 }
{ "_id" : ObjectId("52853809bb1177ca391c2946"), "Ticker" : "OLP", "Profit Margin" : 0.97 }
{ "_id" : ObjectId("52853809bb1177ca391c29c8"), "Ticker" : "PBT", "Profit Margin" : 0.97 }
{ "_id" : ObjectId("52853802bb1177ca391c1d1b"), "Ticker" : "CRT", "Profit Margin" : 0.969 }
{ "_id" : ObjectId("52853805bb1177ca391c22aa"), "Ticker" : "HCAP", "Profit Margin" : 0.967 }
{ "_id" : ObjectId("5285380fbb1177ca391c318d"), "Ticker" : "WHX", "Profit Margin" : 0.966 }
{ "_id" : ObjectId("52853807bb1177ca391c2779"), "Ticker" : "MSB", "Profit Margin" : 0.963 }
{ "_id" : ObjectId("5285380bbb1177ca391c2cbe"), "Ticker" : "SBR", "Profit Margin" : 0.959 }
{ "_id" : ObjectId("52853808bb1177ca391c28a3"), "Ticker" : "NRT", "Profit Margin" : 0.958 }
{ "_id" : ObjectId("5285380bbb1177ca391c2cfb"), "Ticker" : "SDR", "Profit Margin" : 0.933 }
{ "_id" : ObjectId("52853805bb1177ca391c22d4"), "Ticker" : "HGT", "Profit Margin" : 0.93 }
{ "_id" : ObjectId("5285380bbb1177ca391c2cfe"), "Ticker" : "SDT", "Profit Margin" : 0.928 }

6. Renomeie o campo “Profit Margin” para apenas “profit”.
> db.stocks.updateMany({"Profit Margin": { $exists: 1}}, {$rename: {"Profit Margin": "Profit"}})

{ "acknowledged" : true, "matchedCount" : 4302, "modifiedCount" : 4302 }

7. Agora liste apenas a empresa e seu respectivo resultado

> db.stocks.aggregate([{$project : {Company : 1, Profit : 1, _id : 0}}  ])

{ "Company" : "iShares MSCI AC Asia Information Tech" }
{ "Company" : "Alcoa, Inc.", "Profit" : 0.013 }
{ "Company" : "Agilent Technologies Inc.", "Profit" : 0.137 }
{ "Company" : "Altisource Asset Management Corporation" }
{ "Company" : "Applied Optoelectronics, Inc.", "Profit" : -0.023 }
{ "Company" : "Atlantic American Corp.", "Profit" : 0.056 }
{ "Company" : "Aaron's, Inc.", "Profit" : 0.06 }
{ "Company" : "AAON Inc.", "Profit" : 0.105 }
{ "Company" : "Advance Auto Parts Inc.", "Profit" : 0.063 }
{ "Company" : "WCM/BNY Mellon Focused Growth ADR ETF" }
{ "Company" : "Almaden Minerals Ltd." }
{ "Company" : "American Assets Trust, Inc.", "Profit" : 0.155 }
{ "Company" : "Advantage Oil & Gas Ltd.", "Profit" : -0.232 }
{ "Company" : "Apple Inc.", "Profit" : 0.217 }
{ "Company" : "iShares MSCI All Country Asia ex Jpn Idx" }
{ "Company" : "Atlas Air Worldwide Holdings Inc.", "Profit" : 0.071 }
{ "Company" : "AllianceBernstein Holding L.P.", "Profit" : 0.896 }
{ "Company" : "ABB Ltd.", "Profit" : 0.069 }
{ "Company" : "Abaxis Inc.", "Profit" : 0.1 }
{ "Company" : "AmerisourceBergen Corporation", "Profit" : 0.005 }

8. Analise as ações. É uma bola de cristal na sua mão... Quais as três ações
você investiria?

> db.stocks.find({"Profit": { $exists: 1}, "Analyst Recom": {$exists: 1}}, {"Ticker" : 1, "Profit" : 1, "Analyst Recom" : 1}).sort( { "Analyst Recom" : -1, "Profit": -1 } ).limit(3).pretty()
{
        "_id" : ObjectId("5285380dbb1177ca391c2f53"),
        "Ticker" : "TNH",
        "Analyst Recom" : 5,
        "Profit" : 0.398
}
{
        "_id" : ObjectId("5285380cbb1177ca391c2d6d"),
        "Ticker" : "SKBI",
        "Analyst Recom" : 5,
        "Profit" : 0.211
}
{
        "_id" : ObjectId("5285380fbb1177ca391c323f"),
        "Ticker" : "YZC",
        "Analyst Recom" : 5,
        "Profit" : 0.143
}

9. Liste as ações agrupadas por setor

> db.stocks.aggregate([{$group:{_id : "$Sector", Acoes : {$push: "$Ticker"}}}, ])

{ "_id" : "Basic Materials", "Acoes" : [ "AA", "AAU", "AAV", "ABX", "ACET", "ACH", "ACI", "ACMP", "ACO", "AE", "AEM", "AG", "AGI", "AGU", "AHGP", "AKG", "AKS", "ALB", "ALDW", "ALJ", "AMCF", "AMRS", "ANR", "ANV", "ANW", "APC", "APA", "APD", "APAGF", "APFC", "APL", "AR", "AREX", "ARLP", "ARG", "ARP", "ARSD", "ASM", "ASH", "ATHL", "ATL", "ATW", "AU", "AUMN", "AUQ", "AUY", "AVD", "AVL", "AWC", "AXAS", "AXLL", "AXX", "AZC", "AXU", "BAA", "BAK", "BAS", "BBEP", "BBG", "BBL", "BCEI", "BCPC", "BHI", "BHP", "BIOA", "BIOF", "BKEP", "BOLT", "BP", "BPL", "BPT", "BPZ", "BRD", "BRN", "BRY", "BTE", "BTU", "BVN", "BWP", "BXE", "CAK", "CAM", "CBT", "CCJ", "CDE", "CDY", "CE", "CENX", "CEO", "CERE", "CERP", "CEP", "CF", "CEQP", "CGG", "CGR", "CGA", "CHGS", "CHK", "CHKR", "CHMT", "CHNR", "CHOP", "CIE", "CJES", "CLB", "CLD", "CLF", "CLMT", "CLR", "CMC", "CMLP", "CMP", "CNQ", "CNX", "COG", "COP", "CPE", "CPSL", "CQP", "CRK", "CRR", "CRT", "CRZO", "CVE", "CVI", "CVRR", "CVX", "CWEI", "CXO", "CYT", "DBLE", "DD", "DDC", "DEJ", "DKL", "DK", "DNN", "DNR", "DO", "DOW", "DPM", "DRD", "DRQ", "DVN", "DVR", "DWSN", "E", "EC", "ECA", "ECT", "EEQ", "EEP", "EGI", "EGN", "EGO", "EGY", "EMES", "EMXX", "EMN", "ENB", "END", "EOG", "EOX", "EPB", "EPD", "EPL", "EPM", "EQM", "EQU", "ERF", "EROC", "ESTE", "ESV", "ETE", "ETP", "EVEP", "EXH", "EXK", "EXLP", "EXXI", "FANG", "FCX", "FES", "FET", "FF", "FGP", "FI", "FISH", "FMC", "FNV", "FOE", "FPP", "FRD", "FSI", "FSM", "FST", "FTI", "FTK", "FUL", "FXEN", "GBR", "GDP", "GEL", "GEVO", "GG", "GFI", "GGB", "GGS", "GLF", "GMET", "GMO", "GNI", "GNE", "GOLD", "GORO", "GPL", "GPRE", "GPOR", "GRA", "GSE", "GSI", "GSJK", "GSM", "GSS", "GST", "GSV", "GTE", "GTU", "GURE", "HAL", "HBM", "HCLP", "HDY", "HEP", "HERO", "HES", "HFC", "HGT", "HL", "HK", "HLX", "HMY", "HNR", "HNRG", "HOS", "HP", "HSC", "HUN", "HUSA", "HWKN", "IAG", "IFNY", "IFF", "IIIN", "IKNX", "IMO", "INT", "IOC", "IOSP", "IPHS", "IPI", "ISRL", "IVAN", "JONE", "JRCC", "KALU", "KBX", "KEG", "KGJI", "KGC", "KIOR", "KMG", "KMI", "KMR", "KMP", "KOG", "KOP", "KOS", "KRA", "KRO", "KWK", "KWR", "LEI", "LGCY", "LGP", "LINE", "LIWA", "LLEN", "LNCO", "LNDC", "LNG", "LODE", "LPI", "LRE", "LSG", "LTBR", "LYB", "LXU", "MACE", "MBII", "MBLX", "MCEP", "MCF", "MCP", "MDM", "MDR", "MDW", "MEIL", "MEMP", "MEOH", "MGH", "MGN", "MHR", "MILL", "MIL", "MMLP", "MMP", "MNGA", "MON", "MOS", "MPC", "MPET", "MPLX", "MPO", "MRO", "MT", "MTDR", "MTL", "MTRN", "MTX", "MUR", "MUX", "MVG", "MVO", "MWE", "MXC", "NAK", "NBR", "NBL", "NCQ", "NDRO", "NE", "NEM", "NEU", "NFG", "NG", "NFX", "NGD", "NGLS", "NGS", "NGL", "NL", "NOA", "NOG", "NOR", "NOV", "NR", "NRP", "NS", "NSH", "NSLP", "NSU", "NTI", "NUE", "NWPX", "OAS", "OCIP", "OCIR", "ODC", "OILT", "OIS", "OII", "OLN", "OKS", "OMN", "OMG", "ORIG", "OSN", "OXF", "OXY", "PAAS", "PAA", "PACD", "PAL", "PAGP", "PBA", "PBF", "PBM", "PBR", "PBR-A", "PBT", "PDCE", "PDH", "PDO", "PDS", "PED", "PEIX", "PENX", "PER", "PES", "PGH", "PGRX", "PHX", "PKD", "PKX", "PLM", "PLG", "PNRG", "POL", "POT", "PPG", "PPP", "PQ", "PSE", "PSTR", "PSXP", "PSX", "PTEN", "PTR", "PURE", "PVA", "PVG", "PWE", "PVR", "PX", "PXD", "PZG", "PZE", "QEP", "QEPM", "QMM", "QRE", "QRM", "RBY", "RCON", "RDC", "RDS-B", "REE", "RECV", "REGI", "REI", "REN", "RES", "REXX", "REX", "RGLD", "RGP", "RIC", "RIG", "RIOM", "RIO", "RNF", "RNO", "ROC", "ROCK", "ROSE", "ROYL", "ROYT", "RPM", "RRC", "RRMS", "RTK", "RVM", "SA", "SAND", "SARA", "SBGL", "SCCO", "SCEI", "SCOK", "SD", "SDLP", "SDR", "SDRL", "SE", "SDT", "SEMG", "SEP", "SFY", "SGU", "SGY", "SHI", "SHLM", "SHW", "SIAL", "SID", "SIM", "SJT", "SLB", "SLCA", "SLW", "SM", "SMG", "SN", "SNP", "SNMX", "SOQ", "SPN", "SQM", "SRLP", "SSN", "SSL", "SSLT", "SSRI", "STLD", "STO", "SU", "SUTR", "SVBL", "SVLC", "SVM", "SWC", "SWN", "SXC", "SXCP", "SXL", "SXT", "SYMX", "SYNL", "SYNM", "SYRG", "SYT", "SZYM", "TAHO", "TAM", "TAS", "TAT", "TC", "TCK", "TCP", "TDW", "TESO", "TEP", "TGA", "TGB", "TGC", "TGD", "TGE", "THM", "TLLP", "TLM", "TLR", "TLP", "TNH", "TORM", "TOT", "TPLM", "TRGP", "TROX", "TRQ", "TRX", "TSO", "TTI", "TX", "UAMY", "UAN", "UEC", "UGP", "UNT", "UPL", "URG", "URRE", "URZ", "USAC", "USAP", "USEG", "USU", "VALE", "VAL", "VET", "VHI", "VGZ", "VLO", "VNR", "VOC", "VTG", "WDFC", "WES", "WFT", "WG", "WGP", "WH", "WHX", "WHZ", "WLB", "WLK", "WLL", "WLT", "WMB", "WNRL", "WNR", "WPX", "WPZ", "WRES", "WTI", "X", "XEC", "XCO", "XOM", "XPL", "XRA", "XTEX", "XTXI", "YONG", "YPF", "YZC", "ZAZA", "ZINC", "ZN" ] }
{ "_id" : "Services", "Acoes" : [ "AAN", "AAP", "AAWW", "ABC", "ABFS", "ABCD", "ABG", "ABM", "ABCO", "ACM", "ACTG", "ACY", "ADS", "ADT", "AEO", "AER", "AEY", "AFCE", "AH", "AHC", "AIR", "AIRT", "AIT", "AL", "ALCS", "ALK", "ALGT", "AMCN", "AMCO", "AMCX", "AMZN", "AN", "ANF", "ANN", "APEI", "APOL", "ARC", "ARCO", "ARDNA", "ARII", "ARKR", "ARO", "ARW", "ASC", "ASEI", "ASFI", "ASGN", "ASCMA", "ASNA", "ASR", "ATAI", "ATHN", "ATSG", "ATV", "AVT", "AXE", "AYR", "AZO", "BAGL", "BAGR", "BAH", "BAMM", "BALT", "BASI", "BBBY", "BBGI", "BBRG", "BBW", "BBY", "BBSI", "BCO", "BDL", "BDMS", "BEBE", "BFAM", "BGFV", "BGI", "BH", "BID", "BIDZ", "BIG", "BJRI", "BKE", "BKS", "BKW", "BLC", "BLDR", "BLMN", "BLOX", "BODY", "BOBE", "BONA", "BONT", "BPI", "BRS", "BSI", "BURL", "BWL-A", "BWLD", "BWS", "BXC", "BYD", "BYI", "CAB", "CACH", "CACI", "CAH", "CAKE", "CALI", "CAP", "CARB", "CAR", "CASS", "CAST", "CASY", "CATM", "CATO", "CBD", "CBK", "CBRL", "CBS", "CBZ", "CCGM", "CCL", "CCO", "CCSC", "CCRN", "CDI", "CDII", "CDW", "CEC", "CEB", "CEA", "CECO", "CEDU", "CETV", "CGI", "CGX", "CHDN", "CHDX", "CHEF", "CHH", "CHKE", "CHRM", "CHRW", "CHS", "CHTR", "CHUY", "CIDM", "CIX", "CJJD", "CKEC", "CKH", "CKP", "CLCT", "CLUB", "CMCSA", "CMG", "CMRE", "CMLS", "CNCO", "CNI", "CNK", "CNR", "CNSI", "CNW", "CNTY", "CNYD", "COCO", "CODI", "CONN", "CORE", "COSI", "COST", "CP", "CPA", "CPHC", "CPLA", "CPLP", "CPRT", "CRAI", "CRMT", "CRRS", "CRRC", "CRV", "CRVP", "CRWN", "CST", "CSS", "CSV", "CSX", "CTAS", "CTCM", "CTCT", "CTHR", "CTP", "CTRN", "CTRP", "CUK", "CVC", "CVG", "CVGI", "CVS", "CVTI", "CVO", "CXW", "CZR", "DAC", "DANG", "DAL", "DAVE", "DCIN", "DCIX", "DDE", "DDS", "DEG", "DENN", "DEST", "DFRG", "DG", "DGIT", "DGSE", "DHT", "DHX", "DIAL", "DIN", "DIS", "DISCA", "DISH", "DIT", "DJCO", "DKS", "DL", "DLHC", "DLIA", "DLTR", "DLX", "DM", "DNKN", "DOVR", "DPZ", "DRII", "DRI", "DRYS", "DSS", "DSX", "DSW", "DTV", "DV", "DVD", "DWA", "DXM", "DXLG", "DXPE", "EAT", "EBAY", "ECHO", "EDG", "EDMC", "EDU", "EDUC", "EEFT", "EGL", "EGLE", "ELRC", "EMMS", "ENG", "ENOC", "ENL", "ENV", "EPAX", "ERA", "ERS", "ESEA", "ESI", "ESSX", "ETM", "EVC", "EVI", "EXAM", "EXLS", "EXPO", "EXPD", "EXPE", "EXPR", "EZPW", "FC", "FCN", "FDO", "FDX", "FINL", "FISV", "FIVE", "FLL", "FLT", "FLWS", "FLY", "FORD", "FORR", "FOXA", "FRAN", "FRED", "FREE", "FRGI", "FRM", "FRO", "FRS", "FSTR", "FTD", "FTDDV", "FUEL", "FUN", "FURX", "FWRD", "FWM", "G", "GAIA", "GASS", "GCFB", "GBX", "GCI", "GCO", "GDOT", "GEO", "GES", "GFN", "GK", "GLBS", "GLNG", "GLOG", "GLP", "GMAN", "GME", "GMLP", "GMT", "GNC", "GNK", "GOL", "GPI", "GPC", "GPN", "GPS", "GPX", "GRAM", "GSH", "GSL", "GSOL", "GTIM", "GTN", "GWR", "GWW", "H", "HAIN", "HAST", "HA", "HCKT", "HCSG", "HD", "HDS", "HDSN", "HGG", "HHS", "HIBB", "HIL", "HMIN", "HMSY", "HOLL", "HOT", "HOTR", "HPOL", "HPY", "HRB", "HSII", "HSIC", "HSNI", "HSON", "HTHT", "HTLD", "HTSI", "HTZ", "HUBG", "HURN", "HVT", "HWCC", "HZO", "ICFI", "ICLD", "IDI", "IHG", "III", "IILG", "IKGH", "IM", "IMAX", "IMKTA", "INOC", "INTX", "INUV", "INWK", "IPG", "IRG", "ISCA", "ISH", "ISIG", "ISLE", "ITRN", "JACK", "JBHT", "JBLU", "JCP", "JEC", "JMBA", "JNY", "JOB", "JOBS", "JOSB", "JRN", "JW-A", "JWN", "KAR", "KBR", "KELYA", "KEX", "KFRC", "KFY", "KKD", "KIRK", "KMX", "KNOP", "KNX", "KONA", "KORS", "KR", "KSS", "KSU", "KTOS", "KUTV", "LABL", "LACO", "LAMR", "LAD", "LAS", "LAWS", "LCC", "LBTYA", "LEE", "LGF", "LFL", "LIME", "LIN", "LINC", "LINTA", "LIOX", "LITB", "LL", "LMCA", "LOJN", "LOPE", "LOV", "LOW", "LPS", "LPSN", "LPX", "LQDT", "LRN", "LTD", "LSTR", "LTM", "LTRE", "LUB", "LUV", "LVNTA", "LUX", "LVS", "LYV", "M", "MAGS", "MAN", "MAR", "MANU", "MATW", "MATX", "MCD", "MCHX", "MCK", "MCOX", "MCRI", "MCO", "MCS", "MDCA", "MDP", "MED", "MEG", "MELI", "MG", "MGA", "MGAM", "MGM", "MGRC", "MGT", "MHGC", "MHH", "MHFI", "MIC", "MLNK", "MM", "MMS", "MMYT", "MNDL", "MNI", "MNTG", "MOC", "MPEL", "MRTN", "MSG", "MSM", "MSO", "MTN", "MUSA", "MWIV", "MWW", "MW", "MYCC", "MYGN", "NAFC", "NAT", "NATH", "NAUH", "NCI", "NCMI", "NDLS", "NED", "NETC", "NEWL", "NEWP", "NEWT", "NFLX", "NGVC", "NILE", "NM", "NMM", "NNA", "NPD", "NRCIB", "NSC", "NSP", "NSSC", "NTN", "NTRI", "NTSC", "NWSA", "NWY", "NXST", "NYNY", "NYT", "OCR", "ODFL", "ODP", "OEH", "OMC", "OMAB", "OMEX", "OMX", "OMI", "ONE", "ONVI", "ORLY", "OSTK", "OUTR", "OWW", "P", "PAC", "PACR", "PAG", "PATR", "PAYX", "PBPB", "PBY", "PCCC", "PCLN", "PCMI", "PDCO", "PDII", "PENN", "PERF", "PETM", "PFMT", "PFSW", "PHII", "PIR", "PLCE", "PMC", "PNK", "PNRA", "POWR", "PRAA", "PRGN", "PRGX", "PRIS", "PRLS", "PRXI", "PRTS", "PSMT", "PSO", "PSUN", "PTEK", "PTNT", "PTSI", "PTSX", "PTRY", "PWX", "PZZA", "PZZI", "QGEN", "QKLS", "QLTY", "QUAD", "QUNR", "R", "RAIL", "RAD", "RADA", "RBA", "RCII", "RCL", "RCMT", "RDI", "RECN", "REIS", "RENN", "RELL", "RENT", "RGC", "RGS", "RH", "RHI", "RICK", "RJET", "RLD", "RLH", "RLGT", "RLJE", "RLOC", "RLOG", "RMGN", "RMKR", "RNDY", "ROIA", "ROL", "ROIAK", "ROST", "RPXC", "RRD", "RRGB", "RRTS", "RSH", "RT", "RTI", "RUSHB", "RUK", "RUTH", "RYAAY", "SAH", "SAIA", "SALE", "SALM", "SAVE", "SB", "SBAC", "SBGI", "SBH", "SBLK", "SBSA", "SBUX", "SCHL", "SCIL", "SCI", "SCOR", "SCVL", "SEAS", "SED", "SFE", "SFL", "SFLY", "SFM", "SFN", "SFXE", "SGA", "SGMS", "SGRP", "SHIP", "SHLD", "SHOS", "SIG", "SINO", "SIRI", "SIX", "SJR", "SKS", "SKYW", "SMRT", "SNI", "SNX", "SONC", "SPCHB", "SPDC", "SPLS", "SPRO", "SPTN", "SRT", "SSI", "SSP", "SSTK", "SSW", "STB", "STAN", "STEI", "STMP", "STN", "STNG", "STNR", "STON", "STRA", "STRZA", "SUSP", "SUSS", "SWFT", "SVU", "SWY", "SYY", "TA", "TAIT", "TAL", "TAST", "TAX", "TBI", "TCS", "TECD", "TEU", "TESS", "TFM", "TGP", "TGH", "TGT", "THI", "TIF", "TISI", "TITN", "TIVO", "TJX", "TK", "TLYS", "TMH", "TMNG", "TNK", "TNP", "TOO", "TOPS", "TRK", "TRI", "TRN", "TSCO", "TTEC", "TTEK", "TTS", "TUC", "TUES", "TUMI", "TV", "TW", "TWC", "TWMC", "TWX", "TXRH", "TYC", "UAL", "UACL", "UEPS", "UHAL", "ULTA", "ULTR", "UNFI", "UNP", "UNTD", "UNTK", "UPG", "UPS", "URBN", "URI", "URS", "USAK", "USAT", "USTR", "UTI", "UTIW", "UUU", "UWN", "VAC", "VALV", "VALU", "VCI", "VIAB", "VIFL", "VISN", "VIPS", "VITC", "VLCCF", "VLGEA", "VLRS", "VNTV", "VOXX", "VPRT", "VRSK", "VSCP", "VSEC", "VSI", "VSR", "VTNC", "VVI", "VVTV", "WAB", "WACLY", "WAG", "WAGE", "WAIR", "WCC", "WERN", "WEN", "WEST", "WEX", "WFM", "WINA", "WLDN", "WLFC", "WMAR", "WMK", "WMT", "WNS", "WOOF", "WPPGY", "WPO", "WSM", "WSO", "WSTC", "WSTG", "WTSL", "WTW", "WWE", "WYNN", "WYN", "WYY", "XOXO", "XPO", "XRS", "XWES", "XUE", "YOD", "YRCW", "YUM", "YUME", "ZAGG", "ZLC", "ZNH", "ZUMZ" ] }
{ "_id" : "Financial", "Acoes" : [ "AAIT", "AAMC", "AAME", "AADR", "AAT", "AAXJ", "AB", "ABCB", "ABR", "ACAS", "ACC", "ACE", "ACCU", "ACFC", "ACG", "ACGL", "ACIM", "ACRE", "ACNB", "ACWI", "ACWX", "ADC", "ADRA", "ADRD", "ADRU", "ADRE", "ADX", "ADZ", "AEC", "AEG", "AEL", "AF", "AFB", "AFCB", "AFFM", "AFK", "AFH", "AFG", "AFL", "AGA", "AFSI", "AGD", "AGF", "AGG", "AGLS", "AGM", "AGO", "AGNC", "AGQ", "AGII", "AGZ", "AHH", "AHL", "AIA", "AI", "AIG", "AHT", "AINV", "AIV", "AIZ", "AJG", "AKP", "AKR", "ALD", "ALEX", "ALFA", "ALL", "ALLB", "ALX", "AMBC", "AMG", "AMH", "AMIC", "AMJ", "AMLP", "AMNB", "AMP", "AMPS", "AMRE", "AMRB", "AMSF", "AMT", "AMTD", "AMTG", "AMU", "ANAT", "ANCB", "ANCX", "ANGL", "ANH", "AOA", "AOD", "AOM", "AOK", "AOR", "AON", "APB", "APAM", "APF", "APO", "APSA", "APTS", "AQQ", "ARCC", "ARCP", "ARE", "ARGT", "ARI", "ARK", "ARL", "AROW", "ARPI", "ARR", "ASA", "ASBB", "ASBC", "ASBI", "ASEA", "ASDR", "ASG", "ASP", "ASPS", "ASRV", "ATAX", "ATLC", "ATLO", "AUD", "AUNZ", "AUSE", "AUBN", "AV", "AVB", "AVK", "AVIV", "AWH", "AWP", "AWF", "AXDI", "AXEN", "AXFN", "AXHE", "AXIT", "AXJL", "AXMT", "AXJS", "AXR", "AXS", "AXSL", "AXTE", "AXP", "AXUT", "AYN", "AYT", "AZIA", "BAB", "BABS", "BABZ", "BAF", "BAC", "BAL", "BANC", "BAM", "BANF", "BANR", "BAP", "BBDO", "BBD", "BBCN", "BBF", "BBK", "BBH", "BBRC", "BBNK", "BBVA", "BBT", "BBX", "BCA", "BCAR", "BCBP", "BCF", "BCM", "BCH", "BCS", "BCSB", "BCV", "BDCS", "BDD", "BDH", "BDGE", "BDJ", "BDN", "BEE", "BEN", "BERK", "BFO", "BFOR", "BFIN", "BFR", "BFK", "BFY", "BFZ", "BGCP", "BGR", "BGT", "BFS", "BGY", "BHD", "BHB", "BHH", "BHK", "BHV", "BHY", "BHLB", "BIB", "BICK", "BIF", "BIE", "BIK", "BIL", "BIZD", "BIV", "BJK", "BK", "BIS", "BJZ", "BKBK", "BKCC", "BKF", "BKJ", "BKK", "BKLN", "BKMU", "BKN", "BKOR", "BKSC", "BKT", "BKU", "BKYF", "BLE", "BLH", "BLJ", "BLK", "BLNG", "BLMT", "BLV", "BLW", "BLX", "BMA", "BME", "BMO", "BMR", "BMRC", "BNA", "BMTC", "BND", "BNCN", "BNDX", "BNCL", "BNJ", "BNO", "BNS", "BNY", "BOE", "BOCH", "BOFI", "BOIL", "BOH", "BOKF", "BOM", "BONO", "BOS", "BOND", "BOXC", "BOTJ", "BPFH", "BPK", "BPOP", "BPO", "BPY", "BQH", "BQY", "BQR", "BPS", "BRAF", "BRAZ", "BRAQ", "BRE", "BRF", "BRK-B", "BRK-A", "BRKL", "BRO", "BRP", "BRXX", "BRT", "BRZS", "BRZU", "BSC", "BSCD", "BSAC", "BSBR", "BSCG", "BSCE", "BSCF", "BSCH", "BSCI", "BSCJ", "BSCK", "BSCL", "BSCM", "BSD", "BSE", "BSP", "BSMX", "BSV", "BSRR", "BTA", "BTF", "BTAL", "BTO", "BTZ", "BUND", "BVA", "BUSE", "BWINB", "BWV", "BWX", "BWZ", "BX", "BXDB", "BXMT", "BXUB", "BXP", "BXS", "BYFC", "BYM", "BZF", "BYLK", "BZQ", "BZM", "C", "CAC", "CACB", "CACC", "CAD", "CAFE", "CAF", "CAFI", "CANE", "CARZ", "CART", "CASH", "CARV", "CATY", "CB", "CBAN", "CBG", "CBF", "CBIN", "CBL", "CBND", "CBNJ", "CBNK", "CBOE", "CBU", "CCA", "CBSH", "CCBG", "CCCR", "CCG", "CCNE", "CCX", "CCXE", "CDR", "CEE", "CEF", "CET", "CEV", "CEW", "CFBK", "CFFI", "CFFN", "CFNB", "CFP", "CFNL", "CFT", "CFR", "CG", "CGO", "CGW", "CH", "CHCO", "CHEV", "CHFN", "CHFC", "CHI", "CHEP", "CHIM", "CHIQ", "CHII", "CHIX", "CHIE", "CHLC", "CHMI", "CHMG", "CHLN", "CHN", "CHOC", "CHSP", "CHW", "CHXF", "CHXX", "CHY", "CIB", "CIA", "CIF", "CIFC", "CIK", "CIM", "CII", "CINF", "CISG", "CIT", "CITZ", "CIU", "CIZN", "CKX", "CLBH", "CLDT", "CLGX", "CLM", "CLI", "CLMS", "CLNY", "CLY", "CM", "CMA", "CMBS", "CMD", "CMF", "CMDT", "CME", "CMK", "CMO", "CMSB", "CMU", "CNA", "CNBC", "CNBKA", "CNDA", "CNO", "CNOB", "CNPF", "CNS", "CNY", "COB", "COBK", "COBZ", "COF", "COLB", "COLE", "CONE", "COPX", "CORN", "CORP", "COR", "COW", "COY", "COWN", "CPER", "CPF", "CPI", "CPSS", "CPTA", "CPT", "CQQQ", "CRBQ", "CRD-B", "CRF", "CRRB", "CRUD", "CRVL", "CS", "CSBK", "CSD", "CSFS", "CSE", "CSFL", "CSG", "CSGP", "CSH", "CSJ", "CSLS", "CSM", "CSMA", "CSMB", "CSP", "CSMN", "CSQ", "CSWC", "CTBI", "CTC", "CTNN", "CTO", "CU", "CUBA", "CUBE", "CUBI", "CUPM", "CUNB", "CURE", "CUT", "CUZ", "CVBF", "CVCY", "CVLY", "CVOL", "CVY", "CWB", "CWBC", "CWI", "CWH", "CXA", "CXE", "CXH", "CXP", "CYB", "CYE", "CYN", "CYS", "CZA", "CZFC", "CZNC", "CZWI", "DAG", "DBA", "DB", "DBB", "DBAP", "DBBR", "DBC", "DBEF", "DBEM", "DBE", "DBGR", "DBIZ", "DBJP", "DBEU", "DBO", "DBUK", "DBP", "DBV", "DBU", "DBS", "DCA", "DCNG", "DCT", "DDF", "DCOM", "DDG", "DDM", "DDP", "DEE", "DEAR", "DEF", "DDR", "DEI", "DEM", "DES", "DEW", "DEX", "DFE", "DFJ", "DFVS", "DFS", "DFT", "DGAZ", "DGICB", "DGL", "DGP", "DGRE", "DGRW", "DGT", "DGS", "DGZ", "DHF", "DHG", "DHIL", "DHS", "DIA", "DHY", "DIG", "DIRT", "DIM", "DJCI", "DIV", "DJP", "DLBS", "DLN", "DLLR", "DLS", "DLR", "DMF", "DMLP", "DNI", "DNBF", "DNL", "DNO", "DNY", "DNP", "DOD", "DOC", "DOG", "DOIL", "DOL", "DOO", "DON", "DOM", "DPD", "DPO", "DPU", "DPK", "DRGS", "DRE", "DRH", "DRN", "DRL", "DRR", "DRV", "DRW", "DSM", "DSI", "DSTJ", "DSUM", "DSU", "DTD", "DTN", "DTF", "DTH", "DTUS", "DTYL", "DTO", "DTYS", "DUG", "DUC", "DUST", "DVM", "DVY", "DVYE", "DVYL", "DVYA", "DWM", "DWTI", "DWX", "DX", "DXJ", "DXD", "DYY", "DZK", "DZZ", "EAD", "EAPS", "EARN", "EBND", "EBMT", "EBSB", "EBTC", "ECH", "ECF", "ECON", "ECPG", "ECNS", "EDC", "EDEN", "EDD", "EDIV", "EDR", "EDZ", "EDV", "EEA", "EEB", "EEH", "EEHB", "EEMA", "EEM", "EEML", "EEME", "EEN", "EELV", "EET", "EEV", "EFA", "EES", "EFG", "EFNL", "EFC", "EFO", "EFR", "EFT", "EFSC", "EFU", "EFV", "EFZ", "EFX", "EGF", "EGBN", "EGPT", "EGRW", "EGP", "EHI", "EHTH", "EIA", "EIM", "EIHI", "EIG", "EIO", "EIDO", "EIP", "EIRL", "EIS", "EIV", "EKH", "ELD", "EJ", "ELS", "EMB", "EMCB", "EMCD", "EMCF", "EMCI", "EMDD", "EMD", "EMDG", "EMDI", "EMEY", "EMFN", "EMF", "EMFT", "EMHD", "EMHY", "EMIF", "EMJ", "EMITF", "EMLC", "EMI", "EMLP", "EMMT", "ENGN", "ENH", "ENY", "ENX", "ENZL", "EOD", "EOI", "EOS", "EPHE", "EPI", "EPOL", "EPP", "EPS", "EPR", "EPU", "EPV", "EQL", "EQR", "EQS", "EQY", "ERC", "ERH", "ERIE", "ERO", "ERX", "ERY", "ERW", "ERUS", "ESBF", "ESBK", "ESD", "ESGR", "ESNT", "ESRT", "ESSA", "ESS", "ESR", "ESXB", "ETF", "ETB", "ETG", "ETFC", "ETJ", "ETO", "ETV", "ETW", "EUFN", "EUM", "EUO", "EU", "ETY", "EUSA", "EV", "EVAL", "EVBN", "EVBS", "EVF", "EVER", "EVG", "EVJ", "EVM", "EVO", "EVN", "EVP", "EVT", "EVR", "EVX", "EVY", "EVV", "EWA", "EWAS", "EWCS", "EWC", "EWBC", "EWD", "EWG", "EWEM", "EWH", "EWHS", "EWI", "EWJ", "EWGS", "EWK", "EWL", "EWM", "EWP", "EWO", "EWQ", "EWRM", "EWRI", "EWRS", "EWS", "EWN", "EWSS", "EWT", "EWUS", "EWV", "EWW", "EWX", "EWY", "EWU", "EWZ", "EWZS", "EXG", "EXI", "EXL", "EXT", "EXR", "EZA", "EZM", "EZU", "EZY", "FAB", "FAD", "EZJ", "FAC", "FAF", "FAN", "FAM", "FAS", "FAUS", "FAV", "FAZ", "FAX", "FBG", "FBC", "FBIZ", "FBMI", "FBNC", "FBNK", "FBP", "FBMS", "FBRC", "FBSS", "FCAN", "FCAP", "FCBC", "FCCO", "FBT", "FCE-A", "FCCY", "FCG", "FCHI", "FCL", "FCH", "FCF", "FCFS", "FCLF", "FCO", "FCNCA", "FCT", "FCTY", "FCVA", "FDD", "FCZA", "FDEF", "FDL", "FDI", "FDN", "FDT", "FDTS", "FDM", "FDV", "FDUS", "FEMS", "FEFN", "FEP", "FEN", "FEO", "FEU", "FEX", "FEZ", "FFA", "FFBC", "FFC", "FFBH", "FFCO", "FFG", "FFIN", "FFKT", "FFIC", "FFKY", "FFNM", "FFNW", "FGB", "FFR", "FGM", "FHC", "FGD", "FHK", "FHY", "FHN", "FIEU", "FIBK", "FIG", "FII", "FILL", "FINF", "FITB", "FIW", "FIVZ", "FISI", "FKU", "FLAG", "FLC", "FLAT", "FLIC", "FLM", "FLOT", "FLRN", "FLTR", "FM", "FMAR", "FMBI", "FMER", "FMK", "FMN", "FMO", "FMNB", "FMD", "FMY", "FNDA", "FNDB", "FNB", "FNDC", "FNDF", "FNDX", "FNF", "FNHC", "FNFG", "FNI", "FNIO", "FNGN", "FNLC", "FOF", "FOL", "FONE", "FNX", "FOR", "FORX", "FPE", "FPT", "FPO", "FPX", "FRA", "FRAK", "FR", "FRBK", "FRC", "FRF", "FRI", "FRN", "FRME", "FRNK", "FSA", "FRT", "FSBK", "FSBW", "FSE", "FSFG", "FSGI", "FSG", "FSC", "FSRV", "FSU", "FSP", "FSZ", "FTA", "FTBK", "FTC", "FTF", "FT", "FTY", "FUD", "FUE", "FUBC", "FULT", "FUND", "FUNC", "FUR", "FVD", "FVL", "FULL", "FWDB", "FWDD", "FVI", "FWDI", "FWV", "FXA", "FXB", "FXC", "FXCH", "FXCB", "FXCM", "FXD", "FXE", "FXG", "FXH", "FXI", "FXL", "FXN", "FXF", "FXO", "FXP", "FXSG", "FXR", "FXU", "FXZ", "FXS", "FXY", "FYX", "GAB", "GAF", "GABC", "GAL", "GAIN", "GAM", "GARS", "GASL", "GASX", "GASZ", "GAZ", "GBB", "GBCI", "GBDC", "GBF", "GBL", "GBLI", "GBNK", "GCAP", "GCA", "GCBC", "GCC", "GCE", "GCH", "GCV", "GDF", "GDL", "GDX", "GDV", "GDXJ", "GEMS", "GERJ", "GEX", "GF", "GFED", "GFIG", "GFY", "GGAL", "GGOV", "GGN", "GGT", "GGP", "GHI", "GHL", "GHYG", "GII", "GIM", "GIY", "GLAD", "GLD", "GLCH", "GLBZ", "GLDI", "GLCB", "GLL", "GLDX", "GLPI", "GLPIV", "GLQ", "GLTR", "GLRE", "GLU", "GLV", "GMF", "GMFS", "GMM", "GMTB", "GNAT", "GML", "GNMA", "GNR", "GNW", "GOF", "GOOD", "GOVT", "GOV", "GPM", "GPT", "GRES", "GREK", "GRF", "GRI", "GRID", "GROW", "GRN", "GRU", "GRT", "GRR", "GRWN", "GSAX", "GS", "GSC", "GSBC", "GSG", "GSGO", "GSRA", "GSP", "GSY", "GSMA", "GSVC", "GTAA", "GTIP", "GTS", "GTWN", "GTY", "GULF", "GURU", "GUR", "GUT", "GVI", "GVT", "GWL", "GUNR", "GXC", "GXG", "GXF", "GYLD", "GZT", "GYRO", "GWX", "HAFC", "HAO", "HAP", "HALL", "HASI", "HAV", "HAWK", "HBCP", "HBC", "HBHC", "HBK", "HBAN", "HBMD", "HBOS", "HBNC", "HCAP", "HCBK", "HBNK", "HCC", "HCI", "HCN", "HCP", "HDB", "HDG", "HDGI", "HDGE", "HEDJ", "HEOP", "HEVY", "HF", "HFBC", "HFFC", "HGI", "HFWA", "HFBL", "HHC", "HHH", "HGSH", "HHY", "HIH", "HIG", "HIFS", "HILO", "HIS", "HIO", "HIX", "HKK", "HIW", "HLSS", "HME", "HMG", "HMH", "HMNF", "HMST", "HMPR", "HMN", "HOMB", "HOME", "HPF", "HPI", "HPP", "HPT", "HPS", "HQH", "HQL", "HR", "HSA", "HRZN", "HSPX", "HST", "HT", "HTBI", "HTA", "HTBK", "HTH", "HTGC", "HTR", "HTLF", "HTD", "HTS", "HTY", "HUSE", "HVPW", "HVB", "HWBK", "HYB", "HYD", "HYEM", "HYF", "HYG", "HYHG", "HYLD", "HYMB", "HYS", "HYT", "HYXU", "HYV", "IAE", "IAF", "IAK", "IAI", "IAH", "IAU", "IAT", "IBB", "IBCB", "IBCD", "IBCC", "IBCA", "IBCE", "IBDA", "IBDB", "IBCP", "IBDD", "IBDC", "IBKC", "IBKR", "IBND", "IBN", "IBOC", "IBTX", "ICB", "ICF", "ICE", "ICI", "ICGE", "ICLN", "ICN", "ICOL", "ICH", "IDHB", "IDHQ", "IDOG", "IDLV", "IDU", "IDV", "IDX", "IDXJ", "IEF", "IEI", "IELG", "IEO", "IEV", "IESM", "IF", "IFEU", "IFAS", "IFGL", "IEZ", "IFN", "IFMI", "IFNA", "IFSM", "IFT", "IGA", "IGD", "IGE", "IGF", "IGN", "IGOV", "IGR", "IGU", "IGM", "IGV", "IHC", "IHF", "IHI", "IHY", "IHT", "IHE", "IID", "IIH", "IIF", "IIM", "IJH", "IJJ", "IJK", "IJR", "IJT", "IJS", "ILB", "ILF", "ILTB", "IMF", "IMCB", "IMH", "INB", "INBK", "INDA", "INDL", "INDB", "INDY", "INCO", "INFL", "ING", "INKM", "INN", "INP", "INR", "INTL", "INTG", "INXX", "INY", "IOO", "IOIL", "IOT", "IPCC", "IPE", "IPD", "IPFF", "IPF", "IPK", "IPN", "IPS", "IPU", "IPW", "IQDF", "IQDE", "IQDY", "IQI", "IRC", "IRE", "IRET", "IRL", "IRR", "IRV", "IRT", "IROQ", "IRS", "IRY", "ISBC", "ISHG", "ISI", "ISL", "ISRA", "IST", "ITA", "ITB", "ITE", "ITF", "ITG", "ITIP", "ITIC", "ITM", "ITOT", "ITR", "ITUB", "IVE", "IVOP", "IVOO", "IVOV", "IVR", "IVW", "IVV", "IWB", "IVOG", "IWC", "IVZ", "IWD", "IWM", "IWL", "IWF", "IWN", "IWR", "IWS", "IWO", "IWV", "IWW", "IWX", "IWY", "IWP", "IXC", "IXG", "IWZ", "IXJ", "IX", "IXN", "IXP", "IYC", "IYF", "IYG", "IYH", "IYE", "IYJ", "IYK", "IYLD", "IYM", "IYR", "IYW", "IYY", "IYT", "IYZ", "JAXB", "JCE", "JDD", "JEM", "JEQ", "JFR", "JFBI", "JFC", "JGBD", "JFBC", "JGBS", "JGG", "JGV", "JHI", "JHS", "JJA", "JJC", "JJE", "JJG", "JHP", "JJM", "JJN", "JJP", "JJS", "JJT", "JJU", "JKD", "JKE", "JKH", "JKF", "JKI", "JKJ", "JKK", "JKL", "JKG", "JLA", "JLL", "JNK", "JMP", "JNS", "JO", "JMI", "JOE", "JOF", "JPC", "JPG", "JPNL", "JPNS", "JPM", "JPS", "JPX", "JPP", "JQC", "JPZ", "JRO", "JSC", "JRS", "JSN", "JTA", "JTD", "JTP", "JUNR", "JXI", "JXSB", "KB", "KBE", "KBWB", "KBWC", "KBWD", "KBWR", "KBWP", "KBWI", "KBWY", "KCE", "KBWX", "KCAP", "KCG", "KEF", "KCLI", "KED", "KF", "KFFB", "KEY", "KFN", "KFS", "KFYP", "KHI", "KIE", "KIM", "KINS", "KIPO", "KKR", "KLD", "KME", "KMM", "KMPR", "KNOW", "KOL", "KOLD", "KORU", "KORZ", "KRE", "KRC", "KRG", "KRNY", "KROO", "KRS", "KRU", "KSM", "KST", "KTF", "KW", "KWT", "KXI", "KYN", "KYE", "L", "LABC", "LAQ", "LAND", "LARK", "LATM", "LAG", "LAZ", "LBAI", "LBF", "LBJ", "LBND", "LCM", "LCNB", "LD", "LDF", "LEAF", "LEO", "LFC", "LGI", "LGLV", "LHO", "LION", "LIT", "LKFN", "LM", "LNBB", "LND", "LNC", "LOAN", "LOR", "LPHI", "LPLA", "LPSB", "LQD", "LSBI", "LRY", "LSBK", "LSC", "LSE", "LSTK", "LTC", "LTL", "LTPZ", "LTS", "LWC", "LVL", "LXP", "LYG", "MAA", "MA", "MAB", "MAC", "MAIN", "MARPS", "MATH", "MATL", "MAV", "MAYS", "MBB", "MBI", "MBG", "MBRG", "MBTF", "MBFI", "MCA", "MBVT", "MBWM", "MCBC", "MCBK", "MCBI", "MCC", "MCGC", "MCI", "MCN", "MCR", "MCRO", "MCY", "MDIV", "MDD", "MDY", "MDYG", "MDYV", "MES", "MEN", "MET", "METR", "MFA", "MFD", "MFG", "MFC", "MFL", "MFI", "MFLR", "MFM", "MFNC", "MFT", "MFV", "MGC", "MFSF", "MGF", "MGI", "MGK", "MGV", "MGYR", "MGU", "MHD", "MHE", "MHF", "MHI", "MHN", "MHY", "MHLD", "MIDU", "MIDZ", "MIN", "MINC", "MINT", "MIG", "MIW", "MITT", "MIY", "MJI", "MKH", "MKL", "MKTX", "MLN", "MLPG", "MLP", "MLPJ", "MLPI", "MLPL", "MLPN", "MLPW", "MLPX", "MLPY", "MLVF", "MMI", "MMC", "MMT", "MMV", "MNA", "MN", "MMU", "MNE", "MNP", "MNR", "MNRK", "MOFG", "MONY", "MOO", "MPA", "MPB", "MPV", "MPW", "MQY", "MQT", "MRF", "MRH", "MRLN", "MS", "MSD", "MSBF", "MSF", "MSB", "MSFG", "MSL", "MSP", "MSXX", "MTB", "MTK", "MTGE", "MTG", "MTR", "MTS", "MTU", "MTUM", "MUA", "MUAC", "MUAF", "MUAG", "MUB", "MUC", "MUE", "MUH", "MUAD", "MUAE", "MUI", "MUJ", "MUNI", "MUS", "MVF", "MVC", "MVT", "MVV", "MXA", "MXE", "MXF", "MXI", "MXN", "MYC", "MYD", "MYI", "MYF", "MYJ", "MYM", "MYN", "MYY", "MZA", "MZF", "MZZ", "NAD", "NAC", "NAN", "NASB", "NASI", "NASH", "NATL", "NAZ", "NAVG", "NBBC", "NBH", "NBCB", "NBG", "NBHC", "NBN", "NBO", "NBTB", "NBTF", "NBW", "NCA", "NCBC", "NCP", "NCO", "NCT", "NCU", "NCV", "NCZ", "NDAQ", "NEA", "NEAR", "NECB", "NEN", "NEWS", "NFBK", "NFJ", "NFO", "NGE", "NGPC", "NGX", "NGZ", "NHI", "NIB", "NHTB", "NICK", "NIM", "NHS", "NINI", "NIO", "NKG", "NKSH", "NKX", "NKY", "NLR", "NLP", "NLY", "NMA", "NMB", "NMFC", "NMI", "NMO", "NMR", "NMT", "NMY", "NMZ", "NNC", "NNJ", "NNI", "NNP", "NNN", "NNY", "NOBL", "NOM", "NOAH", "NORW", "NOVB", "NPBC", "NPF", "NPI", "NPM", "NPP", "NPT", "NPV", "NPY", "NQC", "NQJ", "NQM", "NQP", "NQS", "NQU", "NQI", "NRIM", "NRF", "NRK", "NRO", "NRZ", "NRT", "NSEC", "NSL", "NSM", "NTC", "NTRS", "NTX", "NUCL", "NUC", "NUGT", "NUJ", "NUM", "NUO", "NUV", "NVC", "NVG", "NVSL", "NVX", "NVY", "NWBI", "NWFL", "NWLI", "NXC", "NXK", "NXJ", "NXN", "NXP", "NXQ", "NXR", "NXM", "NY", "NYC", "NXZ", "NYF", "NYCB", "NYH", "NYMT", "NZF", "NZH", "NYX", "O", "OAK", "OABC", "OAKS", "OBAS", "OBAF", "OCFC", "OB", "OCN", "OEF", "OFED", "OFF", "OFC", "OFG", "OFS", "OHI", "OIA", "OIH", "OIL", "OILZ", "OLBK", "OKSB", "OLEM", "OLO", "OLP", "ONB", "ONEF", "ONEK", "ONN", "ONFC", "ONEQ", "OPHC", "OPOF", "OPY", "ORI", "ORM", "ORIT", "ORRF", "OSBC", "OSHC", "OTR", "OTP", "OVBC", "OVLY", "OZM", "OZRK", "PAGG", "PAF", "PAI", "PALL", "PACW", "PB", "PBCP", "PBD", "PBE", "PBCT", "PBHC", "PBIB", "PBJ", "PBIP", "PBP", "PBS", "PBW", "PCC", "PCBK", "PBNY", "PCEF", "PCF", "PCK", "PCH", "PCL", "PCM", "PCN", "PCQ", "PCY", "PDN", "PDP", "PDM", "PDT", "PEB", "PEBO", "PEBK", "PEJ", "PEI", "PEK", "PEOP", "PEO", "PERM", "PEX", "PEY", "PEZ", "PFA", "PFBC", "PFBX", "PFBI", "PFEM", "PFD", "PFF", "PFI", "PFIG", "PFL", "PFLT", "PFG", "PFM", "PFN", "PFO", "PFS", "PFSI", "PFXF", "PGC", "PGD", "PGHY", "PGF", "PGJ", "PGM", "PGP", "PGX", "PGR", "PHB", "PHDG", "PHD", "PHF", "PHH", "PHK", "PHO", "PHT", "PHYS", "PIC", "PICB", "PICK", "PID", "PIE", "PICO", "PIN", "PIO", "PIM", "PIQ", "PIV", "PJB", "PIZ", "PJG", "PJM", "PJC", "PJP", "PKB", "PJF", "PKBK", "PKO", "PKW", "PKY", "PL", "PLBC", "PLCC", "PLD", "PLND", "PLMT", "PLTM", "PLW", "PMBC", "PMF", "PML", "PMM", "PMNA", "PMO", "PMR", "PMT", "PMX", "PNBK", "PNF", "PNC", "PNFP", "PNI", "PNQI", "PNNT", "PNX", "PNXQ", "PPBI", "PPA", "PPH", "PPLT", "PPR", "PPS", "PQSC", "PPT", "PRA", "PRB", "PRF", "PRFE", "PRFF", "PRFG", "PRFH", "PRE", "PRFM", "PRFN", "PRFQ", "PRFU", "PRFS", "PRFZ", "PRI", "PRK", "PRN", "PROV", "PRU", "PSAU", "PSA", "PSBH", "PSB", "PSCC", "PSCD", "PSCF", "PSCH", "PSCI", "PSCT", "PSCM", "PSCU", "PSCE", "PSEC", "PSI", "PSJ", "PSK", "PSL", "PSQ", "PSP", "PSR", "PST", "PSTB", "PTF", "PTH", "PTM", "PTP", "PTY", "PUI", "PUK", "PUW", "PULB", "PVI", "PVD", "PWB", "PW", "PWC", "PWJ", "PWO", "PVTB", "PWP", "PWOD", "PWT", "PWV", "PWY", "PWZ", "PXE", "PXF", "PXH", "PXI", "PXJ", "PXLC", "PXLV", "PXMC", "PXMG", "PXMV", "PXN", "PXQ", "PXLG", "PXSV", "PXR", "PXSG", "PYH", "PYN", "PYZ", "PZA", "PZC", "PXSC", "PZI", "PZT", "PZN", "PZD", "QAI", "QCLN", "QCCO", "QDEF", "QCRH", "QABA", "QEH", "QDYN", "QID", "QDF", "QIWI", "QLTA", "QLTB", "QLTC", "QLD", "QQEW", "QQQ", "QQQC", "QQQE", "QMN", "QQQX", "QTEC", "QTS", "QQXT", "RALS", "RAND", "RAS", "RAVI", "RBL", "RBPAA", "RBCAA", "RCD", "RBS", "RCG", "RCKB", "RCAP", "RCS", "RDIV", "RDN", "RE", "REG", "REK", "REM", "REMX", "RESI", "RETL", "REW", "REXI", "REXR", "REZ", "RFG", "RF", "RFV", "RGA", "RFI", "RGI", "RHP", "RIF", "RHS", "RINF", "RING", "RIT", "RIVR", "RJA", "RJN", "RJZ", "RJF", "RKH", "RJI", "RLI", "RLJ", "RLGY", "RLY", "RMAX", "RM", "RMT", "RNE", "RNR", "RNST", "RNP", "ROIC", "ROLA", "ROM", "ROMA", "ROOF", "RPG", "RPI", "RPAI", "RPV", "RPT", "RPX", "RQI", "RRF", "RRGR", "RSE", "RSCO", "RSO", "RSP", "RSU", "RSW", "RSX", "RSXJ", "RTH", "RTLA", "RTM", "RTL", "RTR", "RUDR", "RUSL", "RUSS", "RVNU", "RVSB", "RVT", "RWG", "RWK", "RWL", "RWJ", "RWM", "RWO", "RWR", "RWV", "RWT", "RWW", "RWX", "RXD", "RWXL", "RXI", "RXL", "RY", "RYF", "RYH", "RYJ", "RYE", "RYT", "RYU", "RZG", "RZV", "SAA", "SAGG", "SAFT", "SAL", "SAN", "SAR", "SASR", "SBB", "SBBX", "SBCF", "SBFG", "SBM", "SBI", "SBND", "SBNY", "SBR", "SBRA", "SBW", "SBSI", "SBY", "SCC", "SBV", "SCBT", "SCD", "SCHA", "SCHB", "SCHC", "SCHE", "SCHF", "SCHG", "SCHO", "SCHP", "SCHR", "SCHV", "SCHX", "SCHW", "SCHZ", "SCIN", "SCIF", "SCJ", "SCO", "SCPB", "SCZ", "SDD", "SDK", "SDIV", "SDOG", "SDOW", "SDP", "SDS", "SDY", "SDYL", "SEA", "SEF", "SEIC", "SF", "SFK", "SFG", "SFI", "SFBC", "SFNC", "SFST", "SGAR", "SGB", "SGF", "SGG", "SGL", "SGM", "SGOL", "SH", "SHBI", "SHG", "SHM", "SHO", "SHV", "SHY", "SIBC", "SIEB", "SIFI", "SIGI", "SIJ", "SIL", "SILJ", "SIR", "SIVR", "SIVB", "SIZE", "SJF", "SIZ", "SJL", "SJH", "SJNK", "SKF", "SKK", "SKT", "SKYY", "SLA", "SLF", "SLM", "SLRC", "SLG", "SLVO", "SLVP", "SLV", "SLX", "SLY", "SLYG", "SLYV", "SMB", "SMBC", "SMDD", "SMFG", "SMH", "SMIN", "SMK", "SMLV", "SMMU", "SMN", "SMMF", "SMPL", "SNBC", "SNFCA", "SNH", "SNLN", "SNV", "SOCB", "SOCL", "SOHO", "SOIL", "SONA", "SOXL", "SOR", "SOXS", "SOXX", "SOYB", "SPBC", "SPE", "SPGH", "SPG", "SPHB", "SPHQ", "SPLV", "SPPR", "SPXH", "SPXL", "SPXS", "SPY", "SPYG", "SPXU", "SPYV", "SQQQ", "SRC", "SRCE", "SRLN", "SRTY", "SRS", "SRV", "SSBI", "SSG", "SSFN", "SSO", "SST", "SSS", "STAG", "STBZ", "STBA", "STC", "STEL", "STIP", "STFC", "STI", "STL", "STND", "STPP", "STPZ", "STRS", "STSA", "STT", "STWD", "SUB", "SUBK", "SUI", "SUNS", "SUSQ", "SVBI", "SVXY", "SWH", "SWS", "SWZ", "SYBT", "SYA", "SYLD", "SZK", "SZO", "TAGS", "TAI", "TAO", "TAN", "TAXI", "TAYC", "TBAR", "TBBK", "TBF", "TBT", "TBNK", "TBX", "TBZ", "TCAP", "TCBI", "TCB", "TCBK", "TCI", "TCFC", "TCRD", "TCO", "TDBK", "TD", "TDH", "TDD", "TDIV", "TDF", "TDN", "TDTF", "TDTT", "TDX", "TDV", "TECL", "TECS", "TEI", "TELOZ", "TENZ", "TFI", "TFSL", "TGR", "THD", "THFF", "THHY", "THG", "THRD", "TICC", "TILT", "TIP", "TINY", "TIPT", "TIPX", "TIPZ", "TKF", "TLH", "TLI", "TLL", "TLT", "TLTD", "TLTE", "TLO", "TMF", "TMK", "TMP", "TMV", "TNA", "TNDQ", "TOK", "TOFC", "TOTS", "TOWN", "TPL", "TPGI", "TPS", "TPRE", "TQQQ", "TRC", "TRCB", "TRF", "TREE", "TRMK", "TRNM", "TRND", "TRNO", "TROW", "TRSK", "TRST", "TRV", "TSBK", "TSC", "TSI", "TSH", "TSRE", "TSS", "TTF", "TTFS", "TTH", "TTT", "TUR", "TUZ", "TVIX", "TVIZ", "TWGP", "TWM", "TWN", "TWOK", "TWQ", "TWO", "TWTI", "TYBS", "TYD", "TY", "TYNS", "TYG", "TYN", "TYO", "TZA", "TZD", "TZE", "TZI", "TZL", "TZG", "TYY", "TZO", "TZV", "UAG", "UBC", "UBD", "UBCP", "UBFO", "UBG", "UBA", "UBM", "UBN", "UBR", "UBNK", "UBOH", "UBS", "UBSH", "UBT", "UCBA", "UBSI", "UCC", "UCD", "UCBI", "UCI", "UCFC", "UCO", "UDN", "UDOW", "UCP", "UDR", "UFCS", "UGA", "UGAZ", "UGE", "UGL", "UHN", "UHT", "UINF", "UIHC", "UKF", "UKK", "UKW", "ULE", "UJB", "ULQ", "UMDD", "UMBF", "UMH", "UMX", "UMPQ", "UNAM", "UNB", "UNG", "UNM", "UNL", "UNTY", "UOIL", "UPRO", "UPV", "UPW", "URE", "URA", "URTH", "USA", "URTY", "USAG", "USCI", "USB", "USBI", "USD", "USL", "USMI", "USO", "UST", "USV", "UTF", "UTH", "UTG", "UTLT", "UUP", "UVG", "UVE", "UVT", "UVSP", "UVXY", "UVU", "UWC", "UWM", "UWTI", "UXI", "UXJ", "UYM", "V", "UYG", "VAW", "VB", "VBF", "VBK", "VBFC", "VBR", "VCF", "VCIT", "VCBI", "VCLT", "VCR", "VCV", "VDC", "VDE", "VCSH", "VEA", "VEGA", "VEGI", "VEU", "VFH", "VGIT", "VGK", "VFL", "VGLT", "VGM", "VGSH", "VGT", "VHT", "VIG", "VIIX", "VIIZ", "VIOO", "VIOV", "VIOG", "VIS", "VIXH", "VKI", "VIXY", "VKQ", "VIXM", "VLT", "VLUE", "VMBS", "VMM", "VMO", "VLY", "VNM", "VNQ", "VNQI", "VNO", "VO", "VOE", "VONE", "VONG", "VONV", "VOOG", "VOOV", "VOT", "VOX", "VOO", "VOYA", "VPFG", "VPL", "VPU", "VQT", "VPV", "VRD", "VR", "VRTA", "VRTB", "VRTS", "VSB", "VSBN", "VSS", "VSPY", "VTA", "VT", "VTHR", "VTN", "VTI", "VTIP", "VTR", "VTWG", "VTWO", "VTWV", "VTV", "VUG", "VV", "VVR", "VWOB", "VWO", "VXF", "VXUS", "VXX", "VXZ", "VYFC", "VYM", "WABC", "WAC", "WAFD", "WAL", "WAYN", "WBB", "WBCO", "WASH", "WBK", "WBKC", "WBS", "WD", "WDIV", "WDTI", "WEA", "WDR", "WEAT", "WEBK", "WEET", "WETF", "WF", "WFBI", "WFC", "WFD", "WIA", "WHLR", "WHG", "WIBC", "WIP", "WITE", "WIW", "WMCR", "WMC", "WMH", "WMW", "WOOD", "WPC", "WPS", "WREI", "WRE", "WRB", "WRI", "WRLD", "WSBC", "WSBF", "WSFS", "WSH", "WSR", "WTFC", "WTBA", "WTM", "WU", "WVFC", "XAA", "XBKS", "XBI", "XES", "XGC", "XHB", "XHE", "XIV", "XLB", "XLE", "XL", "XLF", "XLG", "XLI", "XLK", "XLP", "XLU", "XLV", "XMLV", "XLY", "XMPT", "XME", "XOOM", "XOVR", "XPH", "XOP", "XPP", "XRO", "XRT", "XSD", "XSLV", "XTL", "XTN", "XVZ", "XVIX", "XXV", "YANG", "Y", "YCL", "YCS", "YDIV", "YAO", "YDKN", "YINN", "YXI", "Z", "YYY", "ZFC", "ZION", "ZF", "ZIV", "ZIPR", "ZROZ", "ZSL", "ZTR" ] }
{ "_id" : null, "Acoes" : [ ] }
{ "_id" : "Conglomerates", "Acoes" : [ "ANDA", "AQU", "CACG", "EAGL", "ENT", "GDEF", "HMTV", "HRG", "HTWO", "IEP", "JACQ", "LDL", "MITSY", "MMM", "MWRX", "NC", "PBSK", "PME", "QPAC", "SAEX", "SPLP" ] }
{ "_id" : "Healthcare", "Acoes" : [ "A", "ABAX", "ABBV", "ABIO", "ABMC", "ABMD", "ABT", "ACAD", "ACHC", "ACHN", "ACOR", "ACST", "ACT", "ACRX", "ACUR", "ADHD", "ADK", "ADUS", "ADXS", "AEGR", "AERI", "AET", "AEZS", "AFAM", "AFFY", "AGEN", "AGIO", "AGN", "AHPI", "AHS", "AIQ", "AIRM", "AKRX", "ALGN", "ALIM", "ALKS", "ALNY", "ALR", "ALSE", "ALXA", "ALXN", "AMAG", "AMBI", "AMED", "AMGN", "AMPE", "AMRI", "AMRN", "AMS", "AMSG", "ANAC", "ANCI", "ANGO", "ANIK", "ANTH", "ANIP", "APPA", "APPY", "APRI", "APT", "ARAY", "ARIA", "ARNA", "ARQL", "ARTC", "ARRY", "ARWR", "ASTM", "ATEC", "ATHX", "ATOS", "ATRC", "ATRI", "ATRS", "AUXL", "AVEO", "AVNR", "AXDX", "AXGN", "AXN", "AZN", "BABY", "BAX", "BAXS", "BCR", "BCRX", "BDSI", "BDX", "BEAT", "BGMD", "BIIB", "BIND", "BIOD", "BIOS", "BIOL", "BKD", "BLUE", "BMRN", "BMY", "BONE", "BOTA", "BRLI", "BSDM", "BSPM", "BSTC", "BSX", "BTX", "BVX", "CADX", "CAPS", "CASM", "CBLI", "CBM", "CBMX", "CBPO", "CBRX", "CBST", "CCM", "CCXI", "CDXS", "CELG", "CEMI", "CEMP", "CERS", "CFN", "CGEN", "CHE", "CHTP", "CI", "CLDX", "CLSN", "CLVS", "CMN", "CMRX", "CNAT", "CNC", "CNDO", "CNMD", "CO", "COO", "CORT", "COV", "CPIX", "CPHI", "CPRX", "CRDC", "CRIS", "CRL", "CRMD", "CRME", "CRTX", "CRY", "CSII", "CSU", "CTIC", "CUR", "CUTR", "CVD", "CVM", "CXM", "CYAN", "CYBX", "CYH", "CYNO", "CYCC", "CYTK", "CYTR", "CYTX", "DARA", "DCTH", "DEPO", "DGX", "DHRM", "DNDN", "DRAD", "DRRX", "DRTX", "DSCI", "DSCO", "DVCR", "DVA", "DVAX", "DXCM", "DXR", "DYAX", "DYNT", "EBS", "ECTE", "ECYT", "EDAP", "ELGX", "ELMD", "ELN", "ELOS", "EMIS", "ENDP", "ENMD", "ENSG", "ENTA", "ENZ", "ENZN", "ENZY", "EPZM", "ERB", "ESC", "ESMC", "ESPR", "ESRX", "ETRM", "EVHC", "EVOK", "EW", "EXAS", "EXAC", "EXEL", "FATE", "FCSC", "FLML", "FMI", "FMS", "FONR", "FOLD", "FPRX", "FRX", "FVE", "GALE", "GALT", "GB", "GENE", "GENT", "GERN", "GEVA", "GHDX", "GILD", "GIVN", "GMED", "GNBT", "GNMK", "GNVC", "GSK", "GTIV", "GTXI", "GWPH", "HAE", "HALO", "HBIO", "HCA", "HEB", "HGR", "HH", "HIIQ", "HITK", "HLS", "HMA", "HNSN", "HNT", "HOLX", "HPTX", "HRC", "HRT", "HSKA", "HSP", "HTBX", "HTWR", "HUM", "HWAY", "HZNP", "IART", "IBIO", "ICCC", "ICEL", "ICLR", "ICPT", "ICUI", "IDIX", "IDRA", "IDXX", "IG", "ILMN", "IMGN", "IMMU", "IMMY", "IMRS", "IMUC", "INCY", "INFU", "INFI", "INO", "INSM", "INSY", "IPCI", "IPCM", "IPXL", "IRIX", "IRWD", "ISIS", "ISR", "ISRG", "ITMN", "IVC", "JAZZ", "JNJ", "KBIO", "KERX", "KIPS", "KND", "KOOL", "KPTI", "KYTH", "LAKE", "LCAV", "LCI", "LDRH", "LFVN", "LH", "LHCG", "LIFE", "LGND", "LLY", "LMAT", "LMNX", "LPDX", "LPNT", "LPTN", "LXRX", "MACK", "MAKO", "MASI", "MD", "MDCI", "MDCO", "MDRX", "MDT", "MDVN", "MDXG", "MEIP", "MELA", "MGCD", "MGLN", "MGNX", "MLAB", "MMSI", "MNKD", "MNK", "MNOV", "MNTA", "MOH", "MR", "MRNA", "MRK", "MSA", "MSON", "MSTX", "MTD", "MYL", "MYRX", "NAII", "NATR", "NAVB", "NBIX", "NBS", "NBY", "NDZ", "NEO", "NEOG", "NHC", "NKTR", "NLNK", "NLTX", "NNVC", "NPSP", "NSPH", "NSTG", "NSPR", "NURO", "NVAX", "NUVA", "NVDQ", "NVGN", "NVO", "NVS", "NWBO", "NXTM", "NYMX", "OCLS", "OCRX", "OFIX", "OGXI", "OGEN", "OHRP", "OMED", "OMER", "ONCY", "ONTX", "ONTY", "ONVO", "OPHT", "OPK", "OPXA", "OREX", "ORMP", "OSIR", "OSUR", "OVAS", "OXBT", "OXGN", "PACB", "PATH", "PBIO", "PBMD", "PBYI", "PCRX", "PCYC", "PDEX", "PDLI", "PETS", "PETX", "PFE", "PGNX", "PHMD", "PIP", "PKI", "PLX", "PMD", "PODD", "POZN", "PPHM", "PRAN", "PRGO", "PRPH", "PRSC", "PRXL", "PRTA", "PSDV", "PSTI", "PTCT", "PTIE", "PTLA", "PTN", "PTX", "Q", "QCOR", "QDEL", "QLTI", "RCPT", "RDNT", "RDY", "REGN", "RELV", "RGLS", "RGEN", "RGDX", "RIGL", "RMD", "RMTI", "RNA", "RNN", "ROCM", "ROSG", "RPRX", "RPTP", "RTIX", "RVP", "SCLN", "SCMP", "SCR", "SEM", "SGEN", "SGMO", "SGNT", "SGYP", "SIGA", "SIRO", "SKBI", "SKH", "SLXP", "SLTM", "SMA", "SNN", "SNSS", "SNTA", "SNTS", "SNY", "SPAN", "SPEX", "SPHS", "SPNC", "SPPI", "SQNM", "SRDX", "SRNE", "SRPT", "SSH", "SSY", "STAA", "STE", "STEM", "STJ", "STML", "STSI", "STXS", "SUPN", "SURG", "SVA", "SYK", "SYN", "TARO", "TEAR", "TECH", "TELK", "TEVA", "TFX", "TGTX", "TGX", "THC", "THLD", "THOR", "THRX", "TMO", "TNGN", "TNXP", "TPI", "TRGT", "TRIB", "TRNX", "TROV", "TSPT", "TSRO", "TTHI", "TTPH", "TXMD", "UAM", "UHS", "ULGX", "UNH", "UNIS", "UPI", "USMD", "USNA", "USPH", "UTHR", "UTMD", "VAR", "VASC", "VCYT", "VICL", "VIVO", "VNDA", "VOLC", "VPHM", "VRML", "VRNM", "VRTX", "VRX", "VSCI", "VSTM", "VTUS", "VVUS", "WAT", "WCG", "WLP", "WMGI", "WST", "WX", "XLRN", "XNPT", "XOMA", "XON", "XRAY", "ZGNX", "ZLCS", "ZIOP", "ZLTQ", "ZMH", "ZTS" ] }
{ "_id" : "Technology", "Acoes" : [ "AAOI", "ABTL", "ACCL", "ACIW", "ACLS", "ACN", "ACTS", "ACTV", "ACXM", "ADBE", "ADAT", "ADI", "ADNC", "ADP", "ADTN", "ADSK", "ADVS", "AEHR", "AEIS", "AERG", "AFFX", "AFOP", "AGYS", "AKAM", "ALAN", "ALOG", "ALOT", "ALLT", "ALTI", "ALTR", "ALU", "ALVR", "ALSK", "ALTV", "AMAP", "AMBA", "AMAT", "AMBT", "AMCC", "AMD", "AMKR", "AMSC", "AMSWA", "AMX", "ANAD", "ANEN", "ANGI", "ANSS", "AOL", "AOSL", "APH", "API", "ARCW", "ARMH", "ARRS", "ARUN", "ARX", "ASIA", "ASMI", "ASML", "ASTI", "ASUR", "ASYS", "ASX", "ATE", "ATEA", "ATGN", "ATMI", "ATNY", "ATML", "ATNI", "ATRM", "ATTU", "ATVI", "AUDC", "AUO", "AVGO", "AVID", "AVG", "AVNW", "AVX", "AWAY", "AWRE", "AXTI", "AYI", "AZPN", "BBOX", "BBRY", "BCE", "BCOM", "BCOR", "BCOV", "BDR", "BELFB", "BHE", "BIDU", "BIO", "BIRT", "BITA", "BLIN", "BLKB", "BMI", "BNFT", "BOSC", "BPHX", "BR", "BRC", "BRCD", "BRCM", "BRKR", "BRKS", "BSFT", "BSQR", "BT", "BTUI", "BV", "BVSN", "CA", "CALL", "CALD", "CALX", "CAMP", "CAMT", "CAVM", "CBB", "CBEY", "CBR", "CCI", "CCIH", "CCMP", "CCOI", "CCUR", "CDNS", "CEL", "CERN", "CEVA", "CGNX", "CHA", "CHKP", "CHL", "CHU", "CHT", "CHYR", "CIEN", "CIMT", "CIS", "CKSW", "CLFD", "CLIR", "CLRX", "CLRO", "CLS", "CMGE", "CMTL", "CNET", "CNIT", "CNQR", "CNSL", "CNTF", "COGO", "CODE", "COHR", "COHU", "COMM", "COOL", "COVR", "COVS", "CPHD", "CPSI", "CPWR", "CRAY", "CREE", "CRDS", "CRM", "CRNT", "CRTO", "CRUS", "CSC", "CSCD", "CSCO", "CSGS", "CSIQ", "CSOD", "CSPI", "CSUN", "CTCH", "CTG", "CTL", "CTRL", "CTSH", "CTRX", "CTS", "CTXS", "CUB", "CVLT", "CVT", "CY", "CYBE", "CYNI", "CYOU", "DAEG", "DAIO", "DATA", "DATE", "DBD", "DCM", "DDD", "DELL", "DGLY", "DGII", "DIOD", "DLB", "DLGC", "DMD", "DMRC", "DNB", "DOX", "DPW", "DQ", "DRAM", "DRCO", "DRIV", "DRWI", "DSPG", "DST", "DSTI", "DSGX", "DTLK", "DTSI", "DVOX", "DWCH", "DWRE", "DYSL", "EA", "EBIX", "ECOM", "EDGW", "EFII", "EFUT", "EGAN", "EGHT", "EGOV", "EIGI", "ELLI", "ELNK", "ELON", "ELSE", "ELTK", "ELX", "EMC", "EMAN", "EMKR", "ENPH", "ENVI", "ENTG", "ENTR", "EONC", "EOPN", "EPAM", "EPAY", "EPIQ", "EQIX", "ERIC", "ESIO", "ESE", "ESP", "ETAK", "EVOL", "EVTC", "EXA", "EXAR", "EXE", "EXFO", "EXTR", "EZCH", "FALC", "FARO", "FB", "FCS", "FDS", "FEIM", "FEIC", "FEYE", "FENG", "FFIV", "FICO", "FIO", "FIS", "FLDM", "FLEX", "FLTX", "FNSR", "FORTY", "FORM", "FRP", "FSL", "FSLR", "FTNT", "FTR", "FU", "GA", "GAME", "GCOM", "GEOS", "GIB", "GIGM", "GIGA", "GIG", "GIMO", "GILT", "GKNT", "GLOW", "GLUU", "GLW", "GNCMA", "GOGO", "GOOG", "GRMN", "GRPN", "GRVY", "GSAT", "GSB", "GSIT", "GSIG", "GTAT", "GUID", "GTT", "GVP", "GWAY", "GWRE", "HAUP", "HCOM", "HILL", "HIMX", "HITT", "HLIT", "HMNY", "HPQ", "HRS", "HSOL", "HSTM", "HTCH", "HTCO", "HURC", "I", "IACI", "IBM", "ICAD", "IDCC", "IDSY", "IDT", "IDTI", "IEC", "IFON", "IGLD", "IGOI", "IGT", "IGTE", "IHS", "IIJI", "IIVI", "IKAN", "IL", "IMI", "IMMR", "IMN", "IMOS", "IMPV", "INAP", "INFA", "INFY", "INFN", "ININ", "INOD", "INPH", "INS", "INTC", "INTT", "INTU", "INVE", "INXN", "INVN", "IO", "IPAS", "IPDN", "IPHI", "IPGP", "IQNT", "IRDM", "IRF", "IRM", "ISIL", "ISNS", "ISS", "ISSI", "IT", "ITI", "ITRI", "IVAC", "IXYS", "JASO", "JBL", "JCOM", "JCS", "JDSU", "JIVE", "JKHY", "JNPR", "JRJC", "JST", "KBALB", "KEM", "KEYW", "KLAC", "KLIC", "KNM", "KONE", "KONG", "KOPN", "KT", "KTCC", "KVHI", "KYO", "LDOS", "LDR", "LDK", "LEAP", "LEDS", "LFUS", "LIQD", "LIVE", "LLNW", "LLTC", "LMOS", "LOCK", "LOCM", "LNKD", "LONG", "LOGI", "LOOK", "LOGM", "LORL", "LPL", "LRAD", "LPTH", "LRCX", "LSCC", "LSI", "LTON", "LTRX", "LTXC", "LUNA", "LVLT", "LXFT", "LXK", "MAMS", "MANH", "MARK", "MANT", "MATR", "MBIS", "MBT", "MCHP", "MCRS", "MCRL", "MDAS", "MCZ", "MDSO", "MEAS", "MEI", "MEET", "MENT", "MERU", "MFLX", "MGIC", "MIND", "MITL", "MIXT", "MITK", "MKSI", "MKTG", "MKTO", "MKTY", "MLNX", "MNDO", "MOBI", "MOCO", "MONT", "MOLX", "MORN", "MOSY", "MOVE", "MPWR", "MRCY", "MRGE", "MRIN", "MRVL", "MSCC", "MSCI", "MSFT", "MSI", "MSPD", "MSTR", "MTSC", "MTSI", "MTSL", "MTSN", "MU", "MVIS", "MX", "MXIM", "MXL", "MXT", "MXWL", "N", "NANO", "NATI", "NCIT", "NCR", "NCTY", "NEON", "NETE", "NEWN", "NICE", "NIHD", "NINE", "NLSN", "NLST", "NMRX", "NOK", "NOW", "NPTN", "NQ", "NSIT", "NSR", "NSYS", "NTAP", "NTE", "NTES", "NTGR", "NTCT", "NTLS", "NTL", "NTT", "NTS", "NTWK", "NUAN", "NVEC", "NVDA", "NVMI", "NVTL", "NXPI", "OCZ", "OCLR", "OESX", "OIBR-C", "OIBR", "OIIM", "OLED", "OMCL", "ONSM", "ONNN", "OPAY", "OPEN", "OPLK", "ORBK", "ORBC", "ORBT", "ORCL", "ORAN", "ORCT", "OTEL", "OTEX", "OTIV", "OVRL", "OVTI", "PACT", "PAMT", "PAR", "PANW", "PCO", "PCTI", "PCYG", "PDFS", "PEGA", "PERI", "PFPT", "PGI", "PHI", "PINC", "PKE", "PKT", "PLAB", "PLCM", "PLNR", "PLT", "PLUS", "PLUG", "PLXS", "PLXT", "PMCS", "PMTC", "PNTR", "POWI", "PRCP", "PRFT", "PRGS", "PRKR", "PRO", "PRSS", "PSEM", "PSMI", "PT", "PTGI", "PTIX", "PTNR", "PULS", "PWRD", "PXLW", "QADA", "QBAK", "QCOM", "QIHU", "QLIK", "QLGC", "QLYS", "QNST", "QTM", "QSII", "QUIK", "QUMU", "RALY", "RATE", "RAX", "RBCN", "RCI", "RDA", "RDCM", "RDWR", "REDF", "RFIL", "RFMD", "RHT", "RITT", "RKUS", "RMBS", "RNET", "RNG", "RNIN", "RNWK", "ROVI", "RP", "RRST", "RSTI", "RST", "RSYS", "RTEC", "RVBD", "RVLT", "RWC", "S", "SAAS", "SABA", "SAIC", "SANM", "SAPE", "SATS", "SAP", "SCKT", "SCMR", "SCON", "SCTY", "SCSC", "SEAC", "SEV", "SFUN", "SGI", "SGK", "SGMA", "SHEN", "SHOR", "SIFY", "SIGM", "SILC", "SIMG", "SIMO", "SINA", "SKM", "SLAB", "SLH", "SLI", "SLP", "SLTC", "SMCI", "SMI", "SMIT", "SMSI", "SMTX", "SMTC", "SNCR", "SNDK", "SNPS", "SOFO", "SOHU", "SOL", "SONS", "SPA", "SPCB", "SPIL", "SPIR", "SPNS", "SPLK", "SPRT", "SPSC", "SPRD", "SPWR", "SQNS", "SQI", "SREV", "SSNC", "SSNI", "SSYS", "ST", "STM", "STP", "STRM", "STRN", "STRP", "STV", "STX", "SUNE", "SUPX", "SWI", "SWIR", "SWKS", "SYKE", "SYMC", "SYMM", "SYNA", "SYNC", "SYNT", "SYPR", "SYX", "T", "TACT", "TAOM", "TBOW", "TCCO", "TCX", "TCL", "TDC", "TDS", "TEF", "TEL", "TEO", "TER", "TI-A", "TI", "TIBX", "TIK", "TIGR", "TISA", "TKC", "TLAB", "TLK", "TMUS", "TNGO", "TNAV", "TQNT", "TRAK", "TRIP", "TRLA", "TRMB", "TRMR", "TRNS", "TRT", "TSEM", "TSL", "TSRA", "TSRI", "TSM", "TSTC", "TST", "TSU", "TSYS", "TTGT", "TTMI", "TU", "TTWO", "TWER", "TWTC", "TWTR", "TXCC", "TXN", "TXTR", "TYL", "TYPE", "TZOO", "UBIC", "UBNT", "UCTT", "UIS", "ULTI", "UMC", "UNXL", "UPIP", "USM", "USMO", "UTEK", "UTSI", "VCLK", "VDSI", "VCRA", "VEEV", "VECO", "VELT", "VG", "VHC", "VIAS", "VIDE", "VICR", "VII", "VIMC", "VIP", "VIV", "VJET", "VMEM", "VLTC", "VMW", "VNET", "VOD", "VOCS", "VPG", "VRNG", "VRNT", "VRSN", "VRTU", "VSAT", "VSH", "VTSS", "VZ", "WAVX", "WBMD", "WDAY", "WDC", "WGA", "WIFI", "WIN", "WIT", "WIRE", "WPCS", "WSTL", "WTT", "WUBA", "WWWW", "XLNX", "XPLR", "XRSC", "XRTX", "XRX", "XXIA", "YELP", "YGE", "YHOO", "YNDX", "YOKU", "YY", "ZHNE", "ZIGO", "ZIXI", "ZNGA", "ZOOM" ] }
{ "_id" : "Consumer Goods", "Acoes" : [ "AAPL", "ABV", "ACAT", "ACCO", "ACU", "ACW", "ADM", "AEPI", "AGRO", "AKO-A", "AKO-B", "ALCO", "ALN", "ALSN", "ALV", "AMWD", "AMTY", "ANDE", "AOI", "APP", "ARCI", "ATR", "ATX", "AVP", "AVY", "AXL", "BC", "BDBD", "BDE", "BEAM", "BERY", "BEST", "BF-B", "BG", "BGS", "BLL", "BMS", "BNNY", "BORN", "BREW", "BRFS", "BRID", "BSET", "BTH", "BTI", "BTN", "BUD", "BWA", "CAAS", "CAG", "CAJ", "CALM", "CAW", "CCE", "CCH", "CCK", "CCU", "CELM", "CELH", "CENT", "CHD", "CHMP", "CHSCP", "CL", "CLW", "CLX", "CMFO", "CMT", "COBR", "COH", "COKE", "COLM", "COTY", "COT", "CPB", "CPGI", "CPS", "CQB", "CRESY", "CRI", "CRMB", "CROX", "CRWS", "CSL", "CTB", "CTIB", "CVGW", "CWTR", "CXDC", "DAKT", "DAN", "DECK", "DEER", "DEO", "DF", "DFZ", "DLA", "DLPH", "DMND", "DOLE", "DORM", "DPS", "DSKX", "DSWL", "DW", "EBF", "ECL", "EDS", "EGT", "EL", "ELY", "ENR", "ESCA", "ESYS", "ETH", "EVK", "EVRY", "F", "FARM", "FBHS", "FBR", "FDML", "FDP", "FFHL", "FHCO", "FIZZ", "FL", "FLO", "FLXS", "FN", "FMX", "FNP", "FOSL", "FOXF", "FSS", "FSYS", "GAGA", "GEF", "GIII", "GIL", "GIS", "GLDC", "GLT", "GM", "GMCR", "GMK", "GNTX", "GPIC", "GPK", "GRIF", "GRO", "GT", "HAS", "HAR", "HBI", "HELE", "HLF", "HMC", "HNI", "HOFT", "HOG", "HRL", "HSH", "HSY", "HY", "IBA", "ICON", "INGR", "IP", "IPAR", "IRBT", "JAH", "JAKK", "JBSS", "JCI", "JJSF", "JOEZ", "JOUT", "JSDA", "JVA", "K", "KEQU", "KID", "KMB", "KNDI", "KNL", "KO", "KOF", "KODK", "KOSS", "KRFT", "KS", "KTEC", "LANC", "LBIX", "LBY", "LCUT", "LEA", "LEG", "LF", "LKQ", "LMNR", "LNCE", "LO", "LUK", "LULU", "LWAY", "LZB", "MAT", "MDLZ", "MERC", "MFRM", "MGPI", "MINI", "MJN", "MKC", "MLHR", "MLR", "MNRO", "MO", "MNST", "MOD", "MOV", "MPAA", "MPX", "MSN", "MTEX", "MTOR", "MWV", "MYE", "NAV", "NCFT", "NKE", "NLS", "NP", "NPK", "NSANY", "NTIC", "NTZ", "NUS", "NUTR", "NWL", "OBT", "OBCI", "OI", "OINK", "OME", "ONP", "OSK", "OXM", "PAY", "PBH", "PBI", "PCAR", "PEP", "PERY", "PF", "PG", "PHG", "PII", "PKG", "PLOW", "PM", "POOL", "POST", "PPC", "PRMW", "PVH", "QTWW", "RAI", "RCKY", "RDEN", "REED", "REMY", "REV", "RFP", "RKT", "RL", "RMCF", "ROG", "ROX", "SAFM", "SAM", "SANW", "SCL", "SCS", "SCSS", "SEB", "SEED", "SEE", "SENEA", "SENEB", "SGC", "SGOC", "SHFL", "SHLO", "SHOO", "SJM", "SKUL", "SKX", "SLGN", "SMP", "SNAK", "SNE", "SODA", "SORL", "SON", "SPAR", "SPU", "SQBG", "SR", "SRI", "STKL", "STLY", "STRI", "STRT", "STS", "STZ", "SUP", "SUMR", "SWSH", "SWM", "SYUT", "TAP", "TBAC", "TEN", "TFCO", "TG", "THO", "THS", "THRM", "THST", "TIS", "TLF", "TM", "TOF", "TPX", "TR", "TRW", "TSLA", "TSN", "TTM", "TUP", "TWI", "TXIC", "UA", "UEIC", "UG", "UFS", "UFPT", "UL", "UN", "UNF", "UVV", "VC", "VCO", "VFC", "VGR", "VIRC", "VRA", "VRS", "WBC", "WEYS", "WGO", "WHR", "WILC", "WNC", "WPP", "WPRT", "WVVI", "WWAV", "WWW", "XNY", "XRM", "ZA", "ZEP", "ZQK", "ZX" ] }
{ "_id" : "Utilities", "Acoes" : [ "ADGE", "AEE", "AEP", "AES", "ALE", "AMID", "APU", "ARTNA", "AT", "ATLS", "ATO", "AVA", "AWK", "AWR", "BEP", "BIP", "BKH", "CDZI", "CHC", "CIG", "CLNE", "CMS", "CNL", "CNP", "CORR", "CPK", "CPL", "CPN", "CTWS", "CWCO", "CWT", "CZZ", "D", "DGAS", "DTE", "DUK", "DYN", "EBR", "ED", "EDE", "EDN", "EE", "EGAS", "ELLO", "EIX", "ELP", "ENI", "EOC", "EQT", "ETR", "EXC", "FCEL", "FE", "FNRG", "GAS", "GXP", "HE", "HNP", "HTM", "IDA", "ITC", "JE", "KEP", "LG", "LNT", "MDU", "MGEE", "MSEX", "NEE", "NGG", "NI", "NJR", "NKA", "NRG", "NU", "NVE", "NWE", "NWN", "NYLD", "OGE", "OKE", "OPTT", "ORA", "OTTR", "PAM", "PCG", "PCYO", "PEG", "PEGI", "PNG", "PNM", "PNW", "PNY", "POM", "POR", "PPL", "RGCO", "SBS", "SCG", "SJI", "SJW", "SMLP", "SO", "SPH", "SRE", "STR", "SWX", "SXE", "TAC", "TE", "TEG", "TGS", "TRP", "UGI", "UIL", "UNS", "UTL", "VVC", "WEC", "WGL", "WR", "WTR", "XEL", "YORW" ] }
{ "_id" : "Industrial Goods", "Acoes" : [ "AAON", "ABB", "ACFN", "ACPW", "ADEP", "ADES", "AEGN", "AERT", "AETI", "AGCO", "AGX", "AIMC", "AIN", "AIRI", "AIXG", "ALG", "AME", "AMOT", "AMRC", "AOS", "AP", "APOG", "APWC", "ARTW", "ARTX", "ASTC", "ASTE", "ATI", "ATK", "ATRO", "ATU", "AVAV", "AVHI", "AWI", "AWX", "AZZ", "B", "BA", "BCC", "BDC", "BEAV", "BECN", "BGC", "BGG", "BIN", "BLDP", "BLT", "BNSO", "BOOM", "BRSS", "BWC", "BWEN", "BZC", "BZH", "CADC", "CAE", "CAS", "CAT", "CBAK", "CBI", "CCC", "CCCL", "CCF", "CCIX", "CDTI", "CECE", "CFI", "CFX", "CHCI", "CIR", "CLC", "CLH", "CLNT", "CLWT", "CMCO", "CMI", "CNHI", "COL", "CPAC", "CPST", "CR", "CREG", "CRH", "CRS", "CSTE", "CSTM", "CUI", "CUO", "CVA", "CVCO", "CVR", "CVU", "CVV", "CW", "CWST", "CX", "CYD", "DAR", "DCI", "DCO", "DE", "DEL", "DGI", "DHI", "DHR", "DOOR", "DOV", "DRC", "DXYN", "DY", "EAC", "ECOL", "EEI", "EFOI", "EME", "EML", "EMR", "ENS", "ERII", "ERJ", "ESL", "ESLT", "ETN", "EVAC", "EXP", "FAST", "FELE", "FIX", "FLIR", "FLOW", "FLR", "FLS", "FTEK", "FWLT", "GAI", "GD", "GE", "GENC", "GFA", "GFF", "GGG", "GHM", "GIFI", "GLDD", "GLPW", "GNRC", "GPRC", "GRC", "GRH", "GTI", "GTLS", "GV", "GVA", "GY", "HAYN", "HCCI", "HDNG", "HEAT", "HEI", "HEES", "HI", "HIHO", "HII", "HNH", "HON", "HOLI", "HOV", "HPJ", "HUB-B", "HW", "HWG", "HXM", "HXL", "HYGS", "ICA", "IDN", "IDSA", "IEX", "IESC", "IGC", "IIN", "IR", "ISSC", "ITT", "ITW", "JBT", "JCTCF", "JHX", "JKS", "JOY", "KAI", "KAMN", "KBH", "KMT", "LAYN", "LECO", "LEN", "LGL", "LII", "LLL", "LMIA", "LMT", "LNN", "LXFR", "LYTS", "MAG", "MAS", "MASC", "MDC", "MEA", "MFRI", "MHK", "MHO", "MICT", "MIDD", "MKTAY", "MLM", "MLI", "MNTX", "MOG-A", "MRC", "MTRX", "MTW", "MTZ", "MTH", "MWA", "MY", "MYRG", "NCS", "NDSN", "NES", "NFEC", "NJ", "NNBR", "NOC", "NPO", "NTK", "NVR", "NX", "OC", "OFLX", "ORB", "ORN", "OSIS", "PATK", "PCP", "PESI", "PFIN", "PGEM", "PGTI", "PH", "PHM", "PIKE", "PKOH", "PLL", "PLPC", "PMFG", "PNR", "POPE", "POWL", "PPO", "PRIM", "PRLB", "PSIX", "PWR", "RAVN", "RBC", "REFR", "RGR", "RINO", "ROK", "ROLL", "ROP", "RS", "RSG", "RSOL", "RTN", "RXN", "RYL", "RYN", "SCHN", "SCX", "SI", "SIF", "SKY", "SMED", "SNA", "SNHY", "SPB", "SPF", "SPR", "SPW", "SRCL", "SSD", "STCK", "STRL", "SVT", "SWHC", "SWK", "SXI", "TASR", "TATT", "TAYD", "TDG", "TDY", "TECUA", "TEX", "TGI", "THR", "THTI", "TILE", "TKR", "TMHC", "TNC", "TOL", "TOWR", "TPC", "TPH", "TREX", "TRIT", "TRS", "TRR", "TS", "TTC", "TWIN", "TXI", "TXT", "UFI", "UFPI", "ULBI", "UQM", "USCR", "USG", "USLM", "UTX", "VE", "VMC", "VMI", "VTNR", "WCN", "WM", "WOR", "WSCI", "WTS", "WWD", "WY", "XIN", "XLS", "XONE", "XYL", "ZBB", "ZBRA", "ZEUS", "ZOLT" ] }

Exercício3 –FraudenaEnron!

1.Liste as pessoas que enviaram e-mails (de forma distinta, ou seja, sem repetir). Quantas pessoas são?


2.Contabilize quantos e-mails tem a palavra “fraud”

> db.eron.count({"message" : /fraud/})
3
