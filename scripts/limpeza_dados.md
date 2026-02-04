
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

A seguir, será feito o carregamento dos dados e a análise inicial do
comportamento dos dados na base de dados Star Wars:

``` r
#carregando a base de dados Star Wars
starwars
```

    ## # A tibble: 87 × 14
    ##    name     height  mass hair_color skin_color eye_color birth_year sex   gender
    ##    <chr>     <int> <dbl> <chr>      <chr>      <chr>          <dbl> <chr> <chr> 
    ##  1 Luke Sk…    172    77 blond      fair       blue            19   male  mascu…
    ##  2 C-3PO       167    75 <NA>       gold       yellow         112   none  mascu…
    ##  3 R2-D2        96    32 <NA>       white, bl… red             33   none  mascu…
    ##  4 Darth V…    202   136 none       white      yellow          41.9 male  mascu…
    ##  5 Leia Or…    150    49 brown      light      brown           19   fema… femin…
    ##  6 Owen La…    178   120 brown, gr… light      blue            52   male  mascu…
    ##  7 Beru Wh…    165    75 brown      light      blue            47   fema… femin…
    ##  8 R5-D4        97    32 <NA>       white, red red             NA   none  mascu…
    ##  9 Biggs D…    183    84 black      light      brown           24   male  mascu…
    ## 10 Obi-Wan…    182    77 auburn, w… fair       blue-gray       57   male  mascu…
    ## # ℹ 77 more rows
    ## # ℹ 5 more variables: homeworld <chr>, species <chr>, films <list>,
    ## #   vehicles <list>, starships <list>

``` r
dados <- starwars

summary(dados)
```

    ##      name               height           mass          hair_color       
    ##  Length:87          Min.   : 66.0   Min.   :  15.00   Length:87         
    ##  Class :character   1st Qu.:167.0   1st Qu.:  55.60   Class :character  
    ##  Mode  :character   Median :180.0   Median :  79.00   Mode  :character  
    ##                     Mean   :174.6   Mean   :  97.31                     
    ##                     3rd Qu.:191.0   3rd Qu.:  84.50                     
    ##                     Max.   :264.0   Max.   :1358.00                     
    ##                     NA's   :6       NA's   :28                          
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##   skin_color         eye_color           birth_year         sex           
    ##  Length:87          Length:87          Min.   :  8.00   Length:87         
    ##  Class :character   Class :character   1st Qu.: 35.00   Class :character  
    ##  Mode  :character   Mode  :character   Median : 52.00   Mode  :character  
    ##                                        Mean   : 87.57                     
    ##                                        3rd Qu.: 72.00                     
    ##                                        Max.   :896.00                     
    ##                                        NA's   :44                         
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##                                                                           
    ##     gender           homeworld           species         
    ##  Length:87          Length:87          Length:87         
    ##  Class :character   Class :character   Class :character  
    ##  Mode  :character   Mode  :character   Mode  :character  
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##                                                          
    ##  films.Length  films.Class  films.Mode
    ##  5          -none-     character      
    ##  6          -none-     character      
    ##  7          -none-     character      
    ##  4          -none-     character      
    ##  5          -none-     character      
    ##  3          -none-     character      
    ##  3          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  6          -none-     character      
    ##  3          -none-     character      
    ##  2          -none-     character      
    ##  5          -none-     character      
    ##  4          -none-     character      
    ##  1          -none-     character      
    ##  3          -none-     character      
    ##  3          -none-     character      
    ##  1          -none-     character      
    ##  5          -none-     character      
    ##  5          -none-     character      
    ##  3          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  2          -none-     character      
    ##  1          -none-     character      
    ##  2          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  3          -none-     character      
    ##  1          -none-     character      
    ##  3          -none-     character      
    ##  2          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  2          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  2          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  3          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  3          -none-     character      
    ##  3          -none-     character      
    ##  3          -none-     character      
    ##  2          -none-     character      
    ##  2          -none-     character      
    ##  2          -none-     character      
    ##  1          -none-     character      
    ##  3          -none-     character      
    ##  2          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  2          -none-     character      
    ##  2          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  2          -none-     character      
    ##  2          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  2          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  2          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  2          -none-     character      
    ##  2          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  1          -none-     character      
    ##  vehicles.Length  vehicles.Class  vehicles.Mode
    ##  2          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  1          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  1          -none-     character               
    ##  2          -none-     character               
    ##  0          -none-     character               
    ##  1          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  1          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  1          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  1          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  1          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  1          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  1          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  0          -none-     character               
    ##  starships.Length  starships.Class  starships.Mode
    ##  2          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  1          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  1          -none-     character                  
    ##  5          -none-     character                  
    ##  3          -none-     character                  
    ##  0          -none-     character                  
    ##  2          -none-     character                  
    ##  2          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  1          -none-     character                  
    ##  1          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  1          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  1          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  1          -none-     character                  
    ##  0          -none-     character                  
    ##  1          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  3          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  1          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  1          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  1          -none-     character                  
    ##  0          -none-     character                  
    ##  1          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  1          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character                  
    ##  1          -none-     character                  
    ##  0          -none-     character                  
    ##  0          -none-     character

