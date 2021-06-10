<div align="left">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original.svg" width=25>
  <sup><a href="https://github.com/joaovictornsv/curso_mongodb">Voltar ao início</a></sup>
</div>

<div align="center">
  <h1>Seção 2</h1>
  <h2>Gerenciamento de bancos de dados</h2>
</div>

<br/>

- Mostrar todos os bancos
```
show dbs
```

- Criando banco temporário (ou mudando de banco)
```bash
#Inicializa o banco
use <banco>
```
- Mostrando banco atual
```
db
```
- Removendo banco de dados
```
db.dropDatabase()
```
---
- Criando collection

Implicitamente (inserindo dados)
```
db.<collection>.insertOne(<dados>)
```

Explicitamente (collection vazia)
```
db.createCollection("nome", { opcões })
```

As opções nos permitem configurar a nossa collection, como setar o número máximo de bytes da collection, número máximo de registro etc. Para ler mais sobre as opções, acesse a [documentação](https://docs.mongodb.com/manual/reference/method/db.createCollection/).

- Exibir todas as collections do banco
```
show collections
```

- Removendo collections
```
db.<collection>.drop()
```
---
- Importando bancos (uma collection)
```
mongoimport <arquivo> -d <database> -c <collection>
```

- Exportando bancos (uma collection)
```
mongoexport -d <database> -c <collection> -o <output> 
```

- Exportando bancos maiores (mais de uma collection)
```
mongodump -d <banco> -o <diretorio>
```

- Importando bancos maiores (mais de uma collection)
```
mongorestore <diretorio>
```

- Removendo todos os bancos
```javascript
Mongo().getDBNames().forEach(function(db) {

  if (['admin', 'config', 'local'].indexOf(db) < 0 ) {
    Mongo().getDB(db).dropDatabase();
  }

});
```

---

- Monitoramento do MongoDB
```
mongostat
```
Podemos checar algumas informações como: quantidade de consultas, rodando, consumo de rede e outros dados.
