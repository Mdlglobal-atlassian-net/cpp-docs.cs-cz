---
title: 'Postupy: Správa symbolů'
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing
- vc.editors.symbol.restrictions.name
- vc.editors.symbol.changing.value
- vc.editors.symbol.restrictions.value
- vc.editors.symbol.changing.header
- vc.editors.symbol.changing.unassigned
- vc.editors.symbol.shared.calculated
helpviewer_keywords:
- symbol names
- symbols [C++], names
- restrictions, symbol names
- numeric values
- symbols [C++], numeric values
- numeric values, changing symbols
- symbols [C++], value restrictions
- restrictions, symbol values
- resource files [C++], multiple
- Resource Includes dialog box [C++]
- symbol header files [C++], changing names
- symbols [C++], symbol header files
- Resource.h
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
- symbols [C++], read-only
- symbols [C++], shared
- symbols [C++], calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
ms.openlocfilehash: 4bc0376b6b5ff402f0cc9f40093e000763ad6656
ms.sourcegitcommit: bec1480a03e7b4070b469a6c131a69f516bbac70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56226368"
---
# <a name="how-to-manage-symbols"></a>Postupy: Správa symbolů

Při vytváření nového prostředku nebo prostředku objektu vývojové prostředí jí přiřadí výchozí název symbolu, například IDD_DIALOG1. Můžete použít [okno vlastností](/visualstudio/ide/reference/properties-window) Chcete-li změnit výchozí název symbolu nebo chcete změnit název žádný symbol už přidružené k prostředku.

Pro symboly přidružený jeden prostředek, můžete použít také **vlastnosti** oknu změnit hodnotu symbolu. Můžete použít [symboly prostředků – dialogové okno](../windows/resource-symbols-dialog-box.md) ke změně hodnoty symbolů není aktuálně přiřazená k prostředku.

Obvykle všechny symbol definice jsou uložené v `Resource.h`. Však může být nutné změnit to zahrnovat název souboru, což umožní, například pracovat s více než jeden soubor prostředků ve stejném adresáři.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*.

