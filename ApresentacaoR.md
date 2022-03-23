## Instalação do R e do Rstudio

-   R:

<a href="https://www.r-project.org/">https://www.r-project.org/</a>

-   Rstudio:

<a href="https://www.rstudio.com/">https://www.rstudio.com/</a>

## R base

    1 + 1

    ## [1] 2

    x = c(3, 4, 5, 7)
    m = matrix(c(1,2,3,4,5,6), 3, 2, byrow=TRUE)

    df = data.frame(nome = c('Joana', 'Marta', 'Félix', 'João', 'Ana'), 
                    sexo = c('F', 'F', 'M', 'M', 'F'),
                    filhos = c(0, 1, 1, 0, 2),
                    notas = c(5.7, 8.8, 9, 6, 10))

    lista = list(num= 1,
                 vetor = x,
                 dataframe = df)

## Gráficos simples

-   pie
-   barplot
-   plot
-   hist
-   boxplot

## Entrada de dados por arquivos

    #setwd('..\\Dados')
    df1 = read.csv('Dados\\teste.csv', header=T)

    df2 = read.table('Dados\\Notas.txt', header=T)

    #install.packages('readxl')
    #install.packages('janitor')
    library(readxl)
    library(janitor)

    milho = read_excel('Dados\\milho_br.xlsx', sheet=3, skip=4)
    colnames(milho) = c('Nível',    'Cód.', 'Município', 
                        'Total', 'Unidade de Medida')
    clean_names(milho)

    ## # A tibble: 5,436 x 5
    ##    nivel cod     municipio                  total unidade_de_medida
    ##    <chr> <chr>   <chr>                      <chr> <chr>            
    ##  1 MU    1100015 Alta Floresta D'Oeste (RO) 6728  Hectares         
    ##  2 MU    1100023 Ariquemes (RO)             1400  Hectares         
    ##  3 MU    1100031 Cabixi (RO)                20020 Hectares         
    ##  4 MU    1100049 Cacoal (RO)                2139  Hectares         
    ##  5 MU    1100056 Cerejeiras (RO)            30050 Hectares         
    ##  6 MU    1100064 Colorado do Oeste (RO)     1550  Hectares         
    ##  7 MU    1100072 Corumbiara (RO)            25090 Hectares         
    ##  8 MU    1100080 Costa Marques (RO)         120   Hectares         
    ##  9 MU    1100098 Espigão D'Oeste (RO)       2284  Hectares         
    ## 10 MU    1100106 Guajará-Mirim (RO)         45    Hectares         
    ## # ... with 5,426 more rows

