# <a name="metadata-and-markdown-template"></a>Šablona metadat a Markdownu

Tato šablona core dokumentace obsahuje příklady syntaxe Markdownu, jakož i pokyny k nastavení metadat. Získat maximum z, musíte zobrazit obojí [nezpracovaná Markdownu](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) a [vykresluje zobrazení](https://github.com/dotnet/docs/blob/master/styleguide/template.md) (například nezpracovaná Markdownu zobrazuje blok metadat zatímco vykreslené zobrazení nepodporuje).

Při vytváření souboru Markdownu, by měl zkopírovat do nového souboru, vyplnit metadata níže, úmluvu nadpis H1 výše na název článku a odstranit obsah.

## <a name="metadata"></a>Metadata

Kompletní blok metadat je uveden výše (v [nezpracovaná Markdownu](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md)), je rozdělený na povinná a volitelná pole. Důležité poznámky:

- Můžete **musí** mít mezeru mezi dvojtečkou (:) a hodnotou elementu metadat.
- Pokud Volitelný element metadat nemá hodnotu, okomentujte elementu znakem # nebo odebrat (nenechávejte ho prázdný ani nepoužívejte "na"); Pokud přidáváte hodnotu do elementu, který bylo označeno jako komentář, nezapomeňte odebrat webu služby #.
- Použití dvojteček v hodnotě (například název) přerušit analyzátoru metadat. V takovém případě před a za název s dvojitými uvozovkami (například `title: "Writing .NET Core console apps: An advanced step-by-step guide"`).
- **název**: Tento název se zobrazí ve výsledcích vyhledávání vyhledávacího webu. Můžete také přidat svislé čáry (|) a potom podle názvu produktu (například `title: Developing Libraries with Cross Platform Tools | .NET Core`). Název není musí být stejný jako název v nadpisu H1 a měl by obsahovat 65 znaků nebo méně (včetně | NÁZEV PRODUKTU).
- **Autor**, **správce**, **ms.reviewer**: pole author musí obsahovat **uživatelské jméno v Githubu** autora, ne jeho alias.  "Správce" a "ms.reviewer" pole, na druhé straně může obsahovat pouze aliasy společnosti Microsoft. MS.Reviewer Určuje název přidružený k článku nebo funkce PM a vývojáře.
- **MS.devlang** definuje technologie. Některé podporované hodnoty jsou: `dotnet`, `cpp`, `csharp`, `fsharp`, `vb` a `xml`.
- **MS.AssetID**: Toto je identifikátor GUID tohoto článku, který se používá pro účely sledování interní například Business Intelligence (BI). Při vytváření nového souboru Markdownu získáte identifikátor GUID z [Online GUID Generator](https://www.guidgenerator.com/).

## <a name="basic-markdown-gfm-and-special-characters"></a>Základní Markdown a GFM, speciální znaky

Všechny základní a GitHub Flavored Markdown (GFM) není podporovaný. Další informace naleznete v tématu:

- [Syntaxe základního Markdownu](https://daringfireball.net/projects/markdown/syntax)
- [Dokumentace ke službě GFM](https://guides.github.com/features/mastering-markdown)

Markdown používá speciální znaky jako \*, \`, a \# pro formátování. Pokud budete chtít obsahovat jednu z těchto znaků v obsahu, musíte udělat jednu ze dvou kroků:

- Vložit zpětné lomítko před speciální znak "před" něj (například `\*` pro \*)
- Použití [kód HTML entity](https://www.ascii.cl/htmlcodes.htm) znaku (například `&#42;` pro &#42;).

## <a name="markdown-editing-tools"></a>Markdown nástroje pro úpravy

Můžete použít [Visual Studio Code](https://code.visualstudio.com/) k úpravám Markdownu dokumentů. VS Code má mnoho užitečná rozšíření Markdownu, například:

- [Docs markdown](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-markdown) společností Microsoft
- [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)

## <a name="file-name"></a>Název souboru

Názvy souborů používají následující pravidla:

- Obsahovat jenom malá písmena, číslice a pomlčky.
- Žádné mezery a interpunkční znaménka. K oddělení slov a čísel v názvu souboru použijte pomlčky.
- Použití akční slovesa, které jsou specifické, jako například vyvíjet, koupit, sestavení, řešení potíží s. Žádná slova - ing.
- Krátká slova - nezahrnují a a, in, or atd.
- Musí být ve formátu Markdown a používat příponu souboru. MD.
- Zachovejte poměrně krátké názvy souborů. Jsou součástí adresy URL pro vaše články.  

## <a name="headings"></a>Záhlaví

Použijte styl věty malá a velká písmena. Použijte vždy velká písmena:

- První slovo nadpis.
- Slovo, které následuje dvojtečka v záhlaví nebo název (například "postupy: řazení pole").

Záhlaví by mělo být provedeno pomocí atx – vizuální styl, tedy použít 1 až 6 znaků hodnoty hash (#) na začátku řádku k označení nadpisu, odpovídající HTML záhlaví úrovně H1 až H6. Příklady první a druhé úrovně hlavičky jsou využité nad.

Existuje **musí** být pouze jeden nadpis první úrovně (H1) v tématu, které se zobrazí jako nadpis na stránce.

Pokud záhlaví končí `#` znak, budete muset přidat další `#` znak end v pořadí pro nadpis vykreslila správně. Například `# Async Programming in F# #`.

Existuje musí být vždy jeden prázdný řádek před a za záhlaví (s výjimkou položky první úrovně).

Nadpisy druhé úrovně se generování obsahu na stránce, která se zobrazí v části "v tomto článku" pod nadpis na stránce.

```markdown
### Third-level heading

#### Fourth-level heading

##### Fifth level heading

###### Sixth-level heading
```

## <a name="text-styling"></a>Styl textu

*Kurzíva*  
Použití uživatelem generovaných názvů souborů, složek a cesty (pro dlouhé položky, rozdělit na vlastním řádku); nové podmínky; názvy parametrů; uživatel zadal hodnot. a adresy URL (Pokud se vykresluje jako odkazy, což je výchozí hodnota).

**Tučné**  
Používá se pro prvky uživatelského rozhraní a klíčová slova jazyka.

## <a name="links"></a>Odkazy

### <a name="internal-links"></a>Vnitřní propojení

Pokud chcete propojit s hlavičkou ve stejném souboru s Markdownem (označované také jako ukotvené odkazy), budete muset zjistit id hlavičky, kterou se snažíte propojit. Potvrďte ID zobrazení zdroje vykreslené článku, vyhledejte id hlavičky (například `id="blockquote"`) a vytvořte odkaz zadáním # + id (například `#blockquote`).
Id se generuje automaticky na základě textu záhlaví. Ano, například dány jedinečný oddíl s názvem `## Step 2`, id bude vypadat takto `id="step-2"`.

- Příklad: [kapitoly 1](#chapter-1)

Odkaz na soubor Markdown ve stejném úložišti, použijte [relativní odkazy](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2), včetně ".md" na konci názvu souboru.

- Příklad: [souboru Readme](../readme.md)
- Příklad: [Vítejte v .NET](../docs/welcome.md)

Odkaz na hlavičku v souboru Markdownu ve stejném úložišti, použijte relativní odkaz + hashtag odkaz.

- Příklad: [komunity .NET](../docs/welcome.md#community)

### <a name="docs-links"></a>Dokumentace odkazy

Odkaz na soubor v jiné úložiště dokumentace, použijte relativní adresu URL webu docs.microsoft.com jako odkaz. Přípona .md nezahrnují.

- Příklad: [dokumentace k univerzální platformě Windows](/windows/uwp)

### <a name="external-links"></a>Externí odkazy

Odkaz na externí soubor, použijte jako odkaz úplnou adresu URL. Použijte adresu URL HTTPS, pokud je k dispozici.

- Příklad: [Githubu](https://www.github.com)

Pokud adresa URL se zobrazí v souboru Markdownu, bude transformovat na prokliknutelný odkaz.

- Příklad: https://www.github.com

### <a name="links-to-apis"></a>Odkazy na rozhraní API

Systém sestavení má některá rozšíření, které umožňují nám odkaz na rozhraní API pro .NET Core, aniž byste museli používat externí odkazy.  
Při připojování k rozhraní API, můžete použít jeho jedinečný identifikátor (UID), který se automaticky generuje ze zdrojového kódu.

Můžete použít jednu z následujících syntaxí:

1. Odkaz markdownu: `[link_text](xref:UID)`
2. Automatické propojení: `<xref:UID>`
3. Zkrácený tvar vlastností formuláře: `@UID`

- Příklad: `@System.String`
- Příklad: `[String class](xref:System.String)`

Další informace o použití tohoto zápisu najdete v tématu [použití křížového odkazu](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference).

> V tuto chvíli, neexistuje žádný snadný způsob, jak najít identifikátory UID. Nejlepší způsob, jak najít identifikátor UID pro rozhraní API je chcete vyhledat v tomto úložišti: [docascode/coreapi](https://github.com/docascode/coreapi). Pracujeme na s lepší systém v budoucnu.

Pokud UID obsahuje speciální znaky \` nebo \#, hodnota UID musí být formátu % 60 a % 23 stejně jako v následujících příkladech HTML:
- Příklad: @System.Threading.Tasks.Task \`stane 1 `@System.Threading.Tasks.Task%601`
- Příklad: @System.Exception.\# ctor se změní `@System.Exception.%23ctor`

## <a name="lists"></a>Seznamy

Prázdné řádky by měly být uzavřeny do seznamů.

### <a name="ordered-lists"></a>Seřazené seznamy

1. Tento
1. je
1. Aplikace
1. Řazení
1. Seznam

#### <a name="ordered-list-with-an-embedded-list"></a>Seřazený seznam s vloženým seznamem

1. Tady
1. obsahuje
1. Aplikace
1. Vložený
    1. Neúspěšné přístupy do Scarlett
    1. Profesor Plum
1. ordered
1. list

### <a name="unordered-lists"></a>Neuspořádané seznamy

- Tento
- is
- a
- seznamy s odrážkami
- list

#### <a name="unordered-list-with-an-embedded-list"></a>Neseřazený seznam s vloženým seznamem

- Tento
- seznamy s odrážkami
- list
    - Mrs. ml
    - Pan zelená
- obsahuje  
- Ostatní
    1. Colonel hořčice
    1. Mrs. prázdné
- seznamy

## <a name="horizontal-rule"></a>Vodorovná čára

___

## <a name="tables"></a>Tabulky

| Tabulky        | Jsou           | Cool  |
| ------------- |:-------------:| -----:|
| sloupec 3 je      | zarovnaný doprava | $ 1 600 |
| sloupec 2 je      | zarovnání na střed      |   $12 |
| sloupec 1 je ve výchozím nastavení | Zarovnat doleva     |    $1 |

Můžete použít [nástroje Generátor tabulku Markdown](https://www.tablesgenerator.com/markdown_tables) usnadňují vytváření je mnohem snazší. Viz také [Markdownu nástrojům pro úpravu](#markdown-editing-tools).

## <a name="code"></a>Kód

Nejlepší způsob, jak zahrnout kód je zahrnout fragmenty kódu z práce ukázky. Vytvoření ukázky postupovat podle pokynů [přispívající průvodce](../CONTRIBUTING.md#contributing-to-samples).

Může obsahovat kód pomocí syntaxe include:

```markdown
[!code-csharp[<title>](<pathToFile>#<RegionName)]
```

V příkladu výše ukazuje C# syntaxe, ale jiné jazyky jsou podporovány.
Použít `code-fsharp` pro F# ukázky; použijte `code-vbnet` pro ukázky jazyka Visual Basic.
Další jazyky, které jsou podporovány jsou:

- JAZYK C++: `code-cpp`
- HTML: `code-html`
- Jazyk JavaScript: `code-javascript`
- Prostředí PowerShell: `code-ps`
- SQL: `code-sql`
- XML: `code-xml`

Text pro umístit `<title>` ukazovat efekt přechodu na text. `<pathToFile>` Je cesta ke zdrojovému souboru. `<RegionName>` By měl být oblast ve zdrojovém kódu, který by měly být zahrnuty. Použití `#region` a `#endregion` preprocesoru syntaxe pro určení oblast kód přikazující zahrnutí.

V případech, kde oblastech nefungují můžete zadat počáteční a koncové fragmentu pomocí název elementu XML v jednořádkový komentář. Například to mohl napsat C#:

```csharp
// <CodeToInclude>
int j = 5;
int i ; 10;
int sum = i + j;
// </CodeToInclude>
```

V jiných jazycích použijte syntaxe komentáře pro daný jazyk.

Nakonec můžete použít čísla řádků: `#L1-L10` zahrnuje řádky 1 až 10. Zabraňte jsme čísla řádků, protože jsou velmi křehký.

Fragmenty kódu z úplné aplikací včetně zajistíte, že veškerý kód spustí prostřednictvím našeho systému kontinuální integrace (CI). Ale pokud potřebujete něco ukazují, že způsobí, že nějaké chyby nebo za běhu, můžete použít vložené bloky kódu.

### <a name="inline-code-blocks-with-language-identifier"></a>Vložené bloky kódu pomocí identifikátor jazyka

Použití tří zpětných apostrofů (\`\`\`) + ID jazyka, které chcete použít barvu specifické pro jazyk kódování v bloku kódu. Tady je úplný seznam [GFM jazyků](https://github.com/jmm/gfm-lang-ids/wiki/GitHub-Flavored-Markdown-(GFM)-language-IDs).

#### <a name="c"></a>C\#

```csharp
using System;
namespace HelloWorld
{
    class Hello
    {
        static void Main() 
        {
            Console.WriteLine("Hello World!");

            // Keep the console window open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

#### <a name="python"></a>Python

```python
friends = ['john', 'pat', 'gary', 'michael']
for i, name in enumerate(friends):
    print "iteration {iteration} is {name}".format(iteration=i, name=name)
```

#### <a name="powershell"></a>PowerShell

```powershell
Clear-Host
$Directory = "C:\Windows\"
$Files = Get-Childitem $Directory -recurse -Include *.log `
-ErrorAction SilentlyContinue
```

### <a name="generic-code-block"></a>Obecný kód bloku

Použití tří zpětných apostrofů (&#96;&#96;&#96;) pro kódování obecný kód bloku.

> Doporučený postup je bloky kódu pomocí jazyka identifikátory, jak je popsáno v předchozí části zajistit správnou syntaxi zvýraznění v webu s dokumentací. Použijte obecný kód bloky pouze v případě potřeby.

```javascript
function fancyAlert(arg) {
    if(arg) {
        $.docs({div:'#foo'})
    }
}
```

### <a name="inline-code"></a>Vložený kód

Pomocí zpětných apostrofů (&#96;) pro `inline code`. Pomocí vloženého kódu pro příkazy příkazového řádku, názvy tabulek a sloupců databáze a výrazy jazyka a názvy funkcí.

## <a name="blockquotes"></a>Bloková citace

> Posledních měl trval po nyní deset miliónů let a reign strašlivých ještěrů dávno skončila. Tady na rovníku, na který by jednoho dne bude známý jako Afrika, boj existence dospěla znovu dosahoval z vrcholu zuřivosti, a Vítěz stále ještě nebyl zřejmý. V této pusté a vyprahlé půdu, pouze malé nebo swift nebo zavilý může rychlým, nebo dokonce Doufáme, že nezbytné k překonání.

## <a name="images"></a>Obrázky

### <a name="static-image-or-animated-gif"></a>Statický obrázek nebo animovaný gif

![Toto je alternativní text](../images/Logo_DotNet.png)

### <a name="linked-image"></a>Propojený obrázek

[![alternativní text pro propojený obrázek](../images/Logo_DotNet.png)](https://dot.net)

## <a name="videos"></a>Videa

### <a name="channel-9"></a>Channel 9

[![Larry Osterman - jeho jednu interakci s Billem Gatesem (přes DOS síťového zásobníku)](https://sec.ch9.ms/ch9/caf5/f8657a22-5b83-47a3-9748-4c1be9fecaf5/Larry-Osterman-His-one-interaction-with-Bill-Gate_960.jpg)
](https://channel9.msdn.com/Blogs/TheChannel9Team/Larry-Osterman-His-one-interaction-with-Bill-Gates-over-DOS-networking-stack)

### <a name="youtube"></a>YouTube

[![Na rozhraní .NET 2/4/2016 - Scottem Hunterem](https://img.youtube.com/vi/g2a4W6Q7aRw/0.jpg)
](https://www.youtube.com/watch?v=g2a4W6Q7aRw)

## <a name="docsmicrosoft-extensions"></a>docs.Microsoft rozšíření

docs.Microsoft poskytuje několik dalších rozšíření Markdown specifický pro GitHub. 

### <a name="alerts"></a>Upozornění

Je třeba použít následující upozornění styly, aby vykreslovaly správné stylem na webu dokumentace. Vykreslovací modul na Githubu však nerozlišují je.

#### <a name="note"></a>Poznámka

> [!NOTE]
> Toto je poznámka

#### <a name="warning"></a>Upozornění

> [!WARNING]
> Toto je upozornění

#### <a name="tip"></a>Tip

> [!TIP]
> Toto je TIP

#### <a name="important"></a>Důležité

> [!IMPORTANT]
> Toto je důležité.

A budete vykreslí se takto: ![upozornění styly](../images/alerts.png)

### <a name="buttons"></a>Tlačítka

> [!div class="button"]
[odkazy v podobě tlačítek](../docs/core/index.md)

Vidíte příklad tlačítek v akci na [dokumentace Intune](https://docs.microsoft.com/intune/get-started/choose-how-to-enroll-devices). 

### <a name="selectors"></a>Selektory

> [!div class="op_single_selector"]
- [macOS](../docs/core/tutorials/using-on-macos.md)
- [Windows](../docs/core/tutorials/using-on-windows.md)

Vidíte příklad selektory akce na [dokumentace Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune#how-your-end-users-get-their-apps).

### <a name="step-by-steps"></a>Krok kroky

>[!div class="step-by-step"]
[Pre](../docs/csharp/expression-trees-interpreting.md)
[další](../docs/csharp/expression-trees-translating.md)

Vidíte příklad krok podle kroků v akce na [dokumentace k Advanced Threat Analytics](https://docs.microsoft.com/advanced-threat-analytics/deploy-use/install-ata-step2).