> [!NOTE]
> Pokud váš projekt již neobsahuje soubor .rc, přečtěte si téma [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

## <a name="symbol-name-restrictions"></a>Omezení názvu symbolu

Omezení pro názvy symbolů jsou následující:

- Všechny [symboly](../windows/symbols-resource-identifiers.md) musí být jedinečné v rámci oboru aplikace. To zabraňuje konfliktní definice symbolu v souborech hlaviček.

- Platné znaky pro název symbolu zahrnout, A-Z, a – z, 0-9 a podtržítka (_).

- Názvy symbolů nemůže začínat číslem a jsou omezené na 247 znaků.

- Názvy symbolů nesmí obsahovat mezery.

- Názvy symbolů se velká a malá písmena, ale je zachováno případ prvním definice symbolu. Hlavičkový soubor, který definuje symboly umožňuje kompilátoru/editor prostředků a programech C++ odkazovat prostředky definované v souboru prostředků. Pro dva názvy symbolů, která se liší pouze v případě, program jazyka C++ se zobrazí dva samostatné symboly, zatímco kompilátor/editor prostředků se zobrazí oba názvy jako odkazující na jeden jeden symbol.

   > [!NOTE]
   > Pokud není podle schématu název standardní symbol (ID*_[keyword]) uvedených níže, a být stejná jako klíčové slovo ví, kompilátor prostředků skriptu, došlo k pokusu o vytvoření souboru skriptu prostředků bude výsledkem chyba zdánlivě náhodný název symbolu se stane s generace, které je obtížné diagnostikovat. Chcete-li tomu zabránit, dodržovat standardní schéma pojmenování.

Názvy symbolů mají popisný předpony, které označují typ prostředku nebo objektů, které představují. Tyto předpony popisný začínat identifikátor kombinaci textu Třídy knihovny MFC (Microsoft Foundation) používá konvence pojmenování symbol je znázorněno v následující tabulce.

|Kategorie|Předpona|Použití|
|--------------|------------|---------|
|Prostředky|IDR_ IDD_ IDC_ IDI_ IDB_|Akcelerátoru nebo nabídky (a související nebo vlastní prostředky) dialogové okno ikony rastrového obrázku kurzoru|
|Položky nabídky|ID_|Položka nabídky|
|Příkazy|ID_|Příkaz|
|Ovládací prvky a podřízená okna|IDC_|Control|
|Řetězce|IDS_|Řetězec do tabulky řetězců|
|MFC|AFX_|Vyhrazeno pro předdefinované symboly MFC|

### <a name="to-change-a-symbol-name-id"></a>Chcete-li změnit název symbolu (ID)

1. V [zobrazení prostředků](../windows/resource-view-window.md), vyberte prostředek.

1. V **vlastnosti** okno, zadejte nový název symbolu nebo vyberte ze seznamu existující symboly v **ID** pole.

   Pokud zadáte nový název symbolu, jí automaticky přiřazena hodnota.

Můžete použít [symboly prostředků – dialogové okno](../windows/resource-symbols-dialog-box.md) změnit názvy symbolů není aktuálně přiřazená k prostředku.

## <a name="symbol-value-restrictions"></a>Omezení hodnoty symbolu

Symbol hodnota může být libovolné celé číslo vyjádřena v normálním způsobem pro # direktivy preprocesoru define. Tady jsou některé příklady hodnot symbolů:

```
18
4001
0x0012
-3456
```

Hodnoty symbolů pro prostředky (akcelerátory, rastrové obrázky, kurzory, dialogová okna, ikony, nabídky, tabulek řetězců a informace o verzi) musí být desítkové číslo v rozsahu od 0 do 32 767 (ale nemůže být šestnáctkové). Hodnoty symbolů pro části prostředků, jako jsou ovládací prvky dialogového okna nebo jednotlivé řetězce v tabulce řetězců může být od 0 do 65 534 nebo od-32 768 do 32 767.

Symboly prostředků jsou čísla 16 bitů. Můžete je zadat jako nebo bez znaménka, ale využívají interně jako celá čísla bez znaménka. Takže záporná čísla bude přetypovat na jejich odpovídající kladnou hodnotu.

Tady jsou některá omezení hodnoty symbolu:

- Vývojové prostředí sady Visual Studio a MFC používají některé počet rozsahů pro zvláštní účely. Všechna čísla sadou nejvýznamnější bit (-32 768 -1 a 32 768 do 65 534, v závislosti na znaménko) jsou vyhrazené knihovny MFC.

- Nejde definovat hodnotu symbolu pomocí jiných řetězců symbol. Například následující definice symbolu se nepodporuje:

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- Makra preprocesoru nelze použít s argumenty jako definice hodnot. Příklad:

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

   není platný výraz bez ohledu na to, co `ID` vyhodnocen v době kompilace.

- Vaše aplikace může mít existující soubor obsahující symboly definované s výrazy. Další informace o tom, jak zahrnout symboly jako jen pro čtení symbolů najdete v tématu [použití sdílených (jen pro čtení) nebo počítané symboly](../windows/including-shared-read-only-or-calculated-symbols.md).

Další informace o počet rozsahů, naleznete v tématu [TN023: Standardní prostředky MFC](../mfc/tn023-standard-mfc-resources.md).

### <a name="to-change-a-symbol-value"></a>Chcete-li změnit hodnotu symbolu

1. V [zobrazení prostředků](../windows/resource-view-window.md), vyberte prostředek.

1. V **vlastnosti** okno, zadejte název symbolu následovaný symbolem rovná a typ integer v **ID** pole, například:

    ```
    IDC_EDITNAME=5100
    ```

Nová hodnota je uložena v hlavičkový soubor symbolů při příštím uložte projekt. Pouze název symbolu zůstává viditelná pole ID. rovnítko a hodnota nejsou zobrazeny po jste ověření.

## <a name="change-or-delete-unassigned-symbols"></a>Změna nebo odstranění nepřiřazených symbolů

Během činnosti v [symboly prostředků – dialogové okno](../windows/resource-symbols-dialog-box.md), můžete upravit nebo odstranit existující symboly, které nejsou přiřazeny k prostředku nebo objekt.

### <a name="to-change-an-unassigned-symbol"></a>Změna nepřiřazených symbolů

1. V **název** vyberte nepřiřazených symbolů a vyberte **změnu**.

1. Upravit vlastnosti name nebo value v polí zobrazených v symbolu **změnit Symbol** dialogové okno.

   > [!NOTE]
   > Chcete-li změnit symbol, který *je* přiřazené k prostředku nebo k objektu, je nutné použít editor prostředků nebo **vlastnosti** okna.

### <a name="to-delete-an-unassigned-unused-symbol"></a>Chcete-li odstranit symbol nepřiřazené (nepoužívané)

V [symboly prostředků – dialogové okno](../windows/resource-symbols-dialog-box.md), vyberte symbol, který chcete odstranit a zvolte **odstranit**.

   > [!NOTE]
   > Před odstraněním nepoužívaných symbolů do souboru prostředků, ujistěte se, že se nepoužívá jako jinde v programu ani soubory prostředků zahrnuté v době kompilace.

## <a name="include-shared-read-only-or-calculated-symbols"></a>Zahrnout sdílených (jen pro čtení) nebo vypočtených symbolů

Při prvním vývojové prostředí přečte soubor prostředků vytvořený v jiné aplikaci, označí všechny soubory zahrnuté záhlaví jen pro čtení. I když můžete použít [dialogové okno prostředek zahrnuje](../windows/resource-includes-dialog-box.md) přidat soubory hlaviček další symbolů jen pro čtení.

Jedním z důvodů, že můžete chtít použít definice symbolů jen pro čtení se pro soubory symbolů, které máte v plánu sdílet mezi více projekty.

Soubory zahrnuté symbolů můžete použít také v případě, že máte existující prostředky s definice symbolů, které definovat hodnotu symbolu pomocí výrazů spíše než jednoduché celých čísel. Příklad:

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)
```

Prostředí se správně interpretovat tyto počítané symboly, pokud:

- Počítané symboly jsou umístěny v souboru symbolů jen pro čtení.

- Soubor prostředků obsahuje prostředky, ke kterým jsou už přiřazené tyto počítané symboly.

- Je očekáván číselný výraz.

> [!NOTE]
> Pokud se očekává řetězec nebo číselný výraz, výraz není vyhodnocen.

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>Zahrnout do souboru prostředků sdílené symboly (pouze pro čtení)

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc a zvolte [prostředek zahrnuje](../windows/resource-includes-dialog-box.md) z místní nabídky.

1. V **měrnice souborů jen pro čtení** pole, použijte `#include` direktivy kompilátoru k určení souboru, kam chcete uchovávat symbolů jen pro čtení.

   Nevolejte soubor `Resource.h`, protože se běžně používá hlavičkový soubor symbolů hlavní název souboru.

   > [!NOTE]
   > **Důležité** zadejte v poli direktivy symbolů jen pro čtení je součástí souboru prostředků přesně během psaní. Ujistěte se, jaký typ neobsahuje chyby syntaxe nebo kontrolu pravopisu.

   Použití **měrnice souborů jen pro čtení** pole mají zahrnout soubory s pouze definice symbolů. Nezahrnují definice prostředků. v opačném případě duplicitní prostředek, který definice se vytvoří, když je soubor uložen.

1. Umístění symbolů v souboru, který jste zadali.

   Symboly v souborech tímto způsobem jsou vyhodnocovány pokaždé, když otevřete soubor prostředků, ale nejsou při uložení souboru nahrazena na disku.

1. Vyberte **OK**.

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Chcete-li změnit název hlavičkový soubor symbolů prostředků

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc a zvolte [prostředek zahrnuje](../windows/resource-includes-dialog-box.md) z místní nabídky.

1. V **hlavičkový soubor symbolů** zadejte nový název pro tento soubor.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)<br/>
[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)<br/>
[Zobrazení symbolů prostředků](../windows/viewing-resource-symbols.md)<br/>