## Tibbles

    library(tidyverse)
    tb1 = tibble(a = c('a', 'g', 'd'), 
                 b = 1:3, 
                 c = c(3.3, 3.4, 3.0), 
                 funcoes=c(mean, max, sd))

    media = tb1$funcoes[[1]]
    media(c(1,2,3))

    ## [1] 2

    df = iris
    tb2 = as_tibble(df)
    tb2

    ## # A tibble: 150 x 5
    ##    Sepal.Length Sepal.Width Petal.Length Petal.Width Species
    ##           <dbl>       <dbl>        <dbl>       <dbl> <fct>  
    ##  1          5.1         3.5          1.4         0.2 setosa 
    ##  2          4.9         3            1.4         0.2 setosa 
    ##  3          4.7         3.2          1.3         0.2 setosa 
    ##  4          4.6         3.1          1.5         0.2 setosa 
    ##  5          5           3.6          1.4         0.2 setosa 
    ##  6          5.4         3.9          1.7         0.4 setosa 
    ##  7          4.6         3.4          1.4         0.3 setosa 
    ##  8          5           3.4          1.5         0.2 setosa 
    ##  9          4.4         2.9          1.4         0.2 setosa 
    ## 10          4.9         3.1          1.5         0.1 setosa 
    ## # ... with 140 more rows

    head(tb2, 10)

    ## # A tibble: 10 x 5
    ##    Sepal.Length Sepal.Width Petal.Length Petal.Width Species
    ##           <dbl>       <dbl>        <dbl>       <dbl> <fct>  
    ##  1          5.1         3.5          1.4         0.2 setosa 
    ##  2          4.9         3            1.4         0.2 setosa 
    ##  3          4.7         3.2          1.3         0.2 setosa 
    ##  4          4.6         3.1          1.5         0.2 setosa 
    ##  5          5           3.6          1.4         0.2 setosa 
    ##  6          5.4         3.9          1.7         0.4 setosa 
    ##  7          4.6         3.4          1.4         0.3 setosa 
    ##  8          5           3.4          1.5         0.2 setosa 
    ##  9          4.4         2.9          1.4         0.2 setosa 
    ## 10          4.9         3.1          1.5         0.1 setosa

    tail(tb2, 10)

    ## # A tibble: 10 x 5
    ##    Sepal.Length Sepal.Width Petal.Length Petal.Width Species  
    ##           <dbl>       <dbl>        <dbl>       <dbl> <fct>    
    ##  1          6.7         3.1          5.6         2.4 virginica
    ##  2          6.9         3.1          5.1         2.3 virginica
    ##  3          5.8         2.7          5.1         1.9 virginica
    ##  4          6.8         3.2          5.9         2.3 virginica
    ##  5          6.7         3.3          5.7         2.5 virginica
    ##  6          6.7         3            5.2         2.3 virginica
    ##  7          6.3         2.5          5           1.9 virginica
    ##  8          6.5         3            5.2         2   virginica
    ##  9          6.2         3.4          5.4         2.3 virginica
    ## 10          5.9         3            5.1         1.8 virginica

    print(tb2, n = Inf)

    ## # A tibble: 150 x 5
    ##     Sepal.Length Sepal.Width Petal.Length Petal.Width Species   
    ##            <dbl>       <dbl>        <dbl>       <dbl> <fct>     
    ##   1          5.1         3.5          1.4         0.2 setosa    
    ##   2          4.9         3            1.4         0.2 setosa    
    ##   3          4.7         3.2          1.3         0.2 setosa    
    ##   4          4.6         3.1          1.5         0.2 setosa    
    ##   5          5           3.6          1.4         0.2 setosa    
    ##   6          5.4         3.9          1.7         0.4 setosa    
    ##   7          4.6         3.4          1.4         0.3 setosa    
    ##   8          5           3.4          1.5         0.2 setosa    
    ##   9          4.4         2.9          1.4         0.2 setosa    
    ##  10          4.9         3.1          1.5         0.1 setosa    
    ##  11          5.4         3.7          1.5         0.2 setosa    
    ##  12          4.8         3.4          1.6         0.2 setosa    
    ##  13          4.8         3            1.4         0.1 setosa    
    ##  14          4.3         3            1.1         0.1 setosa    
    ##  15          5.8         4            1.2         0.2 setosa    
    ##  16          5.7         4.4          1.5         0.4 setosa    
    ##  17          5.4         3.9          1.3         0.4 setosa    
    ##  18          5.1         3.5          1.4         0.3 setosa    
    ##  19          5.7         3.8          1.7         0.3 setosa    
    ##  20          5.1         3.8          1.5         0.3 setosa    
    ##  21          5.4         3.4          1.7         0.2 setosa    
    ##  22          5.1         3.7          1.5         0.4 setosa    
    ##  23          4.6         3.6          1           0.2 setosa    
    ##  24          5.1         3.3          1.7         0.5 setosa    
    ##  25          4.8         3.4          1.9         0.2 setosa    
    ##  26          5           3            1.6         0.2 setosa    
    ##  27          5           3.4          1.6         0.4 setosa    
    ##  28          5.2         3.5          1.5         0.2 setosa    
    ##  29          5.2         3.4          1.4         0.2 setosa    
    ##  30          4.7         3.2          1.6         0.2 setosa    
    ##  31          4.8         3.1          1.6         0.2 setosa    
    ##  32          5.4         3.4          1.5         0.4 setosa    
    ##  33          5.2         4.1          1.5         0.1 setosa    
    ##  34          5.5         4.2          1.4         0.2 setosa    
    ##  35          4.9         3.1          1.5         0.2 setosa    
    ##  36          5           3.2          1.2         0.2 setosa    
    ##  37          5.5         3.5          1.3         0.2 setosa    
    ##  38          4.9         3.6          1.4         0.1 setosa    
    ##  39          4.4         3            1.3         0.2 setosa    
    ##  40          5.1         3.4          1.5         0.2 setosa    
    ##  41          5           3.5          1.3         0.3 setosa    
    ##  42          4.5         2.3          1.3         0.3 setosa    
    ##  43          4.4         3.2          1.3         0.2 setosa    
    ##  44          5           3.5          1.6         0.6 setosa    
    ##  45          5.1         3.8          1.9         0.4 setosa    
    ##  46          4.8         3            1.4         0.3 setosa    
    ##  47          5.1         3.8          1.6         0.2 setosa    
    ##  48          4.6         3.2          1.4         0.2 setosa    
    ##  49          5.3         3.7          1.5         0.2 setosa    
    ##  50          5           3.3          1.4         0.2 setosa    
    ##  51          7           3.2          4.7         1.4 versicolor
    ##  52          6.4         3.2          4.5         1.5 versicolor
    ##  53          6.9         3.1          4.9         1.5 versicolor
    ##  54          5.5         2.3          4           1.3 versicolor
    ##  55          6.5         2.8          4.6         1.5 versicolor
    ##  56          5.7         2.8          4.5         1.3 versicolor
    ##  57          6.3         3.3          4.7         1.6 versicolor
    ##  58          4.9         2.4          3.3         1   versicolor
    ##  59          6.6         2.9          4.6         1.3 versicolor
    ##  60          5.2         2.7          3.9         1.4 versicolor
    ##  61          5           2            3.5         1   versicolor
    ##  62          5.9         3            4.2         1.5 versicolor
    ##  63          6           2.2          4           1   versicolor
    ##  64          6.1         2.9          4.7         1.4 versicolor
    ##  65          5.6         2.9          3.6         1.3 versicolor
    ##  66          6.7         3.1          4.4         1.4 versicolor
    ##  67          5.6         3            4.5         1.5 versicolor
    ##  68          5.8         2.7          4.1         1   versicolor
    ##  69          6.2         2.2          4.5         1.5 versicolor
    ##  70          5.6         2.5          3.9         1.1 versicolor
    ##  71          5.9         3.2          4.8         1.8 versicolor
    ##  72          6.1         2.8          4           1.3 versicolor
    ##  73          6.3         2.5          4.9         1.5 versicolor
    ##  74          6.1         2.8          4.7         1.2 versicolor
    ##  75          6.4         2.9          4.3         1.3 versicolor
    ##  76          6.6         3            4.4         1.4 versicolor
    ##  77          6.8         2.8          4.8         1.4 versicolor
    ##  78          6.7         3            5           1.7 versicolor
    ##  79          6           2.9          4.5         1.5 versicolor
    ##  80          5.7         2.6          3.5         1   versicolor
    ##  81          5.5         2.4          3.8         1.1 versicolor
    ##  82          5.5         2.4          3.7         1   versicolor
    ##  83          5.8         2.7          3.9         1.2 versicolor
    ##  84          6           2.7          5.1         1.6 versicolor
    ##  85          5.4         3            4.5         1.5 versicolor
    ##  86          6           3.4          4.5         1.6 versicolor
    ##  87          6.7         3.1          4.7         1.5 versicolor
    ##  88          6.3         2.3          4.4         1.3 versicolor
    ##  89          5.6         3            4.1         1.3 versicolor
    ##  90          5.5         2.5          4           1.3 versicolor
    ##  91          5.5         2.6          4.4         1.2 versicolor
    ##  92          6.1         3            4.6         1.4 versicolor
    ##  93          5.8         2.6          4           1.2 versicolor
    ##  94          5           2.3          3.3         1   versicolor
    ##  95          5.6         2.7          4.2         1.3 versicolor
    ##  96          5.7         3            4.2         1.2 versicolor
    ##  97          5.7         2.9          4.2         1.3 versicolor
    ##  98          6.2         2.9          4.3         1.3 versicolor
    ##  99          5.1         2.5          3           1.1 versicolor
    ## 100          5.7         2.8          4.1         1.3 versicolor
    ## 101          6.3         3.3          6           2.5 virginica 
    ## 102          5.8         2.7          5.1         1.9 virginica 
    ## 103          7.1         3            5.9         2.1 virginica 
    ## 104          6.3         2.9          5.6         1.8 virginica 
    ## 105          6.5         3            5.8         2.2 virginica 
    ## 106          7.6         3            6.6         2.1 virginica 
    ## 107          4.9         2.5          4.5         1.7 virginica 
    ## 108          7.3         2.9          6.3         1.8 virginica 
    ## 109          6.7         2.5          5.8         1.8 virginica 
    ## 110          7.2         3.6          6.1         2.5 virginica 
    ## 111          6.5         3.2          5.1         2   virginica 
    ## 112          6.4         2.7          5.3         1.9 virginica 
    ## 113          6.8         3            5.5         2.1 virginica 
    ## 114          5.7         2.5          5           2   virginica 
    ## 115          5.8         2.8          5.1         2.4 virginica 
    ## 116          6.4         3.2          5.3         2.3 virginica 
    ## 117          6.5         3            5.5         1.8 virginica 
    ## 118          7.7         3.8          6.7         2.2 virginica 
    ## 119          7.7         2.6          6.9         2.3 virginica 
    ## 120          6           2.2          5           1.5 virginica 
    ## 121          6.9         3.2          5.7         2.3 virginica 
    ## 122          5.6         2.8          4.9         2   virginica 
    ## 123          7.7         2.8          6.7         2   virginica 
    ## 124          6.3         2.7          4.9         1.8 virginica 
    ## 125          6.7         3.3          5.7         2.1 virginica 
    ## 126          7.2         3.2          6           1.8 virginica 
    ## 127          6.2         2.8          4.8         1.8 virginica 
    ## 128          6.1         3            4.9         1.8 virginica 
    ## 129          6.4         2.8          5.6         2.1 virginica 
    ## 130          7.2         3            5.8         1.6 virginica 
    ## 131          7.4         2.8          6.1         1.9 virginica 
    ## 132          7.9         3.8          6.4         2   virginica 
    ## 133          6.4         2.8          5.6         2.2 virginica 
    ## 134          6.3         2.8          5.1         1.5 virginica 
    ## 135          6.1         2.6          5.6         1.4 virginica 
    ## 136          7.7         3            6.1         2.3 virginica 
    ## 137          6.3         3.4          5.6         2.4 virginica 
    ## 138          6.4         3.1          5.5         1.8 virginica 
    ## 139          6           3            4.8         1.8 virginica 
    ## 140          6.9         3.1          5.4         2.1 virginica 
    ## 141          6.7         3.1          5.6         2.4 virginica 
    ## 142          6.9         3.1          5.1         2.3 virginica 
    ## 143          5.8         2.7          5.1         1.9 virginica 
    ## 144          6.8         3.2          5.9         2.3 virginica 
    ## 145          6.7         3.3          5.7         2.5 virginica 
    ## 146          6.7         3            5.2         2.3 virginica 
    ## 147          6.3         2.5          5           1.9 virginica 
    ## 148          6.5         3            5.2         2   virginica 
    ## 149          6.2         3.4          5.4         2.3 virginica 
    ## 150          5.9         3            5.1         1.8 virginica

