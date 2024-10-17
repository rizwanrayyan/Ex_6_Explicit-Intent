# Ex.No:6 Implement an application that uses Explicit Intent using Android


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.

## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

Step 1: Design the layout in `activity_main.xml` with a `TextView`, `EditText`, and a "Factorial" button.

Step 2: Create a second layout in `activity_second.xml` with `TextView` to display the result.

Step 3: In `MainActivity.java`, set up an event listener for the "Factorial" button and retrieve the user input.

Step 4: Calculate the factorial of the input number in the button click handler.

Step 5: Pass the factorial result to `SecondActivity` using an `Intent`.

Step 6: In `SecondActivity.java`, retrieve the result from the `Intent` and display it in the `TextView`.

Step 7: Save and run the application.

## PROGRAM:
### MainActivity.java:
```
package com.example.ex6;

import androidx.appcompat.app.AppCompatActivity;
import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;

public class MainActivity extends AppCompatActivity {
    EditText e1;
    Button res;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        e1=findViewById(R.id.editTextTextPersonName);
        res=findViewById(R.id.button);
        res.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view)
            {
                int n1=Integer.parseInt(e1.getText().toString());
                int sum =1;
                while(n1!=0)
                {
                    sum = sum * n1;
                    n1--;
                }
                Intent intent=new Intent(getApplicationContext(),SecondActivity.class);
                intent.putExtra("key",sum);
                startActivity(intent);
            }
        });
    }
}
```
### SecondActivity.java:
```
package com.example.ex6;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.content.Intent;
import android.os.Bundle;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class SecondActivity extends AppCompatActivity {

    TextView t1;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);
        t1=findViewById(R.id.textView);
        Intent intent=getIntent();
        int result=intent.getIntExtra("key",0);
        t1.setText(Integer.toString(result));
    }
}
```
### Activity_Main.XML:
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"
    android:background="#272525">

    <TextView
        android:paddingTop="90px"
        android:id="@+id/textview"
        android:layout_width="match_parent"
        android:layout_height="55dp"
        android:fontFamily="sans-serif-black"
        android:lineSpacingExtra="12sp"
        android:text="ENTER THE NUMBER"
        android:textAlignment="center"
        android:textAppearance="@style/TextAppearance.AppCompat.Large"
        android:textColor="#FF0000"
        android:textSize="20sp"
        android:textStyle="bold"
        tools:layout_editor_absoluteX="97dp"
        tools:layout_editor_absoluteY="175dp"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.671"/>


    <EditText
        android:textColor="#FFFFFF"
        android:id="@+id/editTextTextPersonName"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:ems="10"
        android:inputType="textPersonName"
        app:layout_constraintBottom_toTopOf="@+id/button"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.671"/>


    <Button
        android:backgroundTint="#FD0000"
        android:textColor="@color/white"
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Factorial"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.622" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
### Activity_Second.XML:
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity2"
    android:background="#272525">

    <TextView

        android:id="@+id/textView"
        android:layout_width="147dp"
        android:layout_height="wrap_content"
        android:fontFamily="sans-serif-black"
        android:text="TextView"
        android:textColor="#FF0000"
        android:textSize="24sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.856"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.447" />

    <TextView
        android:textColor="#FFFFFF"
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:fontFamily="sans-serif-black"
        android:text="Factorial is  : "
        android:textAlignment="textEnd"
        android:textAllCaps="true"
        android:textSize="20sp"
        android:textStyle="italic"
        android:typeface="normal"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.171"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.45" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
### AndroidMainfest.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    package="com.example.ex6">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:supportsRtl="true"
        android:theme="@style/Theme.EX6"
        tools:targetApi="31">
        <activity android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        <activity android:name=".SecondActivity" />
    </application>

</manifest>
```
## OUTPUT:
![Screenshot 2024-10-16 084047](https://github.com/user-attachments/assets/0317a90e-a5a2-4603-952f-ed09978637da)

![Screenshot 2024-10-16 084545](https://github.com/user-attachments/assets/48772166-acd0-4c35-b2ae-27c15d3a8324)


## RESULT:

Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.
