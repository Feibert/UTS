# DeretBilanganFibonacci

# UTS PEMROGRAMAN MOBILE 1

Nama : Feibert Sianturi

NIM : 312210578

Kelas : TI.22.A5

Mata Kuliah : Pemrograman Mobile 1

Dosen Pengampu : Donny Maulana, S.Kom.,M.M.S.I.

Tugas : Buatlah Method Program java Toast Number, dengan menghasilkan Bilangan Fibonacci

## Daftar Isi
| No.| DAFTAR ISI |        Here                           |
|----|------------|----------------------------------------|
| 1. | Layout     | [Click Here](#layout)               |
| 2. | Java       | [Click Here](#java-class)     |
| 3. | Design     | [Click Here](#tampilan-design)      |
| 4. | Hasil Run  | [Click Here](#hasil-run)            |

> - Disini, saya akan mengerjakan dan menjelaskan tugas dari mata kuliah "Pemrograman Mobile 1" yaitu membuat sebuah aplikasi untuk menampilkan bilangan Fibonacci. Selain itu saya juga akan merubah sedikit tampilan dari yang diperintahkan pada tugas, yaitu menambah tombol `Restart` dan menambah tombol `Masukkan Angka Limit` 


## Layout
Pada layout ini, saya membuat tiga button dan satu textview :
1. `button_limit`, berfungsi sebagai tombol “Set Limit” yang nantinya ketika di tekan akan muncul sebuah pop-up untuk masukan limit angka yang ingin kita hitung.
2. `button_count`, berfungsi sebagai tombol “count” yang nantinya ketika tombol ditekan akan menghitung bilangan fibonaccinya sesuai dengan yang kita limit. Juga berbeda warna pada setiap angka, agar tidak keliru.
3. 'button_restart', berfungsi sebagai tombol restart yang nantinya angka akan kembali ke awal.
4. Textview `show_count`, yang berfungsi untuk menampilkan angka atau bilangan fibonaccinya yang tepat berada di tengah.

Berikut adalah coding pada menu layout :

> - **activity_toast.xml**
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/button_toast"
        android:layout_width="226dp"
        android:layout_height="52dp"
        android:layout_marginTop="4dp"
        android:background="@color/colorPrimary"
        android:onClick="setLimit"
        android:text="NumMax"
        android:textColor="@android:color/white"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.987"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/button"
        android:layout_width="185dp"
        android:layout_height="58dp"
        android:layout_marginTop="4dp"
        android:background="@color/colorPrimary"
        android:text="Toast"
        android:textColor="@android:color/white"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="MissingConstraints" />

    <Button
        android:id="@+id/button2"
        android:layout_width="204dp"
        android:layout_height="wrap_content"
        android:background="@color/colorPrimary"
        android:onClick="countUp"
        android:text="@string/button_label_count"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.99"
        app:layout_constraintStart_toStartOf="parent" />

    <Button
        android:id="@+id/back"
        android:layout_width="204dp"
        android:layout_height="wrap_content"
        android:background="@color/colorPrimary"
        android:onClick="Back"
        android:text="@string/Back"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore=",Rtlcompat"/>

    <TextView
        android:id="@+id/show_count"
        android:layout_width="407dp"
        android:layout_height="626dp"
        android:background="#FFFF00"
        android:gravity="center_vertical"
        android:text="1"
        android:textAlignment="center"
        android:textColor="@color/colorPrimary"
        android:textSize="160sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/button2"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/button_toast"
        tools:ignore=",Rtlcompat" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

> - **Strings.xml**
```
<resources>
    <string name="app_name">Toast</string>
    <string name="button_label_toast">Toast</string>
    <string name="button_label_count">Count</string>
    <string name="count_initial_value">0</string>
    <string name="coast_message">Hello Toast</string>
    <string name="Back">Exit</string>
</resources>
```

> - **Colors.xml**
```
<resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="blue">#3700B3</color>
    <color name="pink">#FFC0CB</color>
    <color name="colorPrimary">#3F5185</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="birumuda">#ABCBFA</color>
    <color name="salem">#F8C6E6</color>
    <color name ="purple">#E3A2ED</color>
    <color name="hijau">#92A676</color>
    <color name="biru">#8FC2EA</color>
    <color name="hijaumuda">#C2E69C</color>
    <color name="kuning">#FFEB3B</color>
    <color name="orange">#FF9800</color>
    <color name="cream">#E6C18A</color>
</resources>
```


## Java class
Pada Java class `MainActivity.java` berisi semua coding untuk menjalankan aplikasi. Seperti fungsi untuk tombol-tombol, dialog set limit, warna yang berbeda pada setiap angka, lalu warna background yang bisa berubah dan rumus bilangan fibonacci.
```
package com.example.myapplication;

import android.app.AlertDialog;
import android.content.DialogInterface;
import android.graphics.Color;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;


public class MainActivity extends AppCompatActivity {
    private TextView show_count;
    private int count = 1;
    private long fibNMinus1 = 1;
    private long fibNMinus2 = 0;
    private int limit = -1;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        show_count = findViewById(R.id.show_count);
    }

    public void countUp(View view) {
        if (count == 0) {
            show_count.setText("1");
        }
        else if (count == 1) {
            show_count.setText("1");
        }
        else {
            if (limit != -1 && count > limit) {
                count = 1;
                fibNMinus1 = 0;
                fibNMinus2 = 1;
                show_count.setText(getString(R.string.count_initial_value));
            }
            else {
                long fibCurrent = fibNMinus1 + fibNMinus2;
                fibNMinus2 = fibNMinus1;
                fibNMinus1 = fibCurrent;

                int colorResId = R.color.orange;
                switch (count % 11) {
                    case 1:
                        colorResId = R.color.orange;
                        break;
                    case 2:
                        colorResId = R.color.hijaumuda;
                        break;
                    case 3:
                        colorResId = R.color.purple;
                        break;
                    case 4:
                        colorResId = R.color.salem;
                        break;
                    case 5:
                        colorResId = R.color.birumuda;
                        break;
                    case 6 :
                        colorResId = R.color.kuning;
                        break;
                    case 7:
                        colorResId = R.color.hijau;
                        break;
                    case 8:
                        colorResId = R.color.cream;
                        break;
                    case 9:
                        colorResId = R.color.pink;
                        break;
                    case 10:
                        colorResId = R.color.biru;
                        break;
                    case 11:
                        colorResId = R.color.colorAccent;
                        break;
                }
                show_count.setTextColor(getResources().getColor(colorResId));
                show_count.setText(String.valueOf(fibCurrent));
                show_count.setBackgroundColor(Color.DKGRAY);
            }
        }

        count++;
    }

    public void Reset(View view) {
        count = 1;
        fibNMinus1 = 1;
        fibNMinus2 = 0;
        show_count.setText(getString(R.string.count_initial_value));
    }

    public void setLimit(View view) {
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("Set Limit");

        final EditText input = new EditText(this);
        input.setInputType(android.text.InputType.TYPE_CLASS_NUMBER);
        builder.setView(input);

        builder.setPositiveButton("OK", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                String limitStr = input.getText().toString();
                limit = Integer.parseInt(limitStr);
            }
        });

        builder.setNegativeButton("Cancel", new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int which) {
                dialog.cancel();
            }
        });

        builder.show();}
}
```


## Tampilan design


![2023-11-19_20h20_56](https://github.com/Feibert/UTS/assets/151450071/2284887b-1f2a-4acf-aafa-38e0a17f94fa)





## Hasil Run 



https://github.com/Hansen021/TUGAS_UTS/assets/129939171/dfcd6ec4-d47f-46ec-8999-dcaf90f1a5c2



