**Getting ALL inputs to an alias**  
*By Toothless#7854 originally but heavily bastardized and used by silverbass#2407*  
  
``{{set("x","%1% %2% %3% %4% %5% %6% %7% %8% %9%")}}{{set("x",x[:x.find("%")-1])}}``  
  
No really that's it. It just goes in and removes everything that hasn't been passed in