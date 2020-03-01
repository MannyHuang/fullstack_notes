# angular 

## cli
```cli
# install cli
npm install -g @angular/cli

# create new app
ng new [appName]

# serve the app
ng serve -o

# genereate component
ng genereate component [compName]

# generate component shorthand
ng g c [compName] --spec false

# generate pipe in specified module
ng g pipe [pipeName] -m [moduleName]

# add pwa functionality
ng add @angular/pwa

# build the app
ng build --prod

# search doc
ng doc [searchTerm]
```

## Roles of Modules
- AppModule
  - import:
    - SharedModule
    - CoreModule
    - LayoutModule
    - RouterModule
    - Angular Module
      - BrowserModule
      - BrowserAnimationsModule
      - HttpClientModule
- LayoutModule
  - import: SharedModule
- LayoutModule
  - don't import: router stuff
  - export: all layout component；
- RouterModule
  - import: SharedModule、CoreModule、LayoutModul, RouteRoutingModule
- CoreModule
  - only providers
- SharedModule
  - general purpose angular modules
    - CommonModule
    - FormsModule
    - RouterModule
    - ReactiveFormsModule)
    - pipes
  - export: all modules
  - should not use provider