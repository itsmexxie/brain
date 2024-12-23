- máme funkci f definovanou v okolí bodu $x_0$
- existuje-li $\lim{x\rightarrow x_0}{\frac{f(x) - f(x_0)}{x - x_0}}$, nazýváme ji derivací funkce f v bodě $x_0$
- označujeme $f'(x)$
- rychlost změny funkční hodnoty
- z geometrického pohledu se jedná o směrnici tečny v daném bodě
- jiné možné vyjádření:
$$
\lim{h\rightarrow 0}{\frac{f(x_0 + h) - f(x_0)}{h}}
$$
- má-li funkce v $x_0$ derivaci, pak je v $x_0$ spojitá
- opačně neplatí, viz $y = |x|$
## Derivace elementárních funkcí
### $y =  c$
$$
\lim{h\rightarrow 0}{\frac{c-c}{h}}=\frac{0}{h}=0
$$
### $y = x^n$
$$
\begin{aligned}
\lim{h\rightarrow 0}{\frac{(x_0+h)^n-x_0^n}{h}} &= \frac{x_0^n+\binom{n}{1}x_0^{n-1}h+...+h^n-x_0^n}{h} \\ &=n*x_0^{n-1}+\binom{n}{2}x_0^{n-2}h+...+h^{n-1} \\ &=n*x_0^{n-1}
\end{aligned}
$$
- v posledním kroku úpravy využijeme faktu, že *h* se blíží nule - "limitní nula"