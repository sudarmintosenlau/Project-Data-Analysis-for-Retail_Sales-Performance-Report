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
Membuat Query dengan menggunakan SQL untuk mendapatkan total penjualan (sales) dan jumlah order (number_of_order) dari tahun 2009 sampai 2012 (years).

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
