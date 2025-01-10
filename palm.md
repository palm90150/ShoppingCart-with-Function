namespace งานวันที่24ธันวาปี2024
{
    public partial class Form1 : Form
    {
        private double change;

        public Form1()
        {
            InitializeComponent();
        }

        private void checkBox2_CheckedChanged(object sender, EventArgs e)
        {

        }

        private void textBox2_TextChanged(object sender, EventArgs e)
        {

        }

        private void textBox1_TextChanged(object sender, EventArgs e)
        {

        }

        private void label1_Click(object sender, EventArgs e)
        {

        }

        private void checkBox1_CheckedChanged(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            try
            {
                double dCash = double.Parse(tb_cash.Text);

                double dBeverageTotal = 0;
                double dFoodTotal = 0;

                if (chb_Coffee.Checked)
                {
                    dBeverageTotal += GetItemTotal(tb_Coffee_Price.Text, tb_Coffee_Quantity.Text);
                }
                if (chb_Greentea.Checked)
                {
                    dBeverageTotal += GetItemTotal(tb_Greentea_Price.Text, tb_Greentea_Quantity.Text);
                }

                if (chb_noodle.Checked)
                {
                    dFoodTotal += GetItemTotal(tb_Noodle_Price.Text, tb_Noodle_Quantity.Text);
                }
                if (chb_pizza.Checked)
                {
                    dFoodTotal += GetItemTotal(tb_Pizza_Price.Text, tb_Pizza_Quantity.Text);
                }

                double dGrandTotal = dBeverageTotal + dFoodTotal;

                double dTotalDiscount = CalculateTotalDiscount(dBeverageTotal, dFoodTotal, dGrandTotal);

                dGrandTotal -= dTotalDiscount;

                if (dCash < dGrandTotal)
                {
                    MessageBox.Show("เงินสดไม่เพียงพอ", "ข้อผิดพลาด", MessageBoxButtons.OK, MessageBoxIcon.Warning);
                    return;
                }

                double dChange = dCash - dGrandTotal;

                total.Text = dGrandTotal.ToString("F2");
                tb_change.Text = dChange.ToString("F2");

                CalculateChangeDenominations(dChange);
            }
            catch (FormatException)
            {
                MessageBox.Show("กรุณากรอกข้อมูลตัวเลขให้ถูกต้อง", "ข้อผิดพลาด", MessageBoxButtons.OK, MessageBoxIcon.Error);
            }
        }

        

        private void textBox11_TextChanged(object sender, EventArgs e)
        {

        }
        private void CalculateChangeDenominations(double change)
        {
            double[] denominations = { 1000, 500, 100, 50, 20, 10, 5, 1, 0.50, 0.25 };
            int[] changeCount = new int[denominations.Length];
            double remainChange = change;

            for (int i = 0; i < denominations.Length; i++)
            {
                changeCount[i] = (int)(remainChange / denominations[i]);
                remainChange %= denominations[i];
            }

            tb_1000.Text = changeCount[0].ToString();
            tb_500.Text = changeCount[1].ToString();
            tb_100.Text = changeCount[2].ToString();
            tb_50.Text = changeCount[3].ToString();
            tb_20.Text = changeCount[4].ToString();
            tb_10.Text = changeCount[5].ToString();
            tb_5.Text = changeCount[6].ToString();
            tb_1.Text = changeCount[7].ToString();
            tb_050.Text = changeCount[8].ToString();
            tb_025.Text = changeCount[9].ToString();
        }


        private double GetItemTotal(string priceText, string quantityText)
        {
            double price = 0, quantity = 0;
            try
            {
                price = double.Parse(priceText);
                quantity = double.Parse(quantityText);
            }
            catch (Exception)
            {
                price = 0;
                quantity = 0;
            }
            return price * quantity;
        }
        private double CalculateTotalDiscount(double dBeverageTotal, double dFoodTotal, double dGrandTotal)
        {
            double dDiscountBev = chb_beverage.Checked ? double.Parse(tb_Beverage_Discount.Text) : 0;
            double dDiscountFood = chb_food.Checked ? double.Parse(tb_Food_Discount.Text) : 0;
            double dDiscountAll = chb_all.Checked ? double.Parse(tb_total_Discount.Text) : 0;

            double dTotalDiscount = (dBeverageTotal * dDiscountBev / 100) + (dFoodTotal * dDiscountFood / 100) + (dGrandTotal * dDiscountAll / 100);

            return dTotalDiscount;
        }
        private void textBox6_TextChanged(object sender, EventArgs e)
        {

        }

        private void textBox13_TextChanged(object sender, EventArgs e)
        {

        }

        private void label2_Click(object sender, EventArgs e)
        {

        }

        private void label3_Click(object sender, EventArgs e)
        {

        }

        private void label4_Click(object sender, EventArgs e)
        {

        }

        private void label5_Click(object sender, EventArgs e)
        {

        }

        private void label6_Click(object sender, EventArgs e)
        {

        }

        private void label8_Click(object sender, EventArgs e)
        {

        }

        private void Form1_Load(object sender, EventArgs e)
        {

        }

        private void groupBox3_Enter(object sender, EventArgs e)
        {

        }

        private void CalculateTotalDiscount(object sender, EventArgs e)
        {

        }
    }
}
