# Mobile_Pertemuan9

![image](https://github.com/Aliyahasmarani/Mobile_Pertemuan9/assets/115197672/f4a554ca-2066-47b7-b10d-c6ea2b5b33f5)

# 1. MEMBUAT SPLASH LOGO LAYOUT (activity_splash_screen.xml)

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    xmlns:tools="http://schemas.android.com/tools"
    tools:context=".SplashScreenActivity">

    <pl.droidsonroids.gif.GifImageView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_centerVertical="true"
        android:adjustViewBounds="false"
        android:id="@+id/bshop"
        android:src="@drawable/bshop" />

    <pl.droidsonroids.gif.GifImageView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/bshop"
        android:adjustViewBounds="false"
        android:src="@drawable/gerak" />
</RelativeLayout>
```

# PENJELASAN

> RelativeLayout: Ini adalah tata letak yang digunakan, yang memungkinkan penempatan elemen-elemen tampilan berdasarkan hubungan relatif satu sama lain. Misalnya, dengan menggunakan atribut android:layout_below="@id/bshop", elemen kedua ditempatkan di bawah elemen pertama.

> GifImageView: Ini adalah elemen yang digunakan untuk menampilkan gambar bergerak (GIF). Dua instance dari GifImageView digunakan di sini.
Instance pertama (bshop) ditempatkan di tengah vertikal layar (android:layout_centerVertical="true") dan mengambil sumber gambar dari file yang disebut "bshop" (android:src="@drawable/bshop").
Instance kedua ditempatkan di bawah instance pertama (android:layout_below="@id/bshop") dan menggunakan gambar dari file "gerak" (android:src="@drawable/gerak").

![image](https://github.com/Aliyahasmarani/Mobile_Pertemuan9/assets/115197672/e394146a-68cd-45cf-88d9-377794f5daf4)

# BERIKUTNYA,  MEMBUAT SPLASH SCREEN JAVANYA (SplashScreenActivity.java)

```
package com.example.myapplication;

import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;
import android.view.WindowManager;

import androidx.appcompat.app.ActionBar;
import androidx.appcompat.app.AppCompatActivity;

public class SplashScreenActivity extends AppCompatActivity {

    private static final long SPLASH_DELAY = 15000;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_splash_screen);
        ActionBar actionBar = getSupportActionBar();
        if (actionBar != null) {
            actionBar.hide();
        }
        getWindow().setFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN, WindowManager.LayoutParams.FLAG_FULLSCREEN);
        new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                Intent intent = new Intent(SplashScreenActivity.this, MainActivity.class);
                startActivity(intent);
                finish();
            }
        }, SPLASH_DELAY);
    }
}
```

# PENJELASAN

### 1. Mengatur Waktu Tampilan Splash Screen:
```
private static final long SPLASH_DELAY = 15000;
```
Ini adalah konstanta yang menentukan berapa lama splash screen akan ditampilkan, diukur dalam milidetik (15 detik dalam kasus ini).

### 2. Metode onCreate():
```
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_splash_screen);
```
> onCreate() adalah metode yang dipanggil ketika aktivitas dimulai. Ini mengatur tata letak tampilan menggunakan file XML dengan nama activity_splash_screen.

> ActionBar actionBar = getSupportActionBar(); digunakan untuk mendapatkan referensi ke ActionBar (bar atas aplikasi).

> actionBar.hide(); menghilangkan ActionBar jika ada, memberikan tampilan layar penuh.

> getWindow().setFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN, WindowManager.LayoutParams.FLAG_FULLSCREEN); juga bertujuan untuk membuat aplikasi tampil dalam mode layar penuh.

> Selanjutnya, menggunakan Handler, aplikasi menunda pindah ke layar utama (MainActivity) dengan membuat Intent dan menjalankan aktivitas tersebut setelah waktu yang ditentukan.

> finish(); digunakan untuk menutup SplashScreenActivity setelah pindah ke MainActivity agar pengguna tidak dapat kembali ke splash screen.

### 3. Pindah ke MainActivity setelah Waktu Tertentu:
```
new Handler().postDelayed(new Runnable() {
    @Override
    public void run() {
        Intent intent = new Intent(SplashScreenActivity.this, MainActivity.class);
        startActivity(intent);
        finish();
    }
}, SPLASH_DELAY);
```
> Di dalam Runnable, kita membuat Intent untuk pindah ke MainActivity.

> startActivity(intent); digunakan untuk memulai aktivitas baru (pindah ke MainActivity).

> finish(); digunakan untuk menutup SplashScreenActivity agar tidak dapat diakses lagi.

# SELANJUTNYA, MEMBUAT BUTTON UNTUK MEMANGGIL SATU PER SATU (INTENT) (activity_main.xml)

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:orientation="vertical"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <com.google.android.material.button.MaterialButton
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Hallo"
        android:id="@+id/hallo"
        android:layout_marginTop="10dp"
        android:layout_marginEnd="10dp"
        android:layout_marginStart="10dp" />

    <com.google.android.material.button.MaterialButton
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Fibonancci"
        android:id="@+id/fibo"
        android:layout_marginTop="10dp"
        android:layout_marginEnd="10dp"
        android:layout_marginStart="10dp" />

    <com.google.android.material.button.MaterialButton
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Scroll Sianida"
        android:id="@+id/scroll"
        android:layout_marginTop="10dp"
        android:layout_marginEnd="10dp"
        android:layout_marginStart="10dp" />

    <com.google.android.material.button.MaterialButton
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="TwoActivity"
        android:id="@+id/twoactivity"
        android:layout_marginTop="10dp"
        android:layout_marginEnd="10dp"
        android:layout_marginStart="10dp" />

    <com.google.android.material.button.MaterialButton
        android:id="@+id/SetAlarm"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="10dp"
        android:layout_marginTop="10dp"
        android:layout_marginRight="10dp"
        android:text="Alarm" />

    <pl.droidsonroids.gif.GifImageView
        android:layout_width="match_parent"
        android:layout_height="200dp"
        android:layout_marginTop="100dp"
        android:adjustViewBounds="false"
        android:src="@drawable/puss" />
</LinearLayout>
```
# PENJELASAN

