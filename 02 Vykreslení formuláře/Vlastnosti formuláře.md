Vlastnosti ovlivňují chování a vzhled formuláře.

### Vzhled a chování okna
- Text – text v titulkovém pruhu (nadpis okna)
- Name – identifikátor formuláře v kódu
- StartPosition – kde se okno objeví při spuštění (CenterScreen, WindowsDefaultLocation...)
- Size / ClientSize – velikost celého okna / vnitřní plochy
- WindowState – Normal, Maximized, Minimized
- FormBorderStyle – styl okraje (Sizable, FixedSingle, None...) – ovlivňuje, jestli jde okno zvětšovat/zmenšovat
- MaximizeBox, MinimizeBox – zda jsou v okně tlačítka pro maximalizaci/minimalizaci
- ControlBox – zda je vůbec zobrazen ovládací box (křížek na zavření atd.)
- Cursor - určuje, jaký kurzor myši se zobrazí

### Barvy a pozadí
- BackColor – barva pozadí formuláře
- BackgroundImage – obrázek na pozadí

Struktura *Color* reprezentuje barvu ve formátu ARGB. "A" představuje komponentu alfa, která udává transparentnost barvy, 
"RGB" pak jednotlivé složky - červenou, zelenou a modrou.  

Příklad užití vlasností formuláře:
```csharp
Form form = new Form();

form.Text = "Okno aplikace";
form.BackColor = Color.Blue;
form.Width = 500;
form.Height = 500;
form.FormBorderStyle = FormBorderStyle.FixedDialog;
form.MaximizeBox = false;
form.Cursor = Cursors.WaitCursor;
form.StartPosition = FormStartPosition.CenterScreen;

Application.Run(form);
```
Výstup programu:  
<img width="485" height="489" alt="Okno aplikace - vlasnosti" src="https://github.com/user-attachments/assets/1623f289-6976-4aa8-bbe6-78f2772d78b5" />

