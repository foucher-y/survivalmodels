The ‘survivalmodels’ package
================

## What is the ‘survivalmodels’ package?

The `survivalmodels` package implements neural networks from the Python
packages [pycox](https://github.com/havakv/pycox). Importantly, this a
lighter but CRAN-compatible version of the ‘survivalmodels’ package
proposed by Raphael Sonabend based on the version 0.1.19. The complete
and updated version is available at this
[link](https://github.com/RaphaelS1/survivalmodels).

## Basic Usage

``` r
# load dependencies
library(survival)

train <- simsurvdata(200)

# Fit the survival neural network
fit <- deepsurv(Surv(time, status) ~ ., data = train, frac = 0.3, activation = "relu",
    num_nodes = c(4L, 8L, 4L, 2L), dropout = 0.1, early_stopping = TRUE, epochs = 100L,
    batch_size = 32L)

# Return survivals for two independent individuals
test <- simsurvdata(1)
predict(fit, newdata = test)
#>   3.33999991416931 3.34299993515015 3.38000011444092 3.38899993896484
#> 0           0.9929           0.9858           0.9786           0.9715
#>   3.43600010871887 3.45600008964539 3.47300004959106 3.48600006103516
#> 0           0.9644           0.9573           0.9502           0.9431
#>   3.49499988555908 3.49900007247925 3.50300002098083 3.50799989700317
#> 0           0.9359           0.9218           0.9146           0.9075
#>   3.52600002288818 3.53500008583069 3.53699994087219 3.54699993133545
#> 0           0.9004           0.8933           0.8862           0.8791
#>   3.58899998664856 4.65999984741211 4.68200016021729 4.79400014877319
#> 0           0.8719           0.8648           0.8577           0.8506
#>   4.84000015258789 4.89699983596802 4.93200016021729 4.93699979782104
#> 0           0.8435           0.8363           0.8292           0.8221
#>   4.94500017166138 4.95900011062622 4.96199989318848 4.98600006103516
#> 0            0.815           0.8079           0.8008           0.7936
#>   4.98899984359741 4.99499988555908 4.99700021743774 5.00400018692017
#> 0           0.7865           0.7794           0.7723           0.7652
#>   5.00799989700317 5.01000022888184 5.02299976348877 5.02600002288818
#> 0           0.7581           0.7439           0.7368           0.7296
#>   5.02799987792969 5.07200002670288 5.18400001525879 5.30700016021729
#> 0           0.7225           0.7154           0.7083           0.7012
#>   5.34200000762939 5.35099983215332 5.35500001907349 5.3600001335144
#> 0           0.6941           0.6869           0.6798          0.6727
#>   5.36100006103516 5.38600015640259 5.39599990844727 5.40999984741211
#> 0           0.6656           0.6585           0.6513           0.6442
#>   5.41300010681152 5.42700004577637 5.42899990081787 5.43400001525879
#> 0           0.6371             0.63           0.6229           0.6158
#>   5.43699979782104 5.44700002670288 5.46700000762939 5.46799993515015
#> 0           0.6086           0.6015           0.5944           0.5733
#>   5.47100019454956 5.47499990463257 5.47700023651123 5.48699998855591
#> 0           0.5662           0.5591           0.5519           0.5378
#>   5.49300003051758 5.49399995803833 5.49499988555908 5.4980001449585
#> 0           0.5307           0.5235           0.5164          0.5093
#>   5.51300001144409 5.53599977493286 5.53800010681152 5.54099988937378
#> 0           0.5022            0.495           0.4809           0.4738
#>   5.54699993133545 5.55000019073486 5.55900001525879 5.56099987030029
#> 0           0.4667           0.4595           0.4524           0.4453
#>   5.56199979782104 5.56400012969971 5.56699991226196 5.57800006866455
#> 0           0.4382            0.431           0.4239           0.4168
#>   5.58500003814697 5.58799982070923 5.59600019454956 5.59700012207031
#> 0           0.4097           0.4025           0.3954           0.3883
#>   6.66099977493286 6.67500019073486 6.69000005722046 6.69099998474121
#> 0           0.3812            0.367           0.3599           0.3528
#>   6.74100017547607 6.77400016784668 6.77600002288818 6.78299999237061
#> 0           0.3457           0.3385           0.3314           0.3243
#>   6.80200004577637 6.80800008773804 6.80999994277954 6.81899976730347
#> 0           0.3172             0.31           0.3029           0.2958
#>   6.86899995803833 6.8769998550415
#> 0           0.2886          0.2886
```

## Python Models

The `survivalmodels` package implements models from Python using
[reticulate](https://cran.r-project.org/package=reticulate). In order to
use these models, the required Python packages must be installed
following with
[reticulate::py_install](https://rstudio.github.io/reticulate/reference/py_install.html).
`survivalmodels` includes a helper function to install the required
`pycox` function (with pytorch if also required). Before running any
models in this package, if you have not already installed `pycox` please
run.

``` r
install_pycox(pip = TRUE, install_torch = FALSE)
```

## Installation

Install the latest release from CRAN:

``` r
install.packages("survivalmodels")
```

Install the development version from GitHub:

``` r
remotes::install_github("RaphaelS1/survivalmodels")
```
