---
title: Nastavení vlastností akcelerátoru (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
- VIRTKEY
- Key property
- ID property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
ms.openlocfilehash: e1fac31635b7ccc09f9c184cf734fa4f7717cb97
ms.sourcegitcommit: 5beace7dcc6bf0e8b8cc96a930e7424f9daa05cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232133"
---
# <a name="setting-accelerator-properties"></a>Nastavení vlastností akcelerátoru

Můžete nastavit vlastnosti akcelerátoru [okno vlastností](/visualstudio/ide/reference/properties-window) kdykoli. Můžete také použít [editor akcelerátorů](../windows/accelerator-editor.md) k úpravě vlastností akcelerátoru v tabulce akcelerátorů. Změny provedené pomocí **vlastnosti** okno nebo **akcelerátoru** editor mít stejný výsledek: úpravy se okamžitě projeví v tabulce akcelerátorů.

## <a name="id-property"></a>ID – vlastnost

**ID** vlastnost odkazuje na každého záznamu tabulky akcelerátorů v programovém kódu. Tato položka je hodnota příkazu, který program se zobrazí, když uživatel stiskne klávesu akcelerátoru nebo kombinace kláves. Chcete-li akcelerátoru, stejně jako položku nabídky, ujistěte se, jejich ID stejné (Pokud je ID tabulky akcelerátorů stejné jako ID prostředku nabídky).

Existují tři vlastnosti každé ID akcelerátoru: **modifikátor** vlastnost, **klíč** vlastnost a **typ** vlastnost.

## <a name="modifier-property"></a>Modifikátor – vlastnost

**Modifikátor** vlastnost nastaví prvek kombinace kláves pro akcelerátor.

> [!NOTE]
> V **vlastnosti** okna, tato vlastnost se zobrazí jako tři samostatné **logická** vlastnosti, které lze ovládat samostatně: **ALT**, **Ctrl**, a **Shift**.

Následují platné položky **modifikátor** vlastnost v tabulce akcelerátorů:

   |Hodnota|Popis|
   |-----------|-----------------|
   |**Žádné**|Jakmile uživatel stiskne pouze **klíč** hodnotu. Tato hodnota se nejefektivněji používá s hodnotami standardu ASCII a ANSI 001 prostřednictvím 026, což je interpretován jako ^ A až ^ Z (**Ctrl + A** prostřednictvím **Ctrl + Z**).|
   |**ALT**|Uživatel musí stisknout klávesu **Alt** klíče před **klíč** hodnotu.|
   |**Ctrl**|Uživatel musí stisknout klávesu **Ctrl** klíče před **klíč** hodnotu. Není platná s typem ASCII.|
   |**SHIFT**|Uživatel musí stisknout klávesu **Shift** klíče před **klíč** hodnotu.|
   |**Ctrl+Alt**|Uživatel musí stisknout klávesu **Ctrl** klíč a **Alt** klíče před **klíč** hodnotu. Není platná s typem ASCII.|
   |**Ctrl+Shift**|Uživatel musí stisknout klávesu **Ctrl** klíč a **Shift** klíče před **klíč** hodnotu. Není platná s typem ASCII.|
   |**Alt + Shift**|Uživatel musí stisknout klávesu **Alt** klíč a **Shift** klíče před **klíč** hodnotu. Není platná s typem ASCII.|
   |**Ctrl+Alt+Shift**|Uživatel musí stisknout klávesu **Ctrl**, **Alt**, a **Shift** před **klíč** hodnotu. Není platná s typem ASCII.|

## <a name="key-property"></a>Klíč – vlastnost

**Klíč** vlastnost nastaví skutečné klíč pro použití jako akcelerátor.

Následují platné položky **klíč** vlastnost v tabulce akcelerátorů:

   |Hodnota|Popis|
   |-----------|-----------------|
   |Celé číslo mezi 0 a 255 ve formátu desetinného čísla.|Hodnota určuje, zda hodnota je považován za ASCII a ANSI následujícím způsobem:<br/><br/>-Jednociferné čísla jsou vždy interpretováno jako odpovídajícího klíče, nikoli jako hodnot ASCII a ANSI.<br/>-Hodnoty 1 až 26, když párový příkaz nulami, jsou interpretovány jako ^ A až ^ Z, která představuje hodnotu ASCII písmena abecedy při stisknutí klávesy **Ctrl** klávesa stisknuta.<br/>-Hodnoty z 27. až 32 jsou vždy interpretován jako trojmístný desetinné hodnoty 027 prostřednictvím 032.<br/>-Hodnot z 033 až 255, ať už před uživatele 0 nebo nejsou vyhodnocena jako hodnoty ANSI.|
   |Klávesnice jeden znak.|Velká písmena A – Z nebo čísla 0 – 9 může být ASCII nebo virtuální klíčových hodnot. jakýkoli jiný znak ASCII je pouze.|
   |Klávesnice jeden znak v rozsahu A – Z (velká písmena pouze) předchází znak stříšky (^) (například ^ C).|Tato možnost zadá hodnotu ASCII klíče při stisknutí s **Ctrl** klávesa stisknuta.|
   |Libovolný platný identifikátor virtuální klávesy.|Pole rozevíracího seznamu klíče v tabulce akcelerátorů obsahuje seznam identifikátorů standardní virtuální klíče.|

> [!NOTE]
> Při zadávání hodnotu ASCII, jsou omezené možnosti modifikátor vlastností. Je pouze klávesu CTRL k dispozici pro použití **Alt** klíč.

> [!TIP]
> Klikněte pravým tlačítkem na položku nebo více položek v tabulce akcelerátorů, zvolte je další způsob, jak definovat klíče akcelerátoru k **další stisknutá klávesa** z místní nabídky a stiskněte klávesy nebo kombinace kláves na klávesnici. **Další stisknutá klávesa** příkazu je také k dispozici **upravit** nabídky.

## <a name="type-property"></a>Typ – vlastnost

**Typ** vlastnost určuje, zda kombinaci kláves přidružené k ID akcelerátoru je interpretován jako hodnotu klíče ASCII a ANSI nebo kombinaci virtuální klávesy. (VIRTKEY).

- Pokud **typ** ASCII, je vlastnost **modifikátor** vlastnosti můžou být jenom `None` nebo `Alt`, nebo může mít akcelerátor, který používá **Ctrl** klíče () určený klíč s předchozím `^`).

- Pokud **typ** vlastnost je VIRTKEY libovolnou kombinaci `Modifier` a `Key` hodnoty je platný.

> [!NOTE]
> Pokud chcete zadat hodnotu do tabulky akcelerátorů a mají hodnotu považovat za ASCII a ANSI, jednoduše klikněte na tlačítko **typ** pro položku v tabulce a z rozevíracího seznamu vyberte ASCII. Ale pokud použijete **další stisknutá klávesa** příkazu (**upravit** nabídky) k určení `Key`, musíte změnit **typ** vlastnost z VIRTKEY ASCII *před* zadávání `Key` kódu.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Úprava v tabulce akcelerátorů](../windows/editing-in-an-accelerator-table.md)<br/>
[Předdefinované klávesy akcelerátoru](../windows/predefined-accelerator-keys.md)<br/>
[Editory prostředků](../windows/resource-editors.md)<br/>
