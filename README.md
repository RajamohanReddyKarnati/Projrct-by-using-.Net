# Projrct-by-using-.Net
//By using system key word it will importing namespaces specified in code
//it import Console class we need to use System key word.
//it will provided by .net framework we can reuse any time any where through out the the application.
using System;

//declaring this namespace is custom namespace with class name program
//scope of name space is control class and method
namespace ConsoleApp1
{
    //class is like blue print of type.A class can contain methods ,events and so on.
    class Program
    {
        //when we declare method as static then class programm exist in memory and can access the class it self
        //void is return type of the method if declare void as return type then we no need to return any values from method

        //Main is entry point of the application program executionm will start from main method
        static void Main(string[] args)
        {
            //Console is a class which imported from system namespace 
            //WriteLine is used to print values in console and move line to next
            Console.WriteLine("Welcome World");
            Console.WriteLine("Welcome advanced languge");
            //DateTime.Now is predefined method from .net framework it will return current datetime
            Console.WriteLine(DateTime.Now);
            Console.ReadLine();
        }
    }
}

//Output:--
//Welcome World
//Welcome advanced languge
//11/9/2021 4:13:44 PM

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1
{
    class Sudoku
    {
        static void Main(string[] args)
        {
            var objsudoku = new char[,]
            {
                {'.','.','.','.','7','.','.','3','5'},
                { '.','.','.','5','9','1','.','.','6'},
                { '.','6','.','.','.','.','8','9','.'},
                { '3','.','.','.','6','.','.','.','8'},
                { '1','.','.','3','.','8','.','.','4'},
                { '6','.','.','.','2','.','.','.','7'},
                { '.','8','2','.','.','.','.','6','.'},
                { '5','.','.','9','1','4','.','.','.'},
                { '9','7','.','.','8','.','.','.','.'},
            };
            ValidateSudoku(objsudoku);
        }
        public static void ValidateSudoku(char[,] objboard)
        {
            if (objboard == null || objboard.Length == 0) 
            {
                return;
            }
            Validate(objboard);

        }
        public static bool Validate(char[,] objboard)
        {
            for (int i = 0; i < objboard.GetLength(0); i++)
            {
                for (int j = 0; j < objboard.GetLength(1); j++)
                {
                    if (objboard[i,j]=='.')
                    {
                        for (char c = '1'; c <='9'; c++)
                        {
                            objboard[i, j] = c;
                            if (IsTrue(objboard,i,j,c))
                            {
                                objboard[i, j] = c;
                                if (Validate(objboard))
                                {
                                    return true;
                                }
                                else
                                {
                                    objboard[i, j] = '.';
                                }
                            }
                        }
                        return false;
                    }
                }
            }
            return true;
        }
        private static  bool IsTrue(char[,] objboard,int row,int col,char c)
        {
            for (int i = 0; i < 9; i++)
            {
                if (objboard[i,col]!='.'&&objboard[i,col]==c)
                {
                    return false;
                }
                if (objboard[row,i]!='.'&& objboard[row,i]==c)
                {
                    return false;
                }
                if (objboard[3*(row/3)+i/3,3*(col/3)+i%3]!='.'&&objboard[3*(row/3)+i/3,3*(col/3)+i%3]==c)
                {
                    return false;
                }
            }
            return true;
        }
    }
}

//Output:--
//219876435
//843591276
//765243891
//324167958
//197258624
//658429317
//482735169
//356914782
//971682543

using System;
using System.Collections.Generic;
using System.Collections.ObjectModel;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp1
{
    public class AddAndRemoveUseingCollection
    {
        public static void Main()
        {
            Collection<string> orderItems = new Collection<string>();
            orderItems.Add("Department");
            orderItems.Add("Grocery");
            orderItems.Add("Food"); 
            orderItems.Add("Accessory"); 
            orderItems.Add("Pharmacies");
            orderItems.Add("Technology");
            orderItems.Add("Pets"); 
            orderItems.Add("Toy"); 
            orderItems.Add("Thrift"); 
            orderItems.Add("Services"); 
            orderItems.Add("Kiosks");
            Console.WriteLine("{0} OrderItems:", orderItems.Count);
            Display(orderItems);
            Console.WriteLine("\nIndexOf(\"Kiosks\"):{0}",orderItems.IndexOf("Kiosks"));
            Console.WriteLine("\nContains(\"Services\"):{0}", orderItems.Contains("Services"));
            Console.WriteLine("\nInsert(2,\"Specialty\")");
            orderItems.Insert(2, "Specialty");
            Display(orderItems);
            Console.WriteLine("\norderItems[2]:{0}", orderItems[2]);
            Console.WriteLine("\norderItems[2]=\"Clothing\"");
            Display(orderItems);
            Console.WriteLine("\nRemove(\"Clothing\"");
            orderItems.Remove("Clothing");
            Display(orderItems);
            Console.WriteLine("\nRemoveAt(0)");
            orderItems.RemoveAt(0);
            Display(orderItems);
            Console.WriteLine("\norderItems.Clear()");
            orderItems.Clear();
            Console.WriteLine("Count:{0}", orderItems.Count);
        }
        private static void Display(Collection<string> tList)
        {
            Console.WriteLine();
            foreach (var item in tList)
            {
                Console.WriteLine(item);
            }
        }
    }
}
