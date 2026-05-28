---
layout: default
class: text-sm
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>10 / 14</span>
</header>

## V. Проверка обратимости ДПФ с помощью теоремы Котельникова-Шеннона

Убедимся в обратимости ДПФ, проведя кривую между узлами сетки $l$ на более частой сетке с шагом $h/10$ 
и используя теорему Котельникова-Шеннона:
<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ p(t) = \sum_{l=0}^{N-1} p(l) sinc \left( \frac{\pi}{h} (t - lh) \right). $$

</div>

<a href="/reversibility_check.html" target="_blank" 
     class="flex items-center gap-5 p-5 border border-white/10 bg-white/5 hover:bg-white/10 hover:border-blue-500/50 rounded-xl transition-all duration-200 group no-underline text-current w-full block">
    <div class="w-12 h-12 rounded-xl bg-blue-500/10 flex items-center justify-center text-xl text-blue-400 group-hover:scale-105 transition-transform shrink-0">
      📊
    </div>
    <div class="text-left">
      <div class="font-bold text-base text-gray-200 group-hover:text-blue-400 transition-colors">Теорема Котельникова-Шеннона</div>
      <div class="text-xs opacity-60 mt-1">Исходный сигнал, дискретный сигнал и восстановленный по теореме Котельникова-Шеннона сигнал</div>
    </div>
</a>
