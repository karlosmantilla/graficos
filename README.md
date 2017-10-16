EMPEZANDO A TRABAJAR CON GRÁFICOS
=======================

### Carlos Mantilla

### 2017-10-15

Algo importante y que muchas veces no se hace es el análisis gráfico.
En la mayoría de los casos se le suele dar más importancia a la presentación de tablas y resúmenes numéricos. Sin embargo, el uso de gráficos llega a ofrecer información que puede ser empleada para fortalecer el análisis o para comprender mejor el fenómeno estudiado  antes de proceder al procesamiento de datos. Veamos un ejemplo simple de un gráfico:

Primero revisemos que no existan objetos previamente creados
```r
> ls()
```

```
[1] "ChooseOutputFormat" "fig.files"          "lines"             
[4] "rmdDir"             "saveDir"           
```
Si los hay, ¿cómo procedemos?

```r
> rm(list=ls(all=TRUE))
```

Una vez se ha limpiado el área de trabajo, procedemos a cargar los datos. Para el ejemplo, usaremos una base de datos suministrada por R:

```r
> head(mtcars)
```

```
                   mpg cyl disp  hp drat    wt  qsec vs am gear carb
Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
```
```r
> ?mtcars
```

```r
> attach(mtcars)
> plot(wt, mpg)
> abline(lm(mpg~wt))
> title("Regresión: MPG|Weight")
> detach(mtcars)
```

Podemos guardar las gráficas. Para lo cual tenemos varias opciones:
1. Usando el menú contextual
2. Mediante el uso de comandos
```r
> pdf("ejemplo.pdf")
> attach(mtcars)
> plot(wt, mpg)
> abline(lm(mpg~wt))
> title("Regression of MPG on Weight")
> detach(mtcars)
> dev.off()
```
```r
> # También se puede emplear:
> # win.metafile()
> # png()
> # jpeg()
> # bmp()
> # tiff()
> # xfig()
> # postscript()
```
```r
> tiff("ejemplo.tiff")
> attach(mtcars)
> plot(wt, mpg)
> abline(lm(mpg~wt))
> title("Regresión MPG|Weight")
> detach(mtcars)
> dev.off()
```
<img src="figure/ejemplo.tiff" title="plot of chunk unnamed-chunk-52" alt="plot of chunk unnamed-chunk-52" width="750" />

```r
> ## Vamos, ahora, a definir algunos parámetros gráficos.
```



```r
> ## Para ello, usemos un ejemplo corto tomado de la literatura.
```



```r
> ## Dos drogas y sus dosis:
```



```r
> # +--------------------------------------------------+
```



```r
> # | Dosage | Response to Drug A | Response to Drug B |
```



```r
> # +--------+--------------------+--------------------+
```



```r
> # |   20   |         16         |          15        |
```



```r
> # |   30   |         20         |          18        |
```



```r
> # |   40   |         27         |          25        |
```



```r
> # |   45   |         40         |          31        |
```



```r
> # |   60   |         60         |          40        |
```



```r
> # +--------------------------------------------------+
```



```r
> dose <- c(20, 30, 40, 45, 60)
```



```r
> drugA <- c(16, 20, 27, 40, 60)
```



```r
> drugB <- c(15, 18, 25, 31, 40)
```



```r
> plot(dose, drugA, type="b")
```

<img src="figure/unnamed-chunk-72-1.png" title="plot of chunk unnamed-chunk-72" alt="plot of chunk unnamed-chunk-72" width="750" />



```r
> opar <- par(no.readonly=TRUE)
```



```r
> par(lty=2, pch=17)
```



```r
> plot(dose, drugA, type="b")
```

<img src="figure/unnamed-chunk-75-1.png" title="plot of chunk unnamed-chunk-75" alt="plot of chunk unnamed-chunk-75" width="750" />



```r
> par(opar)
```



```r
> plot(dose, drugA, type="b", lty=2, pch=17)
```

<img src="figure/unnamed-chunk-77-1.png" title="plot of chunk unnamed-chunk-77" alt="plot of chunk unnamed-chunk-77" width="750" />



```r
> plot(dose, drugA, type="b", lty=3, lwd=3, pch=15, cex=2)
```

<img src="figure/unnamed-chunk-78-1.png" title="plot of chunk unnamed-chunk-78" alt="plot of chunk unnamed-chunk-78" width="750" />



```r
> library(RColorBrewer)
```



```r
> n <- 7
```



```r
> mycolors <- brewer.pal(n, "Set1")
```



```r
> barplot(rep(1,n), col=mycolors)
```

