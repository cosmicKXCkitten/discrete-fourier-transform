---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>8 / 14</span>
</header>

## IV. Реализация обратного ДПФ

Теперь реализуем алгоритм обратного ДПФ для сеточной функции по формуле:
<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ p(l) = \sum_{l=0}^{N-1} \overline{p_{T}(n)} W_N^{nl}. $$

</div>