``` r
dados
```

    ## # A tibble: 87 × 14
    ##    name     height  mass hair_color skin_color eye_color birth_year sex   gender
    ##    <chr>     <int> <dbl> <chr>      <chr>      <chr>          <dbl> <chr> <chr> 
    ##  1 Luke Sk…    172    77 blond      fair       blue            19   male  mascu…
    ##  2 C-3PO       167    75 <NA>       gold       yellow         112   none  mascu…
    ##  3 R2-D2        96    32 <NA>       white, bl… red             33   none  mascu…
    ##  4 Darth V…    202   136 none       white      yellow          41.9 male  mascu…
    ##  5 Leia Or…    150    49 brown      light      brown           19   fema… femin…
    ##  6 Owen La…    178   120 brown, gr… light      blue            52   male  mascu…
    ##  7 Beru Wh…    165    75 brown      light      blue            47   fema… femin…
    ##  8 R5-D4        97    32 <NA>       white, red red             NA   none  mascu…
    ##  9 Biggs D…    183    84 black      light      brown           24   male  mascu…
    ## 10 Obi-Wan…    182    77 auburn, w… fair       blue-gray       57   male  mascu…
    ## # ℹ 77 more rows
    ## # ℹ 5 more variables: homeworld <chr>, species <chr>, films <list>,
    ## #   vehicles <list>, starships <list>

``` r
#verificando se há valores NA's
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
dados$height
```

    ##  [1] 172 167  96 202 150 178 165  97 183 182 188 180 228 180 173 175 170 180  66
    ## [20] 170 183 200 190 177 175 180 150  NA  88 160 193 191 170 185 196 224 206 183
    ## [39] 137 112 183 163 175 180 178  79  94 122 163 188 198 196 171 184 188 264 188
    ## [58] 196 185 157 183 183 170 166 165 193 191 183 168 198 229 213 167  96 193 191
    ## [77] 178 216 234 188 178 206  NA  NA  NA  NA  NA

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
Poe Dameron: 172 BB8: 67 Captain Phasma: 200 Dessa forma, será imputado
tais valores para conhecidos para eliminar os NA’s:

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
dados$mass
```

    ##  [1]   77.0   75.0   32.0  136.0   49.0  120.0   75.0   32.0   84.0   77.0
    ## [11]   84.0     NA  112.0   80.0   74.0 1358.0   77.0  110.0   17.0   75.0
    ## [21]   78.2  140.0  113.0   79.0   79.0   83.0     NA     NA   20.0   68.0
    ## [31]   89.0   90.0     NA   45.0   66.0   82.0     NA     NA     NA   40.0
    ## [41]     NA     NA   80.0     NA   55.0   15.0   45.0     NA   65.0   84.0
    ## [51]   82.0   87.0     NA   50.0     NA     NA   80.0     NA   85.0     NA
    ## [61]     NA   80.0   56.2   50.0     NA   80.0     NA   79.0   55.0  102.0
    ## [71]   88.0     NA     NA     NA   48.0     NA   57.0  159.0  136.0   79.0
    ## [81]   48.0   80.0     NA     NA     NA     NA     NA

``` r
count(dados[is.na(dados$mass),]) #há 6 observações sem a altura (height)
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
mass: Wilhuff Tarkin  
Mon Mothma  
Arvel Crynyd  
Finis Valorum  
Rugor Nass  
Ric Olié  
Watto  
Quarsh Panaka  
Shmi Skywalker  
Bib Fortuna … Jocasta Nu  
R4-P17  
San Hill  
Finn  
Rey  
Poe Dameron  
BB8  
Captain Phasma Totalizando 28 personagens sem os dados referentes à
variável mass.

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
  filter(is.na(dados$mass)) %>% 
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