> LinearLayout: Ini adalah tata letak utama yang mengatur elemen-elemen anak secara vertikal. Semua elemen anak (tombol dan gambar animasi) akan ditata secara berurutan dari atas ke bawah.

> MaterialButton: Ini adalah elemen tombol yang berasal dari desain material Android. Setiap tombol memiliki lebar penuh (match_parent) dan ada beberapa properti seperti teks, ID, dan margin untuk menentukan jarak antara tombol.

> GifImageView: Ini adalah elemen untuk menampilkan gambar bergerak (GIF). Elemen ini memiliki lebar penuh, tinggi tetap (200dp), dan ditempatkan di atas layar (android:layout_marginTop="100dp").

![image](https://github.com/Aliyahasmarani/Mobile_Pertemuan9/assets/115197672/3819e1b9-5ee9-44a4-ba7e-5595d53f4752)

# SETELAH ITU, MULAI DI ATUR DALAM JAVANYA (MainActivity.java)

```
package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.provider.AlarmClock;
import android.view.View;

import com.google.android.material.button.MaterialButton;

public class MainActivity extends AppCompatActivity{

    private MaterialButton buttonFirst;
    private MaterialButton buttonSecond;
    private MaterialButton buttonHallo;
    private MaterialButton buttonFibonacci;
    private MaterialButton buttonScroll;
    private MaterialButton buttonAlarm;


    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        buttonSecond = findViewById(R.id.twoactivity);
        buttonFirst = findViewById(R.id.twoactivity);
        buttonHallo = findViewById(R.id.hallo);
        buttonFibonacci = findViewById(R.id.fibo);
        buttonScroll = findViewById(R.id.scroll);
        buttonAlarm = findViewById(R.id.SetAlarm);

        setIntent();
    }
    private void setIntent() {
        buttonSecond.setOnClickListener(view -> {
            Intent intent = new Intent(this, SecondActivity.class);
            startActivity(intent);
            finish();
        });

        buttonFirst.setOnClickListener(view -> {
            Intent intent = new Intent (this, FirstActivity.class);
            startActivity(intent);
        });

        buttonHallo.setOnClickListener(view -> {
            Intent intent = new Intent (this, HalloActivity.class);
            startActivity(intent);
        });

        buttonFibonacci.setOnClickListener(view -> {
            Intent intent = new Intent (this, Fibonacci.class);
            startActivity(intent);
        });

        buttonScroll.setOnClickListener(view -> {
            Intent intent = new Intent (this, ScrollSianida.class);
            startActivity(intent);
        });

        buttonAlarm.setOnClickListener(view -> {
            Intent intent = new Intent (AlarmClock.ACTION_SHOW_ALARMS);
            startActivity(intent);
        });
    }


}
```

# PENJELASAN 

Penjelasan singkat:

> Mendapatkan Referensi Tombol: Mendapatkan referensi ke setiap tombol dari tata letak menggunakan findViewById.

> Tindakan untuk Setiap Tombol: Dalam metode setIntent(), ditetapkan tindakan (intent) untuk masing-masing tombol. Tindakan ini menentukan aktivitas yang akan dimulai ketika tombol ditekan.

> Misalnya, jika tombol "TwoActivity" ditekan, aplikasi akan beralih ke SecondActivity. Sama halnya dengan tombol-tombol lainnya, masing-masing memiliki tindakan khususnya.

![image](https://github.com/Aliyahasmarani/Mobile_Pertemuan9/assets/115197672/04ae13ac-890a-429c-93bf-8309b828684c)

# TERAKHIR, DIATUR DALAM MANIFEST NYA

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">
    <uses-permission android:name="com.android.alarm.permission.SET_ALARM" />

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.MyApplication"
        tools:targetApi="31">
        <activity
            android:name=".SplashScreenActivity"
            android:exported="true"
            android:label="Fibonacci">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        <activity
            android:name=".MainActivity"
            android:exported="true"/>

        <activity
            android:name=".ScrollSianida"
            android:exported="true"/>

        <activity
            android:name=".Fibonacci"
            android:exported="true"/>

        <activity
            android:name=".HalloActivity"
            android:exported="true"/>

        <activity
            android:name=".FirstActivity"
            android:exported="true"/>

        <activity
            android:name=".SecondActivity"
            android:exported="true"/>


    </application>

</manifest>
```

# PENJELASAN

### 1. Izin Penggunaan Alarm:
```
<uses-permission android:name="com.android.alarm.permission.SET_ALARM" />
```
Elemen ini menunjukkan bahwa aplikasi ini membutuhkan izin untuk mengatur alarm pada perangkat.

### 2. Deklarasi Aplikasi:
```
<application
    android:allowBackup="true"
    android:dataExtractionRules="@xml/data_extraction_rules"
    android:fullBackupContent="@xml/backup_rules"
    android:icon="@mipmap/ic_launcher"
    android:label="@string/app_name"
    android:roundIcon="@mipmap/ic_launcher_round"
    android:supportsRtl="true"
    android:theme="@style/Theme.MyApplication"
    tools:targetApi="31">
```
> allowBackup: Mengizinkan pencadangan aplikasi.
> dataExtractionRules: Menentukan aturan ekstraksi data.
> fullBackupContent: Menentukan aturan pencadangan penuh.
> icon: Menentukan ikon aplikasi.
> label: Menentukan nama aplikasi.
> roundIcon: Menentukan ikon aplikasi untuk tampilan bulat.
> supportsRtl: Menunjukkan dukungan untuk tata letak dari kanan ke kiri.
> theme: Menentukan tema aplikasi.
> tools:targetApi: Menentukan versi target API untuk alat pengembangan.

### 3. Aktivitas Utama (SplashScreenActivity):
```
<activity
    android:name=".SplashScreenActivity"
    android:exported="true"
    android:label="Fibonacci">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```
> name: Menentukan kelas aktivitas utama (SplashScreenActivity).
> exported: Menunjukkan apakah aktivitas ini dapat diakses oleh aplikasi lain.
> label: Menentukan label (nama) aktivitas pada layar perangkat.
> intent-filter: Menentukan tindakan dan kategori yang harus dijalankan oleh sistem saat aplikasi diluncurkan.

![image](https://github.com/Aliyahasmarani/Mobile_Pertemuan9/assets/115197672/f9714d22-a943-4210-b6e6-db9d1f36c4ef)

# HASIL AKHIR

https://github.com/Aliyahasmarani/Mobile_Pertemuan9/assets/115197672/fd375a4e-48da-4fad-93e4-cc2a7fe4fcf1





