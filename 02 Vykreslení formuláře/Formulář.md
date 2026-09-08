Dialogová okna, která řeší komunikaci s uživatelem a okna vytvářející aplikaci nazýváme **formuláře** a jejich třídou je třída **Form**.  

Pomocí příkazu 
```csharp
Form formular = new Form();
```  
vytvoříme instanci formuláře. Pro zobrazení v programu je třeba použít metodu **Show**.
```csharp
form.Show();
```  
Po spuštění programu se formulář na malou chvíli zobrazí a zase hned zmizí. Proto musíme použít z jmenného prostoru **System.Windows.Forms** třídu **Application** a její metodu **Run()**. Tato metoda spustí smyčku zpráv a díky tomu formulář zůstane zobrazený. Pro správnou funkčnost je potřeba použít v metodě _Run()_ parametr našeho vytvořeného formuláře.  
```csharp
Application.Run(formular); 
```    
Nyní přidejte k našemu kódu další dva formuláře. Pro přehlednější výstup použijeme vlastnost _Text_ a pojmenujeme jednotlivé formuláře. 
```csharp
Form formular1 = new Form();
Form formular2 = new Form();
Form formular3 = new Form();

formular1.Text = "První formulář";
formular2.Text = "Druhý formulář";
formular3.Text = "Třetí formulář";

formular2.Show();
formular3.Show();

Application.Run(formular1); 
```
<img width="1569" height="986" alt="form1" src="https://github.com/user-attachments/assets/c9b79e8d-c02a-4b59-8740-65758909e746" />  
Vyzkoušíme postupně zavírat naše okna. Všimněte si, že zavřením hlavního (prvního) formuláře dojde k zavření všech oken a ukončení aplikace.

      
