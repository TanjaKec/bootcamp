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
## 1       2012935
## 2       2013953
## 3       2145293
## 4       2243257
## 5       2259394
## 6       2265749
## 7       2266092
## 8       2280771
## 9       2283848
## 10      2285406
##                                                                                                                                                                            NazivDokumenta
## 1  Предмет набавке је услуга у области одбране и безбедности - брокерска услуга, у смислу Закона о извозу и увозу наоружања и војне опреме ("Службени гласник РС" број 66/2015), ЈН 45/18
## 2                                                                                                                                                                Наоружање и војна опрема
## 3                                                                                                                                    Електро материјал и расветна опрема, ЈН број M-59/18
## 4                                                                                                                                    Набавка средстава за одржавање хигијене ЈНМВ 3/2019 
## 5                                                                                                                                                           ЈНВВ 05/19 – Електроматеријал
## 6                                                                                                                                   Јавна набавка извођење екскурзије и наставе у природи
## 7                                                                                                                                                              Подлога за спортске терене
## 8                                                                                                                               ЈНМВ бр.3/2019-набавка намирница и прехрамбених производа
## 9                                                                                                                                                               Штампање часописа Градина
## 10                                                                                                                                     Изградња спољашњег осветљења у котларници Ц.Звезда
##                                                               NazivNarucioca
## 1  МИНИСТАРСТВО ОДБРАНЕ, СЕКТОР ЗА МАТЕРИЈАЛНЕ РЕСУРСЕ, УПРАВА ЗА СНАБДЕВАЊЕ
## 2  МИНИСТАРСТВО ОДБРАНЕ, СЕКТОР ЗА МАТЕРИЈАЛНЕ РЕСУРСЕ, УПРАВА ЗА СНАБДЕВАЊЕ
## 3                                         Институт за кукуруз "Земун Поље", 
## 4                                   Предшколска установа "Олга Јовичић Рита"
## 5                        Јавна медијска установа"Радио-телевизија Војводине"
## 6                                                       ОШ,,ВЕРА БЛАГОЈЕВИЋ"
## 7                                    Јавно предузеће "Ада Циганлија" Београд
## 8                                          Основна школа "Димитрије Туцовић"
## 9                                             Установа Нишки културни центар
## 10                                                              ЈКП"Топлана"
##    MaticniBroj       PIB IdMesto IdOpstina IdVrstaPostupka
## 1      7093608 102116082  791091     70220               4
## 2      7093608 102116082  791091     70220               3
## 3      7017618 100001589  791059     70157               7
## 4      7101074 101250091  719714     70653               7
## 5      8859230 104423678  802824     80284               1
## 6      7121245 101192778  725196     70734               7
## 7      7451440 100115129  791113     70254               1
## 8      7109695 101074721  745405     71234               7
## 9     17254839 100620097  792055     71323               1
## 10     7205929 100327422  724548     70726               7
##                                                                                                                                                                            PredmetNabavke
## 1                                                                                                                                                                            друге услуге
## 2                                                                                                                                                                             друга добра
## 3   потрошни материјал (за обављање делатности, за одржавање објеката, канцеларијски и рачунарски материјал, средства за прање и чишћење, општи ситни инвентар, папирна конфекција и сл.)
## 4   потрошни материјал (за обављање делатности, за одржавање објеката, канцеларијски и рачунарски материјал, средства за прање и чишћење, општи ситни инвентар, папирна конфекција и сл.)
## 5   потрошни материјал (за обављање делатности, за одржавање објеката, канцеларијски и рачунарски материјал, средства за прање и чишћење, општи ситни инвентар, папирна конфекција и сл.)
## 6                                                                                                                                                                            друге услуге
## 7                                                                                                                                                                             друга добра
## 8                                                                                                                                                                        храна, намирнице
## 9                                                                                                                       издавачке и штампарске услуге на хонорарној или уговорној основи 
## 10                                                                                                                                                                 електричне инсталације
##    VrstaPredmeta
## 1         услуге
## 2          добра
## 3          добра
## 4          добра
## 5          добра
## 6         услуге
## 7          добра
## 8          добра
## 9         услуге
## 10        радови
##                                                                                                                                                                                                                                                                                   OpstiRecnikNabavki
## 1                                                                                                                                                                                                                                                                                  Одбрамбене услуге
## 2                                                                                                                                                                                                                                                          Моторна возила за превоз 10 или више лица
## 3                                                                                                                                                                                                                                                              Расветна опрема и електричне светиљке
## 4                                                                                                                                                                                                                                                                               Производи за чишћење
## 5  Пригушнице за сијалице или цеви са пражњењем,Изолована жица и каблови,Расветна опрема и електричне светиљке,Електрични материјал и прибор,Електронски, електромеханички и електротехнички материјал,Телекомуникациона опрема и материјал,Конектори за оптичка влакна,Апарати са оптичким влакнима
## 6                                                                                                                                                                                                                                                                       Услуге организације путовања
## 7                                                                                                                                                                                                                                             Опрема за спортове на спортским игралиштима и теренима
## 8                                                                                                                                                                                                                                                              Храна, пиће, дуван и сродни производи
## 9                                                                                                                                                                                                                                                                           Часописи,Услуге штампања
## 10                                                                                                                                                                                                                            Радови на постављању електричних инсталација и електро-монтажни радови
##         KontaktOsoba                  Telefon DatumPoslednjeIzmene
## 1     Мишо Симоновић   011/2059-168, 2059-019  2019-05-10 08:34:31
## 2     Мишо Симоновић   011/2059-168, 2059-019  2019-05-08 14:16:16
## 3     Јелена Бајагић             011/3756-704  2019-05-10 11:43:03
## 4   Здравко Глишовић              036/316-040  2019-05-06 09:15:15
## 5      Маја Смиљанић             021/210-1779  2019-05-08 10:53:22
## 6      Драган Гаврић              015/818/177  2019-05-09 10:19:48
## 7       Љиљана Јелић              011 7857224  2019-05-08 11:23:29
## 8    Борка Милојевић                031831268  2019-05-07 15:43:09
## 9      Наташа Ристић 018/595-740; 018/595-741  2019-05-08 09:40:01
## 10 Новица Стојановић              016/246-410  2019-05-03 12:55:04
##    IdDelatnost IdOblikOrg IdOblikSvoj IdKategorija PozivZaPodnosenjePonuda
## 1         8422         71           5            1                       0
## 2         8422         71           5            1                       0
## 3         7211         85           5            9                       1
## 4         8891         85           5            5                       1
## 5         6020         85           5            9                       1
## 6         8520         85           5            5                       1
## 7         8130         17           5            7                       1
## 8         8520         85           5            5                       1
## 9         9004         85           1            4                       1
## 10        3530         17           5            7                       1
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
## 3                            0                                        1
## 4                            0                                        0
## 5                            0                                        0
## 6                            0                                        3
## 7                            0                                        0
## 8                            0                                        0
## 9                            0                                        0
## 10                           0                                        0
##    ObavestenjeOZakljucenomUgovoru ObavestenjeORezultatuKonkursa
## 1                               0                             0
## 2                               0                             0
## 3                               2                             0
## 4                               3                             0
## 5                               0                             0
## 6                               2                             0
## 7                               1                             0
## 8                               6                             0
## 9                               0                             0
## 10                              0                             0
##    ObavestenjeOObustaviPostupkaJavneNabavke
## 1                                         0
## 2                                         0
## 3                                         0
## 4                                         0
## 5                                         0
## 6                                         1
## 7                                         0
## 8                                         0
## 9                                         0
## 10                                        0
##    PodaciOIzmeniUgovoraOJavnojNabavci KonkursnaDokumentacija
## 1                                   0                      0
## 2                                   0                      0
## 3                                   0                      1
## 4                                   0                      1
## 5                                   0                      2
## 6                                   0                      1
## 7                                   0                      1
## 8                                   0                      1
## 9                                   0                      1
## 10                                  0                      1
##    ObavestenjeOProduzenjuRoka PregovarackiBezPonuda
## 1                           0                     0
## 2                           0                     0
## 3                           1                     0
## 4                           0                     0
## 5                           1                     0
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
## 1                     0                              0
## 2                     0                              0
## 3                     0                              1
## 4                     3                              0
## 5                     4                              0
## 6                     0                              1
## 7                     1                              0
## 8                     1                              0
## 9                     1                              0
## 10                    1                              0
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
## 1  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2012935
## 2  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2013953
## 3  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2145293
## 4  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2243257
## 5  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2259394
## 6  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2265749
## 7  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2266092
## 8  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2280771
## 9  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2283848
## 10 http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2285406
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

1)	Open source software such as R and Git are extensively used in data science. Can you reasearch the tools that are available for data science, both open and closed sourced. Write a short brief about the proosand cons for both types of softwares.

2)	Investigate the importance of open source data and identify where open source data can readily be found on the Internet. 

3) Write an explanations of the benefits of open source models for policy makings by local authoroties and government in general.


-----------------------------
© 2019 Tatjana Kecojevic
