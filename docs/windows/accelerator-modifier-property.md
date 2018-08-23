---
title: Vlastnost modifikátoru akcelerátoru | Dokumentace Microsoftu
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
ms.openlocfilehash: 7e6750bfc0195eaaa350b829d1d899f648e9fe0e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592633"
---
# <a name="accelerator-modifier-property"></a>Vlastnost modifikátoru akcelerátoru

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

[Nastavení vlastností akcelerátoru](../windows/setting-accelerator-properties.md)  
[Editor akcelerátorů](../windows/accelerator-editor.md)