---
date: "2016-04-09T16:50:16+02:00"
title: Inport Data inot R
output: 
  learnr::tutorial
weight: 8
---

It’s the first big hurdle to dealing with data in R. 

You have most likelly used to look, organise and examine your data files in Excel.

Opening data in R is fairly simply, but organising it for the analysis it might takes some thought and consideration. You'll guess that it is possible to use **File | Import Dataset** menu option in RStudio to import your data, however we’re going to do it the proper way with a command.

There are many packages that lets R import all types of data, but with the restriction of time in his bootcamp we will focus on `CSV` files and you can try to explore the rest for yourself.

Comma separated files are the most common way to save spreadsheets that doesn’t require a licenced, usually not free program to open. Importing `CSV` is part of base R and you can use `read.csv()` function to do so. 


##### `read.csv()`

Let us go to <https://data.gov.rs/> Serbian open data portal. In particular, let us try to access ["Подаци из Огласа јавних набавки са Портала јавних набавки"](https://data.gov.rs/sr/datasets/podatsi-iz-oglasa-javnikh-nabavki-sa-portala-javnikh-nabavki/) and inport this data to R.

We are not going to download it onto our local computers, but rather we will import it to R directly from the web using the link.


```r
df_csv <- read.csv("http://portal.ujn.gov.rs/OpenD/Tekuci_Mesec.csv", stringsAsFactors = FALSE)
head(df_csv, 10)
```

