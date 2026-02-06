``` r
#carregando o pacote/coleção de pacote tidyverse
#install.packages("tidyverse")
library(tidyverse)
```

    ## Warning: pacote 'tidyverse' foi compilado no R versão 4.5.2

    ## Warning: pacote 'ggplot2' foi compilado no R versão 4.5.2

    ## Warning: pacote 'tibble' foi compilado no R versão 4.5.2

    ## Warning: pacote 'tidyr' foi compilado no R versão 4.5.2

    ## Warning: pacote 'readr' foi compilado no R versão 4.5.2

    ## Warning: pacote 'purrr' foi compilado no R versão 4.5.2

    ## Warning: pacote 'dplyr' foi compilado no R versão 4.5.2

    ## Warning: pacote 'stringr' foi compilado no R versão 4.5.2

    ## Warning: pacote 'forcats' foi compilado no R versão 4.5.2

    ## Warning: pacote 'lubridate' foi compilado no R versão 4.5.2

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.6
    ## ✔ forcats   1.0.1     ✔ stringr   1.6.0
    ## ✔ ggplot2   4.0.1     ✔ tibble    3.3.0
    ## ✔ lubridate 1.9.4     ✔ tidyr     1.3.2
    ## ✔ purrr     1.2.0     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
#install.packages("skimr")
library(skimr)
```

    ## Warning: pacote 'skimr' foi compilado no R versão 4.5.2

A seguir, será feito o carregamento dos dados e a análise inicial do
comportamento dos deles na base de dados Star Wars:

``` r
#carregando a base de dados Star Wars
head(starwars)
```

    ## # A tibble: 6 × 14
    ##   name      height  mass hair_color skin_color eye_color birth_year sex   gender
    ##   <chr>      <int> <dbl> <chr>      <chr>      <chr>          <dbl> <chr> <chr> 
    ## 1 Luke Sky…    172    77 blond      fair       blue            19   male  mascu…
    ## 2 C-3PO        167    75 <NA>       gold       yellow         112   none  mascu…
    ## 3 R2-D2         96    32 <NA>       white, bl… red             33   none  mascu…
    ## 4 Darth Va…    202   136 none       white      yellow          41.9 male  mascu…
    ## 5 Leia Org…    150    49 brown      light      brown           19   fema… femin…
    ## 6 Owen Lars    178   120 brown, gr… light      blue            52   male  mascu…
    ## # ℹ 5 more variables: homeworld <chr>, species <chr>, films <list>,
    ## #   vehicles <list>, starships <list>

``` r
tail(starwars)
```

    ## # A tibble: 6 × 14
    ##   name      height  mass hair_color skin_color eye_color birth_year sex   gender
    ##   <chr>      <int> <dbl> <chr>      <chr>      <chr>          <dbl> <chr> <chr> 
    ## 1 Tion Med…    206    80 none       grey       black             NA male  mascu…
    ## 2 Finn          NA    NA black      dark       dark              NA male  mascu…
    ## 3 Rey           NA    NA brown      light      hazel             NA fema… femin…
    ## 4 Poe Dame…     NA    NA brown      light      brown             NA male  mascu…
    ## 5 BB8           NA    NA none       none       black             NA none  mascu…
    ## 6 Captain …     NA    NA none       none       unknown           NA fema… femin…
    ## # ℹ 5 more variables: homeworld <chr>, species <chr>, films <list>,
    ## #   vehicles <list>, starships <list>

``` r
dados <- starwars
```

Com uma visão global, será visualizado se há dados faltantes (NA’s) e em
quais variáveis

``` r
#verificando se há valores NA's
skim(dados)
```

|                                                  |       |
|:-------------------------------------------------|:------|
| Name                                             | dados |
| Number of rows                                   | 87    |
| Number of columns                                | 14    |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |       |
| Column type frequency:                           |       |
| character                                        | 8     |
| list                                             | 3     |
| numeric                                          | 3     |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |       |
| Group variables                                  | None  |

Data summary

**Variable type: character**

| skim_variable | n_missing | complete_rate | min | max | empty | n_unique | whitespace |
|:--------------|----------:|--------------:|----:|----:|------:|---------:|-----------:|
| name          |         0 |          1.00 |   3 |  21 |     0 |       87 |          0 |
| hair_color    |         5 |          0.94 |   4 |  13 |     0 |       11 |          0 |
| skin_color    |         0 |          1.00 |   3 |  19 |     0 |       31 |          0 |
| eye_color     |         0 |          1.00 |   3 |  13 |     0 |       15 |          0 |
| sex           |         4 |          0.95 |   4 |  14 |     0 |        4 |          0 |
| gender        |         4 |          0.95 |   8 |   9 |     0 |        2 |          0 |
| homeworld     |        10 |          0.89 |   4 |  14 |     0 |       48 |          0 |
| species       |         4 |          0.95 |   3 |  14 |     0 |       37 |          0 |

**Variable type: list**

| skim_variable | n_missing | complete_rate | n_unique | min_length | max_length |
|:--------------|----------:|--------------:|---------:|-----------:|-----------:|
| films         |         0 |             1 |       24 |          1 |          7 |
| vehicles      |         0 |             1 |       11 |          0 |          2 |
| starships     |         0 |             1 |       16 |          0 |          5 |

**Variable type: numeric**

| skim_variable | n_missing | complete_rate |   mean |     sd |  p0 |   p25 | p50 |   p75 | p100 | hist  |
|:--------------|----------:|--------------:|-------:|-------:|----:|------:|----:|------:|-----:|:------|
| height        |         6 |          0.93 | 174.60 |  34.77 |  66 | 167.0 | 180 | 191.0 |  264 | ▂▁▇▅▁ |
| mass          |        28 |          0.68 |  97.31 | 169.46 |  15 |  55.6 |  79 |  84.5 | 1358 | ▇▁▁▁▁ |
| birth_year    |        44 |          0.49 |  87.57 | 154.69 |   8 |  35.0 |  52 |  72.0 |  896 | ▇▁▁▁▁ |

``` r
#verificando em quais variáveis há valores NA's
cat("As variáveis que possuem dados faltantes são:\n")
```

    ## As variáveis que possuem dados faltantes são:

``` r
for(i in names(dados)){
  if(any(is.na(dados[[i]]))){
    cat("•",i,"\n")
  }
}
```

    ## • height 
    ## • mass 
    ## • hair_color 
    ## • birth_year 
    ## • sex 
    ## • gender 
    ## • homeworld 
    ## • species

Verifica-se logo que as variáveis acima possuem valores faltantes
(Na’s). Dessa forma, é necessário tratá-las:

``` r
#height
head(dados$height)
```

    ## [1] 172 167  96 202 150 178

``` r
tail(dados$height)
```

    ## [1] 206  NA  NA  NA  NA  NA

``` r
count(dados[is.na(dados$height),]) #há 6 observações sem a altura (height)
```

    ## # A tibble: 1 × 1
    ##       n
    ##   <int>
    ## 1     6

``` r
dados[is.na(dados$height),]
```

    ## # A tibble: 6 × 14
    ##   name      height  mass hair_color skin_color eye_color birth_year sex   gender
    ##   <chr>      <int> <dbl> <chr>      <chr>      <chr>          <dbl> <chr> <chr> 
    ## 1 Arvel Cr…     NA    NA brown      fair       brown             NA male  mascu…
    ## 2 Finn          NA    NA black      dark       dark              NA male  mascu…
    ## 3 Rey           NA    NA brown      light      hazel             NA fema… femin…
    ## 4 Poe Dame…     NA    NA brown      light      brown             NA male  mascu…
    ## 5 BB8           NA    NA none       none       black             NA none  mascu…
    ## 6 Captain …     NA    NA none       none       unknown           NA fema… femin…
    ## # ℹ 5 more variables: homeworld <chr>, species <chr>, films <list>,
    ## #   vehicles <list>, starships <list>

``` r
dados %>%
  filter(is.na(height)) %>%
  select(name)
