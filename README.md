# Firefly usage in IPAC/Caltech (ADASS2018)

Scratch notes to copy/paste examples URLs during focus demo ADASS XXVII, 11/13/2018.
(For localhost example, please clone [Firefly](https://github.com/Caltech-IPAC/Firefly) and build/deploy ```gradle :firefly:bAD```
Then demos are here: http://localhost:8080/firefly/demo/ffapi-*.html

## DEMO

### Searching datasets Brushing/Linking

Search with [IRSAviewer](https://irsa.ipac.caltech.edu/irsaviewer/)

WISE search 300" around Pleiades, m109, or favorite object

I can save table, highlight rows, filter, add footprint, change hips, fits when zoom in/out

### Lightcurve

Search via Gator m109, 20" [on WISE Multiepoch photo](https://irsa.ipac.caltech.edu/cgi-bin/Gator/nph-query?catalog=allwise_p3as_mep&spatial=cone&radius=20&radunits=arcsec&objstr=11h57m35.98s+53d22m28.3s)

m109 light curve wise result: https://irsa.ipac.caltech.edu/workspace/TMP_fd7GHO_4548/Gator/irsa/4602/tbview.html

### Finder Chart
https://irsa.ipac.caltech.edu/onlinehelp/finderchart/#id=api

### API usage: NED, ATLAS, Herchel, etc
- docs: file:///Users/ejoliet/projects/firefly/build/firefly/war/docs/js/index.html
    - gradle :firefly:buildJsDoc
- See Atlas example, show page source
    - https://irsa.ipac.caltech.edu/data/SPITZER/Abell1763/
- NED: API + IRSAViewer usage
    - http://ned.ipac.caltech.edu/?q=byname&list_limit=5&omegam=0.27&obj_sort=RA%20or%20Longitude&extend=no&out_csys=Equatorial&img_stamp=YES&objname=arp220&out_equinox=J2000.0&corr_z=1&omegav=0.73&of=pre_text&hconst=73&keyword=objname
    - launch IRSAViewer from there
- http://localhost:8080/firefly/demo/ffapi-highlevel-test.html, taken SIA url example from [here](https://irsa.ipac.caltech.edu/docs/irsa_image_server.html)

```
function loadSIA() {
            var req = firefly.util.table.makeFileRequest('SIA result images',
                    'https://irsa.ipac.caltech.edu/ibe/sia/wise/allsky/4band_p1bm_frm?POS=20,40',
                    null,
                    { pageSize: 15,
                        META_INFO: {
                            positionCoordColumns: 'ra_obj;dec_obj;EQ_J2000',
                            datasource: 'sia_url'
                        }
                    });
            firefly.getViewer().showTable( req, {removable: true, showUnits: false, showFilters: true});
        }
```

### HiPS: 
SDSS, dss, allwise, 2mass + ivo:// url from here https://irsa.ipac.caltech.edu/data/hips/list

[Show six HiPS in one](http://localhost:8080/firefly/demo/six.html)

more here [IRSAViewer](https://irsa.ipac.caltech.edu/irsaviewer)

### Dev
[MOC, Footprint](http://localhost:8080/firefly/), [Slate](http://localhost:8080/firefly/demo/ffapi-slate-test2.html)

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
```
jupyter notebook
```
