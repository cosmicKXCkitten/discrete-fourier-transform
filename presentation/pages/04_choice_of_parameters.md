---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>4 / 14</span>
</header>

## II. Выбор оптимальных параметров сетки

Найдем минимальный шаг и количество точек для временной сетки, чтобы избежать эффекта наложения частот (алиасинга). Минимальный шаг временной сетки согласно критерию Найквиста равен $dt = \frac{1}{2 f_{max}}$. В данной задаче максимальная частота в бигармоническом сигнале равна $f_{max} = 4\text{МГц}$. Таким образом, условие для оптимального шага по времени выглядит следующим образом:

<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ dt < \frac{1}{2 f_{max}} = \frac{1}{8\text{МГц}}. $$

</div>

Для получения более точных значений и красивых графиков было выбрано следующее значение шага для временной сетки:

<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ dt = \frac{1}{25 f_{max}} = \frac{1}{100\text{МГц}} = 10\text{нс}. $$

</div>