```

    ## # A tibble: 6 × 1
    ##   name          
    ##   <chr>         
    ## 1 Arvel Crynyd  
    ## 2 Finn          
    ## 3 Rey           
    ## 4 Poe Dameron   
    ## 5 BB8           
    ## 6 Captain Phasma

Após uma conferência no Wookieepedia, enciclopédia criada sobre Star
Wars, nota-se que os personagens adiante possuem as respectivas alturas:

Arvel Crynyd: não encontrado (desconhecido/unknown) Finn: 178 Rey: 170
Poe Dameron: 172 BB8: 67 Captain Phasma: 200

Dessa forma, será imputado tais valores para conhecidos para eliminar os
NA’s:

``` r
dados[c(28, 83, 84, 85, 86, 87), c("name","height")]
```

    ## # A tibble: 6 × 2
    ##   name           height
    ##   <chr>           <int>
    ## 1 Arvel Crynyd       NA
    ## 2 Finn               NA
    ## 3 Rey                NA
    ## 4 Poe Dameron        NA
    ## 5 BB8                NA
    ## 6 Captain Phasma     NA

``` r
dados[c(28, 83, 84, 85, 86, 87), "height"] <- c(NA, 178, 170, 172, 67, 200)
dados[c(28, 83, 84, 85, 86, 87), c("name","height")]
```

    ## # A tibble: 6 × 2
    ##   name           height
    ##   <chr>           <int>
    ## 1 Arvel Crynyd       NA
    ## 2 Finn              178
    ## 3 Rey               170
    ## 4 Poe Dameron       172
    ## 5 BB8                67
    ## 6 Captain Phasma    200

``` r
#mass
head(dados$mass)
```

    ## [1]  77  75  32 136  49 120

``` r
tail(dados$mass)
```

    ## [1] 80 NA NA NA NA NA

``` r
count(dados[is.na(dados$mass),])
```

    ## # A tibble: 1 × 1
    ##       n
    ##   <int>
    ## 1    28

``` r
dados[is.na(dados$mass),]
```

    ## # A tibble: 28 × 14
    ##    name     height  mass hair_color skin_color eye_color birth_year sex   gender
    ##    <chr>     <int> <dbl> <chr>      <chr>      <chr>          <dbl> <chr> <chr> 
    ##  1 Wilhuff…    180    NA auburn, g… fair       blue              64 male  mascu…
    ##  2 Mon Mot…    150    NA auburn     fair       blue              48 fema… femin…
    ##  3 Arvel C…     NA    NA brown      fair       brown             NA male  mascu…
    ##  4 Finis V…    170    NA blond      fair       blue              91 male  mascu…
    ##  5 Rugor N…    206    NA none       green      orange            NA male  mascu…
    ##  6 Ric Olié    183    NA brown      fair       blue              NA male  mascu…
    ##  7 Watto       137    NA black      blue, grey yellow            NA male  mascu…
    ##  8 Quarsh …    183    NA black      dark       brown             62 male  mascu…
    ##  9 Shmi Sk…    163    NA black      fair       brown             72 fema… femin…
    ## 10 Bib For…    180    NA none       pale       pink              NA male  mascu…
    ## # ℹ 18 more rows
    ## # ℹ 5 more variables: homeworld <chr>, species <chr>, films <list>,
    ## #   vehicles <list>, starships <list>

``` r
rownames(dados)[is.na(dados$mass)]
```

    ##  [1] "12" "27" "28" "33" "37" "38" "39" "41" "42" "44" "48" "53" "55" "56" "58"
    ## [16] "60" "61" "65" "67" "72" "73" "74" "76" "83" "84" "85" "86" "87"

``` r
dados %>%
  filter(is.na(mass)) %>%
  select(name)