```
##    SifraNabavke
## 1       2243257
## 2       2285406
## 3       2297971
## 4       2298786
## 5       2299034
## 6       2300589
## 7       2319203
## 8       2319205
## 9       2319209
## 10      2319217
##                                                                                              NazivDokumenta
## 1                                                      Набавка средстава за одржавање хигијене ЈНМВ 3/2019 
## 2                                                        Изградња спољашњег осветљења у котларници Ц.Звезда
## 3                                                                               набавка електричне енергије
## 4    ЈНМВ 1.1.8-19 БИОМЕДИЦИНСКИ ЛАБОРАТОРИЈСКИ МИКРОСКОП СА ДИГИТАЛНОМ КАМЕРОМ ЗА ДИЈАГНОСТИКУ ТУБЕРКУЛОЗЕ
## 5                                                  ЈНМВ 1.1.7-19 Суви стерилизатор (лабораторијска сушница)
## 6                                                                               Дератизација и дезинсекција
## 7                                            ОДЛУКА о додели уговора за прву партију за електричну енергију
## 8                                                              БЕТОНИРАЊЕ ПЕШАЧКЕ СТАЗЕ У ШКОЛСКОМ ДВОРИШТУ
## 9                                                                           Медицински потрошни материјал\t
## 10 пружањe услуга ангажовања координатора за безбедност за извођење радова и израду плана превентивних мера
##                                                   NazivNarucioca
## 1                       Предшколска установа "Олга Јовичић Рита"
## 2                                                   ЈКП"Топлана"
## 3                                      ДУ'' Дечија радост'' Ириг
## 4  Специјална болница за плућне болести "др Васа Савић" Зрењанин
## 5  Специјална болница за плућне болести "др Васа Савић" Зрењанин
## 6                                 Геронтолошки центар "Нови Сад"
## 7                            Музичка школа "др Милоје Милојевић"
## 8                                 Техничка школа "Михајло Пупин"
## 9                                  Општа Болница "Стефан Високи"
## 10            Канцеларија за локални економски развој и пројекте
##    MaticniBroj       PIB IdMesto IdOpstina IdVrstaPostupka
## 1      7101074 101250091  719714     70653               7
## 2      7205929 100327422  724548     70726               7
## 3      8383634 101380998  801895     80187               7
## 4      8671923 101161066  801542     80152               7
## 5      8671923 101161066  801542     80152               7
## 6      8066191 102187298  802824     80284               7
## 7      7151373 101941898  718980     70645               1
## 8      8004056 100698386  801747     80179               7
## 9      6113079 101401162  740721     71102               1
## 10    17620541 100232752  792047     71331               7
##                                                                                                                                                                            PredmetNabavke
## 1   потрошни материјал (за обављање делатности, за одржавање објеката, канцеларијски и рачунарски материјал, средства за прање и чишћење, општи ситни инвентар, папирна конфекција и сл.)
## 2                                                                                                                                                                  електричне инсталације
## 3                                                                                                                                                              добра у области енергетике
## 4                                                                                                   техничка опрема за обављање делатности (уређаји, машине, апарати, механизација и сл.)
## 5                                                                                                   техничка опрема за обављање делатности (уређаји, машине, апарати, механизација и сл.)
## 6                                                                                                                                                                            друге услуге
## 7                                                                                                                                                              добра у области енергетике
## 8                                                                                                                                                                опште грађевински радови
## 9   потрошни материјал (за обављање делатности, за одржавање објеката, канцеларијски и рачунарски материјал, средства за прање и чишћење, општи ситни инвентар, папирна конфекција и сл.)
## 10                                                                                                                                                         здравствене и социјалне услуге
##    VrstaPredmeta
## 1          добра
## 2         радови
## 3          добра
## 4          добра
## 5          добра
## 6         услуге
## 7          добра
## 8         радови
## 9          добра
## 10        услуге
##                                                        OpstiRecnikNabavki
## 1                                                    Производи за чишћење
## 2  Радови на постављању електричних инсталација и електро-монтажни радови
## 3  Електрична енергија, енергија за грејање, соларна и нуклеарна енергија
## 4     Медицинска опрема, фармацеутски производи и производи за личну негу
## 5                                                            Стерилизатор
## 6                         Услуге чишћења и санитације,Услуге дератизације
## 7                                                     Електрична енергија
## 8                                       Радови на изградњи пешачких стаза
## 9                                           Медицински потрошни материјал
## 10                               Услуге у области здравства и безбедности
##                                              KontaktOsoba
## 1                                        Здравко Глишовић
## 2                                       Новица Стојановић
## 3                                   Јелена Тадић Ђурђевић
## 4                Прим. мр мед. сц. др  Светлана Јовановић
## 5                Прим. мр мед. сц. др  Светлана Јовановић
## 6                                          Гроздана Пешут
## 7                                    Светлана Стојилковић
## 8                                          Снежана Иваниш
## 9                                         Зоран Голубовић
## 10 Милан Ранђеловић; Миодраг Милошевић; Мила Димитријевић
##                 Telefon DatumPoslednjeIzmene IdDelatnost IdOblikOrg
## 1           036/316-040  2019-05-06 09:15:15        8891         85
## 2           016/246-410  2019-05-03 12:55:04        3530         17
## 3           022/461-322  2019-05-03 10:16:33        8891         85
## 4           023/561-115  2019-05-03 12:25:26        8610         85
## 5           023/561-115  2019-05-03 12:16:38        8610         85
## 6  021/450-266 lok. 118  2019-05-06 11:14:11        8730         85
## 7            034/305135  2019-05-03 18:22:15        8532         85
## 8           022/561-661  2019-05-02 00:44:16        8532         85
## 9         026/330 - 330  2019-05-02 16:41:15        8610         85
## 10          018/209-239  2019-05-02 16:50:20        8411         73
##    IdOblikSvoj IdKategorija PozivZaPodnosenjePonuda
## 1            5            5                       1
## 2            5            7                       1
## 3            1            5                       1
## 4            5            3                       1
## 5            5            3                       1
## 6            5            6                       1
## 7            5            5                       0
## 8            5            5                       1
## 9            5            3                       1
## 10           5            8                       1
##    PozivZaPodnosenjePrijava ObavestenjeOSistemuDinamickeNabavke
## 1                         0                                   0
## 2                         0                                   0
## 3                         0                                   0
## 4                         0                                   0
## 5                         0                                   0
## 6                         0                                   0
## 7                         0                                   0
## 8                         0                                   0
## 9                         0                                   0
## 10                        0                                   0
##    PozivZaUcesceNaKonkursZaDizajn ObavestenjeOPriznavanjuKvalifikacije
## 1                               0                                    0
## 2                               0                                    0
## 3                               0                                    0
## 4                               0                                    0
## 5                               0                                    0
## 6                               0                                    0
## 7                               0                                    0
## 8                               0                                    0
## 9                               0                                    0
## 10                              0                                    0
##    ObavestenjeOPriznavanjuKvalifikacijeURestriktivnomPostupku
## 1                                                           0
## 2                                                           0
## 3                                                           0
## 4                                                           0
## 5                                                           0
## 6                                                           0
## 7                                                           0
## 8                                                           0
## 9                                                           0
## 10                                                          0
##    PodaciOObjaviIDodeliUgovora ObavestenjeOZakljucenomOkvirnomSporazumu
## 1                            0                                        0
## 2                            0                                        0
## 3                            0                                        0
## 4                            0                                        0
## 5                            0                                        0
## 6                            0                                        0
## 7                            0                                        0
## 8                            0                                        0
## 9                            0                                        0
## 10                           0                                        0
##    ObavestenjeOZakljucenomUgovoru ObavestenjeORezultatuKonkursa
## 1                               3                             0
## 2                               0                             0
## 3                               0                             0
## 4                               0                             0
## 5                               0                             0
## 6                               0                             0
## 7                               0                             0
## 8                               0                             0
## 9                               0                             0
## 10                              0                             0
##    ObavestenjeOObustaviPostupkaJavneNabavke
## 1                                         0
## 2                                         0
## 3                                         0
## 4                                         0
## 5                                         0
## 6                                         0
## 7                                         0
## 8                                         0
## 9                                         0
## 10                                        0
##    PodaciOIzmeniUgovoraOJavnojNabavci KonkursnaDokumentacija
## 1                                   0                      1
## 2                                   0                      1
## 3                                   0                      1
## 4                                   0                      1
## 5                                   0                      1
## 6                                   0                      1
## 7                                   0                      0
## 8                                   0                      1
## 9                                   0                      8
## 10                                  0                      1
##    ObavestenjeOProduzenjuRoka PregovarackiBezPonuda
## 1                           0                     0
## 2                           0                     0
## 3                           0                     0
## 4                           0                     0
## 5                           0                     0
## 6                           0                     0
## 7                           0                     0
## 8                           0                     0
## 9                           0                     0
## 10                          0                     0
##    ObavestenjeOZastitiPrava MisljenjeUpraveJN
## 1                         0                 0
## 2                         0                 0
## 3                         0                 0
## 4                         0                 0
## 5                         0                 0
## 6                         0                 0
## 7                         0                 0
## 8                         0                 0
## 9                         0                 0
## 10                        0                 0
##    OdlukaOPriznavanjuKvalifikacije OdlukaOIskljucenjuKandidata
## 1                                0                           0
## 2                                0                           0
## 3                                0                           0
## 4                                0                           0
## 5                                0                           0
## 6                                0                           0
## 7                                0                           0
## 8                                0                           0
## 9                                0                           0
## 10                               0                           0
##    OdlukaODodeliUgovora OdlukaODodeliOkvirnogSporazuma
## 1                     3                              0
## 2                     1                              0
## 3                     1                              0
## 4                     1                              0
## 5                     1                              0
## 6                     1                              0
## 7                     0                              0
## 8                     0                              0
## 9                     0                              0
## 10                    0                              0
##    ObavestenjeOPonistenjuPostupka OdlukaOObustaviPostupka
## 1                               0                       0
## 2                               0                       0
## 3                               0                       0
## 4                               0                       0
## 5                               0                       0
## 6                               0                       0
## 7                               0                       0
## 8                               0                       0
## 9                               0                       0
## 10                              0                       0
##    OdlukaONastavkuPostupka OdlukaKomisijeOZakljucenjuUgovora
## 1                        0                                 0
## 2                        0                                 0
## 3                        0                                 0
## 4                        0                                 0
## 5                        0                                 0
## 6                        0                                 0
## 7                        0                                 0
## 8                        0                                 0
## 9                        0                                 0
## 10                       0                                 0
##    ObavestenjeOPriznavanjuKvalifikacijeOpste
## 1                                          0
## 2                                          0
## 3                                          0
## 4                                          0
## 5                                          0
## 6                                          0
## 7                                          0
## 8                                          0
## 9                                          0
## 10                                         0
##                                                                Link
## 1  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2243257
## 2  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2285406
## 3  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2297971
## 4  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2298786
## 5  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2299034
## 6  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2300589
## 7  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2319203
## 8  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2319205
## 9  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2319209
## 10 http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2319217
```

