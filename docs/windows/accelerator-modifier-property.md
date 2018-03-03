---
title: "Vlastnost modifikátoru akcelerátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Modifier property
ms.assetid: f05a9379-e037-4cfb-b6ef-d2c655bcfa7f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 63d6a4b526fc1f2aeb2a942e682a8c7cc6f9b58c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="accelerator-modifier-property"></a>Vlastnost modifikátoru akcelerátoru
Dále jsou právní položky pro vlastnost modifikátor v tabulce akcelerátorů.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|**None**|Uživatel stiskne pouze hodnotu klíče. Efektivní používá se s hodnoty ASCII nebo ANSI 001 až 026, který je interpretován jako ^ A prostřednictvím ^ Z (CTRL + A pomocí kombinace kláves CTRL-Z).|  
|**ALT**|Uživatel musí stisknutím klávesy ALT před hodnotu klíče.|  
|**CTRL**|Uživatel musí stisknutím klávesy CTRL před hodnotu klíče. Není platný typ ASCII.|  
|**Posunutí**|Uživatel musí stisknutím klávesy SHIFT před hodnotu klíče.|  
|**Ctrl + Alt**|Uživatel musí stiskněte klávesu CTRL a klávesu ALT před hodnotu klíče. Není platný typ ASCII.|  
|**Ctrl + Shift**|Uživatel musí stiskněte klávesu CTRL a SHIFT klíč před hodnotu klíče. Není platný typ ASCII.|  
|**Alt + Shift**|Uživatel musí stisknutím klávesy ALT a klávesu SHIFT před hodnotu klíče. Není platný typ ASCII.|  
|**Ctrl + Alt + Shift**|Uživatel musí stisknout klávesu CTRL, ALT a SHIFT před hodnotu klíče. Není platný typ ASCII.|  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Nastavení vlastností akcelerátoru](../windows/setting-accelerator-properties.md)   
 [Editor akcelerátorů](../windows/accelerator-editor.md)