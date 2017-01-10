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
| Name               | Endpoint | Operation hooks invoked |
|--------------------|----------|----------|-------|
| bulkUpdate
| changes
| checkpoint
| count                 | GET /_modelName_/count | access, loaded
| create                | POST /_modelName_ | before save, after save, loaded, persist
| createChangeStream    | GET /_modelName_/change-stream<br />POST /_modelName_/change-stream |
| createUpdates
| currentCheckpoint
| destroyAll
| destroyById           | DELETE /_modelName_/_modelID_ | access, before save, after save, loaded, persist
| diff
| enableChangeTracking
| exists                | GET /_modelName_/_modelID_/exists<br />HEAD /_modelName_/_modelID_ | access, loaded
| find                  | GET /_modelName_ | access, loaded
| findById              | GET /_modelName_/_modelID_ | access, loaded
| findOne               | GET /_modelName_/findOne | access, loaded
| findOrCreate            
| getChangeModel
| geIdName
| getSourceId
| handleChangeError
| rectifyChange
| replaceById
| replaceOrCreate
| replicate
| updateAll             | POST /_modelName_/update | access, before save, after save, persist
| upsert                | PUT /_modelName_ | access, before save, after save, loaded, persist
| upsertWithWhere       
|
| prototype.destroy   
| prototype.getId
| prototype.getIdName
| prototype.isNewRecord
| prototype.reload
| prototype.replaceAttributes
| prototype.save
| prototype.updateAttribute  
| prototype.updateAttributes | PUT /_modelName_/_modelID_ | before save, after save, loaded, persist

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
