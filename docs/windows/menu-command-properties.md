---
title: Příkazy nabídky (C++)
ms.date: 02/15/2019
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
ms.openlocfilehash: 972478923a7c4c60d8ff949c5532b00a1de1efc0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075506"
---
# <a name="menu-commands-c"></a>Příkazy nabídky (C++)

Níže uvedené informace jsou uspořádány podle vlastností **nabídky** , které se zobrazí v [okně Vlastnosti](/visualstudio/ide/reference/properties-window) při výběru příkazu nabídky. Ty jsou uvedeny v abecedním pořadí, přestože okno **vlastnosti** také umožňuje zobrazit tyto vlastnosti podle kategorie.

|Vlastnost|Popis|
|--------------|-----------------|
|**Rozdělován**|Může to být jedna z těchto hodnot:<br/>  - **none**: žádné přerušení. Toto nastavení je výchozí.<br/>  - **sloupec**: u statických nabídek tato hodnota umístí příkaz nabídky na nový řádek.<br/>      Pro místní nabídky tato hodnota umístí příkaz nabídky do nového sloupce bez dělicí čáry mezi sloupce.<br/>      Nastavení této vlastnosti ovlivňuje vzhled nabídky pouze v době běhu, nikoli v editoru nabídek.<br />   - **bar**: totéž jako **sloupec** s výjimkou pro místní nabídky, tato hodnota odděluje nový sloupec ze starého sloupce se svislou čárou.<br/>      Nastavení této vlastnosti ovlivňuje vzhled nabídky pouze v době běhu, nikoli v **editoru nabídek**.|
|**Popisku**|Text popisku příkazu nabídky (název nabídky) Chcete-li vytvořit jedno z písmen v popisku příkazu nabídky s použitím klávesové zkratky, uveďte před ním znak ampersand (&).|
|**Kontrolovaný**|Při **hodnotě true**se zpočátku kontroluje příkaz nabídky. Zadejte: **bool**. Výchozí hodnota: **false**.|
|**Enabled** (Povoleno)|Je-li nastavena **hodnota false**, položka nabídky je zakázána.|
|**Zobrazena šedě**|Při **hodnotě true**je příkaz nabídky zpočátku šedý a neaktivní. Zadejte: **bool**. Výchozí hodnota: **false**.|
|**Pomoc**|Zarovná položku nabídky doprava. Výchozí hodnota: **false**.<br/><br/>Například příkaz nabídky **help** je vždycky na pravé straně všech aplikací Windows. Pokud tuto vlastnost nastavíte pro položku nabídky, tato položka se zobrazí v pravém horním rohu a na konci této nabídky. Platí pro položky nejvyšší úrovně.|
|**ID**|Symbol definovaný v hlavičkovém souboru. Typ: **symbol**, **celé číslo**nebo **řetězec v uvozovkách**.<br/><br/>Můžete použít libovolný symbol, který je běžně k dispozici v některém z editorů, i když [okno Vlastnosti](/visualstudio/ide/reference/properties-window) neposkytuje rozevírací seznam, ze kterého můžete vybírat.|
|**Popup**|Pokud je nastaveno na **true**, je příkaz nabídky místní nabídkou. Zadejte: **bool**. Výchozí hodnota: **true** pro nabídky nejvyšší úrovně na řádku nabídek, jinak **false**.|
|**Výzv**|Obsahuje text, který se zobrazí ve stavovém řádku při zvýraznění tohoto příkazu nabídky. Text je umístěn v tabulce řetězců se stejným identifikátorem jako příkaz nabídky.<br/><br/>Tato vlastnost je k dispozici pro jakýkoliv typ projektu, ale Běhová funkce je specifická pro knihovnu MFC.|
|**Zarovnat zprava doleva**|Pravým tlačítkem myši Zarovná příkaz nabídky na řádku nabídek v době běhu. Zadejte: **bool**. Výchozí hodnota: **false**.|
|**Vpravo od levého pořadí**|Umožňuje příkazům nabídky zobrazovat zprava doleva, pokud je rozhraní lokalizované do libovolného jazyka, který čte zprava doleva, jako je například hebrejština nebo arabština.|
|**Oddělovač**|Pokud je nastaveno na **true**, příkaz nabídky je oddělovač. Zadejte: **bool**. Výchozí hodnota: **false**.|

