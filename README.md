package com.example.calculator;  

import android.os.Bundle;  
import android.view.View;  
import android.widget.Button;  
import android.widget.EditText;  
import android.widget.TextView;  

import androidx.appcompat.app.AppCompatActivity;  
import androidx.core.view.WindowInsetsCompat;  
import androidx.core.view.ViewCompat;  
  
public class MainActivity extends AppCompatActivity {  
    EditText a, r, y;  
    Button calc;  
    TextView ans;  
  
    @Override  
    protected void onCreate(Bundle savedInstanceState) {  
        super.onCreate(savedInstanceState);  
        setContentView(R.layout.activity_main);  
    
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {  
            WindowInsetsCompat systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());  
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);  
            return insets;  
        });  
  
        a = findViewById(R.id.Amount);  
        r = findViewById(R.id.roi);  
        y = findViewById(R.id.year);  
        calc = findViewById(R.id.button);  
        ans = findViewById(R.id.Answer);  
  
        calc.setOnClickListener(new View.OnClickListener() {  
            @Override  
            public void onClick(View view) {  
                int amt = Integer.parseInt(a.getText().toString());  
                int rate = Integer.parseInt(r.getText().toString());  
                int tenure = Integer.parseInt(y.getText().toString());  
  
                int answer = (amt * rate * tenure) / 100;  
                ans.setText(String.valueOf(answer));  
            }    
        });  
    }  
}  