<img src="figure/unnamed-chunk-82-1.png" title="plot of chunk unnamed-chunk-82" alt="plot of chunk unnamed-chunk-82" width="750" />



```r
> n <- 10
```



```r
> mycolors <- rainbow(n)
```



```r
> pie(rep(1, n), labels=mycolors, col=mycolors)
```

<img src="figure/unnamed-chunk-85-1.png" title="plot of chunk unnamed-chunk-85" alt="plot of chunk unnamed-chunk-85" width="750" />



```r
> mygrays <- gray(0:n/n)
```



```r
> pie(rep(1, n), labels=mygrays, col=mygrays)
```

<img src="figure/unnamed-chunk-87-1.png" title="plot of chunk unnamed-chunk-87" alt="plot of chunk unnamed-chunk-87" width="750" />



```r
> par(font.lab=3, cex.lab=1.5, font.main=4, cex.main=2)
```



```r
> windowsFonts(
+ A=windowsFont("Arial Black"),
+ B=windowsFont("Bookman Old Style"),
+ C=windowsFont("Comic Sans MS")
+ )
```



```r
> dose <- c(20, 30, 40, 45, 60)
```



```r
> drugA <- c(16, 20, 27, 40, 60)
```



```r
> drugB <- c(15, 18, 25, 31, 40)
```



```r
> opar <- par(no.readonly=TRUE)
```



```r
> par(pin=c(2, 3))
```



```r
> par(lwd=2, cex=1.5)
```



```r
> par(cex.axis=.75, font.axis=3)
```



```r
> plot(dose, drugA, type="b", pch=19, lty=2, col="red")
```

<img src="figure/unnamed-chunk-97-1.png" title="plot of chunk unnamed-chunk-97" alt="plot of chunk unnamed-chunk-97" width="750" />



```r
> plot(dose, drugB, type="b", pch=23, lty=6, col="blue", bg="green")
```

<img src="figure/unnamed-chunk-98-1.png" title="plot of chunk unnamed-chunk-98" alt="plot of chunk unnamed-chunk-98" width="750" />



```r
> par(opar)
```



```r
> plot(dose, drugA, type="b",
+ col="red", lty=2, pch=2, lwd=2,
+ main="Pruebas Clínicas para Droga A",
+ sub="Estos son Datos Hipotéticos",
+ xlab="Dosis", ylab="Respuesta de la Droga",
+ xlim=c(0, 60), ylim=c(0, 70))
```

<img src="figure/unnamed-chunk-100-1.png" title="plot of chunk unnamed-chunk-100" alt="plot of chunk unnamed-chunk-100" width="750" />



```r
> title(main="My Title", col.main="red",
+ sub="My Subtitle", col.sub="blue",
+ xlab="My X label", ylab="My Y label",
+ col.lab="green", cex.lab=0.75)
```

```
Error in title(main = "My Title", col.main = "red", sub = "My Subtitle", : plot.new has not been called yet
```



```r
> dev.off()
```

```
pdf 
  4 
```



```r
> ## Veamos algo más creativo:
```



```r
> x <- c(1:10)
```



```r
> y <- x
```



```r
> z <- 10/x
```



```r
> opar <- par(no.readonly=TRUE)
```



```r
> par(mar=c(5, 4, 4, 8) + 0.1)
```



```r
> plot(x, y, type="b",
+ pch=21, col="red",
+ yaxt="n", lty=3, ann=FALSE)
```

<img src="figure/unnamed-chunk-109-1.png" title="plot of chunk unnamed-chunk-109" alt="plot of chunk unnamed-chunk-109" width="750" />



```r
> lines(x, z, type="b", pch=22, col="blue", lty=2)
```

```
Error in plot.xy(xy.coords(x, y), type = type, ...): plot.new has not been called yet
```



```r
> axis(2, at=x, labels=x, col.axis="red", las=2)
```

```
Error in axis(2, at = x, labels = x, col.axis = "red", las = 2): plot.new has not been called yet
```



```r
> axis(4, at=z, labels=round(z, digits=2),
+ col.axis="blue", las=2, cex.axis=0.7, tck=-.01)
```

```
Error in axis(4, at = z, labels = round(z, digits = 2), col.axis = "blue", : plot.new has not been called yet
```



```r
> mtext("y=1/x", side=4, line=3, cex.lab=1, las=2, col="blue")
```

```
Error in mtext("y=1/x", side = 4, line = 3, cex.lab = 1, las = 2, col = "blue"): plot.new has not been called yet
```



```r
> title("An Example of Creative Axes",
+ xlab="X values",
+ ylab="Y=X")
```

