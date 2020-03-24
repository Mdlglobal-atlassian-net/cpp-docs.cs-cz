---
title: Editor akcelerátorůC++()
ms.date: 02/14/2019
f1_keywords:
- vc.editors.accelerator.F1
- vc.editors.accelerator
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [C++], accelerator key
- accelerator keys [C++]
- resource editors [C++], Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
- VIRTKEY
- Key property
- ID property
- accelerator tables [C++], editing
- keyboard shortcuts [C++], editing in an accelerator table
- searching, in accelarator tables
- accelerator tables [C++], finding entries
- accelerator tables [C++], adding entries
- New Accelerator command
- accelerator tables [C++], deleting entries
- keyboard shortcuts [C++], deleting entry from accelerator table
- accelerator tables [C++], copying entries
- rc files [C++], moving an accelerator table entry
- .rc files [C++], moving accelerator table entries
- accelerator tables [C++], moving entries
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
ms.openlocfilehash: 80ef6cc9ec956d0041c4aa3fb6a6211868cc9d73
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167560"
---
# <a name="accelerator-editor-c"></a>Editor akcelerátorůC++()

Tabulka akcelerátorů je prostředek C++ systému Windows, který obsahuje seznam klávesových zkratek nazývaných klávesových zkratek a identifikátorů příkazů, které jsou k nim přidruženy. Program může mít více než jednu tabulku akcelerátorů.

Akcelerátory se standardně používají jako klávesové zkratky pro příkazy programu, které jsou také k dispozici v nabídce nebo na panelu nástrojů. Tabulku akcelerátorů však můžete použít k definování kombinací kláves pro příkazy, které nemají přidružený objekt uživatelského rozhraní.

> [!TIP]
> Pokud používáte **Editor akcelerátorů**, klikněte pravým tlačítkem myši a zobrazte místní nabídku s častými příkazy. Dostupné příkazy závisí na tom, na čemu ukazatel odkazuje.

Můžete použít [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code) k připojení příkazů akcelerátorového klíče ke kódu. Seznam předdefinovaných klávesových zkratek najdete v tématu [klávesy akcelerátoru](../windows/predefined-accelerator-keys.md).

> [!NOTE]
> Windows neumožňuje vytvářet prázdné tabulky akcelerátorů. Pokud vytvoříte tabulku akcelerátorů bez zadání, odstraní se automaticky při uložení tabulky.

## <a name="accelerator-properties"></a>Vlastnosti akcelerátoru

Vlastnosti akcelerátoru můžete v [okno Vlastnosti](/visualstudio/ide/reference/properties-window) kdykoli nastavit. **Editor akcelerátorů** můžete použít také k úpravě vlastností akcelerátoru v tabulce akcelerátorů. Změny provedené v okně **vlastnosti** nebo **editoru akcelerátorů** mají stejný výsledek, úpravy se v tabulce akcelerátorů projeví okamžitě.

Vlastnost **ID** odkazuje na každý záznam tabulky akcelerátoru v programovém kódu. Tato položka je hodnota příkazu, kterou program obdrží, když uživatel stiskne klávesovou zkratku nebo kombinaci kláves. Chcete-li, aby byl akcelerátor stejný jako položka nabídky, změňte **ID** stejným způsobem, pokud je **ID** tabulky akcelerátorů stejné jako **ID** pro prostředek nabídky.

Každé **ID** akcelerátoru má tři vlastnosti: **Modifikátor**, **klíč**a **typ** .

Vlastnost **modifikátoru** nastavuje kombinace kláves ovládacího prvku pro akcelerátor.

> [!NOTE]
> V okně **vlastnosti** je vlastnost **modifikátoru** zobrazená jako tři samostatné **logické** vlastnosti, kterou lze ovládat nezávisle: **ALT**, **CTRL**a **SHIFT**.

Níže jsou uvedené platné položky pro vlastnost **Modifikátor** v tabulce akcelerátorů:

   |Hodnota|Popis|
   |-----------|-----------------|
   |**NTato**|Uživatel stiskne pouze hodnotu **klíče** .<br/><br/>Tato hodnota se nejúčinnějším způsobem používá pro hodnoty ASCII/ANSI 001 až 026, která je interpretována jako ^ A až ^ Z (**CTRL + A** prostřednictvím **CTRL + Z**).|
   |**ALT**|Uživatel musí stisknout klávesu **ALT** před hodnotou **klíče** .|
   |**Podržte**|Uživatel musí stisknout **klávesu CTRL** před hodnotou **klíče** , není platný s typem ASCII.|
   |**Posouvá**|Uživatel musí před hodnotou **klíče** stisknout klávesu **SHIFT** .|
   |**CTRL + ALT**|Uživatel musí stisknout **kombinaci kláves CTRL** a **ALT** před hodnotou **klíče** , není platný s typem ASCII.|
   |**CTRL + SHIFT**|Uživatel musí stisknout **kombinaci kláves CTRL** a **SHIFT** před hodnotou **klíče** , není platný s typem ASCII.|
   |**ALT + SHIFT**|Uživatel musí stisknout klávesu **ALT** a **SHIFT** před hodnotou **klíče** , který není platný pro typ ASCII.|
   |**CTRL + ALT + SHIFT**|Uživatel musí stisknout **kombinaci kláves CTRL**, **ALT**a **SHIFT** před hodnotou **klíče** , není platný s typem ASCII.|

