---
theme: seriph
background: unsplash.com
class: text-center
highlighter: shiki
drawings:
  persist: false
transition: slide-left
title: Дискретное преобразование Фурье
katex: true
---

<link rel="stylesheet" href="jsdelivr.net">

## Дискретное преобразование Фурье

<div class="pt-8 opacity-80 text-sm tracking-wide">
  МГУ имени М.В. Ломоносова <br>
  Физический факультет &middot; Кафедра акустики
</div>

<div class="mt-16 grid grid-cols-2 gap-10 text-left text-sm border-t border-white/20 pt-6">
  <div>
    <span class="opacity-60 block">Выполнил:</span>
    <strong>Студент группы 424</strong> <br>
    Епишин Константин Дмитриевич
  </div>
  <div>
    <span class="opacity-60 block">Куратор группы:</span>
    Нартов Федор Андреевич
  </div>
</div>

<div class="mt-8 text-xs font-mono opacity-50">
  Вариант 2 &middot; 2026
</div>

---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-6">
  <span>Дискретное преобразование Фурье</span>
  <span>1 / 13</span>
</header>

## Содержание

<nav class="space-y-2 mt-6 text-xs">
  <div class="flex items-center gap-3">
    <span class="bg-gray-200 text-gray-700 rounded-full w-8 h-8 flex items-center justify-center font-bold text-xs">I</span>
    <span>Аналитический расчет</span>
  </div>
  <div class="flex items-center gap-3">
    <span class="bg-gray-200 text-gray-700 rounded-full w-8 h-8 flex items-center justify-center font-bold text-xs">II</span>
    <span>Выбор оптимальных параметров</span>
  </div>
  <div class="flex items-center gap-3">
    <span class="bg-gray-200 text-gray-700 rounded-full w-8 h-8 flex items-center justify-center font-bold text-xs">III</span>
    <span>Прямое отображение ДПФ</span>
  </div>
  <div class="flex items-center gap-3">
    <span class="bg-gray-200 text-gray-700 rounded-full w-8 h-8 flex items-center justify-center font-bold text-xs">IV</span>
    <span>Обратное отображение ДПФ</span>
  </div>
  <div class="flex items-center gap-3">
    <span class="bg-gray-200 text-gray-700 rounded-full w-8 h-8 flex items-center justify-center font-bold text-xs">V</span>
    <span>Проверка обратимости ДПФ с помощью теоремы Котельникова-Шеннона</span>
  </div>
  <div class="flex items-center gap-3">
    <span class="bg-gray-200 text-gray-700 rounded-full w-8 h-8 flex items-center justify-center font-bold text-xs">VI</span>
    <span>Анализ эталонной реализации из пакета `numpy.fft`</span>
  </div>
  <div class="flex items-center gap-3">
    <span class="bg-gray-200 text-gray-700 rounded-full w-8 h-8 flex items-center justify-center font-bold text-xs">VII</span>
    <span>Аналитический расчет спектра производной</span>
  </div>
  <div class="flex items-center gap-3">
    <span class="bg-gray-200 text-gray-700 rounded-full w-8 h-8 flex items-center justify-center font-bold text-xs">VIII</span>
    <span>Прямое отображение ДПФ для производной</span>
  </div>
  <div class="flex items-center gap-3">
    <span class="bg-gray-200 text-gray-700 rounded-full w-8 h-8 flex items-center justify-center font-bold text-xs">IX</span>
    <span>Обратное отображение ДПФ для производной</span>
  </div>
</nav>

---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>2 / 13</span>
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

---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>3 / 13</span>
</header>

## I. Аналитический расчет

<a href="/analytical_signal.html" target="_blank" 
     class="flex items-center gap-5 p-5 border border-white/10 bg-white/5 hover:bg-white/10 hover:border-blue-500/50 rounded-xl transition-all duration-200 group no-underline text-current w-full block">
    <div class="w-12 h-12 rounded-xl bg-blue-500/10 flex items-center justify-center text-xl text-blue-400 group-hover:scale-105 transition-transform shrink-0">
      📊
    </div>
    <div class="text-left">
      <div class="font-bold text-base text-gray-200 group-hover:text-blue-400 transition-colors">Результаты аналитического расчета</div>
      <div class="text-xs opacity-60 mt-1">Исходный сигнал, амплитуда, фаза, действительная и мнимая части</div>
    </div>
</a>

---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>4 / 13</span>
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

---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>5 / 13</span>
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

---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>6 / 13</span>
</header>

## III. Реализация прямого ДПФ

Определим универсальную базисную функцию разложения в ряд Фурье на равномерной временной сетке:
<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ W_N^{nl} = exp \left( i \frac{2 \pi n l}{N} \right). $$

</div>

```python
def W(N: int, n: ArrayLike, l: ArrayLike, sign: float = 1.0) -> NDArray[np.complex128]:
    return np.exp(sign * (2.0 * np.pi * 1.0j * np.outer(n, l)) / (N))
```

Теперь реализуем алгоритм прямого ДПФ для сеточной функции по формуле:
<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ \overline{p_{T}(n)} = \frac{1}{N} \sum_{l=0}^{N-1} p(l) W_N^{-nl}. $$

</div>

---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>7 / 13</span>
</header>

## III. Реализация прямого ДПФ

<div class="my-4">

```python
def fft_direct_mapping(signal: ArrayLike, time: ArrayLike, N: int) -> NDArray[np.complex128]:
    signal_grid = np.asarray(signal, dtype=np.float64)
    time_grid = np.asarray(time, dtype=np.float64)
    
    n = np.arange(N)
    l = np.arange(len(time_grid))

    W_matrix = W(N=N, n=n, l=l, sign=-1.0)
    
    return (1.0 / N) * (W_matrix @ signal_grid)
```

