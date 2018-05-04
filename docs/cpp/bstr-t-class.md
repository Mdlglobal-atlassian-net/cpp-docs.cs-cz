---
title: _bstr_t – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t
dev_langs:
- C++
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8bea9f863df08342f17419a16b14579fa6a257b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="bstrt-class"></a>_bstr_t – třída
**Konkrétní Microsoft**  
  
 A `_bstr_t` zapouzdřují [BSTR datový typ](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228). Třída spravuje přidělení prostředků a navrácení prostřednictvím volání funkce **SysAllocString** a **SysFreeString** a dalších `BSTR` rozhraní API v případě nutnosti. `_bstr_t` Třída používá, aby se zabránilo nadměrnému zatížení při počítání referencí.  
  
### <a name="construction"></a>Konstrukce  
  
|||  
|-|-|  
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|Vytvoří `_bstr_t` objektu.|  
  
### <a name="operations"></a>Operace  
  
|||  
|-|-|  
|[přiřazení](../cpp/bstr-t-assign.md)|Kopie `BSTR` do `BSTR` zabalené službou `_bstr_t`.|  
|[Attach](../cpp/bstr-t-attach.md)|Odkazy `_bstr_t` obálka pro `BSTR`.|  
|[Kopírování](../cpp/bstr-t-copy.md)|Vytvoří kopii zapouzdřené `BSTR`.|  
|[Detach](../cpp/bstr-t-detach.md)|Vrátí `BSTR` zabalené službou `_bstr_t` a odpojí `BSTR` z `_bstr_t`.|  
|[Getaddress –](../cpp/bstr-t-getaddress.md)|Odkazuje na `BSTR` zabalené službou `_bstr_t`.|  
|[Getbstr –](../cpp/bstr-t-getbstr.md)|Odkazuje na začátku `BSTR` zabalený pomocí `_bstr_t`.|  
|[Délka](../cpp/bstr-t-length.md)|Vrátí počet znaků `_bstr_t`.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](../cpp/bstr-t-operator-equal.md)|Přiřadí novou hodnotu na stávající `_bstr_t` objektu.|  
|[+= – operátor](../cpp/bstr-t-operator-add-equal-plus.md)|Přidá konec znaků `_bstr_t` objektu.|  
|[+ – operátor](../cpp/bstr-t-operator-add-equal-plus.md)|Zřetězí dva řetězce.|  
|[! – operátor](../cpp/bstr-t-operator-logical-not.md)|Ověří, zda obsah zapouzdřeného `BSTR` je **NULL** řetězec.|  
|[Operator ==,! =, \<, >, \<=, > =](../cpp/bstr-t-relational-operators.md)|Porovná dva `_bstr_t` objekty.|  
|[operátor wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|Extrahování ukazatele na zapouzdřené Unicode nebo vícebajtových `BSTR` objektu.|  
  
**Konkrétní Microsoft END**  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<comutil.h >  
  
 **Lib:** comsuppw.lib nebo comsuppwd.lib (viz [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) informace)  
  
## <a name="see-also"></a>Viz také  
 [Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)