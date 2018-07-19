---
title: _variant_t::Attach | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42c275d085434cc8077a0629429c7c0e1cbbfcc3
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947681"
---
# <a name="varianttattach"></a>_variant_t::Attach
**Specifické pro Microsoft**  
  
 Připojí `VARIANT` objektu do `_variant_t` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
void Attach(VARIANT& varSrc);  
```  
  
#### <a name="parameters"></a>Parametry  
 *varSrc*  
 A `VARIANT` objektu, který chcete připojit k tomuto `_variant_t` objektu.  
  
## <a name="remarks"></a>Poznámky  
 Převezme vlastnictví `VARIANT` zapouzdřením ho. Tato členská funkce uvolní všechny existující zapouzdřené `VARIANT`, pak zkopíruje zadané `VARIANT`a nastaví její `VARTYPE` VT_EMPTY Ujistěte se, že její prostředky lze pouze budou vydány `_variant_t` destruktor.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [_variant_t – třída](../cpp/variant-t-class.md)