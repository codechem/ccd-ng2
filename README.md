
[![Build Status](https://travis-ci.org/codechem/ccd-ng2.svg?branch=master)](https://travis-ci.org/codechem/ccd-ng2)

<div style="display:flex;align-items:center;>
<label style="height:30px;height: 40px; line-height: 30px; padding-right: 20px;">
    
</label>
<a href="https://github.com/codechem/ccd" style="padding-right: 20px;display:flex;align-items:center;"">
    <label style="height:30px;height: 40px; line-height: 30px;padding-right: 10px;">
        <b>NG2 Decorator for CCD Framework</b>
    </label>
    <img style="height:60px" src="https://raw.githubusercontent.com/codechem/ccd-snippets/master/images/ccdLogo.png"></img>
</a>
</div>

## CCD-NG2 

Provides ```@ngGenSvc``` decorator that generates angular2 services for a given ```CCController```
### Example
```typescript 
@ngSvcGen('./client/svc', true)
class HelloCtrl extends CCController{
    @get('/hello/:name')    
    helloWorld(req, res){
        return `hello ${req.params.name}`
    }

    @post('/:id')    
    doSomething(req, res){
        return ....
    }
    ...
}
```

### Output in ```./client/svc```:
```typescript
import { Injectable } from '@angular/core';
import { SimpleRestService } from 'ccNgRest';

@Injectable()
export class HelloCtrlSvc{
    constructor(private rest: SimpleRestService){}

    helloWorld(name){
        return this.rest.get('/hello/'+name);
    }

    doSomething(id, payload){
        return this.rest.post('/'+id, payload);
    }
}
```
