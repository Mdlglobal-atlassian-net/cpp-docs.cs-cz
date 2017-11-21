---
title: _variant_t::Attach | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
dev_langs: C++
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 893cf8c10fce70645fa42373f08e6b4636e41d11
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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