## Tibbles com a função tribble

    notas = tribble(~aluno, ~ano, ~mat, ~port, ~sexo,
                    'João', 2003, 9, 9, 'M',
                    'João', 2004, 8,8.9, 'M',
                    'João', 2005, 8.5, 7, 'M',
                    'Ana', 2003, 9.1,7.8, 'F',
                    'Ana', 2005, 9.1, 8, 'F'
    )

## Operador pipe

pipe:
<a href="https://www.datacamp.com/community/tutorials/pipe-r-tutorial">https://www.datacamp.com/community/tutorials/pipe-r-tutorial</a>

tidyverse:
<a href="https://oliviergimenez.github.io/intro_tidyverse/#7">https://oliviergimenez.github.io/intro\_tidyverse/\#7</a>

    #install.packages('tidyverse')
    library(tidyverse)
    min(max(round(sqrt(1:40), 1)))

    ## [1] 6.3

    (1:40) %>% 
      sqrt() %>% 
      round(1) %>% 
      max() %>% 
      min()

    ## [1] 6.3

## Pivot\_longer

    dados = read_excel('Dados\\populacao.xls', skip = 3, sheet = 1)

    dados.org = dados %>% pivot_longer(cols = `1960`:`2020`, 
                           names_to = "ano", values_to = "populacao")

    #billboard

    billboard.org = billboard %>% pivot_longer(cols = wk1:wk76, 
                                        names_to = "semana", 
                                        values_to = "rank")
    #billboard.org

