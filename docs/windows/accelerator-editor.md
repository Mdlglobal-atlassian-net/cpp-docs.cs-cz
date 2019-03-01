---
title: Editor akcelerátorů (C++)
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
ms.openlocfilehash: 21f588f6103195d9fe977d0b019b911b33f43105
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210832"
---
# <a name="accelerator-editor-c"></a>Editor akcelerátorů (C++)

Tabulky akcelerátorů je prostředek C++ Windows, který obsahuje seznam klávesy akcelerátoru (označované také jako klávesové zkratky) a identifikátory příkazů, které jsou s nimi spojeny. Program může mít více než jedné tabulky akcelerátoru.

Za normálních okolností akcelerátorů jsou použity jako klávesové zkratky pro příkazy programu, které jsou dostupné také na nabídku nebo panel nástrojů. Můžete však použít tabulky akcelerátorů k definování kombinace kláves pro příkazy, které nemají objekt uživatelského rozhraní k nim má přiřazené.

Můžete použít [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code) připojit klíče příkazy akcelerátoru ke kódu.

Seznam předdefinovaných klávesové zkratky, naleznete v tématu [klávesové zkratky](../windows/predefined-accelerator-keys.md).

> [!TIP]
> Při použití **Editor akcelerátorů**, klikněte pravým tlačítkem a zobrazit místní nabídku příkazů časté. Dostupné příkazy závisí na ukazatel odkazuje na.

> [!NOTE]
> Windows neumožňuje vytvářet tabulky prázdný akcelerátoru. Pokud jste se žádné položky tabulky akcelerátorů, je odstraněn automaticky při ukládání tabulky.

## <a name="accelerator-properties"></a>Vlastnosti akcelerátoru

Můžete nastavit vlastnosti akcelerátoru [okno vlastností](/visualstudio/ide/reference/properties-window) kdykoli. Můžete také použít **Editor akcelerátorů** k úpravě vlastností akcelerátoru v tabulce akcelerátorů. Změny provedené pomocí **vlastnosti** okno nebo **Editor akcelerátorů** mít stejný výsledek, změny se okamžitě projeví v tabulce akcelerátorů.

### <a name="id-property"></a>ID – vlastnost

**ID** vlastnost odkazuje na každého záznamu tabulky akcelerátorů v programovém kódu. Tato položka je hodnota příkazu, který program přijímá při stisknutí klávesy akcelerátoru nebo kombinace kláves. Ujistěte se, aby akcelerátoru stejný jako položku nabídky, jejich **ID** stejné, dokud **ID** akcelerátoru tabulka je stejné jako **ID** prostředku nabídky.

Existují tři vlastnosti pro každý akcelerátor **ID**: **Modifikátor**, **klíč**, a **typu**

#### <a name="modifier-property"></a>Vlastnost modifikátoru

**Modifikátor** vlastnost nastaví prvek kombinace kláves pro akcelerátor.

> [!NOTE]
> V **vlastnosti** okně **modifikátor** se zobrazí jako tři samostatné **logická** vlastnosti, které lze ovládat samostatně: **ALT**, **Ctrl**, a **Shift**.

Následují platné položky **modifikátor** vlastnost v tabulce akcelerátorů:

   |Hodnota|Popis|
   |-----------|-----------------|
   |**Žádné**|Jakmile uživatel stiskne pouze **klíč** hodnotu. Tato hodnota se nejefektivněji používá s hodnotami standardu ASCII a ANSI 001 prostřednictvím 026, což je interpretován jako ^ A až ^ Z (**Ctrl + A** prostřednictvím **Ctrl + Z**).|
   |**ALT**|Uživatel musí stisknout klávesu **Alt** před **klíč** hodnotu.|
   |**Ctrl**|Uživatel musí stisknout klávesu **Ctrl** před **klíč** hodnotu. Není platná s typem ASCII.|
   |**SHIFT**|Uživatel musí stisknout klávesu **Shift** před **klíč** hodnotu.|
   |**Ctrl+Alt**|Uživatel musí stisknout klávesu **Ctrl** a **Alt** před **klíč** hodnotu. Není platná s typem ASCII.|
   |**Ctrl+Shift**|Uživatel musí stisknout klávesu **Ctrl** a **Shift** před **klíč** hodnotu. Není platná s typem ASCII.|
   |**Alt + Shift**|Uživatel musí stisknout klávesu **Alt** a **Shift** před **klíč** hodnotu. Není platná s typem ASCII.|
   |**Ctrl+Alt+Shift**|Uživatel musí stisknout klávesu **Ctrl**, **Alt**, a **Shift** před **klíč** hodnotu. Není platná s typem ASCII.|

