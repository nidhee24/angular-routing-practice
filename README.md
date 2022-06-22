## NOTES

<a routerLink="/users">

if the above anchor tag is in app component then if we remove / like this <a routerLink="users"> then it will work perfectly fine but if there are nested component and if you removed / in routerLink then it will give error because in root component there is by default http://localhost/4200/ so there will be no change but if you go one level down then it will take different path ex. users/users so there will be error as there is no such path registered in app module.

but if you use relative path as path of directory in app,
like if you go one path up
<a routerLink="../users">


## We can get currently active route by injecting of type ActivatedRoute and make sure to import it from @angular/router package

Activated route simply injects the currently active routes so for the component you loaded, this will be the route which loaded this component and the route simply is kind of a complex JS obj which keeps a lot of meta information about the currently active route.

## NOTE: The ActivatedRoute Object we injected after giving dynamic path will give us an access to the id passed in URL => Selected user

dynamic path in app module:
#  path:'users/:id/:name', component:UserComponent

## how to access this parameters so in ts file use ActivatedRoute
 user: {id: number, name: string};

  constructor(private route: ActivatedRoute) { }

  ngOnInit() {
    this.user = {
      id:this.route.snapshot.params['id'],
      name:this.route.snapshot.params['name']
    }
  }

  but the above only happens when we are on other component.

  now we can do if we on same component usinf params observable
  Observables are features added by some other third party package, not by angular but heavily work by angular which allows to work with asynchronous tasks and this is ASync task as parameter might changes