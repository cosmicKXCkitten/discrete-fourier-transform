---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>13 / 14</span>
</header>

## VII. Аналитический расчет спектра производной

Для коэффициентов ряда Фурье для производной сигнала получим следующее выражение:
<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ 
     \overline{\dot{p}_{T}(f_n)} = -2 \pi f a_0 \left( I(n, -1) - I(n, 1) + \frac{1}{2} I(n, -2) - \frac{1}{2} I(n, 2) \right), \quad
    I(n, k) = \frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} e^{i \omega_0 (k - n) t} \, dt = 
    \begin{cases}
        1, & n = k \\
        0, & n \neq k
    \end{cases}
  $$

</div>

Отсюда видно, что спектр производной сигнала является дискретным с пиками на частотах $\omega_0$, $-\omega_0$, $2\omega_0$, $-2\omega_0$.

<a href="/analytical_derivative.html" target="_blank" 
     class="flex items-center gap-5 p-5 border border-white/10 bg-white/5 hover:bg-white/10 hover:border-blue-500/50 rounded-xl transition-all duration-200 group no-underline text-current w-full block">
    <div class="w-12 h-12 rounded-xl bg-blue-500/10 flex items-center justify-center text-xl text-blue-400 group-hover:scale-105 transition-transform shrink-0">
      📊
    </div>
    <div class="text-left">
      <div class="font-bold text-base text-gray-200 group-hover:text-blue-400 transition-colors">Результаты аналитического расчета спектра производной</div>
      <div class="text-xs opacity-60 mt-1">Исходный сигнал, амплитуда, фаза, действительная и мнимая части</div>
    </div>
</a>