## <a name="associate-menu-commands"></a>Přidružit příkazy nabídky

K dispozici jsou často časy, kdy chcete příkaz nabídky a kombinaci kláves vystavovat stejným příkazem programu. Identické příkazy jsou vydávány pomocí **editoru nabídek** pro přiřazení stejného identifikátoru prostředku k příkazu nabídky a k záznamu v tabulce akcelerátorů vaší aplikace. Pak upravíte [Titulek](../windows/menu-command-properties.md) příkazu nabídky a zobrazí se název klávesy akcelerátoru.

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Přidružení příkazu nabídky ke klávese akcelerátoru

1. V **editoru nabídek**vyberte příkaz nabídky, který chcete.

1. V [okně Vlastnosti](/visualstudio/ide/reference/properties-window)přidejte do vlastnosti **Caption** (název) klávesu akcelerátoru:

   - Po zadání popisku nabídky zadejte řídicí sekvenci pro tabulátor (\t), aby byly všechny klávesové zkratky v nabídce zarovnané doleva.

   - Zadejte název modifikační klávesy (**CTRL**, **ALT**nebo **SHIFT**) následovaný symbolem plus ( **+** ) a názvem, písmenem nebo symbolem dalšího klíče.

   Chcete-li například přiřadit příkaz **Ctrl**+**o** k příkazu **otevřít** v nabídce **soubor** , upravte **Titulek** příkazu nabídky tak, aby vypadal jako následující text:

   ```
   &Open...\tCtrl+O
   ```

   Příkaz nabídky v **editoru nabídek** se aktualizuje tak, aby odrážel nový titulek při psaní.

1. [Vytvořte položku akcelerátor – tabulka](../windows/adding-an-entry-to-an-accelerator-table.md) v editoru **akcelerátorů** a přiřaďte ji stejnému identifikátoru jako příkaz nabídky. Použijte kombinaci kláves, kterou si myslíte, že se snadno pamatuje.

Aplikace MFC může zobrazit popisný text pro každý z příkazů nabídky, které uživatel může vybrat. Přiřaďte textový řetězec k příkazu nabídky pomocí vlastnosti **prompt** v okně **vlastnosti** a zobrazte tak popisný text. Pokud máte řetězec v [tabulce řetězců](../windows/string-editor.md) , jehož ID je stejné jako příkaz, aplikace MFC automaticky zobrazí tento prostředek řetězce ve stavovém řádku běžící aplikace, když uživatel najede myší na položku nabídky.

- K přidružení příkazu nabídky k textovému řetězci stavového řádku v aplikacích MFC v **editoru nabídek**vyberte příkaz nabídky. V [okně Vlastnosti](/visualstudio/ide/reference/properties-window)zadejte do pole **příkazového řádku** přidružený text stavového řádku.

V C++ projektu můžete přiřadit přístupový klíč (k ovládacímu prvku, který uživateli umožňuje vybrat nabídku pomocí klávesnice) pro nabídky a příkazy nabídek.

- Chcete-li přiřadit klávesu Access (klávesovou zkratku) k příkazu nabídky, zadejte ampersand (`&`) před písmeno v nabídce název nebo název příkazu k zadání písmena jako odpovídajícího přístupového klíče.

   Například "& soubor" nastaví **Alt**+**F** jako klávesovou zkratku pro nabídku **soubor** v aplikacích napsaných pro Microsoft Windows.

   Položka nabídky poskytne viditelné upozornění, že jedno z písmen má přiřazenou klávesovou zkratku. Písmeno následující po ampersandu bude podtržené (závisí na operačním systému).

> [!NOTE]
> Zajistěte, aby všechny přístupové klávesy v nabídce byly jedinečné kliknutím pravým tlačítkem myši na nabídku a výběrem možnosti **zkontrolovat klávesové zkratky**.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editor nabídek](../windows/menu-editor.md)

<!--
[Strings (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>-->