## Pivot\_wider

    dados = tribble(~n, ~aluno, ~discip, ~nota,
                    1,   'Ana', 'port',      7,
                    2,   'Ana',  'mat',      9,
                    3,   'Ana',  'geo',      8,
                    4,   'Miguel','mat',   9.8
                    )
    #dados

    dados.org = dados %>% pivot_wider(names_from = discip, values_from = nota,
                          values_fill = list(nota=0))
    #dados.org

## Separete

    table3

    ## # A tibble: 6 x 3
    ##   country      year rate             
    ## * <chr>       <int> <chr>            
    ## 1 Afghanistan  1999 745/19987071     
    ## 2 Afghanistan  2000 2666/20595360    
    ## 3 Brazil       1999 37737/172006362  
    ## 4 Brazil       2000 80488/174504898  
    ## 5 China        1999 212258/1272915272
    ## 6 China        2000 213766/1280428583

    table3 %>% separate(col=rate, into = c("casos", "pop"), 
                        sep = "/", convert = T)

    ## # A tibble: 6 x 4
    ##   country      year  casos        pop
    ##   <chr>       <int>  <int>      <int>
    ## 1 Afghanistan  1999    745   19987071
    ## 2 Afghanistan  2000   2666   20595360
    ## 3 Brazil       1999  37737  172006362
    ## 4 Brazil       2000  80488  174504898
    ## 5 China        1999 212258 1272915272
    ## 6 China        2000 213766 1280428583

