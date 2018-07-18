---
title: _bstr_t – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 15ed9c32a204bdef726a5ace88d811d2eeeb2c53
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027245"
---
# <a name="bstrt-class"></a>_bstr_t – třída
**Specifické pro Microsoft**  
  
 A `_bstr_t` zapouzdřuje objektu [datový typ BSTR](http://msdn.microsoft.com/1b2d7d2c-47af-4389-a6b6-b01b7e915228). Třída spravuje a pomocí volání funkce zrušení přidělení prostředků `SysAllocString` a `SysFreeString` a dalších `BSTR` rozhraní API. `_bstr_t` Třída používá počítání odkazů, aby se zabránilo nadměrnému zatížení.  
  
### <a name="construction"></a>Konstrukce  
  
|||  
|-|-|  
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|Vytvoří `_bstr_t` objektu.|  
  
### <a name="operations"></a>Operace  
  
|||  
|-|-|  
|[přiřazení](../cpp/bstr-t-assign.md)|Kopie `BSTR` do `BSTR` uzavřenou `_bstr_t`.|  
|[Attach](../cpp/bstr-t-attach.md)|Odkazy `_bstr_t` obálky `BSTR`.|  
|[kopírování](../cpp/bstr-t-copy.md)|Vytvoří kopii zapouzdřeného `BSTR`.|  
|[Detach](../cpp/bstr-t-detach.md)|Vrátí `BSTR` uzavřenou `_bstr_t` a odpojí `BSTR` z `_bstr_t`.|  
|[GetAddress](../cpp/bstr-t-getaddress.md)|Odkazuje `BSTR` uzavřenou `_bstr_t`.|  
|[Getbstr –](../cpp/bstr-t-getbstr.md)|Odkazuje na začátku `BSTR` uzavřenou `_bstr_t`.|  
|[Délka](../cpp/bstr-t-length.md)|Vrátí počet znaků `_bstr_t`.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](../cpp/bstr-t-operator-equal.md)|Přiřadí novou hodnotu do existujícího `_bstr_t` objektu.|  
|[+= – operátor](../cpp/bstr-t-operator-add-equal-plus.md)|Připojí znaky na konec objektu `_bstr_t` objektu.|  
|[+ – operátor](../cpp/bstr-t-operator-add-equal-plus.md)|Spojuje dva řetězce.|  
|[! – operátor](../cpp/bstr-t-operator-logical-not.md)|Ověří, zda zapouzdřený `BSTR` je prázdný řetězec.|  
|[operátor ==,! =, \<, >, \<=, > =](../cpp/bstr-t-relational-operators.md)|Porovná dva `_bstr_t` objekty.|  
|[operátor wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|Extrahovat ukazatele na zapouzdřený objekt Unicode nebo vícebajtový `BSTR` objektu.|  
  
**Specifické pro END Microsoft**  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<comutil.h >  
  
 **Lib:** comsuppw.lib nebo comsuppwd.lib (viz [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Další informace)  
  
## <a name="see-also"></a>Viz také  
 [Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)