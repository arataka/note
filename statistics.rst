=====
統計 
=====

整理待ちのものとか 
===================


ベータ分布のモードを求める． 
-----------------------------

.. math::

   & f(x|a,b) = \frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)} x^{a-1} (1-x)^{b-1}\\
   & \textrm{Find mode:} \\
   & f'(x) = \frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)}
   [ (a-1)x^{a-2} (1-x)^{b-1} - x^{a-1} (b-1)(1-x)^{b-2} ] = 0 \\
   & \Rightarrow (a-1) x^{a-2} (1-x)^{b-1} - x^{a-1} (b-1) (1-x)^{b-2} = 0 \\
   & \Rightarrow (a-1) (1-x) - x (b-1) = 0 \\
   & \Rightarrow a - ax - 1 + x - xb + x = 0 \\
   & \Rightarrow x(2 - a - b) = 1 - a \\
   & \Rightarrow x = \frac{1-a}{2-a-b} = \frac{a-1}{a+b-2}

http://formula.s21g.com/formulae/2944

元ネタ(というかこれを清書しただけ):
http://www.actuary.com/actuarial-discussion-forum/showthread.php?t=1434


ベータ分布の積分(間違い探し) 
-----------------------------

.. math::

  \int_0^1 x^{a-1} (1-x)^{b-1} dx
  &= \left[ \frac{x^a}{a} - \frac{x^{a+b-1}}{a+b-1} \right]_0^1 \\
  &= \frac{1}{a} - \frac{1}{a+b-1} \\
  &= \frac{b-1}{a(a+b-1)} 

http://formula.s21g.com/formulae/2945

-> 解答:
`Twitter / 北のぷらす(三日目東N19a): @tkf (x^(a-1))*(1-x)^(b-1) ...`__

__ http://twitter.com/pullus/status/2891230472

