# Project-Data-Analysis-for-Retail_Sales-Performance-Report
Project dari  DQLab tentang Melakukan analisis terhadap performance dari DQLab Store dengan menggunakan MySQL.

Dataset yang digunakan berisi transaksi dari tahun 2009 sampai dengan tahun 2012 dengan jumlah raw data sebanyak 5500, termasuk di dalamnya order status yang terbagi menjadi order finished, order returned dan order cancelled. Adapun dataset yang sudah diberikan dan akan digunakan pada project ini berisi data sebagai berikut:
* OrderID
* Order Status
* Customer
* Order Date
* Order Quantity
* Sales
* Discount %
* Discount
* Product Category
* Product Sub-Category
  
![dqlab_sales_store_table](https://user-images.githubusercontent.com/72337233/95158070-e90f2380-07c4-11eb-99e7-629354aedad9.png)

Nama tabel yang akan digunakan pada project ini adalah dqlab_sales_store

Dalam Project ini tugas yang ingin kerjakan:
1. Performa Keseluruhan Toko berdasarkan Tahun
2. Kinerja Keseluruhan berdasarkan Sub Kategori Produk
3. Efektivitas dan Efisiensi Promosi Berdasarkan Tahun
4. Efektivitas dan Efisiensi Promosi Berdasarkan Sub Kategori Produk
5. Transaksi Pelanggan per Tahun

### 1. Performa Keseluruhan Toko berdasarkan Tahun
Membuat Query dengan menggunakan SQL untuk mendapatkan **total penjualan** (sales) dan **jumlah order** (number_of_order) dari tahun **2009 sampai 2012** (years).

```
SELECT 
	left(order_date,4) as years,
	sum(sales) as sales,
	count(order_status) as number_of_order 
FROM 
	dqlab_sales_store
WHERE 
	order_status = 'Order Finished'
GROUP BY 
	left(order_date,4);
```
keluaran:

![image](https://user-images.githubusercontent.com/62486840/147625177-54f8b733-1731-4515-a386-726049f470bd.png)

### 2. Kinerja Keseluruhan berdasarkan Sub Kategori Produk
Membuat Query dengan menggunakan SQL untuk mendapatkan **total penjualan** (sales) berdasarkan **sub category dari produk** (product_sub_category) pada **tahun 2011 dan 2012** saja (years). 
```
SELECT 
	left(order_date,4) as years,
	product_sub_category,sum(sales) as sales
FROM 
	dqlab_sales_store
WHERE 
	left(order_date,4) in ('2011','2012') and order_status = 'Order Finished'
GROUP BY 
	left(order_date,4),product_sub_category
ORDER BY 
	left(order_date,4),sum(sales) 
DESC;
```
keluaran:

![image](https://user-images.githubusercontent.com/62486840/147625515-18caa6b6-b197-4e4e-be66-7b08cdc9f776.png)




Project ini dapat diakses melalui https://academy.dqlab.id/main/package/project/182?pf=0.

![image](https://user-images.githubusercontent.com/62486840/147624891-ec494703-94ef-4705-b697-e6ac166b4e26.png)
