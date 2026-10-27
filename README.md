
# Ex.No:3 Design an android application Send SMS using Intent.


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

## PROGRAM:
```

Program to print the text create your own content providers to get contacts details.
Developed by: ISRAVEL Y
Registeration Number : 212225240054

```
### MainActivity.java
```java
package com.example.sendsms;

import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.telephony.SmsManager;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {
    private EditText inputPh;
    private EditText inputMsg;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        inputPh = findViewById(R.id.editTextText2);
        inputMsg = findViewById(R.id.editTextText);
        Button sendBtn = findViewById(R.id.button);
        sendBtn.setOnClickListener(view -> sendSms());
    }

    private void sendSms() {
        String ph = inputPh.getText().toString();
        String msg = inputMsg.getText().toString();
        if (ph.isEmpty() || msg.isEmpty()) {
            return;
        }
        Intent i = new Intent(Intent.ACTION_SENDTO);
        i.setData(Uri.parse("smsto:" + ph));
        i.putExtra("sms_body", msg);
        if(i.resolveActivity(getPackageManager()) != null) startActivity(i);
    }
}
```

### activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:scaleX="1"
    android:scaleY="1"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView"
        android:layout_width="188dp"
        android:layout_height="25dp"
        android:fontFamily="cursive"
        android:scaleX="1.7"
        android:scaleY="1.5"
        android:text="Exp 3 - Sending SMS using Intent"
        app:layout_constraintBottom_toTopOf="@+id/textView2"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.6" />

    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="80dp"
        android:fontFamily="sans-serif-black"
        android:scaleX="1.2"
        android:text="ISRAVEL Y - 212225240054"
        app:layout_constraintBottom_toTopOf="@+id/editTextText2"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent" />

    <EditText
        android:id="@+id/editTextText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginEnd="56dp"
        android:layout_marginBottom="80dp"
        android:ems="10"
        android:hint="Type your message"
        android:inputType="text"
        app:layout_constraintBottom_toTopOf="@+id/button"
        app:layout_constraintEnd_toEndOf="parent" />

    <EditText
        android:id="@+id/editTextText2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="16dp"
        android:ems="10"
        android:hint="Enter mobile number"
        android:inputType="text"
        app:layout_constraintBottom_toTopOf="@+id/editTextText"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.256"
        app:layout_constraintStart_toEndOf="@+id/textView3" />

    <TextView
        android:id="@+id/textView3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="88dp"
        android:layout_marginTop="88dp"
        android:scaleX="1.6"
        android:scaleY="1.5"
        android:text="Ph no:"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView2" />

    <TextView
        android:id="@+id/textView4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="52dp"
        android:scaleX="1.4"
        android:scaleY="1.5"
        android:text="Msg:"
        app:layout_constraintBottom_toTopOf="@+id/button"
        app:layout_constraintEnd_toStartOf="@+id/editTextText"
        app:layout_constraintHorizontal_bias="0.834"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView3"
        app:layout_constraintVertical_bias="0.0" />

    <Button
        android:id="@+id/button"
        android:onClick="sendSms"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="80dp"
        android:text="Send sms"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.486"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
### AndroidManifest.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:scaleX="1"
    android:scaleY="1"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView"
        android:layout_width="188dp"
        android:layout_height="25dp"
        android:fontFamily="cursive"
        android:scaleX="1.7"
        android:scaleY="1.5"
        android:text="Exp 3 - Sending SMS using Intent"
        app:layout_constraintBottom_toTopOf="@+id/textView2"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.6" />

    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="80dp"
        android:fontFamily="sans-serif-black"
        android:scaleX="1.2"
        android:text="ISRAVEL Y - 212225240054"
        app:layout_constraintBottom_toTopOf="@+id/editTextText2"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent" />

    <EditText
        android:id="@+id/editTextText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginEnd="56dp"
        android:layout_marginBottom="80dp"
        android:ems="10"
        android:hint="Type your message"
        android:inputType="text"
        app:layout_constraintBottom_toTopOf="@+id/button"
        app:layout_constraintEnd_toEndOf="parent" />

    <EditText
        android:id="@+id/editTextText2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="16dp"
        android:ems="10"
        android:hint="Enter mobile number"
        android:inputType="text"
        app:layout_constraintBottom_toTopOf="@+id/editTextText"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.256"
        app:layout_constraintStart_toEndOf="@+id/textView3" />

    <TextView
        android:id="@+id/textView3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="88dp"
        android:layout_marginTop="88dp"
        android:scaleX="1.6"
        android:scaleY="1.5"
        android:text="Ph no:"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView2" />

    <TextView
        android:id="@+id/textView4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="52dp"
        android:scaleX="1.4"
        android:scaleY="1.5"
        android:text="Msg:"
        app:layout_constraintBottom_toTopOf="@+id/button"
        app:layout_constraintEnd_toStartOf="@+id/editTextText"
        app:layout_constraintHorizontal_bias="0.834"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView3"
        app:layout_constraintVertical_bias="0.0" />

    <Button
        android:id="@+id/button"
        android:onClick="sendSms"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="80dp"
        android:text="Send sms"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.486"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

## OUTPUT

<img width="1535" height="862" alt="image" src="https://github.com/user-attachments/assets/4edf63d9-a5b6-4c92-a3d6-37dd6a5d02f3" />

<img width="1528" height="862" alt="image" src="https://github.com/user-attachments/assets/d2cc4d3b-d3a2-490c-83c2-a072a86e0ac5" />

<img width="1535" height="862" alt="image" src="https://github.com/user-attachments/assets/5bb87e5f-e2d8-4a5a-b731-529cf7f0133a" />


## RESULT
Thus a Simple Android Application create and design an android application Send SMS using Intent using Android Studio is developed and executed successfully.
