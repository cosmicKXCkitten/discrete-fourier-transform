---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>2 / 14</span>
</header>

## I. Аналитический расчет

Исходный акустический сигнал представляет собой сумму двух гармоник с параметрами $a_0 = 0.1 \text{МПа}, f_0 = 2.0 \text{МГц}$:
<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ p(t) = 2 a_0 sin (\omega_0 t) + a_0 sin (2 \omega_0 t), \quad \omega_0 = 2 \pi f_0. $$

</div>

Расчет коэффициентов ряда Фурье осуществляется по формуле:
<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ \overline{p_{T}(f_n)} = \frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} p(t) e^{-2 \pi i f_n t} \, dt, \quad f_n = \frac{n}{T}, \quad f_n = n f_0. $$

</div>

В результате преобразования сигнала с помощью формулы Эйлера для коэффициентов Фурье получится следующее выражение:
<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ 
    \overline{p_{T}(f_n)} = i a_0 \left( I(n, -1) - I(n, 1) + \frac{1}{2} I(n, -2) - \frac{1}{2} I(n, 2) \right), \quad
    I(n, k) = \frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} e^{i \omega_0 (k - n) t} \, dt = 
    \begin{cases}
        1, & n = k \\
        0, & n \neq k
    \end{cases}
  $$

</div>
