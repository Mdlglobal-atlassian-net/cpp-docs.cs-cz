---
title: "výchozí obor názvů | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96b4fc906048d8f8e02d5359526e095c0f12118d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
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
|[default::(type_name)::Equals](../cppcx/default-type-name-equals-method.md)|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.|  
|[default::(type_name)::GetHashCode](../cppcx/default-type-name-gethashcode-method.md)|Vrátí kód hash této instance.|  
|[default::(type_name)::GetType](../cppcx/default-type-name-gettype-method.md)|Vrátí řetězec, který představuje aktuální typ.|  
|[default::(type_name)::ToString](../cppcx/default-type-name-tostring-method.md)|Vrátí řetězec, který představuje aktuální typ.|  
  
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