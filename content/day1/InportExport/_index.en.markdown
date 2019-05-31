---
date: "2016-04-09T16:50:16+02:00"
title: Import Data inot R
output: 
  learnr::tutorial
weight: 8
---

It’s the first big hurdle to dealing with data in R. 

You are most likelly to have looked at, organised and examined your data files in Excel.

Opening data in R is fairly simply, but organising it for analysis might take some thought and consideration. You'll guess that it is possible to use **File | Import Dataset** menu option in RStudio to import your data, however we’re going to do it the proper way with a command.

There are many packages that let R import all types of data, but with the restriction of time in this bootcamp we will focus on `CSV` files and you can try to explore the rest for yourself.

Comma separated files are the most common way to save spreadsheets that don’t require a licenced, usually not free program to open. Importing `CSV` is part of base R and you can use `read.csv()` function to do so. 


##### `read.csv()`

Let us go to <https://data.gov.rs/> Serbian open data portal. In particular, let us try to access ["Подаци из Огласа јавних набавки са Портала јавних набавки"](https://data.gov.rs/sr/datasets/podatsi-iz-oglasa-javnikh-nabavki-sa-portala-javnikh-nabavki/) and import this data to R.

We are not going to download it onto our local computers, but rather we will import it to R directly from the web using the link.


```r
df_csv <- read.csv("http://portal.ujn.gov.rs/OpenD/Tekuci_Mesec.csv", stringsAsFactors = FALSE)
head(df_csv, 10)
```

