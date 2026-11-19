
# Ex.No:3 Design an android application Send SMS using Intent.
# DATE : 6.11.2026

## AIM:

To create and design an android application Send SMS using Intent using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as smsintent and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Send SMS and Display details give in MainActivity file.

Step 7: Save and run the application.


```
Developed by: M Mohamed Ashfaq
Registeration Number : 212224240090
```

## PROGRAM:
Program to create and design an android application Send SMS using Intent.

## MAINACTIVITY.JAVA:
```
package com.example.smsapplication;

import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText phone, message;
    Button send;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        phone = findViewById(R.id.phone);
        message = findViewById(R.id.message);
        send = findViewById(R.id.send);

        send.setOnClickListener(v -> {
            String number = phone.getText().toString().trim();
            String msg = message.getText().toString().trim();

            if (number.isEmpty() || msg.isEmpty()) {
                Toast.makeText(this,
                        "Enter phone number and message",
                        Toast.LENGTH_SHORT).show();
                return;
            }

            Intent intent = new Intent(
                    Intent.ACTION_SENDTO,
                    Uri.parse("smsto:" + Uri.encode(number))
            );

            intent.putExtra("sms_body", msg);

            try {
                startActivity(intent);
            } catch (android.content.ActivityNotFoundException e) {
                Toast.makeText(this,
                        "No SMS application found",
                        Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```
## ACTIVITY_MAIN.XML:
```

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="24dp"
    android:background="#E0F7FA">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="SMS Application"
        android:textSize="28sp"
        android:textStyle="bold"
        android:textColor="#006064"
        android:layout_marginBottom="24dp" />

    <EditText
        android:id="@+id/phone"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Mobile Number"
        android:inputType="phone" />

    <EditText
        android:id="@+id/message"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter the Message"
        android:inputType="textMultiLine"
        android:minLines="3"
        android:gravity="top" />

    <Button
        android:id="@+id/send"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Send SMS"
        android:layout_marginTop="20dp" />

</LinearLayout>
```
## ANDROIDMANIFEST.XML:
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Mysheets">
        <activity
            android:name=".MainActivity"
            android:exported="true"
            android:windowSoftInputMode="adjustResize">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>


```


## OUTPUT:

<img width="1586" height="992" alt="Android Studio SMS App Preview" src="https://github.com/user-attachments/assets/e2fb1c97-49d7-4fee-87f1-4a08c9b6a536" />

<img width="1586" height="992" alt="Android Studio SMS App Emulator Preview" src="https://github.com/user-attachments/assets/17358e33-992c-4ea1-b666-e11160b090b8" />



## RESULT:
Thus a Simple Android Application create and design an android application Send SMS using Intent using Android Studio is developed and executed successfully.
