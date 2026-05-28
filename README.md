# Ex.No:5 Develop a simple application for proximity sensor using Sensor Manager in android studio.


## AIM:

To develop a sensor application for proximity sensor using sensor manager in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Giraffe)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as proximitysensor and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Display process of proximitysensor in android mobile devices.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to print the process of proximitysensor in android mobile devices”.
Developed by: MONISH R
Registeration Number : 212223220061
*/
```
## MainActivity.java
```
package com.example.proximitysensor;


import androidx.appcompat.app.AppCompatActivity;

import android.content.Context;
import android.hardware.Sensor;
import android.hardware.SensorEvent;
import android.hardware.SensorEventListener;
import android.hardware.SensorManager;
import android.os.Bundle;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    TextView sensorStatusTV;
    SensorManager sensorManager;
    Sensor proximitySensor;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        sensorStatusTV = findViewById(R.id.text);

        // Calling sensor service
        sensorManager = (SensorManager) getSystemService(Context.SENSOR_SERVICE);

        // Accessing proximity sensor
        proximitySensor = sensorManager.getDefaultSensor(Sensor.TYPE_PROXIMITY);

        // Checking sensor availability
        if (proximitySensor == null) {

            Toast.makeText(this,
                    "No proximity sensor found in device.",
                    Toast.LENGTH_SHORT).show();

            finish();

        } else {

            // Register sensor listener
            sensorManager.registerListener(
                    proximitySensorEventListener,
                    proximitySensor,
                    SensorManager.SENSOR_DELAY_NORMAL);
        }
    }

    // Sensor Event Listener
    SensorEventListener proximitySensorEventListener =
            new SensorEventListener() {

                @Override
                public void onAccuracyChanged(Sensor sensor, int accuracy) {

                }

                @Override
                public void onSensorChanged(SensorEvent event) {

                    // Checking sensor type
                    if (event.sensor.getType() == Sensor.TYPE_PROXIMITY) {

                        if (event.values[0] == 0) {

                            // Object is near
                            sensorStatusTV.setText("Near");

                        } else {

                            // Object is away
                            sensorStatusTV.setText("Away");
                        }
                    }
                }
            };
}
```
## activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/text"
        android:layout_width="299dp"
        android:layout_height="453dp"
        android:textSize="60dp"
        android:text="Status"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>

```
## OUTPUT
<img width="1806" height="986" alt="Screenshot 2026-05-27 080746" src="https://github.com/user-attachments/assets/7df75084-2960-4221-b8e9-532864467575" />




## RESULT
Thus a Simple Android Application to display the details of proximity sensor using sensor manager in Android Studio is developed and executed successfully.
