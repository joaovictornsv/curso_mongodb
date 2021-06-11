<div align="left">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original.svg" width=25>
  <sup><a href="https://github.com/joaovictornsv/curso_mongodb">Voltar ao início</a></sup>
</div>

<div align="center">
  <h1>Seção 3</h1>
  <h2>Inserção de dados</h2>
</div>

<br/>

- Inserindo dados
```
db.<collection>.insertOne({ <dados> })
```

- Inserindo vários dados
```
db.<collection>.insertMany([ <dados...> ])
```

- Write Concern

É uma configuração que pode ser inserida no `insertMany`. Ela permite limitar o tempo de execução da inserção, retornando um erro de *time out* caso exceda o mesmo.

Exemplo:
```bash
db.<collection>.insertMany([ <dados...> ], { w: 'majority', wtimeout: 100 })
# A inserção tem 100ms para ser executada
```
