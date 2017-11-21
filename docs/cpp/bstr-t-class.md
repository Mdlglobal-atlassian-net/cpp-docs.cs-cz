---
title: "_bstr_t – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _bstr_t
dev_langs: C++
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0af38fe5e88540bf7e8947808c49c5283d742a4a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|[Přiřazení](../cpp/bstr-t-assign.md)|Kopie `BSTR` do `BSTR` zabalené službou `_bstr_t`.|  
|[Připojení](../cpp/bstr-t-attach.md)|Odkazy `_bstr_t` obálka pro `BSTR`.|  
|[kopírování](../cpp/bstr-t-copy.md)|Vytvoří kopii zapouzdřené `BSTR`.|  
|[Odpojení](../cpp/bstr-t-detach.md)|Vrátí `BSTR` zabalené službou `_bstr_t` a odpojí `BSTR` z `_bstr_t`.|  
|[Getaddress –](../cpp/bstr-t-getaddress.md)|Odkazuje na `BSTR` zabalené službou `_bstr_t`.|  
|[Getbstr –](../cpp/bstr-t-getbstr.md)|Odkazuje na začátku `BSTR` zabalený pomocí `_bstr_t`.|  
|[Délka](../cpp/bstr-t-length.md)|Vrátí počet znaků `_bstr_t`.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](../cpp/bstr-t-operator-equal.md)|Přiřadí novou hodnotu na stávající `_bstr_t` objektu.|  
|[+= – operátor](../cpp/bstr-t-operator-add-equal-plus.md)|Přidá konec znaků `_bstr_t` objektu.|  
|[operátor +](../cpp/bstr-t-operator-add-equal-plus.md)|Zřetězí dva řetězce.|  
|[Operator – operátor!](../cpp/bstr-t-operator-logical-not.md)|Ověří, zda obsah zapouzdřeného `BSTR` je **NULL** řetězec.|  
|[Operator ==,! =, \<, >, \<=, > =](../cpp/bstr-t-relational-operators.md)|Porovná dva `_bstr_t` objekty.|  
|[operátor wchar_t * &#124; Char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|Extrahování ukazatele na zapouzdřené Unicode nebo vícebajtových `BSTR` objektu.|  
  
**Konkrétní Microsoft END**  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** comutil.h  
  
 **Lib:** comsuppw.lib nebo comsuppwd.lib (viz [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) informace)  
  
## <a name="see-also"></a>Viz také  
 [Třídy podpory modelu comp kompilátoru](../cpp/compiler-com-support-classes.md)