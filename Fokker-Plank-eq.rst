========================
Fokker–Planck equation 
========================

Fokker–Planck equation は粒子の運動を確率密度 :math:`P(x,t)`
の時間変化で記述する式．

.. warning::

  確率密度 :math:`P(x,t)` は，通常の確率密度の表記と違い，規格化の条件は
  :math:`\int_{-\infty}^{\infty} P(x,t) dx =1` である．
  言い換えると，すべての時間で粒子は必ず
  存在する．通常の確率密度の表記では :math:`\int P(x,y) dxdy =1` なので，
  誤解があるかもしれない．というか授業中にひっかかった部分．

Fokker–Planck equation の導出
===============================

Chapman–Kolmogorov equation
----------------------------

- 確率 :math:`P(x,t|x_0) \Delta x` を，「 :math:`x_0` にあった粒子が時間
  :math:`t` 経った後に :math:`[x,x+\Delta x]` に存在する確率」とする．
- 確率 :math:`P(x,t|x_0)` は :math:`t<0` の状態と独立 (Markov 過程)．

この条件下で以下の二式が成り立つ．

.. math::

  P(x,0|x_0) &= \delta (x-x_0) \\
  P(x,t+\Delta t|x_0) &= \int_{-\infty}^{\infty}
  P(x',t|x_0) P(x,\Delta t|x') dx'

最後の式を Chapman–Kolmogorov equation と言う．

参考:

- `Chapman-Kolmogorov Equation -- from Wolfram MathWorld`__
- `Chapman–Kolmogorov equation - Wikipedia, the free encyclopedia`__

__ http://mathworld.wolfram.com/Chapman-KolmogorovEquation.html
__ http://en.wikipedia.org/wiki/Chapman%E2%80%93Kolmogorov_equation


Kramers-Moyal expansion
-----------------------

Chapman–Kolmogorov equation において積分変数を
:math:`x'` から :math:`\Delta x=x-x'` へ
変換し， :math:`x'=x-\Delta x` を代入した

.. math::

  P(x,t+\Delta t|x_0) &= \int_{-\infty}^{\infty}
  P(x-\Delta x, t|x_0) P(x,\Delta t|x-\Delta x) d(\Delta x)

の左辺を :math:`\Delta t` で，
右辺を :math:`\Delta x` で展開する [#f1]_ ．

.. math::

  \mathrm{l.h.s}
  &= P(x,t|x_0) + \frac{\partial P}{\partial t} \Delta t

.. math::

  \mathrm{r.h.s}
  &= \int_{-\infty}^{\infty} P(x-\Delta x, t|x_0)
  P(x+\Delta x-\Delta x,\Delta t|x-\Delta x) d(\Delta x) \\
  %
  &= \int_{-\infty}^{\infty} \sum_{n=0}^{\infty}
  \frac{(-\Delta x)^n}{n!} \frac{\partial^n}{\partial x^n}
  \left\{
    P(x, t|x_0) P(x+\Delta x,\Delta t|x)
  \right\}
  d(\Delta x) \\
  %
  &= \sum_{n=0}^{\infty} \frac{(-1)^n}{n!}
  \frac{\partial^n}{\partial x^n}
  \left\{
    P(x, t|x_0)
    \int_{-\infty}^{\infty} P(x+\Delta x,\Delta t|x) (\Delta x)^n d(\Delta x)
  \right\} \\
  %
  &= P(x, t|x_0)
  \int_{-\infty}^{\infty} P(x+\Delta x,\Delta t|x) d(\Delta x)
  + \sum_{n=1}^{\infty} \frac{(-1)^n}{n!}
  \frac{\partial^n}{\partial x^n}
  \left\{
    P(x, t|x_0)
    \int_{-\infty}^{\infty} P(x+\Delta x,\Delta t|x) (\Delta x)^n d(\Delta x)
  \right\} \\
  %
  &= P(x, t|x_0)
  + \Delta t \sum_{n=0}^{\infty} \frac{(-1)^n}{n!}
  \frac{\partial^n}{\partial x^n} \{ \alpha_n P(x, t|x_0) \}

ここで，

.. math::

  \alpha_n
  = \frac{1}{\Delta t} \langle \Delta x^n \rangle
  = \frac{1}{\Delta t} \int_{-\infty}^{\infty}
  P(x+\Delta x,\Delta t|x) (\Delta x)^n d(\Delta x)

とおいた．

以上から，最初の式は両辺を :math:`\Delta t` で割って，
以下のように変形できる．

.. math::

  \frac{\partial P}{\partial t}
  &= \sum_{n=1}^{\infty} \frac{(-1)^n}{n!}
  \frac{\partial^n}{\partial x^n} \{ \alpha_n P \}

これを Kramers-Moyal expansion と言う．

.. rubric:: Footnotes

.. [#f1]

  :math:`\Delta x` の積分範囲が :math:`(-\infty,\infty)` なので，
  :math:`\Delta x` は微小量ではない．微小量でなくてもテイラー展開は
  成立するので問題ない．


Brown 運動をする場合 
---------------------

Brown 運動(Langevin equation で記述可能な現象)では，
以下の関係が成り立つ．

- :math:`\langle (\Delta x)^1 \rangle \sim \Delta t` 
- :math:`\langle (\Delta x)^2 \rangle \sim \Delta t`
- :math:`\langle (\Delta x)^n \rangle \sim 0\ (n \ge 3)`

  - 証明できるらしい．

.. note::

  証明どうやるんだろう．


よって，以下の Fokker–Planck equation を得る．

.. math::

  \frac{\partial P}{\partial t} =
  - \frac{\partial}{\partial x} (\alpha_1 P)
  + \frac{1}{2} \frac{\partial^2}{\partial x^2} (\alpha_2 P)
