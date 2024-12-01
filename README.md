Ordering C#

A Program that allows entry of  numbers and letters and then sorts them into ascending or descending order, based on user input. 


    using System;
    using System.Collections.Generic;
    using System.ComponentModel;
    using System.Data;
    using System.Drawing;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    using System.Windows.Forms;
    
    namespace Ordering
    {
        public partial class letterasc : Form
        {
    
            private List<int> numbers = new List<int>();
            private List<char> letters = new List<char>(); 
    
            public letterasc()
            {
                InitializeComponent();
                ascendingbtn.Enabled = false;
                Descendingbtn.Enabled = false;
                button2.Enabled = false;
                lettersdecs.Enabled = false;
            }
    
            private void addbtn_Click(object sender, EventArgs e)
            {
                numbers.Clear();
                string input = textBox1.Text;
                textBox1.Clear();
    
                numbers = input.Split(',')
                .Select(n => int.Parse(n.Trim())) // Trim and parse each number A LINQ method that applies a transformation to each element of the array.
                .ToList();//place that into the numbers list
                MessageBox.Show("Your list has been saved");
                ascendingbtn.Enabled = true;
                Descendingbtn.Enabled = true;
                
    
    
            }
    
    
            private void ascendingbtn_Click(object sender, EventArgs e)
            {
                numbers.Sort();
    
                label1.Text = "Sorted Numbers: " + string.Join(", ", numbers);//convert sorted numbers back to a string and display in the label
            }
    
            private void Descendingbtn_Click(object sender, EventArgs e)
            {          
                numbers.Sort();
                numbers.Reverse();
    
                label1.Text = "Sorted Numbers: " + string.Join(", ", numbers);//convert sorted numbers back to a string and display in the label
            }
    
    
    
    
            private void lettersadd_Click(object sender, EventArgs e)
            {
                string word = textBox2.Text;
                word = word.ToLower();
                letters = word.ToList();
                MessageBox.Show("Your list has been saved");
                button2.Enabled = true;
                lettersdecs.Enabled = true;
            }
    
            private void button2_Click(object sender, EventArgs e)
            {
                letters.Sort();
    
                label3.Text = "Sorted Letters: " + string.Join(", ", letters);
            }
    
            private void lettersdecs_Click(object sender, EventArgs e)
            {
                letters.Sort();
                letters.Reverse();
                label3.Text = "Sorted Letters: " + string.Join(", ", letters);
            }
    
    
        }
    }
