# Firefly in IRSA (ADASS2018)

## DEMO

### Lightcurve

m109 light curve wise: https://irsa.ipac.caltech.edu/workspace/TMP_fd7GHO_4548/Gator/irsa/4602/tbview.html


### Finder Chart
https://irsa.ipac.caltech.edu/onlinehelp/finderchart/#id=api

### API usage: NED, ATLAS, Herchel, etc
- docs file:///Users/ejoliet/projects/firefly/build/firefly/war/docs/js/index.html
    - gradle :buildJsDoc
- See Atlas example, show page source
    - https://irsa.ipac.caltech.edu/data/SPITZER/Abell1763/
- NED: API + IRSAViewer usage
    - http://ned.ipac.caltech.edu/?q=byname&list_limit=5&omegam=0.27&obj_sort=RA%20or%20Longitude&extend=no&out_csys=Equatorial&img_stamp=YES&objname=arp220&out_equinox=J2000.0&corr_z=1&omegav=0.73&of=pre_text&hconst=73&keyword=objname
    - launch IRSAViewer from there
- demo/ffapi-sia.html , see SIA url example https://irsa.ipac.caltech.edu/docs/irsa_image_server.html

### HIPS: 
SDSS, dss, allwise, 2mass + ivo:// url from here https://irsa.ipac.caltech.edu/data/hips/list

more here http://aladin.u-strasbg.fr/java/nph-aladin.pl?frame=aladinHpxList

### Dev
MOC
Footprint
Slate

### Demo python:
- install FF client for python
```
  git clone https://github.com/Caltech-IPAC/firefly_client.git
  cd firefly_client/
  pip install -e .
 wget http://web.ipac.caltech.edu/staff/roby/demo/2mass-m31-green.fits
 wget http://web.ipac.caltech.edu/staff/roby/demo/m31-2mass-2412-row.tbl
  python
```
- in py console, import and launch viewer
```
from firefly_client import FireflyClient
fc = FireflyClient('https://irsa.ipac.caltech.edu/irsaviewer')
```
#show image
```fval = fc.upload_file('2mass-m31-green.fits')
fc.show_fits(fval)
```

#display table
``` tval = fc.upload_file('m31-2mass-2412-row.tbl')
   fc.show_table(tval)
```

#notebook
```jupyter notebook
 ```