**Klíčová** vlastnost nastavuje skutečný klíč, který se má použít jako akcelerátor.

Níže jsou uvedené platné položky pro **klíčovou** vlastnost v tabulce akcelerátorů:

   |Hodnota|Popis|
   |-----------|-----------------|
   |Celé číslo mezi 0 a 255 v desítkovém formátu.|Hodnota určuje, zda je hodnota považována za ASCII nebo ANSI následujícím způsobem:<br/><br/>   – Jednociferné číslice se vždycky interpretují jako odpovídající klíč, nikoli jako hodnoty ASCII nebo ANSI.<br/>   -Hodnoty od 1 do 26, pokud předcházejí nula, se interpretují jako ^ A až ^ Z, který představuje hodnotu ASCII písmen abecedy při stisknutí klávesy **CTRL** .<br/>   -Hodnoty z 27-32 jsou vždy interpretovány jako desítkové hodnoty se třemi číslicemi 027 až 032.<br/>   -Hodnoty od 033 do 255, ať už předcházejí 0 nebo not, se interpretují jako hodnoty ANSI.|
   |Jeden znak klávesnice.|Velká písmena A – Z nebo čísla 0-9 mohou být hodnoty ASCII nebo hodnoty virtuálního klíče. Jakýkoli jiný znak je pouze ASCII.|
   |Jedna klávesa v rozsahu A – Z (jenom velká písmena), před kterou předchází blikající znak stříšky (^), například ^ C.|Tato možnost zadá hodnotu ASCII klíče při stisknutí klávesy **CTRL** .|
   |Libovolný platný identifikátor virtuálního klíče.|**Pole rozevíracího seznamu v** tabulce akcelerátorů obsahuje seznam identifikátorů Standard Virtual Key.|

> [!NOTE]
> Při zadávání hodnoty ASCII jsou možnosti vlastností **modifikátoru** omezené. Jediný řídicí klíč, který je k dispozici pro použití, je klávesa **ALT** .

> [!TIP]
> Klávesová zkratka pro definování klávesových zkratek: klikněte pravým tlačítkem myši na položku nebo na několik záznamů v tabulce akcelerátorů, zvolte možnost **Další typ klávesy** a stiskněte libovolnou klávesu nebo kombinaci kláves na klávesnici.
>
> Tento příkaz **dalšího typu klíče** je k dispozici také v nabídce **Upravit** .

Vlastnost **Type** určuje, zda kombinace klávesových zkratek přidružených k **ID** akcelerátoru je interpretována jako hodnota klíče ASCII/ANSI nebo kombinace virtuálního klíče (VIRTKEY).

- Je-li vlastnost **Type** nastavena na hodnotu **ASCII**, vlastnost **Modifikátor** může být pouze `None` nebo `Alt`nebo může mít akcelerátor, který používá klávesu **CTRL** , jak je uvedeno před klíčem pomocí `^`.

- Pokud je vlastnost **Type** **VIRTKEY**, jakákoli kombinace **modifikátoru** a **klíčových** hodnot je platná.

> [!NOTE]
> Chcete-li zadat hodnotu do tabulky akcelerátorů a hodnotu, která bude zpracována jako ASCII/ANSI, vyberte **typ** položky v tabulce a v rozevíracím seznamu vyberte možnost **ASCII** . Pokud však použijete příkaz **Next Key** Type z nabídky **Upravit** k zadání **klíče**, je nutné *před* zadáním kódu **klíče** změnit vlastnost **Type** z **VIRTKEY** na **ASCII** .

## <a name="accelerator-tables"></a>Tabulky akcelerátorů

V C++ projektu můžete upravit tabulku akcelerátorů přímo pomocí místních úprav v **editoru akcelerátorů**.

Níže uvedené postupy odkazují na použití standardních vlastností stránky, ale v místních úpravách i v metodě stránky vlastností mají stejný výsledek. Změny provedené pomocí stránek vlastností nebo pomocí místních úprav se okamžitě projeví v tabulce akcelerátorů.

### <a name="to-edit-in-an-accelerator-table"></a>Úprava v tabulce akcelerátorů

