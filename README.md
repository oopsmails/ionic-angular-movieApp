# ionic-angular-movieApp

https://ionicacademy.com/ionic-4-app-api-calls/

## movies.page

- returning Observable in .ts
```
results: Observable<any>;
...
searchChanged() {
    // Call our service function which returns an Observable
    this.results = this.movieService.searchData(this.searchTerm, this.type);
}
```
- use async pipe in html

`<ion-item button *ngFor="let item of (results | async)" [routerLink]="['/', 'movies', item.imdbID]">`


## movie-details.page

- using normal Observable.subscribe()

```
ngOnInit() {
    // Get the ID that was passed with the URL
    const id = this.activatedRoute.snapshot.paramMap.get('id');

    // Get the information from the API
    this.movieService.getDetails(id).subscribe(result => {
      this.information = result;
    });
}
```

- open web site page

```
openWebsite() {
    window.open(this.information.Website, '_blank');
}
```

## Using @ionic/lab

- Install the Lab Package

`npm i @ionic/lab`

- Run your app with device preview and platform styles

`ionic lab`


