---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>9 / 14</span>
</header>

## IV. Реализация обратного ДПФ

<div class="my-4">

```python
def fft_reverse_mapping(spectrum: NDArray, time: NDArray, N: int) -> NDArray[np.complex128]:
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