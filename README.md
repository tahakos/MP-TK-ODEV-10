# MP-TK-ODEV-10

package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;

public class MainActivity extends AppCompatActivity{

EditText kullaniciEdit;
@Override
protected void onCreate(Bundle savedInstanceState) {
 super.onCreate(savedInstanceState);
 setContentView(R.layout.activity_main);
 kullaniciEdit=findViewById(R.id.kullaniciEdit);
 SharedPreferences sharedPreferences=this.getPreferences(Context.MODE_PRIVATE);
 String gelenveri=sharedPreferences.getString(“kullanici”,””);
 if(!gelenveri.isEmpty()){
 kullaniciEdit.setText(gelenveri);
 }
}
public void btnKaydetClick(View view){
 String veri;
 veri = kullaniciEdit.getText().toString();
 SharedPreferences sharedPreferences=this.getPreferences(Context.MODE_PRIVATE);
 
 SharedPreferences.Editor editor=sharedPreferences.edit();
 editor.putString(“kullanici”,veri);
 editor.apply();
 
 if(veri==AppCompatDelegate.MODE_NIGHT_NO)
 radioacik.setChecked(true);
else
 radioKaranlik.setChecked(true);
 
 public void onRadioClicked(View view){
 boolean checked=((RadioButton)view).isChecked();
 switch (view.getId()){
 case R.id.radioAcik:
 if(checked){
 AppCompatDelegate.setDefaultNightMode(AppCompatDelegate.MODE_
NIGHT_NO);
 editor.putInt(“tema”,AppCompatDelegate.MODE_NIGHT_NO);
 editor.apply();
 }
 break;
 case R.id.radioKaranlik:
 if(checked){
 AppCompatDelegate.setDefaultNightMode(AppCompatDelegate.MODE_
NIGHT_YES);
 editor.putInt(“tema”,AppCompatDelegate.MODE_NIGHT_YES);
 editor.apply();
 }
 break;
 }
}

protected void onDestroy() {
 sharedPreferences=null;
 super.onDestroy();
}

INSERT INTO <tablo ismi> ( <sütun adı>, <diğer sütunlar>…) values(<değerler>)
  
  SELECT <sütun adları> FROM <tablo adı> WHERE <kısıtlamalar> ORDER BY <sıralama türü>
  
  
 SQLiteDatabase database;
  
  database = this.openOrCreateDatabase(<Veri Tabanı Adı>, MODE_PRIVATE, null);
  
  String TABLO=”CREATE TABLE IF NOT EXISTS urunler(id INTEGER PRIMARY KEY,”;
TABLO+=”urunadi VARCHAR,”;
TABLO+=”fiyat DOUBLE,”;
TABLO+=”adet INTEGER)”;
database.execSQL(TABLO);
  
  String SORGU=”INSERT INTO urunler(urunadi,fiyat,adet) VALUES(?,?,?)”;
SQLiteStatement durumlar=database.compileStatement(SORGU);
durumlar.bindString(1,”Televizyon”);
durumlar.bindString(2,12500.00);
durumlar.bindLong(3,12);
durumlar.execute();
  
  String SORGU=”DELETE FROM urunler WHERE id=?”;
SQLiteStatement durumlar=database.compileStatement(SORGU);
durumlar.bindLong(1,2);
durumlar.execute();
  
  String SORGU=”UPDATE ürünler SET fiyat=? WHERE id=?”;
SQLiteStatement durumlar=database.compileStatement(SORGU);
durumlar.bindString(1,145);
durumlar.bindLong(2,3);
durumlar.execute();