```

    ## # A tibble: 28 × 1
    ##    name          
    ##    <chr>         
    ##  1 Wilhuff Tarkin
    ##  2 Mon Mothma    
    ##  3 Arvel Crynyd  
    ##  4 Finis Valorum 
    ##  5 Rugor Nass    
    ##  6 Ric Olié      
    ##  7 Watto         
    ##  8 Quarsh Panaka 
    ##  9 Shmi Skywalker
    ## 10 Bib Fortuna   
    ## # ℹ 18 more rows

Dessa forma, os seguintes personagens estão sem valores na variável
mass:

Wilhuff Tarkin  
Mon Mothma  
Arvel Crynyd  
Finis Valorum  
Rugor Nass  
Ric Olié  
Watto  
Quarsh Panaka  
Shmi Skywalker  
Bib Fortuna

…

Jocasta Nu  
R4-P17  
San Hill  
Finn  
Rey  
Poe Dameron  
BB8  
Captain Phasma

Totalizando 28 personagens sem os dados referentes à variável mass.

Diferentemente da variável height, que possuia 6 dados faltantes, na
variável em questão, há 28 observações, o que dificulta a procura de
cada personagem e imputação manual. A partir disso, pensei imputar pelo
método das tendências centrais, utilizando a mediana, mas diferenciandos
por espécies e gênero, quando há.

O ideal seria usar um modelo de regressão para prever os valores, mas,
por limitação técnica, não será possível. No entanto, a utilização da
mediana não é indevida: tem embasamento e procedência, principalmente
com os cuidados em relação aos fatores citados.

Assim, é preciso verificar a espécie e o gênero de cada observação:

``` r
dados %>% 
  filter(is.na(mass)) %>% 
  select(name, species, gender) %>% 
  arrange(desc(species), group_by = T)