The other way is to download it and to save it at your working directory.

Let us download ["Регистар повлачћених произвођача електричне енергије"](https://data.gov.rs/s/resources/registar-povlashtshenikh-proizvodjacha-elektrichne-energije/20170221-142908/povlasceni.csv) and save it on your computers.

Make sure you save the file into your R-Project working directory before you ask R to execute the following

```
df_csv <- read.csv("poslodavci.csv", stringsAsFactors = FALSE)
```

What do you think about this dataset?

##### readr::read_csv()

Just so you can see how easy is to use other packages for inporting data into R the code below illustrates the use of read_csv().

```
## If you don't have readr installed yet, uncomment and run the line below
#install.packages("readr")
library(readr)
df_csv <- read_csv("poslodavci.csv")
df_csv
```

You can use R with appropriate package to access other data formats. For example `jsonlite` package for `json` files or `foreign` package for `SPSS` data files. Try to look through the help of the packages you've been introduced to and discuver other options.


## YOUR TURN 👇

1)	Open source software such as R and Git are extensively used in data science. Can you reasearch the tools that are available for data science, both open and closed sourced. Write a short brief about the prones and cons for both types of softwares.

2)	Investigate the importance of open source data and identify where open source data can readily be found on the Internet. 

3) Write an explanations of the benefits of open source models for policy makings by local authoroties and government in general.


-----------------------------
© 2019 Tatjana Kecojevic