#### <a name="key-property"></a>Klíčová vlastnost

**Klíč** vlastnost nastaví skutečné klíč pro použití jako akcelerátor.

Následují platné položky **klíč** vlastnost v tabulce akcelerátorů:

   |Hodnota|Popis|
   |-----------|-----------------|
   |Celé číslo mezi 0 a 255 ve formátu desetinného čísla.|Hodnota určuje, zda hodnota je považován za ASCII a ANSI následujícím způsobem:<br/><br/>   -Jednociferné čísla jsou vždy interpretováno jako odpovídajícího klíče, nikoli jako hodnot ASCII a ANSI.<br/>   -Hodnoty 1 až 26, když párový příkaz nulami, jsou interpretovány jako ^ A až ^ Z, která představuje hodnotu ASCII písmena abecedy při stisknutí klávesy **Ctrl** klávesa stisknuta.<br/>   -Hodnoty z 27. až 32 jsou vždy interpretován jako trojmístný desetinné hodnoty 027 prostřednictvím 032.<br/>   -Hodnot z 033 až 255, ať už před uživatele 0 nebo nejsou vyhodnocena jako hodnoty ANSI.|
   |Klávesnice jeden znak.|Velká písmena A – Z nebo čísla 0 – 9 může být ASCII nebo virtuální hodnoty klíče. Jakýkoli jiný znak ASCII je pouze.|
   |Klávesnice jeden znak v rozsahu A – Z (velká písmena pouze) předchází znak stříšky (^).<br/><br/>Například ^ C.|Tato možnost zadá hodnotu ASCII klíče při stisknutí s **Ctrl** klávesa stisknuta.|
   |Libovolný platný identifikátor virtuální klávesy.|V rozevíracím seznamu **klíč** v tabulce akcelerátorů pole obsahuje seznam identifikátorů standardní virtuální klíče.|

> [!NOTE]
> Při zadávání hodnotu ASCII **modifikátor** vlastnost možnosti jsou omezené. Je pouze klávesu CTRL k dispozici pro použití **Alt** klíč.

> [!TIP]
> Zástupce pro definování klíče akcelerátoru k je klikněte pravým tlačítkem na položku nebo více položek v tabulce akcelerátorů. Zvolte **další stisknutá klávesa** a stisknutím klávesy nebo kombinace kláves na klávesnici.
>
> **Další stisknutá klávesa** příkazu je také k dispozici **upravit** nabídky.

#### <a name="type-property"></a>Typ vlastnosti

**Typ** vlastnost určuje, zda klávesovou zkratku přidružený akcelerátor **ID** je interpretován jako hodnotu klíče ASCII a ANSI nebo kombinaci virtuální klávesy. (VIRTKEY).

- Pokud **typ** vlastnost **ASCII**, **modifikátor** vlastnosti můžou být jenom `None` nebo `Alt`, nebo může mít akcelerátor, který používá **Ctrl** klíč (určený klíč s předchozím `^`).

- Pokud **typ** vlastnost **VIRTKEY**, libovolnou kombinaci **modifikátor** a **klíč** hodnoty je platný.

> [!NOTE]
> Pokud chcete zadat hodnotu do tabulky akcelerátorů a mají hodnotu považován za ASCII a ANSI, vyberte **typ** pro položku v tabulce a vybrat **ASCII** z rozevíracího seznamu. Ale pokud používáte **další stisknutá klávesa** příkaz **upravit** nabídek k určení **klíč**, musíte změnit **typ** vlastnost z **VIRTKEY** k **ASCII** *před* zadávání **klíč** kódu.

## <a name="accelerator-tables"></a>Tabulek akcelerátorů

V projektu v jazyce C++ můžete upravit přímo s místní úpravy. v tabulky akcelerátorů **Editor akcelerátorů**.

Použití standardních stránkách vlastností najdete v níže uvedených postupech, ale úpravy na místě a metoda stránka Vlastnosti mít stejný výsledek. Změny provedené pomocí stránky vlastností nebo pomocí úpravy na místě se okamžitě projeví v tabulce akcelerátorů.

Úprava v tabulce akcelerátorů:

1. Otevřete poklepáním na ikonu v tabulce akcelerátorů [zobrazení prostředků](../windows/resource-view-window.md).

1. Vyberte položku v tabulce a vybrat, zda chcete aktivovat místní úpravy.

