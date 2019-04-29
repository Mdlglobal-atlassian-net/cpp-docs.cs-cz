---
title: _bstr_t – třída
ms.date: 11/04/2016
f1_keywords:
- _bstr_t
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
ms.openlocfilehash: f394a48c0326058be705d14fb0413e23e8052ae2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386158"
---
# <a name="bstrt-class"></a>_bstr_t – třída

**Microsoft Specific**

A `_bstr_t` zapouzdřuje objektu [datový typ BSTR](/previous-versions/windows/desktop/automat/bstr). Třída spravuje a pomocí volání funkce zrušení přidělení prostředků `SysAllocString` a `SysFreeString` a dalších `BSTR` rozhraní API. **_Bstr_t** třída používá počítání odkazů, aby se zabránilo nadměrnému zatížení.

### <a name="construction"></a>Konstrukce

|||
|-|-|
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|Vytvoří `_bstr_t` objektu.|

### <a name="operations"></a>Operace

|||
|-|-|
|[Assign](../cpp/bstr-t-assign.md)|Kopie `BSTR` do `BSTR` uzavřenou `_bstr_t`.|
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

**Header:** \<comutil.h>

**Lib:** comsuppw.lib nebo comsuppwd.lib (viz [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Další informace)

## <a name="see-also"></a>Viz také:

[Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)