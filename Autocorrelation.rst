==========================
自己相関(Autocorrelation) 
==========================

自己相関関数 と スペクトル 
===========================

自己相関関数(Autocorrelation function) 
---------------------------------------

.. math::

  G(\tau) := \lim_{T\to \infty} \frac{1}{T} \int_0^T dt x(t) x(t+\tau)


スペクトル(spectrum) 
---------------------

.. math::

  y(\omega) &= \int_0^T dt e^{- i\omega t} x(t) \\
  S(\omega) &:= \lim_{T\to \infty} \frac{1}{2\pi T} |y(\omega)|^2


フーリエ変換/逆変換 の関係 
---------------------------

.. math::

  & S(\omega) \\
  &= \lim_{T\to \infty} \frac{1}{2\pi T}
  \left| \int_0^T dt e^{- i\omega t} x(t) \right|^2\\
  %
  &= \lim_{T\to \infty} \frac{1}{2\pi T}
  \left( \int_0^T dt_1 e^{- i\omega t_1} x(t_1) \right)
  \left( \int_0^T dt_2 e^{+ i\omega t_2} x(t_2) \right) \\
  %
  &= \lim_{T\to \infty} \frac{1}{2\pi T} \int_0^T dt_1 \int_0^T  dt_2
  e^{i\omega (t_2 - t_1)} x(t_1) x(t_2)

変数変換 :math:`\tau=t_2-t_1, t_1=\tau_2-\tau=t_1` をする．積分区間は，

- :math:`t_1 \in [0,T]`, :math:`t_2 \in [0,T]` が
- :math:`\tau \in [-T,T]`, :math:`t_1 \in [-\tau,T-\tau]` に変わる．

:math:`dt_1 dt_2 = d\tau dt_1` より [#f1]_ ，

.. math::

  &= \lim_{T\to \infty} \frac{1}{2\pi T}
  \int_{-T}^T d\tau
  \int_{-\tau}^{T-\tau} dt_1 e^{i \omega \tau} x(t_1) x(t_1+\tau) \\
  %
  &= \lim_{T\to \infty} \frac{1}{2\pi}
  \int_{-T}^T d\tau e^{i \omega \tau}
  \frac{1}{T}
  \int_{-\tau}^{T-\tau} dt_1 x(t_1) x(t_1+\tau) \\
  %
  &= \lim_{T\to \infty} \frac{1}{2\pi}
  \int_{-T}^T d\tau e^{i \omega \tau}
  \left(
    \frac{1}{T}
    \int_{-\tau}^{0} dt_1 x(t_1) x(t_1+\tau)
    +
    \underline{
      \frac{1}{T}
      \int_{0}^{T} dt_1 x(t_1) x(t_1+\tau)
    }
    +
    \frac{1}{T}
    \int_{T}^{T-\tau} dt_1 x(t_1) x(t_1+\tau)
  \right) \\
  %
  &= \frac{1}{2\pi}
  \int_{-\infty}^\infty d\tau e^{i \omega \tau}
  \underline{ G(\tau) }

.. note::

  最後の極限操作が無理やりな感じだけど，成り立たない場合ってどんな場合だろう？

.. rubric:: Footnotes

.. [#f1]

  :math:`\tau=\tau(t_1,t_2)=t_2-t_1, t_1=t_1(t_1,t_2)=t_1`
  のヤコビアンを計算すると，

  .. math::
  
    \begin{vmatrix}
      \frac{\partial t_1}{\partial t_1} & \frac{\partial t_1}{\partial t_2} \\
      \frac{\partial\tau}{\partial t_1} & \frac{\partial\tau}{\partial t_2} \\
    \end{vmatrix}
    =
    \begin{vmatrix}
       1 & 0 \\
      -1 & 1 \\
    \end{vmatrix}
    = 1

  となる．


別の定義でも 
=============

.. math::

  G(\tau) &:= \lim_{T\to \infty} \frac{1}{2T} \int_{-T}^T dt x(t) x(t+\tau) \\
  y(\omega) &= \int_{-T}^T dt e^{- i\omega t} x(t) \\
  S(\omega) &:= \lim_{T\to \infty} \frac{1}{2 T} |y(\omega)|^2 \\
  %
  &= \lim_{T\to \infty} \frac{1}{2T}
  \int_{-2T}^{2T} d\tau e^{i \omega \tau}
  \frac{1}{2T}
  \int_{-T-\tau}^{T-\tau} dt_1 x(t_1) x(t_1+\tau) \\
  %
  &= \int_{-\infty}^\infty d\tau e^{i \omega \tau} G(\tau)
