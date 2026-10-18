# Ndom a ciapa i fons: dati delle province

Pacchetti provincia per l'app Android **Ndom a ciapa i fons**, che stima le zone buone per cercare porcini
(*Boletus edulis*, *aereus*, *reticulatus*, *pinophilus*).

Ogni provincia è divisa in celle da 250 m. Per ogni cella il pacchetto contiene il tipo di bosco, la quota, la
pendenza, l'esposizione e il comune. L'app ci aggiunge il meteo (scaricato sul telefono da Open-Meteo) e i
ritrovamenti vicini e calcola un indice da 0 a 100 per specie.

I file sono nelle [release](../../releases) del repository, non nel codice.

## Contenuto

| File | Cosa contiene |
|---|---|
| `indice.json` | elenco delle province: versione, dimensione, impronta sha256 dello zip, province confinanti, contorno semplificato |
| `<SIGLA>.zip` | pacchetto di una provincia (es. `PR.zip`): celle, confine, punti meteo, ritrovamenti pubblici, parametri di calcolo |

L'app legge `indice.json` all'indirizzo
`https://github.com/caombog/ndom-dati/releases/latest/download/indice.json` e scarica solo le province scelte.
Il formato è descritto in `docs/formato_pacchetto.md` del progetto che genera i dati.

## Come si aggiornano

I pacchetti si generano con il progetto Python dell'app (`scripts/prepare_all.py`, poi `scripts/export_package.py`)
e si caricano nella release `dati`. Quando un pacchetto cambia, cambia la sua versione nell'indice e l'app
propone l'aggiornamento.

## Fonti e licenze

I pacchetti sono elaborati da questi dati, che restano dei rispettivi titolari:

- **Boschi (tutta Italia)**: Corine Land Cover 2018.
  © European Union, Copernicus Land Monitoring Service 2018, European Environment Agency (EEA).
  Uso libero con citazione della fonte.
- **Boschi (Lombardia)**: Carta forestale (tipi forestali), Regione Lombardia,
  [Geoportale della Lombardia](https://www.geoportale.regione.lombardia.it).
  Licenza indicata nella scheda del dato (per i dati forestali regionali, in genere CC BY 4.0).
- **Boschi (Sardegna)**: Carta dell'Uso del Suolo 2008 e Carta forestale del Distretto Arci-Grighine,
  Regione Autonoma della Sardegna, [Sardegna Geoportale](https://www.sardegnageoportale.it).
  Licenza indicata nella scheda del dato (per molti dati regionali CC BY 4.0).
- **Quote, pendenza ed esposizione**: Copernicus DEM GLO-90.
  Produced using Copernicus WorldDEM™-90 © DLR e.V. 2010-2014 and © Airbus Defence and Space GmbH 2014-2018,
  provided under COPERNICUS by the European Union and ESA; all rights reserved.
  [doi:10.5270/ESA-c5d3d65](https://doi.org/10.5270/ESA-c5d3d65)
- **Confini di province e comuni**: ISTAT (CC BY), nella versione GeoJSON di
  [openpolis/geojson-italy](https://github.com/openpolis/geojson-italy) (CC BY 4.0).
- **Ritrovamenti pubblici**: [GBIF.org](https://www.gbif.org) e [iNaturalist](https://www.inaturalist.org).
  Ogni ritrovamento mantiene la licenza del record originale (CC0, CC BY o CC BY-NC, a seconda dell'autore):
  nei pacchetti c'è il link alla scheda di ciascuno. Quelli CC BY-NC non sono utilizzabili a scopo commerciale.

Non fanno parte dei pacchetti, ma l'app li usa direttamente:

- **Meteo**: [Open-Meteo](https://open-meteo.com) (CC BY 4.0; l'API gratuita è per uso non commerciale).
- **Carte di base**: OpenTopoMap (© OpenStreetMap, SRTM, CC BY-SA), [OpenFreeMap](https://openfreemap.org)
  (© OpenMapTiles, © OpenStreetMap contributors), Esri World Imagery (© Esri);
  rilievo ombreggiato dai Terrain Tiles (Mapzen, AWS Open Data).

## Licenza dei pacchetti

I pacchetti (l'elaborazione: celle, tipi di bosco per cella, quote, esposizioni, parametri di calcolo) sono
distribuiti con licenza [Creative Commons Attribuzione 4.0 Internazionale (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/deed.it):
puoi usarli, anche per scopi commerciali, citando "Ndom a ciapa i fons" e le fonti elencate sopra.

Restano valide le licenze dei dati di partenza: in particolare i ritrovamenti pubblici mantengono quella del
singolo record (alcuni sono CC BY-NC).

## Avvertenza

L'indice è una stima basata su modelli e dati con i loro limiti: non garantisce la presenza di funghi.
Prima di raccogliere verifica sempre le regole della tua regione (permessi, quantità, giorni consentiti)
e rispetta le proprietà private e le aree protette.
