---
title: výchozí obor názvů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 4712e9dc-57ba-43cc-811e-022e1dae4de8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87510fe7eee6a8027e5375f82f2b6ce7bf74ec3c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589731"
---
# <a name="default-namespace"></a>výchozí obor názvů
`default` Obory názvů předdefinovaných typů, které jsou podporovány C + +/ CX.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace default;  
```  
  
### <a name="members"></a>Členové  
 Všechny vestavěné typy dědí následující členy.  
  
|||  
|-|-|  
|[default::(type_name)::Equals](../cppcx/default-type-name-equals-method.md)|Určuje, zda se zadaný objekt rovná aktuálnímu objektu.|  
|[default::(type_name)::GetHashCode](../cppcx/default-type-name-gethashcode-method.md)|Vrátí kód hash této instance.|  
|[default::(type_name)::GetType](../cppcx/default-type-name-gettype-method.md)|Vrátí řetězec, který reprezentuje aktuálního typu.|  
|[default::(type_name)::ToString](../cppcx/default-type-name-tostring-method.md)|Vrátí řetězec, který reprezentuje aktuálního typu.|  
  
### <a name="built-in-types"></a>Vestavěné typy  
  
|Název|Popis|  
|----------|-----------------|  
|`char16`|16bitové nečíselná hodnota, která představuje bod kódu Unicode (UTF-16).|  
|`float32`|IEEE 754 číslo s 32 bitů s plovoucí desetinnou čárkou|  
|`float64`|IEEE 754 číslo s 64bitovým kompilátorem s plovoucí desetinnou čárkou|  
|`int16`|16bitové celé číslo se znaménkem.|  
|`int32`|32bitové celé číslo se znaménkem.|  
|`int64`|64bitové celé číslo se znaménkem.|  
|`int8`|8bitové podepsaný číselnou hodnotu.|  
|`uint16`|16bitové celé číslo bez znaménka.|  
|`uint32`|32bitové celé číslo bez znaménka.|  
|`uint64`|64bitové celé číslo bez znaménka.|  
|`uint8`|8bitové hodnoty bez znaménka číselná.|  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** vccorlib.h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)