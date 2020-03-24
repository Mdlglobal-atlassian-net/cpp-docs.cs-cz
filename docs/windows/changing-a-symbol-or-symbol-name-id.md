---
title: 'Postupy: Správa symbolů'
ms.date: 02/14/2019
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
ms.openlocfilehash: 845834679bca274f1f2ca7a363b8a0681fb8f328
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215193"
---
# <a name="how-to-manage-symbols"></a>Postupy: Správa symbolů

Při vytváření nového objektu prostředku nebo prostředku mu vývojové prostředí přiřadí výchozí název symbolu, například `IDD_DIALOG1`. Můžete použít [okno Vlastnosti](/visualstudio/ide/reference/properties-window) ke změně výchozího názvu symbolu nebo ke změně názvu libovolného symbolu, který je už přidružený k prostředku.

Pro symboly přidružené k jednomu prostředku můžete také použít okno **vlastnosti** ke změně hodnoty symbolu. Pomocí [dialogového okna symboly prostředků](../windows/resource-symbols-dialog-box.md) můžete změnit hodnotu symbolů, které nejsou aktuálně přiřazeny k prostředku.

Normálně se všechny definice symbolů ukládají v `Resource.h`. Je ale možné, že budete muset změnit tento název souboru include, abyste mohli například pracovat s více než jedním souborem prostředků ve stejném adresáři.

> [!NOTE]
> Pokud projekt ještě neobsahuje soubor. RC, přečtěte si téma [Postupy: vytváření prostředků](../windows/how-to-create-a-resource-script-file.md).

## <a name="symbol-name-restrictions"></a>Omezení názvu symbolu

Omezení pro názvy symbolů jsou následující:

- Všechny [symboly](../windows/symbols-resource-identifiers.md) musí být jedinečné v rámci rozsahu aplikace, aby nedocházelo ke konfliktům definic symbolů v hlavičkových souborech.

- Platné znaky pro název symbolu zahrnují A-Z, a-z, 0-9 a podtržítka (_).

- Názvy symbolů nemůžou začínat číslicí a můžou být omezené na 247 znaků.

- Názvy symbolů nesmí obsahovat mezery.

- V názvech symbolů se nerozlišují velká a malá písmena, ale zachová se případ první definice symbolu.

   Hlavičkový soubor, který definuje symboly, je používán kompilátorem, C++ editorem nebo programem prostředků k odkazování na prostředky, které jsou definovány v souboru prostředků. U dvou názvů symbolů, které se liší pouze v případě C++ , program uvidí dva samostatné symboly, zatímco kompilátor prostředků nebo editor uvidí oba názvy jako odkazy na jeden jediný symbol.

> [!NOTE]
> Pokud nedodržujete standardní schéma názvu symbolu (ID * _ [klíčové slovo]) uvedené níže a váš název symbolu bude stejný jako klíčové slovo známé pro kompilátor skriptu prostředků, pokus o sestavení souboru skriptu prostředků bude mít za následek zdánlivou náhodnou generaci chyb. To se obtížně diagnostikuje. Aby k tomu nedocházelo, je nutné dodržovat standardní schéma pojmenování.

Názvy symbolů mají popisné předpony, které označují druh prostředku nebo objektu, který představují. Tyto popisné předpony začínají IDENTIFIKÁTORem kombinace textu. Knihovna Microsoft Foundation Class (MFC) používá konvence pojmenovávání symbolů, které jsou uvedeny v následující tabulce:

|Kategorie|Směr|Použití|
|--------------|------------|---------|
|Prostředky|IDR_, IDD_, IDC_, IDI_, IDB_|Akcelerátor nebo nabídka (a přidružené nebo vlastní prostředky), dialogové okno, kurzor, ikona, rastrový obrázek|
|Položky nabídky|ID_|Položka nabídky|
|Příkazy|ID_|Příkaz|
|Ovládací prvky a podřízená okna|IDC_|Řízení|
|Řetězce|IDS_|Řetězec v tabulce řetězců|
|MFC|AFX_|Vyhrazeno pro předdefinované symboly knihovny MFC|

### <a name="to-change-a-symbol-name-id"></a>Změna názvu symbolu (ID)

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources)vyberte prostředek.

1. V okně **vlastnosti** zadejte nový název symbolu nebo vyberte ze seznamu existujících symbolů v poli **ID** .

   Pokud zadáte nový název symbolu, automaticky se mu přiřadí hodnota.

> [!NOTE]
> Pomocí [dialogového okna symboly prostředků](../windows/resource-symbols-dialog-box.md) můžete změnit názvy symbolů, které nejsou aktuálně přiřazeny k prostředku.

## <a name="symbol-value-restrictions"></a>Omezení hodnoty symbolu

Hodnota symbolu může být libovolné celé číslo vyjádřené běžným způsobem pro `#define` direktivy preprocesoru. Tady je několik příkladů hodnot symbolů:

```
18
4001
0x0012
-3456
```

Hodnoty symbolů pro prostředky, jako jsou akcelerátory, bitmapy, kurzory, dialogová okna, ikony, nabídky, tabulky řetězců a informace o verzi, musí být desítková čísla v rozsahu od 0 do 32 767, ale nemohou být hexadecimální. Hodnoty symbolů pro části prostředků, jako jsou například ovládací prvky dialogového okna nebo jednotlivé řetězce v tabulce řetězců, mohou být od 0 do 65 534 nebo z-32 768 do 32 767. Další informace o rozsahech čísel naleznete v tématu [TN023: Standard MFC Resources](../mfc/tn023-standard-mfc-resources.md).

Symboly prostředků jsou 16bitová čísla. Můžete je zadat jako signed nebo bez znaménka, ale budou použity interně jako celá čísla bez znaménka, takže záporná čísla budou převedena na odpovídající kladnou hodnotu.

