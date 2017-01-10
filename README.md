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
| bulkUpdate    | POST /:modelName/bulk-update
| changes       | GET /:modelName/changes *
| checkpoint    | POST /:modelName/checkpoint * 
| count         | GET /:modelName/count | access, loaded
| create                | POST /:modelName | before save, after save, loaded, persist
| createChangeStream    | GET /:modelName/change-stream<br />POST /:modelName/change-stream |
| createUpdates         | POST /:modelName/create-updates
| currentCheckpoint     | GET /:modelName/checkpoint * 
| destroyAll / remove / deleteAll       | DELETE /:modelName
| destroyById / removeById / deleteById | DELETE /:modelName/:modelId | access, before save, after save, loaded, persist
| diff | POST /_modelName_/diff *
| enableChangeTracking
| exists                | GET /:modelName/:modelId/exists<br />HEAD /:modelName/:modelId | access, loaded
| find                  | GET /:modelName | access, loaded
| findById              | GET /:modelName/:modelId | access, loaded
| findLastChange        | GET /:modelName/:modelId/changes/last
| findOne               | GET /:modelName/findOne | access, loaded
| findOrCreate            
| getChangeModel
| geIdName
| getSourceId
| handleChangeError
| rectifyAllChanges   | POST /:modelName/rectify-all *
| rectifyChange       | POST /:modelName/:modelId/rectify-change *
| replaceById
| replaceOrCreate
| replicate
| updateAll / update      | POST /:modelName/update | access, before save, after save, persist
| updateLastChange        | PUT /:modelName/:modelId/changes/last
| upsert / updateOrCreate | PUT /:modelName | access, before save, after save, loaded, persist
| upsertWithWhere       
|
| prototype.destroy / prototype.remove / prototype.delete  
| prototype.getId
| prototype.getIdName
| prototype.isNewRecord
| prototype.reload
| prototype.replaceAttributes
| prototype.save
| prototype.updateAttribute  
| prototype.updateAttributes | PUT /:modelName/:modelId | before save, after save, loaded, persist
 
* : if trackChanges enabled

### Relations

| Name                    | Static | Method | Route     
|-------------------------|--------|--------|----------
| __get__relation         | false  | POST   | /:modelName/:modelId/relation
| __create__relation      | false  | POST   | /:modelName/:modelId/relation
| __delete__relation      | false  | DELETE | /:modelName/:modelId/relation
| __findById__relation    | false  | GET    | /:modelName/:modelId/relation/:fk
| __updateById__relation  | false  | PUT    | /:modelName/:modelId/relation/:fk
| __destroyById__relation | false  | DELETE | /:modelName/:modelId/relation/:fk
| __count__relation       | false  | GET    | /:modelName/:modelId/relation/count
