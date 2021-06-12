PlotMeth
========

BatMeth2: An Integrated Package for Bisulfite DNA Methylation Data Analysis with Indel-sensitive Mapping.  

.. contents:: 
    :local:

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


bt2heatmap
----------

.. code:: bash

    $ python bt2heatmap.py -m H3K4me3.bdgene.GENE.cg.txt -l bg \
    -o test0.pdf -z k43 -sl TSS -el TTS

.. image:: ../media/plot-heatmap-0.png

.. code:: bash

    $ python bt2heatmap.py -m H3K4me3.bdgene.TSS.cg.txt H3K4me3.bdgene.TTS.cg.txt \
        -l tss tts -o test.pdf --zMax 0.1 --colorMap vlag --centerlabel center -z bd

.. image:: ../media/plot-heatmap-1.png

.. code:: bash

    $ python bt2heatmap.py -m H3K4me3.bdgene.TSS.cg.txt H3K4me3.bdgene.TTS.cg.txt \
        H3K4me3.unbdgene.TSS.cg.txt H3K4me3.unbdgene.TTS.cg.txt \
        -l test end -o test2.pdf --zMax 0.05 --centerlabel center \
        --plotmatrix 2x2 --colorList white,red -z bd unbd

.. image:: ../media/plot-heatmap-2.png

.. code:: bash

    $ python bt2heatmap.py -f H3K4me3.bdgene.body.cg.txt H3K4me3.bdgene.body.cg.txt \
        H3K4me3.unbdgene.body.cg.txt H3K4me3.unbdgene.body.cg.txt \
        -l test end -o test3.pdf --zMax 0.5 --centerlabel center \
        --plotmatrix 2x2 -z bd unbd

.. image:: ../media/plot-heatmap-3.png

.. code:: bash

    $ python bt2heatmap.py -m H3K4me3.bdgene.TSS.cg.txt H3K4me3.bdgene.TTS.cg.txt \
        H3K4me3.bdgene.TSS.chg.txt H3K4me3.bdgene.TTS.chg.txt \
        H3K4me3.bdgene.TSS.chh.txt H3K4me3.bdgene.TTS.chh.txt \
        -l H3K4me3.bdgene-tss H3K4me3.bdgene-tts \
        -o H3K4me3.bdgene.TSS_TTS.heatmap.pdf --plotmatrix 3x2 \
        --centerlabel center -z cg chg chh --zMax 0.3 1 0.01

.. image:: ../media/plot-heatmap-4.png

bt2chrprofile
-------------

bt2boxplot
----------

.. tip:: For feature requests or bug reports please open an issue `on github <http://github.com/ZhouQiangwei/BatMeth2>`__.
