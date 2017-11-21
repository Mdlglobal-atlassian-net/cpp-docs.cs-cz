---
title: "_variant_t – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _variant_t
dev_langs: C++
helpviewer_keywords:
- _variant_t class [C++], operators
- _variant_t class
- _variant_t class [C++], member functions
- VARIANT object
- VARIANT object [C++], COM encapsulation
ms.assetid: 6a3cbd4e-0ae8-425e-b4cf-ca0df894c93f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1afc35836f170a03ec7b8f4d8e20a1ff02995c23
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="variantt-class"></a>_variant_t – třída
**Konkrétní Microsoft**  
  
 A `_variant_t` zapouzdřují `VARIANT` datového typu. Třída spravuje přidělení prostředků a navrácení a provádí volání funkce na **VariantInit** a **VariantClear** podle potřeby.  
  
### <a name="construction"></a>Konstrukce  
  
|||  
|-|-|  
|[_variant_t](../cpp/variant-t-variant-t.md)|Vytvoří `_variant_t` objektu.|  
  
### <a name="operations"></a>Operace  
  
|||  
|-|-|  
|[Připojení](../cpp/variant-t-attach.md)|Připojí **VARIANT** objektu do `_variant_t` objektu.|  
|[Zrušte zaškrtnutí](../cpp/variant-t-clear.md)|Vymaže obsah zapouzdřeného **VARIANT** objektu.|  
|[ChangeType –](../cpp/variant-t-changetype.md)|Typ se změní `_variant_t` objekt, který má uvedené **VARTYPE**.|  
|[Odpojení](../cpp/variant-t-detach.md)|Umožňuje odpojit zapouzdřené **VARIANT** objekt z tohoto `_variant_t` objektu.|  
|[SetString –](../cpp/variant-t-setstring.md)|To přiřadí řetězec `_variant_t` objektu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[Operátor =](../cpp/variant-t-operator-equal.md)|Přiřadí novou hodnotu na stávající `_variant_t` objektu.|  
|[Operator ==,! =](../cpp/variant-t-relational-operators.md)|Porovnat `_variant_t` objekty pro rovnosti nebo nerovnosti.|  
|[Extraktory](../cpp/variant-t-extractors.md)|Extrahovat data z zapouzdřené **VARIANT** objektu.|  
  
**Konkrétní Microsoft END**  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** comutil.h  
  
 **Lib:** comsuppw.lib nebo comsuppwd.lib (viz [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) informace)  
  
## <a name="see-also"></a>Viz také  
 [Třídy podpory modelu comp kompilátoru](../cpp/compiler-com-support-classes.md)