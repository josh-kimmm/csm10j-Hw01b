import java.io.FileReader;
import java.util.*;
import java.io.FileNotFoundException;


public class Hw01b {
    static Scanner console = new Scanner(System.in);
    
    public static void main(String[] args)throws FileNotFoundException
    {
        String filename = "stocks.txt";
        Scanner inFile = new Scanner(new FileReader(filename));
        double StockPrice;
        String name;
        char choice;
        Vector<String> StockName = new Vector<String>();
        Vector<Double> StockPriceMin = new Vector<Double>();
        Vector<Double> StockPriceMax = new Vector<Double>();
        Vector<Double> StockPriceTotal = new Vector<Double>();
        Vector<Integer> AvgCounter = new Vector<Integer>();
        
        StockName.addElement(inFile.next());
        StockPriceMin.addElement(inFile.nextDouble());
        StockPriceMax.addElement(StockPriceMin.elementAt(0));
        StockPriceTotal.addElement(StockPriceMin.elementAt(0));
        AvgCounter.addElement(1);
        
        while(inFile.hasNext())
        {
            int compare,i;
            compare = i = StockName.size();
            name = inFile.next();
            StockPrice = inFile.nextDouble();
            for(int count = 0; count < i; count++)
            {
                if(name.equals(StockName.elementAt(count)))
                {
                    if(StockPrice < StockPriceMin.elementAt(count))
                    {
                        StockPriceMin.add(count, StockPrice);
                        StockPriceMin.remove(count + 1);
                    }
                    else if(StockPrice > StockPriceMax.elementAt(count))
                    {
                        StockPriceMax.add(count,StockPrice);
                        StockPriceMax.remove(count + 1);
                    }
                    StockPriceTotal.add(count, (StockPrice + StockPriceTotal.elementAt(count)));
                    StockPriceTotal.remove(count + 1);
                    AvgCounter.add(count, AvgCounter.elementAt(count) + 1);
                    AvgCounter.remove(count + 1);
                }
                else
                    compare--;
            }
            if(compare == 0)
            {
                StockName.addElement(name);
                StockPriceMin.addElement(StockPrice);
                StockPriceMax.addElement(StockPrice);
                StockPriceTotal.addElement(StockPrice);
                AvgCounter.addElement(1);
            }
                    
        }
        inFile.close();
        boolean run = true;
        do
        {
            System.out.println("Enter '1' to get max, min, and avg of a stock");
            System.out.println("Enter '2' to get stock ticker with highest price");
            System.out.println("Enter '3' to get stock ticker with lowest price");
            System.out.println("Enter 'c' to change the stockfile name");
            System.out.println("Enter 'q' to quit");
            System.out.print("Your Choice: ");
            choice = console.next().charAt(0);
            
            switch(choice)
            {
                case '1':
                    System.out.print("Enter a stock ticker: ");
                    name = console.next();
                    GetStockStats(name, StockName, StockPriceMin, StockPriceMax,
                            StockPriceTotal, AvgCounter);
                    break;
                case '2':
                    GetStockHighLow(1, StockName, StockPriceMin, StockPriceMax);
                    break;
                case '3':
                    GetStockHighLow(0, StockName, StockPriceMin, StockPriceMax);
                    break;
                case'c':
                case'C':
                    System.out.print("Enter a stock filename: ");
                    filename = console.next();
                    inFile = new Scanner(new FileReader(filename));
                    StockName = new Vector<String>();
                    StockPriceMin = new Vector<Double>();
                    StockPriceMax = new Vector<Double>();
                    StockPriceTotal = new Vector<Double>();
                    AvgCounter = new Vector<Integer>();
        
                    StockName.addElement(inFile.next());
                    StockPriceMin.addElement(inFile.nextDouble());
                    StockPriceMax.addElement(StockPriceMin.elementAt(0));
                    StockPriceTotal.addElement(StockPriceMin.elementAt(0));
                    AvgCounter.addElement(1);
                    while(inFile.hasNext())
                    {
                        int compare,i;
                        compare = i = StockName.size();
                        name = inFile.next();
                        StockPrice = inFile.nextDouble();
                        for(int count = 0; count < i; count++)
                        {
                            if(name.equals(StockName.elementAt(count)))
                            {
                                if(StockPrice < StockPriceMin.elementAt(count))
                                {
                                    StockPriceMin.add(count, StockPrice);
                                    StockPriceMin.remove(count + 1);
                                }
                                else if(StockPrice > StockPriceMax.elementAt(count))
                                {
                                    StockPriceMax.add(count,StockPrice);
                                    StockPriceMax.remove(count + 1);
                                }
                                StockPriceTotal.add(count, (StockPrice + StockPriceTotal.elementAt(count)));
                                StockPriceTotal.remove(count + 1);
                                AvgCounter.add(count, AvgCounter.elementAt(count) + 1);
                                AvgCounter.remove(count + 1);
                            }
                            else
                                compare--;
                        }
                        if(compare == 0)
                        {
                            StockName.addElement(name);
                            StockPriceMin.addElement(StockPrice);
                            StockPriceMax.addElement(StockPrice);
                            StockPriceTotal.addElement(StockPrice);
                            AvgCounter.addElement(1);
                        }

                    }
                    inFile.close();
                break;
                case 'q':
                case 'Q':
                    System.out.print("Goodbye.");
                    run = false;
                break;

            }
            
        }while(run);
        
    }
        
    static void GetStockStats(String name, Vector<String>StockName,Vector<Double>StockPriceMin,
            Vector<Double>StockPriceMax,Vector<Double> StockPriceTotal,Vector<Integer>AvgCounter)
    {
        name = name.toLowerCase();
        for(int count = 0; count < StockName.size(); count++)
        {
            if(name.equals(StockName.elementAt(count).toLowerCase()))
            {
                System.out.printf("%s min: %.2f max: %.2f avg: %.2f\n",
                        StockName.elementAt(count),StockPriceMin.elementAt(count),
                        StockPriceMax.elementAt(count),
                        (StockPriceTotal.elementAt(count) / AvgCounter.elementAt(count)));
                return;
            }
        }
        System.out.print(name.toUpperCase() + " was not found\n");
    }
    
    static void GetStockHighLow(int option,Vector<String>StockName,
            Vector<Double>StockPriceMin, Vector<Double>StockPriceMax)
    {
        if(option == 1)
        {
            double highestprice = StockPriceMax.elementAt(0);
            int index = 0;
            for(int count = 1; count < StockName.size(); count++)
            {
                if(highestprice < StockPriceMax.elementAt(count))
                {
                    highestprice = StockPriceMax.elementAt(count);
                    index = count;
                }
            }
            System.out.printf("%s has the highest price of %.2f\n",
                    StockName.elementAt(index), highestprice);
        }
        else
        {
            double lowestprice = StockPriceMin.elementAt(0);
            int index = 0;
            for(int count = 1; count < StockName.size(); count++)
            {
                if(lowestprice > StockPriceMin.elementAt(count))
                {
                    lowestprice = StockPriceMin.elementAt(count);
                    index = count;
                }
            }
            System.out.printf("%s has the lowest price of %.2f\n",
                    StockName.elementAt(index), lowestprice);
        }
    }
  
}
