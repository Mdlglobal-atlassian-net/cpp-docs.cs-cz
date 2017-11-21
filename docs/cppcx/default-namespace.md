---
title: "výchozí obor názvů | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 9d1c04acc5754627906448db9ac4f3afd65fbe7c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="default-namespace"></a>výchozí obor názvů
`default` Obor názvů rozsahy vestavěné typy, které jsou podporovány C + +/ CX.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace default;  
```  
  
### <a name="members"></a>Členové  
 Všechny vestavěné typy dědit následující členy.  
  
|||  
|-|-|  
|[Výchozí:: (type_name):: rovná se](../cppcx/default-type-name-equals-method.md)|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.|  
|[Výchozí:: (type_name):: GetHashCode](../cppcx/default-type-name-gethashcode-method.md)|Vrátí kód hash této instance.|  
|[Výchozí:: (type_name):: GetType](../cppcx/default-type-name-gettype-method.md)|Vrátí řetězec, který představuje aktuální typ.|  
|[Výchozí:: (type_name):: ToString](../cppcx/default-type-name-tostring-method.md)|Vrátí řetězec, který představuje aktuální typ.|  
  
### <a name="built-in-types"></a>Vestavěné typy  
  
|Název|Popis|  
|----------|-----------------|  
|`char16`|Hodnota číselného typu 16bitové, který představuje bod kódování Unicode (UTF-16).|  
|`float32`|IEEE 754 32-bit s plovoucí desetinnou čárkou číslo.|  
|`float64`|IEEE 754 64-bit s plovoucí desetinnou čárkou číslo.|  
|`int16`|16bitové znaménkem.|  
|`int32`|32-bit znaménkem.|  
|`int64`|64bitová verze znaménkem.|  
|`int8`|8bitové podepsaný číselnou hodnotu.|  
|`uint16`|16bitové celé číslo bez znaménka.|  
|`uint32`|32bitové celé číslo bez znaménka.|  
|`uint64`|64bitové celé číslo bez znaménka.|  
|`uint8`|8bitové nepodepsané číselnou hodnotu.|  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** vccorlib.h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)