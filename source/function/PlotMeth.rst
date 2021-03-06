PlotMeth
========

BatMeth2: An Integrated Package for Bisulfite DNA Methylation Data Analysis with Indel-sensitive Mapping.  

.. contents:: 
    :local:

python library
--------------

install library required

.. code:: bash

    pip install numpy
    pip install pandas
    pip install matplotlib
    pip install seaborn


bt2profile
----------

Plot DNA methlation profile across gene/ TE/ predefined bed region, such as peak or dmr region.
The input DNA methylation level matrix is produced by :doc:`MethyGff`.


The *.TSSprofile.txt *.centerprofile.txt and *.AverMethylevel.txt are calulated by :doc:`MethyGff`.

.. code:: bash

    $ BatMeth2 methyGff -o H3K4me3.bdgene H3K4me3.unbdgene \
        -G genome.fa -m methratio.txt \
        -b H3K4me3.bdgene.bed H3K4me3.unbdgene.bed -B

    $ bt2profile.py -f H3K4me3.bdgene.TSSprofile.txt \
        H3K4me3.unbdgene.TSSprofile.txt \
        -l H3K4me3.bdgene H3K4me3.unbdgene \
        --outFileName H3K4me3.output.meth.pdf \
        -s 1 1 -xl up2k TSS down2k --context C 

.. image:: ../media/profile-tss.png
   :height: 300 px
   :width: 400 px
   :alt: profile
   :align: center

.. code:: bash

    $ BatMeth2 methyGff -o active random \
        -G genome.fa -m methratio.txt \
        -b active.bed random.bed -B

    $ bt2profile.py -f active.centerprofile.txt \
        random.centerprofile.txt \
        -l active random \
        --outFileName active_random.output.meth.pdf \
        -s 1 1 -xl up2k center down2k

.. image:: ../media/profile-center.png

.. code:: bash

    $ bt2profile.py -f H3K27me3.bdgene.AverMethylevel.txt \
        H3K27me3.unbdgene.AverMethylevel.txt \
        -l H3K27me3.bdgene H3K27me3.unbdgene \
        --outFileName H3K27me3.output.meth.pdf \
        -s 1 1 1 -xl up2k TSS TES down2k

.. image:: ../media/profile-body.png
   :height: 300 px
   :width: 400 px
   :alt: profile
   :align: center


bt2basicplot
------------

.. code:: bash

    $ python3 bt2basicplot.py -c coverfile.txt coverfile2.txt -o tt.pdf

.. image:: ../media/plot-basic-coverage.png
   :height: 300 px
   :width: 560 px
   :alt: coverage
   :align: center

.. code:: bash

    $ python3 bt2basicplot.py -f prefix1.gene.cg.txt prefix2.gene.cg.txt \
        -c coverfile.txt coverfile2.txt -o tt.pdf

.. image:: ../media/plot-basic-boxplot.png
   :height: 300 px
   :width: 600 px
   :alt: boxplot
   :align: center

.. image:: ../media/plot-basic-corplot1.png
   :height: 300 px
   :width: 600 px
   :alt: corplot1
   :align: center

.. image:: ../media/plot-basic-corplot2.png
   :height: 300 px
   :width: 360 px
   :alt: corplot2
   :align: center

.. image:: ../media/plot-basic-coverage.png
   :height: 300 px
   :width: 600 px
   :alt: coverage
   :align: center

bt2chrprofile
-------------

bt2heatmap
----------

.. code:: bash

    $ python bt2heatmap.py -m H3K4me3.bdgene.GENE.cg.txt -l bg \
    -o test0.pdf -z k43 -sl TSS -el TTS

.. image:: ../media/plot-heatmap-0.png
   :height: 380 px
   :width: 200 px
   :alt: heatmap0
   :align: center

.. code:: bash

    $ python bt2heatmap.py -m H3K4me3.bdgene.TSS.cg.txt H3K4me3.bdgene.TTS.cg.txt \
        -l tss tts -o test.pdf --zMax 0.1 --colorMap vlag --centerlabel center -z bd

.. image:: ../media/plot-heatmap-1.png
   :height: 460 px
   :width: 400 px
   :alt: heatmap0
   :align: center

.. code:: bash

    $ python bt2heatmap.py -m H3K4me3.bdgene.TSS.cg.txt H3K4me3.bdgene.TTS.cg.txt \
        H3K4me3.unbdgene.TSS.cg.txt H3K4me3.unbdgene.TTS.cg.txt \
        -l test end -o test2.pdf --zMax 0.05 --centerlabel center \
        --plotmatrix 2x2 --colorList white,red -z bd unbd

.. image:: ../media/plot-heatmap-2.png
   :height: 500 px
   :width: 400 px
   :alt: heatmap0
   :align: center

.. code:: bash

    $ python bt2heatmap.py -f H3K4me3.bdgene.body.cg.txt H3K4me3.bdgene.body.cg.txt \
        H3K4me3.unbdgene.body.cg.txt H3K4me3.unbdgene.body.cg.txt \
        -l test end -o test3.pdf --zMax 0.5 --centerlabel center \
        --plotmatrix 2x2 -z bd unbd

.. image:: ../media/plot-heatmap-3.png
   :height: 500 px
   :width: 400 px
   :alt: heatmap0
   :align: center

.. code:: bash

    $ python bt2heatmap.py -m H3K4me3.bdgene.TSS.cg.txt H3K4me3.bdgene.TTS.cg.txt \
        H3K4me3.bdgene.TSS.chg.txt H3K4me3.bdgene.TTS.chg.txt \
        H3K4me3.bdgene.TSS.chh.txt H3K4me3.bdgene.TTS.chh.txt \
        -l H3K4me3.bdgene-tss H3K4me3.bdgene-tts \
        -o H3K4me3.bdgene.TSS_TTS.heatmap.pdf --plotmatrix 3x2 \
        --centerlabel center -z cg chg chh --zMax 0.3 1 0.01

.. image:: ../media/plot-heatmap-4.png
   :height: 500 px
   :width: 400 px
   :alt: heatmap0
   :align: center


.. tip:: DNA methylation level distribution on chromosome (bt2chrplot) and DNA methylation level distribution (bt2visul) are currently being tested, and we will update them as soon as possible.
         
        Note: @HZAU.

.. tip:: For feature requests or bug reports please open an issue `on github <http://github.com/ZhouQiangwei/BatMeth2>`__.