```
##    SifraNabavke
## 1       2012319
## 2       2012935
## 3       2013953
## 4       2053986
## 5       2092908
## 6       2128866
## 7       2145293
## 8       2153342
## 9       2243257
## 10      2259394
##                                                                                                                                                                                                                                                                                       NazivDokumenta
## 1                                                                                                                                                                                                                                                                         Униформа војничка маскирна
## 2                                                                                                             Предмет набавке је услуга у области одбране и безбедности - брокерска услуга, у смислу Закона о извозу и увозу наоружања и војне опреме ("Службени гласник РС" број 66/2015), ЈН 45/18
## 3                                                                                                                                                                                                                                                                           Наоружање и војна опрема
## 4                                                                                                                                                                                                                                                                                     83/18 Муниција
## 5                                                                                                                                                                                                                                                                                     91/18 Муниција
## 6  Јавна набавка услуга у области одбране и безбедности која се спроводи у преговарачком поступку без објављивања позива за подношење понуда, предмет набавке-Опрема за спашавање живота посаде, заштитна опрема и други уређаји за присилно напуштање ваздухоплова у опасности, број набавке 111/18
## 7                                                                                                                                                                                                                                               Електро материјал и расветна опрема, ЈН број M-59/18
## 8                                                                                                                                                                                                                                                             Унутрашња расвета кабине и инсталације
## 9                                                                                                                                                                                                                                               Набавка средстава за одржавање хигијене ЈНМВ 3/2019 
## 10                                                                                                                                                                                                                                                                     ЈНВВ 05/19 – Електроматеријал
##                                                               NazivNarucioca
## 1  МИНИСТАРСТВО ОДБРАНЕ, СЕКТОР ЗА МАТЕРИЈАЛНЕ РЕСУРСЕ, УПРАВА ЗА СНАБДЕВАЊЕ
## 2  МИНИСТАРСТВО ОДБРАНЕ, СЕКТОР ЗА МАТЕРИЈАЛНЕ РЕСУРСЕ, УПРАВА ЗА СНАБДЕВАЊЕ
## 3  МИНИСТАРСТВО ОДБРАНЕ, СЕКТОР ЗА МАТЕРИЈАЛНЕ РЕСУРСЕ, УПРАВА ЗА СНАБДЕВАЊЕ
## 4  МИНИСТАРСТВО ОДБРАНЕ, СЕКТОР ЗА МАТЕРИЈАЛНЕ РЕСУРСЕ, УПРАВА ЗА СНАБДЕВАЊЕ
## 5  МИНИСТАРСТВО ОДБРАНЕ, СЕКТОР ЗА МАТЕРИЈАЛНЕ РЕСУРСЕ, УПРАВА ЗА СНАБДЕВАЊЕ
## 6  МИНИСТАРСТВО ОДБРАНЕ, СЕКТОР ЗА МАТЕРИЈАЛНЕ РЕСУРСЕ, УПРАВА ЗА СНАБДЕВАЊЕ
## 7                                         Институт за кукуруз "Земун Поље", 
## 8                   ГШ ВС - Копнена Војска - Технички Ремонтни Завод "Чачак"
## 9                                   Предшколска установа "Олга Јовичић Рита"
## 10                       Јавна медијска установа"Радио-телевизија Војводине"
##    MaticniBroj       PIB IdMesto IdOpstina IdVrstaPostupka
## 1      7093608 102116082  791091     70220               3
## 2      7093608 102116082  791091     70220               4
## 3      7093608 102116082  791091     70220               3
## 4      7093608 102116082  791091     70220               3
## 5      7093608 102116082  791091     70220               3
## 6      7093608 102116082  791091     70220               3
## 7      7017618 100001589  791059     70157               7
## 8      7093608 102116082  746061     71242               4
## 9      7101074 101250091  719714     70653               7
## 10     8859230 104423678  802824     80284               1
##                                                                                                                                                                            PredmetNabavke
## 1                                                                                                                                                                             друга добра
## 2                                                                                                                                                                            друге услуге
## 3                                                                                                                                                                             друга добра
## 4                                                                                                                                                                             друга добра
## 5                                                                                                                                                                             друга добра
## 6                                                                                                                                                                            друге услуге
## 7   потрошни материјал (за обављање делатности, за одржавање објеката, канцеларијски и рачунарски материјал, средства за прање и чишћење, општи ситни инвентар, папирна конфекција и сл.)
## 8                                                                                                                                                                             друга добра
## 9   потрошни материјал (за обављање делатности, за одржавање објеката, канцеларијски и рачунарски материјал, средства за прање и чишћење, општи ситни инвентар, папирна конфекција и сл.)
## 10  потрошни материјал (за обављање делатности, за одржавање објеката, канцеларијски и рачунарски материјал, средства за прање и чишћење, општи ситни инвентар, папирна конфекција и сл.)
##    VrstaPredmeta
## 1          добра
## 2         услуге
## 3          добра
## 4          добра
## 5          добра
## 6         услуге
## 7          добра
## 8          добра
## 9          добра
## 10         добра
##                                                                                                                                                                                                                                                                                   OpstiRecnikNabavki
## 1                                                                                                                                                                                                                                                                                   Борбене униформе
## 2                                                                                                                                                                                                                                                                                  Одбрамбене услуге
## 3                                                                                                                                                                                                                                                          Моторна возила за превоз 10 или више лица
## 4                                                                                                                                                                                                                                                                                           Муниција
## 5                                                                                                                                                                                                                                                                                           Муниција
## 6                                                                                                                                                                                                                                                                                  Одбрамбене услуге
## 7                                                                                                                                                                                                                                                              Расветна опрема и електричне светиљке
## 8                                                                                                                                                                                                                                             Системи за команду, управљање, комуникацију и рачунаре
## 9                                                                                                                                                                                                                                                                               Производи за чишћење
## 10 Пригушнице за сијалице или цеви са пражњењем,Изолована жица и каблови,Расветна опрема и електричне светиљке,Електрични материјал и прибор,Електронски, електромеханички и електротехнички материјал,Телекомуникациона опрема и материјал,Конектори за оптичка влакна,Апарати са оптичким влакнима
##          KontaktOsoba                Telefon DatumPoslednjeIzmene
## 1      Мишо Симоновић 011/2059-168, 2059-019  2019-05-27 09:49:08
## 2      Мишо Симоновић 011/2059-168, 2059-019  2019-05-10 08:34:31
## 3      Мишо Симоновић 011/2059-168, 2059-019  2019-05-08 14:16:16
## 4      Мишо Симоновић 011/2059-168, 2059-019  2019-05-24 09:00:15
## 5      Мишо Симоновић 011/2059-168, 2059-019  2019-05-24 09:01:34
## 6      Мишо Симоновић 011/2059-168, 2059-019  2019-05-29 11:03:29
## 7      Јелена Бајагић           011/3756-704  2019-05-10 11:43:03
## 8  цл Дмитар Карличић 032/372-666, локал 287  2019-05-30 07:46:31
## 9    Здравко Глишовић            036/316-040  2019-05-06 09:15:15
## 10      Маја Смиљанић           021/210-1779  2019-05-08 10:53:22
##    IdDelatnost IdOblikOrg IdOblikSvoj IdKategorija PozivZaPodnosenjePonuda
## 1         8422         71           5            1                       0
## 2         8422         71           5            1                       0
## 3         8422         71           5            1                       0
## 4         8422         71           5            1                       0
## 5         8422         71           5            1                       0
## 6         8422         71           5            1                       0
## 7         7211         85           5            9                       1
## 8         8422         90           5            9                       0
## 9         8891         85           5            5                       1
## 10        6020         85           5            9                       1
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
## 7                            0                                        1
## 8                            0                                        0
## 9                            0                                        0
## 10                           0                                        0
##    ObavestenjeOZakljucenomUgovoru ObavestenjeORezultatuKonkursa
## 1                               0                             0
## 2                               0                             0
## 3                               0                             0
## 4                               0                             0
## 5                               0                             0
## 6                               0                             0
## 7                               3                             0
## 8                               0                             0
## 9                               3                             0
## 10                              4                             0
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
## 1                                   0                      0
## 2                                   0                      0
## 3                                   0                      0
## 4                                   0                      0
## 5                                   0                      0
## 6                                   0                      0
## 7                                   0                      1
## 8                                   0                      0
## 9                                   0                      1
## 10                                  0                      2
##    ObavestenjeOProduzenjuRoka PregovarackiBezPonuda
## 1                           0                     0
## 2                           0                     0
## 3                           0                     0
## 4                           0                     0
## 5                           0                     0
## 6                           0                     0
## 7                           1                     0
## 8                           0                     0
## 9                           0                     0
## 10                          1                     0
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
## 3                     0                              0
## 4                     0                              0
## 5                     0                              0
## 6                     0                              0
## 7                     0                              1
## 8                     0                              0
## 9                     3                              0
## 10                    4                              0
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
## 1  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2012319
## 2  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2012935
## 3  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2013953
## 4  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2053986
## 5  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2092908
## 6  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2128866
## 7  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2145293
## 8  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2153342
## 9  http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2243257
## 10 http://portal.ujn.gov.rs/Dokumenti/JavnaNabavka.aspx?idd=2259394
```

