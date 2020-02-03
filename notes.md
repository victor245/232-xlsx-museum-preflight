## `232-xlsx-museum-preflight`

- revision: February 2020.

#### `xlsx2json.js`

mapping cols to json

```
- xid              // A
- sec              // B
- yp               // C
- circa            // D
- pic              // E : jpeg
- co               // F : country
- h1               // G
- isoc             // H
- h2               // I
- root             // J : other name, author (root-name)!
- yf               // K : year founded
- fr               // L : texte francais
- mk               // M : marque
- en               // N : english
- zh               // O : english
- ci               // P : city
- ci 'sa           // Q : street address
- links            // R : pdf[]
- flags            // S : [RT..]
- npages           // T : number of pages
- rev              // U : revision date (Update)
- com              // V : comments
- ori              // W : origine source du document.
```

#### `reformat.js`
- convert CC (country codes) into ISO.
- trim all fields
- extract {legalName, aka} from isoc (sec 1, sec 2)
- extract {titre, auteurs} from isoc (sec>=3)
- normalize/split flags: deleted, restricted, transcription
- split h2 (col I) into multiple {keywords-products}
- split mk (col M) into multiple marques
- merge cols (R,T) into links[] multiple {fn,np} (pdf-fileNAme, #pages)

#### LOG.

##### Mon Feb 3, 2020
```
101-validate-xlsx.js
  read museum.xls (link to latest)
  $ ln -sf 0-Heating-Museum-from-start-to-31-12-2019-FRENCN-20200203.xlsx museum.xlsx
  errors/alerts are on stdout
  $ 101-validate-xlsx | grep ALERT
```