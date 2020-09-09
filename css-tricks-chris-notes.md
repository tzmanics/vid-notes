# getting setup
## install ng

npm i @angular/cli

## create a new project

ng new <project-name>
cd <project-name>
ng serve
localhost:4200

## add scully

ng add @scullyio/init
ng build --prod
npm run scully:serve

// project now in dist/static

# creating a blog
## add scully blog support
ng generate @scullyio/init:blog
//you can use another name for the dir after the colon

# create the entry point
ng generate module home --route=home --module=app-routing

# change route
code src/app/app-routing.module.ts

```ts
{
  path: '',
  loadChildren: () ...
```

# add route discovery

code src/app/home home.component.ts

```ts
import { ScullyRoutesService, ScullyRoute } from '@scullyio/ng-lib';
import { Observable } from 'rxjs';

@Component()
//...
export class HomeComponent implements OnInit {
  links$: Observable<ScullyRoute[]> = this.scully.available$;

    constructor(private scully: ScullyRoutesService) {}

      ngOnInit() {
        this.links$.subscribe((links) => {
          console.log(links);
        });
      }
    }


```