The other way is to download it and to save it to your working directory.

Let us download ["Регистар повлачћених произвођача електричне енергије"](https://data.gov.rs/s/resources/registar-povlashtshenikh-proizvodjacha-elektrichne-energije/20170221-142908/povlasceni.csv) and save it on your computers.

Make sure you save the file into your R-Project working directory before you ask R to execute the following

```
df_csv <- read.csv("poslodavci.csv", stringsAsFactors = FALSE)
```

What do you think about this dataset?

##### readr::read_csv()

Just so you can see how easy it is to use other packages for importing data into R the code below illustrates the use of read_csv().

```
## If you don't have readr installed yet, uncomment and run the line below
#install.packages("readr")
library(readr)
df_csv <- read_csv("poslodavci.csv")
df_csv
```

You can use R with appropriate packages to access other data formats. For example `jsonlite` package for `json` files or `foreign` package for `SPSS` data files. Try to look through the help of the packages you've been introduced to and discover other options.


## YOUR TURN 👇

1)	Open source software such as R and Git are extensively used in data science. Can you research the tools that are available for data science, both open and closed source. Write a short brief about the pros and cons for both types of software.

2)	Investigate the importance of open source data and identify where open source data can readily be found on the Internet. 

3) Write an explanation of the benefits of open source models for policy makings by local authorities and governments in general.

##### useful resource

`R osnove` by [dr Dejan B. Stojanovic](http://www.ilfe.org/sr/doc-dr-dejan-stojanovi%C4%87) is a book which  guides you to the world of statistical programming with R in an informative and easy to follow way. The book is written in Serbian and you can access it from [rzanat.rs](http://rzanat.rs/)  

-----------------------------
© 2019 Tatjana Kecojevic