1. Vyberte z rozevíracího seznamu nebo zadejte místo, kde můžete provádět změny:

   - Pro **ID**, vyberte ze seznamu nebo typu, který chcete upravit.

   - Pro **modifikátor**, vyberte ze seznamu.

   - Pro **klíč**, vyberte ze seznamu nebo typu, který chcete upravit.

   - Pro **typ**vyberte **ASCII** nebo **VIRTKEY** ze seznamu.

Vyhledání položky v tabulce akcelerátorů otevřít:

1. Otevřete poklepáním na ikonu v tabulce akcelerátorů [zobrazení prostředků](../windows/resource-view-window.md).

1. Vyberte sloupec head k řazení obsahu sloupce podle abecedy. Vyberte například **ID** zobrazíte všechna ID v tabulce akcelerátorů podle abecedy.

   Potom můžete vyhledat v seznamu a vyhledejte položku.

Chcete-li přidat položku do tabulky akcelerátorů:

1. Otevřete poklepáním na ikonu v tabulce akcelerátorů [zobrazení prostředků](../windows/resource-view-window.md).

1. Klikněte pravým tlačítkem v tabulce akcelerátorů a zvolte **nový akcelerátor** z místní nabídky, nebo vyberte položku prázdný řádek v tabulce dole.

1. Vyberte **ID** z rozevíracího seznamu v **ID** pole nebo zadejte nový *ID* v **ID** pole.

1. Typ *klíč* chcete použít jako akcelerátor, nebo klikněte pravým tlačítkem a zvolte **další stisknutá klávesa** z místní nabídky nastavení kombinaci kláves, nebo přejděte do nabídky **upravit**  >  **Další stisknutá klávesa**.

1. Změnit **modifikátor** a **typ**, v případě potřeby a stiskněte klávesu **Enter**.

   > [!NOTE]
   > Ujistěte se, že se všechny akcelerátory, které definujete. Může mít několik kombinace kláves, které jsou přiřazeny stejnému identifikátoru s neplatí výplně, například **Ctrl**+**P** a **F8** lze obě přiřadit ID_PRINT. Však mít přiřazeno více než jeden ID nebude fungovat dobře, například kombinaci kláves **Ctrl**+**Z** přiřazená ID_SPELL_CHECK a ID_THESAURUS.

Chcete-li odstranit záznam z tabulky akcelerátorů:

1. Otevřete poklepáním na ikonu v tabulce akcelerátorů [zobrazení prostředků](../windows/resource-view-window.md).

1. Vyberte položku, kterou chcete odstranit nebo podržte stisknutou klávesu **Ctrl** nebo **Shift** klíče při výběru k výběru více položek.

1. Klikněte pravým tlačítkem a zvolte **odstranit**, nebo přejděte do nabídky **upravit** > **odstranit**.

> [!TIP]
> Odstranit zástupce je stisknutím klávesy **odstranit** klíč.

Přesunutí nebo kopírování záznamu tabulky akcelerátorů do jiného souboru skriptu prostředků:

1. Otevřete v tabulkách akcelerátoru v obou souborů skriptu prostředků a vyberte položku, kterou chcete přesunout.

1. Z **upravit** nabídce zvolte **kopírování** nebo **Vyjmout**.

1. Vyberte položku v cílovém souboru skriptu prostředků a od **upravit** nabídce zvolte **vložit**.

> [!NOTE]
> Můžete také použít klávesové zkratky pro kopírování a vkládání.

Změna vlastností vícenásobných kláves akcelerátoru:

1. Otevřete poklepáním na ikonu v tabulce akcelerátorů [zobrazení prostředků](../windows/resource-view-window.md).

1. Vyberte klávesy akcelerátoru chcete změnit tím, že se **Ctrl** klíče při výběru každé z nich.

1. Přejděte [okno vlastností](/visualstudio/ide/reference/properties-window) a zadejte hodnoty, které chcete všechny vybrané akcelerátorů sdílet.

> [!NOTE]
> Každá hodnota modifikátor se zobrazí jako vlastnost typu Boolean v **vlastnosti** okna. Pokud změníte [modifikátor](../windows/accelerator-modifier-property.md) hodnotu **vlastnosti** okně tabulky akcelerátorů považuje za new – modifikátor doplněk žádné modifikátory, které byly dříve. Z tohoto důvodu Pokud nastavíte všechny hodnoty modifikátor, musíte nastavit všechny z nich zajistit, že každý akcelerátor sdílí stejný **modifikátor** nastavení.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)<br/>
[Klávesy akcelerátoru](../windows/predefined-accelerator-keys.md)<br/>