```
Error in title("An Example of Creative Axes", xlab = "X values", ylab = "Y=X"): plot.new has not been called yet
```



```r
> par(opar)
```



```r
> dev.off()
```

```
pdf 
  4 
```



```r
> # Pongamos la leyenda y grafiquemos ambos casos
```



```r
> dose <- c(20, 30, 40, 45, 60)
```



```r
> drugA <- c(16, 20, 27, 40, 60)
```



```r
> drugB <- c(15, 18, 25, 31, 40)
```



```r
> opar <- par(no.readonly=TRUE)
```



```r
> par(lwd=2, cex=1.5, font.lab=2)
```



```r
> plot(dose, drugA, type="b",
+ pch=15, lty=1, col="red", ylim=c(0, 60),
+ main="Drug A vs. Drug B",
+ xlab="Drug Dosage", ylab="Drug Response")
```

<img src="figure/unnamed-chunk-123-1.png" title="plot of chunk unnamed-chunk-123" alt="plot of chunk unnamed-chunk-123" width="750" />



```r
> lines(dose, drugB, type="b",
+ pch=17, lty=2, col="blue")
```

```
Error in plot.xy(xy.coords(x, y), type = type, ...): plot.new has not been called yet
```



```r
> abline(h=c(30), lwd=1.5, lty=2, col="gray")
```

```
Error in int_abline(a = a, b = b, h = h, v = v, untf = untf, ...): plot.new has not been called yet
```



```r
> library(Hmisc)
```



```r
> minor.tick(nx=3, ny=3, tick.ratio=0.5)
```

```
Error in (function (side, at = NULL, labels = TRUE, tick = TRUE, line = NA, : plot.new has not been called yet
```



```r
> legend("topleft", inset=.05, title="Drug Type", c("A","B"),
+ lty=c(1, 2), pch=c(15, 17), col=c("red", "blue"))
```

```
Error in strwidth(legend, units = "user", cex = cex, font = text.font): plot.new has not been called yet
```



```r
> par(opar)
```



```r
> attach(mtcars)
```

```
The following object is masked from package:ggplot2:

    mpg
```



```r
> plot(wt, mpg,
+ main="Mileage vs. Car Weight",
+ xlab="Weight", ylab="Mileage",
+ pch=18, col="blue")
```

<img src="figure/unnamed-chunk-131-1.png" title="plot of chunk unnamed-chunk-131" alt="plot of chunk unnamed-chunk-131" width="750" />



```r
> text(wt, mpg,
+ row.names(mtcars),
+ cex=0.6, pos=4, col="red")
```

```
Error in text.default(wt, mpg, row.names(mtcars), cex = 0.6, pos = 4, : plot.new has not been called yet
```



```r
> detach(mtcars)
```



```r
> opar <- par(no.readonly=TRUE)
```



```r
> par(cex=1.5)
```



```r
> plot(1:7,1:7,type="n")
```

<img src="figure/unnamed-chunk-136-1.png" title="plot of chunk unnamed-chunk-136" alt="plot of chunk unnamed-chunk-136" width="750" />



```r
> text(3,3,"Example of default text")
```

```
Error in text.default(3, 3, "Example of default text"): plot.new has not been called yet
```



```r
> text(4,4,family="mono","Example of mono-spaced text")
```

```
Error in text.default(4, 4, family = "mono", "Example of mono-spaced text"): plot.new has not been called yet
```



```r
> text(5,5,family="serif","Example of serif text")
```

```
Error in text.default(5, 5, family = "serif", "Example of serif text"): plot.new has not been called yet
```



```r
> par(opar)
```



```r
> attach(mtcars)
```

```
The following object is masked from package:ggplot2:

    mpg
```



```r
> opar <- par(no.readonly=TRUE)
```



```r
> par(mfrow=c(2,2))
```



```r
> plot(wt,mpg, main="Scatterplot of wt vs. mpg")
```

<img src="figure/unnamed-chunk-144-1.png" title="plot of chunk unnamed-chunk-144" alt="plot of chunk unnamed-chunk-144" width="750" />



```r
> plot(wt,disp, main="Scatterplot of wt vs. disp")
```

<img src="figure/unnamed-chunk-145-1.png" title="plot of chunk unnamed-chunk-145" alt="plot of chunk unnamed-chunk-145" width="750" />



```r
> hist(wt, main="Histogram of wt")
```

<img src="figure/unnamed-chunk-146-1.png" title="plot of chunk unnamed-chunk-146" alt="plot of chunk unnamed-chunk-146" width="750" />



```r
> boxplot(wt, main="Boxplot of wt")
```

