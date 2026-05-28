---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>6 / 14</span>
</header>

## III. Реализация прямого ДПФ

Определим универсальную базисную функцию разложения в ряд Фурье на равномерной временной сетке:
<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ W_N^{nl} = exp \left( i \frac{2 \pi n l}{N} \right). $$

</div>

```python
def W(N: int, n: NDArray, l: NDArray, sign: float = 1.0) -> NDArray[np.complex128]:
    return np.exp(sign * (2.0 * np.pi * 1.0j * np.outer(n, l)) / (N))
```

Теперь реализуем алгоритм прямого ДПФ для сеточной функции по формуле:
<div class="bg-grey-50 border border-gray-200 rounded-lg p-1 my-4 shadow-sm text-center">

  $$ \overline{p_{T}(n)} = \frac{1}{N} \sum_{l=0}^{N-1} p(l) W_N^{-nl}. $$

</div>