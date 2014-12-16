
ls *.svg | sed 's/\.svg//' > x

for i in `cat x` ; do
   # generate the .pdf_tex files:
   ~/bin/svgToPdfTex $i

   # update the embedded paths:
   perl -p -i -e "s,$i.pdf,../../figures/ece1254/report_svg,$i.pdf," $i.pdf_tex
done

