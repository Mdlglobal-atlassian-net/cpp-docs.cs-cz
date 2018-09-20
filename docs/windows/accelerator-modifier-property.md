---
title: Vlastnost modifikátoru akcelerátoru (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3c053af58842c75910b0214ae828c652daa33a81
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389288"
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