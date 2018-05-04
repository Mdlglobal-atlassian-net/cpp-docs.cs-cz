---
title: _variant_t::Attach | Microsoft Docs
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
ms.openlocfilehash: 93c4ec0b4d25f1ca0ec03d9aae1dd9e1c16b79a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="varianttattach"></a>_variant_t::Attach
**Konkrétní Microsoft**  
  
 Připojí **VARIANT** objektu do `_variant_t` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      void Attach(  
   VARIANT& varSrc   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *varSrc*  
 A **VARIANT** objekt, který má být připojen k tomuto `_variant_t` objektu.  
  
## <a name="remarks"></a>Poznámky  
 Přebírá vlastnictví **VARIANT** zapouzdřením ho. Tato funkce člen uvolní všechny existující zapouzdřené **VARIANT**, pak zkopíruje zadaných **VARIANT**a nastaví její **VARTYPE** k `VT_EMPTY` a ujistěte se jeho prostředky lze vydat pouze `_variant_t` destruktor.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_variant_t – třída](../cpp/variant-t-class.md)