Projenin amacı :Internet kafelerde kullanılan otomasyon sisteminin daha şık ve kolay bir ara yüz ile geliştirilmesidir.
Proje özellikleri: Masalar oturulan süre ve marketten alınanlar menüleri olacaktır daimi müşterilere belli oranda indirim uygulanacaktır.
Projenin dili C# olup müşterilere masalara ve market ürünlerine ait veritabanı bağlantısı olacaktır.





# Internetcafeotomasyonu





using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Data.OleDb;
using System.Windows.Forms;
 
namespace WindowsFormsApplication9
{
public partial class Form1 : Form
{
 
public Form2 frm2;
public Form3 frm3;
public Form4 frm4;
public Form5 frm5;
public Form6 frm6;
public Form7 frm7;
//public Form8 frm8;
public int sayi=0,hak=3,sure=60;
public OleDbConnection bag = new OleDbConnection("Provider=Microsoft.Jet.Oledb.4.0; Data Source=vt1.mdb");
public DataSet dtst = new DataSet();
public OleDbCommand kmt = new OleDbCommand();
public void listele()
{
bag.Open();
OleDbDataAdapter adtr = new OleDbDataAdapter("Select * From yongiris", bag);
adtr.Fill(dtst, "yongiris");
dataGridView1.DataSource = dtst;
dataGridView1.DataMember = "yongiris";
bag.Close();
adtr.Dispose();
 
}
public Form1()
{
InitializeComponent();
frm2 = new Form2();
frm3 = new Form3();
frm4 = new Form4();
frm5 = new Form5();
frm6 = new Form6();
frm7 = new Form7();
//frm8 = new Form8();
 
frm2.frm1 = this;
frm3.frm1=this;
frm4.frm1 = this;
frm5.frm1 = this;
frm6.frm1 = this;
frm7.frm1 = this;
//frm8.frm1 = this;
 
}
public void listele2()
{
bag.Open();
OleDbDataAdapter adtr = new OleDbDataAdapter("Select * From masaac", bag);
adtr.Fill(dtst, "masaac");
frm7.dataGridView1.DataSource = dtst;
frm7.dataGridView1.DataMember = "masaac";
bag.Close();
adtr.Dispose();
}
 
private void Form1_Load(object sender, EventArgs e)
{
label6.Hide();
label7.Hide();
//arama();
listele();
 
label4.DataBindings.Add("Text", dtst, "yongiris.k_ad");
label5.DataBindings.Add("Text", dtst, "yongiris.sifre");
 
if (label4.Text == "" || label5.Text == "")
{
sayi = 1;
label3.Text = "Veri tabanında geçerli k.ad ve şifre bulunmamaktadır.Şuan gireceğiniz k_ad ve şifre hep sayılsak";
button3.Enabled = false;
 
}
if (label4.Text != "" &amp; label5.Text!= "")
{
sayi = 2;
label3.Text = "Lütfen Kullanıcı Adı ve Şifreyi giriniz";
button3.Enabled = true;
 
}
 
label4.Hide();
label5.Hide();
dataGridView1.Hide();
}
 
private void button1_Click(object sender, EventArgs e)
{
 
if (sayi == 2)
{
if (textBox1.Text == label4.Text &amp;&amp; textBox2.Text == label5.Text)
{
this.Hide();
frm3.Show();
 
}
