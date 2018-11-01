---
title: Vlastnost modifikátoru akcelerátoru (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
ms.openlocfilehash: f9dfcbde68d2b3d1ebdd1b94aa40339bbc0ff4e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650671"
---
# <a name="accelerator-modifier-property-c"></a>Vlastnost modifikátoru akcelerátoru (C++)

Následují platné položky pro vlastnost modifikátor v tabulce akcelerátorů.

|Hodnota|Popis|
|-----------|-----------------|
|**None**|Jakmile uživatel stiskne pouze **klíč** hodnotu. Co nejefektivnějšímu používá se s hodnotami standardu ASCII a ANSI 001 prostřednictvím 026, což je interpretován jako ^ A až ^ Z (CTRL-A pomocí CTRL-Z).|
|**ALT**|Uživatel musí stisknout klávesu **Alt** klíče před **klíč** hodnotu.|
|**CTRL**|Uživatel musí stisknout klávesu **Ctrl** klíče před **klíč** hodnotu. Není platná s typem ASCII.|
|**SHIFT**|Uživatel musí stisknout klávesu **Shift** klíče před **klíč** hodnotu.|
|**Ctrl + Alt**|Uživatel musí stisknout klávesu **Ctrl** klíč a **Alt** klíče před **klíč** hodnotu. Není platná s typem ASCII.|
|**Ctrl + Shift**|Uživatel musí stisknout klávesu **Ctrl** klíč a **Shift** klíče před **klíč** hodnotu. Není platná s typem ASCII.|
|**Alt + Shift**|Uživatel musí stisknout klávesu **Alt** klíč a **Shift** klíče před **klíč** hodnotu. Není platná s typem ASCII.|
|**Ctrl + Alt + Shift**|Uživatel musí stisknout klávesu **Ctrl**, **Alt**, a **Shift** před **klíč** hodnotu. Není platná s typem ASCII.|

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Nastavení vlastností akcelerátoru](../windows/setting-accelerator-properties.md)<br/>
[Editor akcelerátorů](../windows/accelerator-editor.md)