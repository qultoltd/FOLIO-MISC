###Vagrant
* Virtal Box telepítése, ha még nincs felrakva
* Érdemes a testing-backend vagrant boxot (https://app.vagrantup.com/folio/boxes/testing-backend) használni mivel 
a böngésző catchel, és ha a teljes testinget használnánk, akkor catchelné a boxban lévő stripes-ot.

## Mindennapos Folio UI fejlesztés előtt:
* ```vagrant up``` a megfelelő vagrant mappában
* PowerShell cd a ui modulokat tartalmazó mappába 

     ```text
     $dirs = Get-ChildItem -Path . | ?{ $_.PSIsContainer }
        $back = pwd
      foreach ($dir in $dirs)
      {
      cd $dir.FullName
      echo $dir.FullName
      git pull origin
      }
      cd $back.Path
     ```
    * ez a parancs az adott mappán belül lévő mappáákon végigmenve mindegyikre külön külön meghívja a ```git pull``` 
    parancsot
          
*   Majd a ```yarn``` vagy a ```yarn install``` parancs futtatásával a yarn leszedi a megfelelő npm modulokat, és 
    lebuildeli a projektet (a mvn hez hasonlóan)
*   Ez után a ```cd stripes-sample-platform ``` mappában ```stripes serve```
    * Ha Memory leak error van egy webpack buildnél akkor csak újra kell indítani
   
   
###Fejlesztés végén pedig    
* Ki kell lőni a stripesot
* Majd a Vagrant-ot ```vagrant halt```     
      
###Ha dropolni akarod az adatbázist
* ```vagrant destroy``` - kitörli a teljes vagrant boxot db-stől...
* majd ugyanitt ```vagrant up```


# Folio alapok
https://dev.folio.org/ 

https://dev.folio.org/start/ 

https://dev.folio.org/tutorials/

https://app.vagrantup.com/folio/boxes/snapshot

### Stripes alapok
Bevezetés, áttekintés: https://github.com/folio-org/stripes-core/blob/master/doc/overview.md

Stripes alapfogalmak: https://github.com/folio-org/stripes-core/blob/master/doc/modules-apps-etc.md

Stripes developer guide: https://github.com/folio-org/stripes-core/blob/master/doc/dev-guide.md

ES6: http://es6-features.org/#Constants

React: https://reactjs.org/ (a tutorialt érdemes végignézni)

JSX: https://jsx.github.io/

Jogosultságkezelés (backendben és UI-on is definiálni kell jogokat!): https://github.com/folio-org/stripes-core/blob/master/doc/permissions.md

UI jogosultságok felvétele (lokális fejlesztésnél érdekes, ha a hasAllPermissions nincs beállítva, jogosultság élesítése elõtt mindenképp érdemes kipróbálni, hogy mûködik-e): https://github.com/folio-org/stripes-core/blob/master/doc/adding-permissions.md

Stripes connect: https://github.com/folio-org/stripes-connect/blob/master/doc/api.md

Storybook a jelenlegi Stripes komponensek vizualizálásához: http://ux.folio.org/storybook-draft/?selectedKind=Accordion&selectedStory=with%20defaults&full=0&addons=1&stories=1&panelRight=0&addonPanel=REACT_STORYBOOK%2Freadme%2Fpanel

http://ux.folio.org/docs/design-guidelines/components/checkbox/

További infók: https://github.com/folio-org/stripes-core



