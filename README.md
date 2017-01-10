# loopback-cheatsheet DRAFT

## CLI commands
| Command | Description |
|----|----|
| ```slc loopback:app [options] [<name>]``` |	Create a new LoopBack application  [(see docs)](https://docs.strongloop.com/display/LB/Application+generator) |
| ```slc loopback:datasource [options] [<name>]``` |	Add a new data source to a LoopBack application [(see docs)](https://docs.strongloop.com/display/LB/Data+source+generator) |
| ```slc loopback:model [options] [<name>]``` |	Add a new model to a LoopBack application [(see docs)](https://docs.strongloop.com/display/public/LB/Model+generator) |
| ```slc loopback:property [options]```	|	Add a new property to an existing model [(see docs)](https://docs.strongloop.com/display/LB/Property+generator) |
| ```slc loopback:acl [options]``` |	Add a new access control list (ACL) entry to the LoopBack application [(see docs)](https://docs.strongloop.com/display/LB/ACL+generator) |
| ```slc loopback:relation [options]``` |	Add a new model relationship [(see docs)](https://docs.strongloop.com/display/public/LB/Relation+generator) |
| ```slc loopback:remote-method [options] [<modelName>] [<methodName>]```	|	Add a new remote method [(see docs)](https://docs.strongloop.com/display/LB/Remote+method+generator) |
| ```slc loopback:middleware [options] [<name>]``` |	Add a new middleware configuration [(see docs)](https://docs.strongloop.com/display/public/LB/Middleware+generator) |
| ```slc loopback:boot-script [options] [<name>]```	|	Add a new boot scripts [(see docs)](https://docs.strongloop.com/display/public/LB/Boot+script+generator) |
| ```slc loopback:export-api-def [options]```	|	Export Swagger API definition  [(see docs)](https://docs.strongloop.com/display/public/LB/API+definition+generator) |
| ```slc loopback:swagger [options] [<name>]``` | Generates a fully-functional application that provides the APIs conforming to the Swagger 2.0 specification [(see docs)](https://docs.strongloop.com/display/public/LB/Swagger+generator) |

## Default remote methods
### PersistedModel
| Name               | Static | Method | Route    | Operation hooks invoked |
|--------------------|--------|--------|----------|-------|
| find               | true   | GET    | /objects | access, loaded
| upsert (updateOrCreate) | true | PUT | /objects | access, before save, after save, loaded, persist
| create             | true   | POST   | /objects | before save, after save, loaded, persist
| findById           | true   | GET    | /objects/:id | access, loaded
| exists             | true   | HEAD   | /objects/:id | access, loaded
| --                 | --     | GET    | /objects/:id/exists |
| updateAttributes   | false  | PUT    | /objects/:id | before save, after save, loaded, persist
| deleteById         | true   | DELETE | /objects/:id | access, before save, after save, loaded, persist
| createChangeStream | true   | GET    | /objects/change-stream |
| --                 | --     | POST   | /objects/change-stream |
| count              | true   | GET    | /objects/count | access, loaded
| findOne            | true   | GET    | /objects/findOne | access, loaded
| updateAll          | true   | POST   | /objects/update | access, before save, after save, persist

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