Mezi omezením hodnot symbolů patří:

- Vývojové prostředí sady Visual Studio a knihovna MFC používají pro zvláštní účely některé rozsahy čísel. Všechna čísla s nejvýznamnější bitovou sadou (-32 768 až-1 nebo 32 768 až 65 534, v závislosti na znaménku) jsou vyhrazena knihovnou MFC.

- Nelze definovat hodnotu symbolu pomocí jiných řetězců symbolů. Například následující definice symbolu není podporována:

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- Makra preprocesoru s argumenty nemůžete použít jako definice hodnot. Následující příklad není platným výrazem bez ohledu na to, co `ID` vyhodnotí v době kompilace:

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

- Vaše aplikace může mít existující soubor, který obsahuje symboly definované pomocí výrazů.

### <a name="to-change-a-symbol-value"></a>Změna hodnoty symbolu

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources)vyberte prostředek.

1. V okně **vlastnosti** zadejte název symbolu následovaný symbolem rovná se a celým číslem v poli **ID** , například:

    ```
    IDC_EDITNAME=5100
    ```

   Nová hodnota je uložena v souboru hlaviček symbolu při příštím uložení projektu. V poli ID zůstane viditelný pouze název symbolu a po ověření se nezobrazí znaménko rovná se a hodnota.

## <a name="change-or-delete-symbols"></a>Změna nebo odstranění symbolů

V [dialogovém okně symboly prostředků](../windows/resource-symbols-dialog-box.md)můžete upravit nebo odstranit existující symboly, které ještě nejsou přiřazené k prostředku nebo objektu.

### <a name="to-change-an-unassigned-symbol"></a>Změna nepřiřazeného symbolu

1. V poli **název** vyberte symbol Nepřiřazeno a zvolte možnost **změnit**.

1. Upravte název nebo hodnotu symbolu v polích, která jsou k dispozici v dialogovém okně **změnit symbol** .

> [!NOTE]
> Chcete-li změnit symbol, který je přiřazen prostředku nebo objektu, je nutné použít okno Editor prostředků nebo **vlastnosti** .

### <a name="to-delete-an-unassigned-unused-symbol"></a>Odstranění nepřiřazeného (nepoužívaného) symbolu

V dialogovém okně **symboly prostředků** vyberte symbol, který chcete odstranit, a zvolte **Odstranit**.

> [!NOTE]
> Před odstraněním nepoužívaného symbolu v souboru prostředků se ujistěte, že se nepoužívá jinde v programu nebo soubory prostředků, které jsou zahrnuty v době kompilace.

## <a name="include-symbols"></a>Zahrnout symboly

Když vývojové prostředí poprvé přečte soubor prostředků vytvořený jinou aplikací, označí všechny zahrnuté soubory hlaviček jako jen pro čtení. I když můžete použít [dialogové okno prostředek obsahuje](../windows/resource-includes-dialog-box.md) k přidání dalších souborů hlaviček symbolů jen pro čtení.

Jedním z důvodů, proč můžete chtít použít definice symbolů jen pro čtení, je pro soubory symbolů, které plánujete sdílet mezi několika projekty.

Zahrnuté soubory symbolů můžete také použít, pokud máte existující prostředky s definicemi symbolů, které používají výrazy místo jednoduchých celých čísel k definování hodnoty symbolu. Příklad:

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)
```

Prostředí bude tyto vypočtené symboly správně interpretovat, pokud:

- Počítané symboly jsou umístěny v souboru symbolů jen pro čtení.

- Váš soubor prostředků obsahuje prostředky, na které jsou tyto počítané symboly již přiřazeny.

- Očekává se numerický výraz.

> [!NOTE]
> Pokud se očekává řetězec nebo číselný výraz, výraz se nevyhodnotí.

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>Zahrnutí sdílených (jen pro čtení) symbolů do souboru prostředků

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources)klikněte pravým tlačítkem myši na soubor *. RC* a vyberte [prostředek zahrnuje](../windows/resource-includes-dialog-box.md).

1. V poli **direktivy symbolů jen pro čtení** Použijte direktivu `#include` kompilátoru k určení souboru, kam chcete zachovat symboly jen pro čtení.

   Nevolejte `Resource.h`souboru, protože se jedná o název souboru, který obvykle používá hlavní hlavičkový soubor symbolů.

   > [!NOTE]
   > Typ, který zadáte do pole **direktivy symbolů jen pro čtení** , se do souboru prostředků zahrne přesně tak, jak ho zadáte. Ujistěte se, že typ neobsahuje žádné pravopisné nebo syntaktické chyby.

   Chcete-li zahrnout soubory s definicemi symbolů, použijte pole **direktivy symbolů jen pro čtení** . Nezahrnovat definice prostředků, jinak se při uložení souboru vytvoří duplicitní definice prostředků.

1. Symboly umístěte do souboru, který jste zadali.

   Symboly v souborech, které jsou obsaženy v tomto způsobu, jsou vyhodnocovány při každém otevření souboru prostředků, ale při uložení souboru nejsou nahrazeny na disku.

1. Vyberte **OK**.

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Změna názvu souboru hlaviček symbolu prostředku

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources)klikněte pravým tlačítkem myši na soubor *. RC* a vyberte možnost [prostředek zahrnuje](../windows/resource-includes-dialog-box.md).

1. Do pole **soubor hlaviček symbolu** zadejte nový název souboru include.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Identifikátory prostředků (symboly)](../windows/symbols-resource-identifiers.md)<br/>
[Postupy: vytváření symbolů](../windows/creating-new-symbols.md)<br/>
[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)<br/>
