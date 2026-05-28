---
layout: default
class: text-sm
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>11 / 14</span>
</header>

## VI. Анализ эталонной реализации из пакета `numpy.fft`

Воспользуемся реализацией прямого и обратного отображения ДПФ из пакета `numpy.fft` и качественно оценим, насколько 
точно они воспроизводят спектр сигнала и его восстановление на примере бигармонического сигнала.

<a href="/reference_implementation_signal.html" target="_blank" 
     class="flex items-center gap-5 p-5 border border-white/10 bg-white/5 hover:bg-white/10 hover:border-blue-500/50 rounded-xl transition-all duration-200 group no-underline text-current w-full block">
    <div class="w-12 h-12 rounded-xl bg-blue-500/10 flex items-center justify-center text-xl text-blue-400 group-hover:scale-105 transition-transform shrink-0">
      📊
    </div>
    <div class="text-left">
      <div class="font-bold text-base text-gray-200 group-hover:text-blue-400 transition-colors">Результаты прямого и обратного преобразований</div>
      <div class="text-xs opacity-60 mt-1">Исходный сигнал, амплитуда, фаза, действительная, мнимая части и восстановленный сигнал</div>
    </div>
</a>

<div class="mt-4 p-2 bg-green-950/40 border border-green-800/60 rounded text-center text-green-300 text-xs">
  Реализация прямого и обратного отображения ДПФ из пакета `numpy.fft` при выбранных параметрах и выбранной сетке достаточно точно
  воспроизводит спектр сигнала и восстанавливает его по спектру. 
</div>
