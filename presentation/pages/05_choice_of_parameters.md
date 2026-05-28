---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>5 / 14</span>
</header>

## II. Выбор оптимальных параметров сетки

Теперь рассчитаем оптимальное количество узлов временной сетки, используя выбранный шаг по времени:

<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ dt = \frac{1}{25 f_{max}} = \frac{1}{50 f_0} = \frac{T}{50} = \frac{T}{N^*} \implies N^* = 50. $$

</div>

Для удобства и повышения точности численных расчетов лучше всего выбирать число точек равное степени двойки, поэтому окончательное оптимальное количество узлов временной сетки можно определить следующим образом:

<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ 2^n = N > N^* = 50 \implies N = 64, n = 6. $$

</div>
