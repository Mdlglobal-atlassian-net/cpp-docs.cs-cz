---
title: Vlastnost klávesy akcelerátoru (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Key property
ms.assetid: d1570cd9-b414-4cd6-96bd-47c38281eaca
ms.openlocfilehash: 0649917900610b8a45c59de05c031ca36d6fcc91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529174"
---
# <a name="accelerator-key-property-c"></a>Vlastnost klávesy akcelerátoru (C++)

Následují platné položky pro vlastnost klíče v tabulce akcelerátorů:

- Celé číslo mezi 0 a 255 ve formátu desetinného čísla. Hodnota určuje, zda hodnota je považován za ASCII a ANSI následujícím způsobem:

   - Jednociferné čísla jsou vždy interpretováno jako odpovídajícího klíče, nikoli jako hodnot ASCII a ANSI.

   - Hodnoty 1 až 26, když párový příkaz nulami, jsou interpretovány jako ^ A až ^ Z, která představuje hodnotu ASCII písmena abecedy při stisknutí klávesy **Ctrl** klávesa stisknuta.

   - Hodnoty z 27. až 32 jsou vždy interpretovány jako trojmístný desetinné hodnoty 027 prostřednictvím 032.

   - Hodnoty z 033 až 255, zda předchází uživatele 0 nebo nejsou vyhodnocena jako hodnoty ANSI.

- Klávesnice jeden znak. Velká písmena A – Z nebo čísla 0 – 9 může být ASCII nebo virtuální klíčových hodnot. jakýkoli jiný znak ASCII je pouze.

- Klávesnice jeden znak v rozsahu A – Z (velká písmena pouze) předchází znak stříšky (^) (například ^ C). To vstupuje do ASCII hodnotu klíče, pokud se stiskne s **Ctrl** klávesa stisknuta.

   > [!NOTE]
   > Při zadávání hodnotu ASCII, jsou omezené možnosti modifikátor vlastností. Je pouze klávesu CTRL k dispozici pro použití **Alt** klíč.

- Libovolný platný identifikátor virtuální klávesy. Pole rozevíracího seznamu klíče v tabulce akcelerátorů obsahuje seznam identifikátorů standardní virtuální klíče.

   > [!TIP]
   > Klikněte pravým tlačítkem na položku nebo více položek v tabulce akcelerátorů, zvolte je další způsob, jak definovat klíče akcelerátoru k **další stisknutá klávesa** z místní nabídky a stiskněte klávesy nebo kombinace kláves na klávesnici. **Další stisknutá klávesa** příkazu je také k dispozici **upravit** nabídky.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Nastavení vlastností akcelerátoru](../windows/setting-accelerator-properties.md)<br/>
[Úprava v tabulce akcelerátorů](../windows/editing-in-an-accelerator-table.md)<br/>
[Editor akcelerátorů](../windows/accelerator-editor.md)