<a href="/fft_direct_mapping.html" target="_blank" 
     class="flex items-center gap-5 p-5 border border-white/10 bg-white/5 hover:bg-white/10 hover:border-blue-500/50 rounded-xl transition-all duration-200 group no-underline text-current w-full block">
    <div class="w-12 h-12 rounded-xl bg-blue-500/10 flex items-center justify-center text-xl text-blue-400 group-hover:scale-105 transition-transform shrink-0">
      📊
    </div>
    <div class="text-left">
      <div class="font-bold text-base text-gray-200 group-hover:text-blue-400 transition-colors">Результаты реализации прямого ДПФ</div>
      <div class="text-xs opacity-60 mt-1">Исходный сигнал, амплитуда, фаза, действительная, мнимая части</div>
    </div>
</a>

</div>

---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>8 / 13</span>
</header>

## IV. Реализация обратного ДПФ

Теперь реализуем алгоритм обратного ДПФ для сеточной функции по формуле:
<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ p(l) = \sum_{l=0}^{N-1} \overline{p_{T}(n)} W_N^{nl}. $$

</div>

---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>9 / 13</span>
</header>

## IV. Реализация обратного ДПФ

<div class="my-4">

```python
def fft_reverse_mapping(spectrum: ArrayLike, time: ArrayLike, N: int) -> NDArray[np.complex128]:
    spectrum_grid = np.asarray(spectrum, dtype=np.complex128)
    time_grid = np.asarray(time, dtype=np.float64)
    
    n = np.arange(N)
    l = np.arange(len(time_grid))
    
    W_matrix = W(N=N, n=l, l=n, sign=1.0)
    
    return W_matrix @ spectrum_grid
```

<a href="/fft_reverse_mapping.html" target="_blank" 
     class="flex items-center gap-5 p-5 border border-white/10 bg-white/5 hover:bg-white/10 hover:border-blue-500/50 rounded-xl transition-all duration-200 group no-underline text-current w-full block">
    <div class="w-12 h-12 rounded-xl bg-blue-500/10 flex items-center justify-center text-xl text-blue-400 group-hover:scale-105 transition-transform shrink-0">
      📊
    </div>
    <div class="text-left">
      <div class="font-bold text-base text-gray-200 group-hover:text-blue-400 transition-colors">Результаты реализации обратного ДПФ</div>
      <div class="text-xs opacity-60 mt-1">Исходный и восстановленный сигналы</div>
    </div>
</a>

</div>

---
layout: default
class: text-sm
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>10 / 13</span>
</header>

## V. Проверка обратимости ДПФ с помощью теоремы Котельникова-Шеннона

Убедимся в обратимости ДПФ, проведя кривую между узлами сетки $l$ на более частой сетке с шагом $h/10$ 
и используя теорему Котельникова-Шеннона:
<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ p(t) = \sum_{l=0}^{N-1} p(l) sinc \left( \frac{\pi}{h} (t - lh) \right). $$

</div>

<a href="/reference_implementation_signal.html" target="_blank" 
     class="flex items-center gap-5 p-5 border border-white/10 bg-white/5 hover:bg-white/10 hover:border-blue-500/50 rounded-xl transition-all duration-200 group no-underline text-current w-full block">
    <div class="w-12 h-12 rounded-xl bg-blue-500/10 flex items-center justify-center text-xl text-blue-400 group-hover:scale-105 transition-transform shrink-0">
      📊
    </div>
    <div class="text-left">
      <div class="font-bold text-base text-gray-200 group-hover:text-blue-400 transition-colors">Теорема Котельникова-Шеннона</div>
      <div class="text-xs opacity-60 mt-1">Исходный сигнал, дискретный сигнал и восстановленный по теореме Котельникова-Шеннона сигнал</div>
    </div>
</a>

---
layout: default
class: text-sm
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>11 / 13</span>
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

---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>12 / 13</span>
</header>

## VII. Аналитический расчет спектра производной

Производная исходного сигнала представляет собой сумму двух гармоник с параметрами $a_0 = 0.1 \text{МПа}, f_0 = 2.0 \text{МГц}$:
<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ \frac{\partial p(t)}{\partial t} = 2 a_0 \omega_0 \cos{(\omega_0 t)} + 2 a_0 \omega_0 \cos{(2 \omega_0 t)}, \quad \omega_0 = 2 \pi f_0. $$

</div>

Для вычисления аналитического спектра производной воспользуемся свойством преобразования Фурье о дифференцировании сигнала по времени,
а также видом спектра исходного сигнала:
<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ \frac{d p(t)}{d t} \stackrel{\mathcal{F}}{\longleftrightarrow} 2 \pi i f \overline{p(f)}, \quad \overline{p(f)} = a_0 i \left( \delta(f + f_0) - \delta(f - f_0) + \frac{1}{2} \delta(f + 2 f_0) - \frac{1}{2} \delta(f - 2 f_0) \right). $$

</div>

В итоге для спектра производной получим следующее выражение:
<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ \frac{\partial p(t)}{\partial t} \stackrel{\mathcal{F}}{\longleftrightarrow} -2 \pi f a_0 \left( \delta(f + f_0) - \delta(f - f_0) + \frac{1}{2} \delta(f + 2 f_0) - \frac{1}{2} \delta(f - 2 f_0) \right). $$

</div>

---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>13 / 13</span>
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
