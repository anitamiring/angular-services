# angular-services
Learning Angular - services 

### About services in Agular
Services have typically 2 usecases:
- code duplication (many components use the same functions eg. log service) 
- data storage (data can be access by many components) 

### Brief project description
This project contain of 3 components:
  - *app.component* - bind everything together (listen to accountAdded and accountChanged event)
  - *account.component* - fire event if account status is changed 
  - *new-acount.component* - listen to a click (new account created) and emit data if button is clicked 
There are 2 services:
  - **logging.service** - common for account.component and new-account.component 
  - Data Service
  
### Using services in Angular 
To instantiate **service** in Agular app we should use ***dependency injectors***. This means that we need to inform Angular that specific component *depends* on some service. As an example here we have *new-account.component* depending on *logging.service* because we want to call method from our logging.servie in this component. To do so, we have to inform Angular that we require such a class: 
- in our component we create constructor which informs which type(class/service) we want to inject 
```
import {LoggingService} from '../logging.service';
constructor (private loggingService: LoggingService) {} <-- This constructor informs about what we want to inject 
```
This works fine, because Angular is responsible for creating/intantiating new objects. We put selectors in our app, so that would be the place where component would be intantiate. Angular is responsible to instantiate object properly. So putting argument in the constructor informs Angular that we require such an argument. Angular recognise it and try to give it to us. So now Angular knows what we want, but it don't know how tu create it. 
- adding providers in our component - it tells Angular how to create an object 
```
@Component({
  .
  .
  .
  providers: [LoggingService]
})
```
- now we can access service propertice in our component eg;
```
this.loggingService.logStatusChange(accountStatus);
```