## Complete

    notas = tribble(~aluno, ~ano, ~mat,
                   'João', 2013, 9,
                   'João', 2014, 8,
                   'João', 2015, 8.5,
                   'Ana', 2013, 9.1,
                   'Ana', 2015, 9.1,
                   'Carla', 2015, 7)

    notas.na = notas %>% complete(aluno, ano)
    notas.na = notas %>% complete(aluno, ano=2013:2017)
    notas.na = notas %>% complete(aluno, ano=2013:2017, fill=list(mat='Sem Nota'))

## Select

    notas %>% select(aluno, mat)

    ## # A tibble: 6 x 2
    ##   aluno   mat
    ##   <chr> <dbl>
    ## 1 João    9  
    ## 2 João    8  
    ## 3 João    8.5
    ## 4 Ana     9.1
    ## 5 Ana     9.1
    ## 6 Carla   7

    #notas %>% select(-ano)

    #notas %>% select(starts_with('al'))

    #notas %>% select(ends_with('t'))

    #notas %>% select(last_col())

    #notas %>% select(contains('a'))
                     
    #notas %>% select(starts_with('a') & ends_with('no'))

## Filter

    notas %>% filter(aluno == 'João')

    ## # A tibble: 3 x 3
    ##   aluno   ano   mat
    ##   <chr> <dbl> <dbl>
    ## 1 João   2013   9  
    ## 2 João   2014   8  
    ## 3 João   2015   8.5

    #notas %>% filter(aluno == 'João', mat > 8.5)

    #notas %>% filter(!aluno %in% c('Ana', 'Carla'))

    #notas %>% filter(!aluno %in% c('Ana', 'Carla'))

