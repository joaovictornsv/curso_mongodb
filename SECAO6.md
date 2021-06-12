<div align="left">
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original.svg" width=25>
  <sup><a href="https://github.com/joaovictornsv/curso_mongodb">Voltar ao início</a></sup>
</div>

<div align="center">
  <h1>Seção 6</h1>
  <h2>Remoção de dados</h2>
</div>

<br/>

- Removendo um dado
```
db.<collection>.deleteOne({ <filtro> })
```


- Removendo vaŕios dados
```
db.<collection>.deleteMany({ <filtro> })
```

- Removendo todos os dados de uma collections

Filtro vazio
```
db.<collection>.deleteMany({})
```