<img src="figure/unnamed-chunk-147-1.png" title="plot of chunk unnamed-chunk-147" alt="plot of chunk unnamed-chunk-147" width="750" />



```r
> par(opar)
```



```r
> detach(mtcars)
```



```r
> attach(mtcars)
```

```
The following object is masked from package:ggplot2:

    mpg
```



```r
> opar <- par(no.readonly=TRUE)
```



```r
> par(mfrow=c(3,1))
```



```r
> hist(wt)
```

<img src="figure/unnamed-chunk-153-1.png" title="plot of chunk unnamed-chunk-153" alt="plot of chunk unnamed-chunk-153" width="750" />



```r
> hist(mpg)
```

<img src="figure/unnamed-chunk-154-1.png" title="plot of chunk unnamed-chunk-154" alt="plot of chunk unnamed-chunk-154" width="750" />



```r
> hist(disp)
```

<img src="figure/unnamed-chunk-155-1.png" title="plot of chunk unnamed-chunk-155" alt="plot of chunk unnamed-chunk-155" width="750" />



```r
> par(opar)
```



```r
> detach(mtcars)
```



```r
> dev.off()
```

```
pdf 
  4 
```



```r
> attach(mtcars)
```

```
The following object is masked from package:ggplot2:

    mpg
```



```r
> layout(matrix(c(1,1,2,3), 2, 2, byrow = TRUE))
```



```r
> hist(wt)
```

<img src="figure/unnamed-chunk-161-1.png" title="plot of chunk unnamed-chunk-161" alt="plot of chunk unnamed-chunk-161" width="750" />



```r
> hist(mpg)
```

<img src="figure/unnamed-chunk-162-1.png" title="plot of chunk unnamed-chunk-162" alt="plot of chunk unnamed-chunk-162" width="750" />



```r
> hist(disp)
```

<img src="figure/unnamed-chunk-163-1.png" title="plot of chunk unnamed-chunk-163" alt="plot of chunk unnamed-chunk-163" width="750" />



```r
> detach(mtcars)
```



```r
> attach(mtcars)
```

```
The following object is masked from package:ggplot2:

    mpg
```



```r
> layout(matrix(c(1, 1, 2, 3), 2, 2, byrow = TRUE),
+ widths=c(3, 1), heights=c(1, 2))
```



```r
> hist(wt)
```

<img src="figure/unnamed-chunk-167-1.png" title="plot of chunk unnamed-chunk-167" alt="plot of chunk unnamed-chunk-167" width="750" />



```r
> hist(mpg)
```

<img src="figure/unnamed-chunk-168-1.png" title="plot of chunk unnamed-chunk-168" alt="plot of chunk unnamed-chunk-168" width="750" />



```r
> hist(disp)
```

<img src="figure/unnamed-chunk-169-1.png" title="plot of chunk unnamed-chunk-169" alt="plot of chunk unnamed-chunk-169" width="750" />



```r
> detach(mtcars)
```



```r
> opar <- par(no.readonly=TRUE)
> par(fig=c(0, 0.8, 0, 0.8))
> plot(mtcars$wt, mtcars$mpg, xlab="Miles Per Gallon", ylab="Car Weight")
```

<img src="figure/unnamed-chunk-173-1.png" title="plot of chunk unnamed-chunk-173" alt="plot of chunk unnamed-chunk-173" width="750" />

```r
> par(fig=c(0, 0.8, 0.55, 1), new=TRUE)
```

```
Warning in par(fig = c(0, 0.8, 0.55, 1), new = TRUE): llamada par(new=TRUE)
sin gráfico
```

```r
> boxplot(mtcars$wt, horizontal=TRUE, axes=FALSE)
```

<img src="figure/unnamed-chunk-175-1.png" title="plot of chunk unnamed-chunk-175" alt="plot of chunk unnamed-chunk-175" width="750" />

```r
> par(fig=c(0.65, 1, 0, 0.8), new=TRUE)
```

```
Warning in par(fig = c(0.65, 1, 0, 0.8), new = TRUE): llamada par(new=TRUE)
sin gráfico
```

```r
> boxplot(mtcars$mpg, axes=FALSE)
```
<img src="figure/unnamed-chunk-177-1.png" title="plot of chunk unnamed-chunk-177" alt="plot of chunk unnamed-chunk-177" width="750" />

```r
> mtext("Enhanced Scatterplot", side=3, outer=TRUE, line=-3)
```

```
Error in mtext("Enhanced Scatterplot", side = 3, outer = TRUE, line = -3): plot.new has not been called yet
```
```r
> par(opar)
```