```

    ## # A tibble: 28 × 3
    ##    name           species   gender   
    ##    <chr>          <chr>     <chr>    
    ##  1 Eeth Koth      Zabrak    masculine
    ##  2 Gasgano        Xexto     masculine
    ##  3 Bib Fortuna    Twi'lek   masculine
    ##  4 Watto          Toydarian masculine
    ##  5 Yarael Poof    Quermian  masculine
    ##  6 San Hill       Muun      masculine
    ##  7 Taun We        Kaminoan  feminine 
    ##  8 Saesee Tiin    Iktotchi  masculine
    ##  9 Wilhuff Tarkin Human     masculine
    ## 10 Mon Mothma     Human     feminine 
    ## # ℹ 18 more rows

Com as espécies disponíveis e o gênero, é necessário encontrar a mediana
de suas categorias.

``` r
species_mass_na <- dados %>% 
  group_by(species) %>% 
  summarise(
    n_personagem = n(),
    n_na_mass = sum(is.na(mass)),
    n_masculine = sum(gender=="masculine", na.rm = TRUE),
    n_feminine = sum(gender=="feminine", na.rm = TRUE),
    n_masculine_na_mass = sum(is.na(mass) & gender=="masculine"),
    n_feminine_na_mass = sum(is.na(mass) & gender=="feminine"),
    prop_na_mass = round((n_na_mass / n_personagem)*100, 2),
    prop_na_masculine = round((n_masculine_na_mass / n_masculine)*100, 2),
    prop_na_feminine = round((n_feminine_na_mass / n_feminine)*100, 2)
  ) %>% 
  filter(n_na_mass>0)

species_mass_na
```

    ## # A tibble: 13 × 10
    ##    species   n_personagem n_na_mass n_masculine n_feminine n_masculine_na_mass
    ##    <chr>            <int>     <int>       <int>      <int>               <int>
    ##  1 Chagrian             1         1           1          0                   1
    ##  2 Droid                6         2           5          1                   1
    ##  3 Gungan               3         1           3          0                   1
    ##  4 Human               35        15          26          9                   9
    ##  5 Iktotchi             1         1           1          0                   1
    ##  6 Kaminoan             2         1           1          1                   0
    ##  7 Muun                 1         1           1          0                   1
    ##  8 Quermian             1         1           1          0                   1
    ##  9 Toydarian            1         1           1          0                   1
    ## 10 Twi'lek              2         1           1          1                   1
    ## 11 Xexto                1         1           1          0                   1
    ## 12 Zabrak               2         1           2          0                   1
    ## 13 <NA>                 4         1           0          0                  NA
    ## # ℹ 4 more variables: n_feminine_na_mass <int>, prop_na_mass <dbl>,
    ## #   prop_na_masculine <dbl>, prop_na_feminine <dbl>

``` r
sum(species_mass_na$n_na_mass)
```

    ## [1] 28

Com essa tabela, é possível observar alguns pontos: 1. há personagens
com NA na massa, mas é o único da base de dados (ex.: Mas Amedda); 2. há
personagens de determinada espécie e gênero com NA na massa, mas é o
único da base de dados (ex.: Yarael Poof e R4-P17);

Assim, é necessário fazer o filtro inicial para eliminar aqueles que do
ponto 1 (n_personagem = n_na_mass) e 2 (n_masculine =
n_masculine_na_mass e n_feminine = n_feminine_na_mass). Para isso, é
preciso retirar aqueles com proporção de personagens com NA na massa
igual a 100% (prop_na_mass = 100) e aqueles que a proporção de NA em um
gênero específico seja igual a 100% (prop_na_masculine = 100 e
prop_na_feminine = 100):

``` r
imput_na_mass <- species_mass_na %>% 
  filter(prop_na_mass < 100, prop_na_masculine < 100, prop_na_feminine < 100)

imput_na_mass
```

    ## # A tibble: 1 × 10
    ##   species n_personagem n_na_mass n_masculine n_feminine n_masculine_na_mass
    ##   <chr>          <int>     <int>       <int>      <int>               <int>
    ## 1 Human             35        15          26          9                   9
    ## # ℹ 4 more variables: n_feminine_na_mass <int>, prop_na_mass <dbl>,
    ## #   prop_na_masculine <dbl>, prop_na_feminine <dbl>

Sendo assim, os únicos que são elegíveis a receber esse tipo de
imputação são os da espécie (specie) humana (Human).

Logo, é preciso estudar os humanas que possuem NA na massa em relação ao
gênero e as quantidades, tanto de cada gênero em relação ao total quanto
de cada gênero em relação aos número de NA na massa.
