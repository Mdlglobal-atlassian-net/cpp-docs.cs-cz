---
title: Vlastnosti příkazu nabídky (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- menu items, properties
- keyboard shortcuts [C++], menu association
- commands [C++], associating menu commands with accelerator keys
- menu commands [C++], associating with keyboard shortcuts
- status bars [C++], associating menu items
- menus [C++], status bar text
- access keys [C++], checking
- menus [C++], shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics [C++], adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics [C++], uniqueness checking
- Check Mnemonics command
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
ms.openlocfilehash: 8989b96640bbb64eb5dcba09d60363dd0989263f
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320572"
---
# <a name="menu-command-properties-c"></a>Vlastnosti příkazu nabídky (C++)

Níže uvedené informace jsou uspořádané podle **nabídky** vlastnosti, které se zobrazují v [okno vlastností](/visualstudio/ide/reference/properties-window) když vyberete příkaz nabídky. Ty jsou uvedeny v abecedním pořadí i když **vlastnosti** okna také umožňuje zobrazit tyto vlastnosti podle kategorie.

|Vlastnost|Popis|
|--------------|-----------------|
|**Konec**|Může být jedna z těchto hodnot:<br /><br />- **Žádný** (výchozí): Žádná zalomení.<br />- **Sloupec**: Tato hodnota pro statické nabídky, umístí příkaz nabídky na nový řádek. Pro místní nabídky umístí tato hodnota příkazu nabídky nový sloupec s žádný zřejmý mezi sloupci. Nastavení této vlastnosti má vliv na vzhled nabídky pouze v době běhu, není v nabídce editoru.<br />- **Panel**: Stejné jako **sloupec** s výjimkou, pro místní nabídky, tato hodnota odděluje nového sloupce ze staré sloupci se zobrazuje svislá čára. Nastavení této vlastnosti není v ovlivňuje vzhled nabídky pouze v době běhu **nabídky** editoru.|
|**Titulek**|Text, který označuje příkaz nabídky (název nabídky). K výběru jedné ze písmena v popiscích nabídky příkazu mnemonická klávesa, předchází znak ampersand (&).|
|**Zaškrtnuto**|Pokud **True**, je příkaz nabídky hesla implicitně zaškrtnuto. Zadejte: **BOOL**. Výchozí hodnota: **False**.|
|**Povoleno**|Pokud **False**, položka nabídky je zakázána.|
|**Šedý**|Pokud **True**, příkaz nabídky je zpočátku šedě a neaktivní. Zadejte: **BOOL**. Výchozí hodnota: **False**.|
|**Pomoc**|Zarovná položky nabídky na pravé straně. Například **pomáhají** příkazu nabídky je vždy na pravé straně ve všech aplikacích pro Windows. Pokud tuto vlastnost nastavíte na položku nabídky, této položky se zobrazí velmi úplně vpravo a na konci velmi nabídky. Platí pro položky nejvyšší úrovně. Výchozí hodnota: **False**.|
|**ID**|Symbol definovaný v souboru hlaviček. Zadejte: **Symbol**, **celé číslo**, nebo **řetězec v uvozovkách**. Můžete použít libovolný symbol, který je běžně k dispozici v editorech, i když [okno vlastností](/visualstudio/ide/reference/properties-window) neposkytuje rozevíracího seznamu pro výběr z.|
|**Popup**|Pokud **True**, příkaz nabídky je rozbalovací nabídky. Zadejte: **BOOL**. Výchozí hodnota: **Hodnota TRUE** pro nejvyšší úrovně nabídky na řádku; jinak nabídek **False**.|
|**Zeptat se**|Obsahuje text, který se zobrazí ve stavovém řádku, když je zvýrazněn tento příkaz. Text je umístěn v tabulce řetězců se stejným identifikátorem příkazu nabídky. Tato vlastnost je k dispozici pro každý typ projektu, ale funkce za běhu je konkrétní knihovny MFC.|
|**Zarovnat zprava doleva.**|Zarovnává doprava příkaz nabídky na řádku nabídek v době běhu. Zadejte: **BOOL**. Výchozí hodnota: **False**.|
|**Right to Left Order**|Umožňuje zobrazovat zprava doleva, pokud rozhraní je lokalizován pro libovolný jazyk, který čte doleva, jako je například hebrejština nebo arabštině příkazů místní nabídky.|
|**Oddělovač**|Pokud **True**, příkaz nabídky je oddělovač. Zadejte: **BOOL**. Výchozí hodnota: **False**.|

## <a name="associate-menu-commands"></a>Přiřazení příkazů nabídky

Jsou často časy, kdy má příkaz nabídky a kombinace kláves stejný příkaz programu. Stejné příkazy jsou vystavované pomocí **nabídky** editor přiřadit stejný identifikátor prostředku pro příkaz nabídky a záznam v tabulce akcelerátorů vaší aplikace. Pak upravíte [titulek](../windows/menu-command-properties.md) příkazu nabídky, aby se zobrazil název klíče akcelerátoru.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Pro přiřazení příkazu nabídky klávese akcelerátoru

1. V **nabídky** editoru vyberte požadovaný příkaz nabídky.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), přidejte název klíče akcelerátoru k **titulek** vlastnost:

   - Po popisek nabídky zadejte řídicí sekvence pro kartu (\t), takže všechno, co jsou klávesové zkratky v nabídce vlevo.

   - Zadejte název modifikační klávesa (**Ctrl**, **Alt**, nebo **Shift**) následované znakem plus (**+**) a název, písmeno, nebo symbol Další klíč.

       Například chcete přiřadit **Ctrl**+**O** k **otevřít** příkaz **souboru** nabídky, změnit příkazu nabídky  **Titulek** tak, aby vypadal jako následující text:

        ```
        &Open...\tCtrl+O
        ```

       Příkaz nabídky v **nabídky** editoru se aktualizuje tak, aby odrážely nový popisek během psaní.