## Mutate / Transmute

    #airquality %>% mutate(rad_solar_med = mean(Solar.R, na.rm = T))

    #airquality %>% mutate(TempC = round((Temp - 32)/1.8,1))

    #airquality %>% transmute(TempC = round((Temp - 32)/1.8,1))

## Joins

<a href="https://r4ds.had.co.nz/relational-data.html">https://r4ds.had.co.nz/relational-data.html</a>

    a = tribble(~id, ~nome, ~idade,
                1, 'Ana', 25,
                2, 'Lucas', 64,
                4, 'Tadeu', 29,
                5, 'Maria', 18,
                6, 'Tony', 21)

    b = tribble(~id, ~mat,
                1, 8.7,
                2, 9.3,
                3, 6.9,
                5, 7.8,
                8, 8)

    #a %>% inner_join(b, by='id')

    #a %>% full_join(b, by='id')

## Arrange

    iris %>% arrange(Sepal.Length) %>% head(5)

    ##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
    ## 1          4.3         3.0          1.1         0.1  setosa
    ## 2          4.4         2.9          1.4         0.2  setosa
    ## 3          4.4         3.0          1.3         0.2  setosa
    ## 4          4.4         3.2          1.3         0.2  setosa
    ## 5          4.5         2.3          1.3         0.3  setosa

    iris %>% arrange(desc(Sepal.Length), Sepal.Width) %>% head(5)

    ##   Sepal.Length Sepal.Width Petal.Length Petal.Width   Species
    ## 1          7.9         3.8          6.4         2.0 virginica
    ## 2          7.7         2.6          6.9         2.3 virginica
    ## 3          7.7         2.8          6.7         2.0 virginica
    ## 4          7.7         3.0          6.1         2.3 virginica
    ## 5          7.7         3.8          6.7         2.2 virginica

## summarise / group\_by

    library(janitor)
    dados = read_excel('Dados\\atlas2013_dadosbrutos_pt.xlsx', sheet = 2)

    dados %>% 
      group_by(ANO) %>% 
      summarise(esp.vida.m = mean(ESPVIDA, na.rm = T),
                esp.vida.d = sd(ESPVIDA, na.rm = T),
                tEnv.max = max(T_ENV, na.rm = T),
                contagem = n()) %>% 
      clean_names()

    ## # A tibble: 3 x 5
    ##     ano esp_vida_m esp_vida_d t_env_max contagem
    ##   <dbl>      <dbl>      <dbl>     <dbl>    <int>
    ## 1  1991       63.7       4.72      12.6     5565
    ## 2  2000       68.4       3.96      15.6     5565
    ## 3  2010       73.1       2.68      20.4     5565

## Ggplot

<a href="https://www.r-project.org/">https://www.r-project.org/</a>

    p = airquality %>% 
      ggplot(aes(Temp)) + 
      geom_area(stat = "bin", fill = 'red', alpha = .5)

    p = airquality %>% 
      ggplot(aes(as.factor(Month), Temp)) +
      geom_boxplot()

    p = airquality %>% 
      ggplot(aes(Temp, Wind)) + 
      geom_hex()