1. Dvojitým kliknutím na ikonu v [prostředky](how-to-create-a-resource-script-file.md#create-resources)otevřete tabulku akcelerátorů.

1. Vyberte položku v tabulce a vyberte možnost aktivace místních úprav.

1. Vyberte z rozevíracího seznamu nebo zadejte místo, kde chcete provádět změny:

   - V poli **ID**vyberte ze seznamu nebo zadejte text, který chcete upravit.

   - V části **Modifikátor**vyberte ze seznamu.

   - V poli **klíč**vyberte ze seznamu nebo zadejte text, který chcete upravit.

   - V seznamu **typ**vyberte **ASCII** nebo **VIRTKEY** .

### <a name="to-find-an-entry-in-an-open-accelerator-table"></a>Vyhledání položky v otevřené tabulce akcelerátorů

1. Dvojitým kliknutím na ikonu v [prostředky](how-to-create-a-resource-script-file.md#create-resources)otevřete tabulku akcelerátorů.

1. Vyberte záhlaví sloupce, chcete-li obsah sloupce seřadit podle abecedy. Vyberte například **ID** , chcete-li zobrazit všechna ID v tabulce akcelerátorů abecedně.

   Potom můžete seznam vyhledat a najít položku.

### <a name="to-add-an-entry-to-an-accelerator-table"></a>Přidání položky do tabulky akcelerátorů

1. Dvojitým kliknutím na ikonu v [prostředky](how-to-create-a-resource-script-file.md#create-resources)otevřete tabulku akcelerátorů.

1. Klikněte pravým tlačítkem myši do tabulky akcelerátoru a vyberte možnost **Nový akcelerátor**, nebo v dolní části tabulky vyberte položku prázdného řádku.

1. V rozevíracím seznamu v poli **ID** vyberte **ID** nebo do pole **ID** zadejte nové *ID* .

1. Zadejte *klíč* , který chcete použít jako akcelerátor, nebo klikněte pravým tlačítkem myši a vyberte klávesu **Další** , abyste nastavili kombinaci kláves, nebo přejděte na nabídku **Upravit** > **Další zadaný klíč**.

1. V případě potřeby změňte **Modifikátor** a **typ**a stiskněte klávesu **ENTER**.

> [!NOTE]
> Ujistěte se, že všechny akcelerátory, které definujete, jsou jedinečné. Ke stejnému ID může být přiřazeno několik kombinací kláves bez navýšení účinku, například **Ctrl**+**P** a **F8** lze přiřadit ID_PRINT. Nicméně kombinace kláves přiřazených k více než jednomu ID nebude správně fungovat, například **Ctrl**+**Z** přiřazená k ID_SPELL_CHECK a ID_THESAURUS.

### <a name="to-delete-an-entry-from-an-accelerator-table"></a>Odstranění položky z tabulky akcelerátorů

1. Dvojitým kliknutím na ikonu v [prostředky](how-to-create-a-resource-script-file.md#create-resources)otevřete tabulku akcelerátorů.

1. Vyberte položku, kterou chcete odstranit, nebo podržte stisknutou **klávesu CTRL** nebo **SHIFT** a při výběru vyberte více položek.

1. Klikněte pravým tlačítkem myši a vyberte **Odstranit**nebo přejděte do nabídky **Upravit** > **Odstranit**.

> [!TIP]
> Můžete také stisknout klávesu **Delete** a odstranit ji.

### <a name="to-move-or-copy-an-accelerator-table-entry-to-another-resource-script-file"></a>Přesunutí nebo zkopírování položky tabulky akcelerátorů do jiného souboru skriptu prostředků

1. Otevřete tabulky akcelerátorů v souborech skriptu prostředků a vyberte položku, kterou chcete přesunout.

1. V nabídce **Úpravy** klikněte na příkaz **Kopírovat** nebo **Vyjmout**.

1. Vyberte položku v souboru skriptu cílového prostředku a v nabídce **Upravit** zvolte možnost **Vložit**.

> [!NOTE]
> Pro kopírování a vkládání můžete také použít klávesové zkratky.

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Změna vlastností vícenásobných kláves akcelerátoru

1. Dvojitým kliknutím na ikonu v [prostředky](how-to-create-a-resource-script-file.md#create-resources)otevřete tabulku akcelerátorů.

1. Vyberte klávesy akcelerátoru, které chcete změnit, a podržením klávesy **CTRL** při výběru každého z nich.

1. Přejít na [okno Vlastnosti](/visualstudio/ide/reference/properties-window) a zadejte hodnoty, které mají všechny vybrané akcelerátory sdílet.

> [!NOTE]
> Každá hodnota modifikátoru se zobrazí jako logická vlastnost v okně **vlastnosti** . Změníte-li hodnotu [modifikátoru](../windows/accelerator-modifier-property.md) v okně **vlastnosti** , zpracuje tabulka akcelerátoru nový modifikátor jako doplněk k jakýmkoli modifikátorům, které dříve existovaly. Z tohoto důvodu, pokud nastavíte hodnoty modifikátoru, je třeba nastavit všechny, aby se zajistilo, že všechny akcelerátory sdílí stejné nastavení **modifikátorů** .

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)<br/>
[Klávesy akcelerátoru](../windows/predefined-accelerator-keys.md)<br/>
