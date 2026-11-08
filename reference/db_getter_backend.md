# Backend functions for data download

Backend functions to download data. See
`?`[`get_c14data`](https://docs.ropensci.org/c14bazAAR/reference/db_getter.md)
for a more simple interface and further information.

## Usage

``` r
get_14cpalaeolithic(db_url = get_db_url("14cpalaeolithic"))

get_14sea(db_url = get_db_url("14sea"))

get_adrac(db_url = get_db_url("adrac"))

get_agrichange(db_url = get_db_url("agrichange"))

get_aida(db_url = get_db_url("aida"))

get_austarch(db_url = get_db_url("austarch"))

get_bda(db_url = get_db_url("bda"))

get_all_dates()

get_calpal(db_url = get_db_url("calpal"))

get_caribbean(db_url = get_db_url("caribbean"))

get_eubar(db_url = get_db_url("eubar"))

get_euroevol(db_url = get_db_url("euroevol"))

get_irdd(db_url = get_db_url("irdd"))

get_jomon(db_url = get_db_url("jomon"))

get_katsianis(db_url = get_db_url("katsianis"))

get_kiteeastafrica(db_url = get_db_url("kiteeastafrica"))

get_medafricarbon(db_url = get_db_url("medafricarbon"))

get_mesorad(db_url = get_db_url("mesorad"))

get_neonet(db_url = get_db_url("neonet"))

get_neonetatl(db_url = get_db_url("neonetatl"))

get_nerd(db_url = get_db_url("nerd"))

get_p3k14c(db_url = get_db_url("p3k14c"))

get_pacea(db_url = get_db_url("pacea"))

get_palmisano(db_url = get_db_url("palmisano"))

get_rado.nb(db_url = get_db_url("rado.nb"))

get_rxpand(db_url = get_db_url("rxpand"))

get_sard(db_url = get_db_url("sard"))

get_tegiszhol(db_url = get_db_url("tegiszhol"))

get_xronos(db_url = get_db_url("xronos"))
```

## Arguments

- db_url:

  Character. URL that points to the c14 archive file.
  [`c14bazAAR::get_db_url()`](https://docs.ropensci.org/c14bazAAR/reference/get_db_info.md)
  fetches the URL from a reference list
