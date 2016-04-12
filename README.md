# loopback-cheatsheet DRAFT

## Default remote methods
### PersistedModel
| Name               | Static | Method | Route     |
|--------------------|--------|--------|----------|
| find               | true   | GET    | /objects
| upsert             | true   | PUT    | /objects
| create             | true   | POST   | /objects
| findById           | true   | GET    | /objects/:id
| exists             | true   | HEAD   | /objects/:id
| --                 | --     | GET    | /objects/:id/exists 
| updateAttributes   | false  | PUT    | /objects/:id
| deleteById         | true   | DELETE | /objects/:id
| createChangeStream | true   | GET    | /objects/change-stream
| --                 | --     | POST   | /objects/change-stream
| count              | true   | GET    | /objects/count
| findOne            | true   | GET    | /objects/findOne
| updateAll          | true   | POST    | /objects/update

### Relations

| Name                    | Static | Method | Route     
|-------------------------|--------|--------|----------
| __get__relation         | false  | POST   | /objects/:id/relation
| __create__relation      | false  | POST   | /objects/:id/relation
| __delete__relation      | false  | DELETE | /objects/:id/relation
| __findById__relation    | false  | GET    | /objects/:id/relation/:fk
| __updateById__relation  | false  | PUT    | /objects/:id/relation/:fk
| __destroyById__relation | false  | DELETE | /objects/:id/relation/:fk
| __count__relation       | false  | GET    | /objects/:id/relation/count
