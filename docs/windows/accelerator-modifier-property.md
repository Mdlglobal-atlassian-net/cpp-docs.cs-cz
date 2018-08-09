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
ms.openlocfilehash: 0788536e776661b9a84a6cccc648a7db68389ae5
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644252"
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