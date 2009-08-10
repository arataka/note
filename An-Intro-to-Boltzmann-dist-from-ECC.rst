====================================================
誤り訂正符号 からの ボルツマン分布 入門(アイディア)
====================================================

誤り訂正符号から自然にボルツマン分布が出てくる例 [高田他]_ ．
物理でボルツマン分布やってなくても，ボルツマン分布が分かるような導入法
にならないかな，と考え中．

.. [高田他] 「誤り訂正符合のナイーブ平均場近似」
            http://ci.nii.ac.jp/naid/110003232345/


誤り訂正符号 
=============

送信側のメッセージ 
-------------------

送信側のメッセージは :math:`N` 次元のバイナリ符号
:math:`\bm{\xi} \in \{ -1, 1 \}^N` だとする．メッセージ :math:`\bm{\xi}` の
正規確率は一様分布

.. math::

  P (\bm{\xi}) = \frac{1}{2^N}

を仮定する．さらに，冗長信号として :math:`\bm{\xi}` の各成分の :math:`r` 個の
積 :math:`\xi_{i_1} \cdots \xi_{i_r}` を送信する．

通信路の性質 
-------------

送信されるメッセージには
正規分布で表現されるノイズが加わり，受信側では

- :math:`\xi_i \to \tau_i`, 
- :math:`\xi_{i_1} \cdots \xi_{i_r} \to J_{i_1 \cdots i_r}`

と変化するとする．つまり，
通信チャンネルの特性は， 条件付確率

.. math::

  P (\bm{J}, \bm{\tau} | \bm{\xi}) =
  \prod_{i_1 < \cdots < i_r} P (J_{i_1 \cdots i_r} | \bm{\xi})
  \prod_{i} P (\tau_i | \bm{\xi})

.. math::

  P (J_{i_1 \cdots i_r} | \bm{\xi})
  =
  \frac{1}{\sqrt{2 \pi \frac{J^2 r!}{N^{r-1}} }}
  \exp \left( -
    \frac{(J_{i_1 \cdots i_r} -\frac{j_0 r!}{N^{r-1}})^2}
    { 2 \frac{J^2 r!}{N^{r-1}} }
  \right)

.. math::

  P (\tau_i | \bm{\xi}) =
  \frac{1}{\sqrt{2 \pi \tau^2 }}
  \exp \left( -
    \frac{ (\tau_i - \tau_0 \xi_i)^2 }{ 2 \tau^2 }
  \right)

で表されると考える．

受信されるメッセージ(事後確率) 
-------------------------------

ベイズの公式から事後確率は
:math:`P (\bm{\xi} | \bm{J}, \bm{\tau})
\propto P (\bm{J}, \bm{\tau} | \bm{\xi}) P (\bm{\xi})` となる．
:math:`P (\bm{\xi})` が一様分布であることを考え， :math:`\bm{\xi}` を
:math:`\bm{\sigma}` で推定することを考えると，事後確率は

.. math::

  P (\bm{\sigma} | \bm{J}, \bm{\tau})
  \propto
  \exp \left(
    \beta \sum_{i_1 < \cdots < i_r}
    J_{i_1 \cdots i_r} \sigma_{i_1} \cdots \sigma_{i_r}
    + h \sum_i \tau_i \sigma_i
  \right)

と推定出来る．パラメタ :math:`\beta, h` の正しい値は
:math:`\beta = j_0/J^2`, :math:`h = \tau_0/\tau^2` であるが，
通信チャンネルの特性も未知であるとすればこれらのパラメタも推定すべき対象となる．

ボルツマン分布 
---------------

式の形から，
この事後確率はハミルトニアン :math:`H` を

.. math::

  \beta H =
  - \beta \sum_{i_1 < \cdots < i_r}
  J_{i_1 \cdots i_r} \sigma_{i_1} \cdots \sigma_{i_r}
  - h \sum_i \tau_i \sigma_i

とするボルツマン分布にしたがうことが分かる．
