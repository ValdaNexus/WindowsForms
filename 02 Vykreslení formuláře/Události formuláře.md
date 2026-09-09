Windows Forms je událostně řízený program. Formuláře a ovládací prvky vyvolávají **události**,
na které uživatel reaguje obsloužením dané události.  
Událostí může být pohyb myší, kliknutí, stisknutí tlačítka aj.  

Jedna z často používaných událostí je událost **_MouseClick_** (reaguje pouze na myš).  
1. Vytvoříme si instanci formuláře. 
2. Vytvoříme obslužnou metodu MujMouseClickEventHandler.  
   Parametry v závorce jsou:  
     **sender**, tj. kdo událost vyvolal (zde formulář)  
     **MouseEventArgs e** nese detaily o kliknutí, např. e.X > souřadnice, e.Button > které tlačítko bylo stisknuto
3. Do těla metody vytvoříme dialogové okno, které nás bude informovat o souřadnicích.
4. Přihlásíme obslužnou metodu k události MouseClick.

``` csharp
Form form = new Form();
form.MouseClick += MujMouseClickEventHandler;

static void MujMouseClickEventHandler(object sender, MouseEventArgs e)
{
  MessageBox.Show($"Kliknuto na souřadnice: X={e.X}, Y={e.Y}");
}
Application.Run(form);
```  
Další příklady na procvičení událostí.    
**Změna barvy po kliknutí**  
``` csharp
Form form = new Form();
form.Text = "Klikni na mě";
form.Width = 400;
form.Height = 300;
form.Click += new EventHandler(ZmenBarvu);

static void ZmenBarvu(object sender, EventArgs e)
{
    Form f = (Form)sender; // "sender" je formulář, na který se kliklo
    f.BackColor = Color.LightGreen;
}
Application.Run(form);
```
**Pozice myši**  
``` csharp
Form form = new Form();
form.MouseMove += new MouseEventHandler(SledujMys);

static void SledujMys(object sender, MouseEventArgs e)
{
    Form f = (Form)sender;
    f.Text = $"Pozice myši: X={e.X}, Y={e.Y}";
}
Application.Run(form);
```  
**Počet kliknutí**  
``` csharp
static int pocetKliknuti = 0;

Form form = new Form();
form.Click += new EventHandler(Klik);

static void Klik(object sender, EventArgs e)
{
    pocetKliknuti++;
    Form f = (Form)sender;
    f.Text = $"Počet kliknutí: {pocetKliknuti}";
}
Application.Run(form);
```  