1. [Vytvoření položky tabulky akcelerátorů](../windows/adding-an-entry-to-an-accelerator-table.md) v **akcelerátoru** editoru a přiřaďte ho stejný identifikátor jako příkaz nabídky. Pomocí kombinace kláves, která si myslíte, že bude snadno pamatovat.

### <a name="to-associate-a-menu-command-with-a-status-bar-text-string-in-mfc-applications"></a>Chcete přidružit k příkazu nabídky stavového řádku textového řetězce v aplikacích MFC

Vaše aplikace knihovny MFC můžete zobrazit popisný text pro všechny příkazy nabídek, které může uživatel vybrat. Zobrazí popisný text každého příkazu nabídky s přiřazením textový řetězec **výzvy** vlastnost **vlastnosti** okna. Pokud máte řetězci [tabulka řetězců](../windows/string-editor.md) jehož ID je stejný jako příkaz, aplikace knihovny MFC, automaticky zobrazí tento prostředek řetězce ve stavovém řádku běžící aplikaci. když uživatel najede myší položku nabídky.

1. V **nabídky** editoru, vyberte příkaz nabídky.

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), zadejte text přidružený stavového řádku v **výzvy** pole.

> [!NOTE]
> Tato sada kroků vyžaduje knihovny MFC.

### <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>Přiřazení (místní) přístupový klíč k příkazu nabídky

V projektu v jazyce C++ můžete přiřadit přístupový klíč (symbol, který umožňuje uživateli vybrat nabídku pomocí klávesnice) do nabídek a příkazů nabídky.

Zadejte znak ampersand (`&`) před písmena v názvu nabídky nebo název příkazu zadat písmeno jako odpovídající přístupový klíč. Například "& soubor" sady **Alt**+**F** jako klávesovou zkratku **souboru** nabídky aplikace napsané pro Microsoft Windows.

   Položka nabídky bude informovat viditelné s jedním z písmen klávesová zkratka přiřazena. Následující písmeno, znak ampersand se zobrazí podtržený (závislý na operační systém).

   > [!NOTE]
   > Ujistěte se, že přístupové klíče v nabídce jsou jedinečné pravým tlačítkem myši na vaše nabídky a zvolením **zkontrolujte klávesových zkratek** z místní nabídky.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor nabídek](../windows/menu-editor.md)<br/>
[Přidání komentářů k nabídce](../windows/adding-commands-to-a-menu.md)<br/>
[Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>