---
layout: default
class: text-xs
---

<header class="flex justify-between text-xs opacity-50 border-b border-gray-200 pb-2 mb-4">
  <span>Дискретное преобразование Фурье</span>
  <span>12 / 14</span>
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