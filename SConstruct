from rsf.proj import *

Fetch('marmvel.hh','marm')
Flow('vel','marmvel.hh',
     '''
     dd form=native | math output="0.001*input"|
     put n1=751 o1=0 d1=0.004 label1=Depth   unit1=km
         n2=2301 o2=0 d2=0.004 label2=Lateral unit2=km
     ''')

Result('marmousi','vel',
     '''
     grey title="Marmousi model" wantitle=y allpos=y color=j
     pclip=100 scalebar=y bartype=v barlabel="V" barunit="m/s"
     ''' )

Flow('mimag1 mimag2','vel',
        '''
        gpurtm imag2=${TARGETS[1]} NJ=6 phost=65
        fm=25 dt=0.0003 tdmute=300
        nt=13000 ns=51 ng=301 
        jsx=40 jsz=0 jgx=1 jgz=0 
        sxbeg=150 szbeg=1 gxbeg=0 gzbeg=1 
        vmute=1.52
        ''')

Result('mimag1','grey allpos=n title="correlation"')
Result('mimag2','grey allpos=n title="normalized_correlation" ')

End()
