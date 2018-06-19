---
title: Vlastnost modifikátoru akcelerátoru | Microsoft Docs
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
ms.openlocfilehash: d99d4656f2835f9adb60f310e429c4ccb97ac7b6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854051"
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