## Windows forms

- Formulář je objekt definovaný třídou Form1.  
- Formulář je třída dědící z třídy Form.  
- V konstruktoru je pouze metoda InitializeComponent().  
- Třída je značená jako partial, což znamená, že je definována ve více souborech.  
 
<img width="1918" height="994" alt="obr1" src="https://github.com/user-attachments/assets/5d0f9bab-00f9-48ce-967c-816631516fea" />

- 🟡 Designer/Návrhář > vzhled formuláře
- 🔴 Properties/Vlastnosti > nastavování vlastností prvkům
- 🟢 ToolBox/Panel nástrojů > seznam ovládajích prvků
- 🔵 Průzkumník řešení > struktura celého projektu

### Krok 1
V Průzkumníku řešení si otevřeme Program.cs (dvojklikem). Zobrazí se nám nový panel. Program.cs je vstupní bod programu, tzn. soubor, který se spustí jako první! Obsahuje metodu main().

```csharp
namespace TvojeAplikace
{
    internal static class Program
    {
        [STAThread]
        static void Main()
        {
            ApplicationConfiguration.Initialize();
            Application.Run(new Form1());
        }
    }
}
```
Obsah metody main nám po spuštění vytvoří formulář a zobrazí se v novém okně. Nyní si můžeme obsah metody main zakomentovat.  
Napíšeme do našeho kódu následující řádek
```csharp
MessageBox.Show("Chcete ukončit aplikaci?");
```
Okna hlášení(MessageBox) > jsou malá okna informující o chybách.    
MessageBox je třída, Show je metoda, která je mnohonásobně přetížená.  
Spustíme program. Výstupem bude hlášení okna.  
<img width="177" height="134" alt="okno" src="https://github.com/user-attachments/assets/acd6d4e5-de79-4c48-98a0-d54da6682de1" />  
Přetížená metoda (overloaded method) je metoda, která má stejný název, ale různé parametry (jiný počet, typ nebo pořadí parametrů). Podle toho, jaké argumenty jí při volání předáme, se automaticky vybere ta správná verze.

Vyzkoušíme si to právě na metodě Show třídy MessageBox.  
- Druhý parametr této metody je řetězec, který se zobrazí v titulku okna.
- Třetí parametr je nastavení tlačítka, které se má zobrazit.
- Čtvrtý parametr je nastavení ikony tlačítka.
- Pátý parametr nám umožňuje nastavit výchozí aktivní tlačítko. Tento parametr je vcelku důležitý, umožní uživateli nastavit výchozí možnost pro stisknutí klávesy ENTER. To může zabránit nechtěnému odkliknutí a tím uživatel nepřijde o důležitá data.  
Metoda show má celkem 21 přetížení.

Vyzkoušíme si tyto parametry použít v programu:  
```csharp
            MessageBox.Show("Chcete ukončit aplikaci?", "Aplikace");

            MessageBox.Show("Chcete ukončit aplikaci?", "Aplikace", MessageBoxButtons.OK);
            MessageBox.Show("Chcete ukončit aplikaci?", "Aplikace", MessageBoxButtons.OKCancel);
            MessageBox.Show("Chcete ukončit aplikaci?", "Aplikace", MessageBoxButtons.YesNo);
            MessageBox.Show("Chcete ukončit aplikaci?", "Aplikace", MessageBoxButtons.AbortRetryIgnore);

            MessageBox.Show("Chcete ukončit aplikaci?", "Aplikace", MessageBoxButtons.OK, MessageBoxIcon.Error);
            MessageBox.Show("Chcete ukončit aplikaci?", "Aplikace", MessageBoxButtons.OKCancel, MessageBoxIcon.Information);
            MessageBox.Show("Chcete ukončit aplikaci?", "Aplikace", MessageBoxButtons.YesNo, MessageBoxIcon.Information);
            MessageBox.Show("Chcete ukončit aplikaci?", "Aplikace", MessageBoxButtons.AbortRetryIgnore, MessageBoxIcon.Stop);

            MessageBox.Show("Chcete ukončit aplikaci?", "Aplikace", MessageBoxButtons.OK, MessageBoxIcon.Error, MessageBoxDefaultButton.Button1);
            MessageBox.Show("Chcete ukončit aplikaci?", "Aplikace", MessageBoxButtons.OKCancel, MessageBoxIcon.Information, MessageBoxDefaultButton.Button2);
            MessageBox.Show("Chcete ukončit aplikaci?", "Aplikace", MessageBoxButtons.YesNo, MessageBoxIcon.Information, MessageBoxDefaultButton.Button1);
            MessageBox.Show("Chcete ukončit aplikaci?", "Aplikace", MessageBoxButtons.AbortRetryIgnore, MessageBoxIcon.Stop, MessageBoxDefaultButton.Button3);
```  
- Všechny verze metody Show vracejí hodnotu výčtu DialogResult.
- DialogResult je výčtový typ(enum), který reprezentuje, jaké tlačítko uživatel v dialogu (např. v MessageBox nebo ve vlastním formuláři) stiskl.
``` csharp
            string textVOkne = "Chcete ukončit aplikaci?";
            string textVTitulku = "Aplikace";

            DialogResult dr = MessageBox.Show(textVOkne, textVTitulku, MessageBoxButtons.YesNo, MessageBoxIcon.Question, MessageBoxDefaultButton.Button2);
            if (dr == DialogResult.Yes)
                MessageBox.Show("Konec");
            else
                MessageBox.Show("Ještě nekončíme");

            //Úkol > nasimulujte okno hlášení, které znáte z běžné práce v OS Windows.
```
