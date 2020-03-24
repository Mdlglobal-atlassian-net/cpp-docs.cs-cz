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
ms.openlocfilehash: 3ef89c6f6742d528c427c49fd2a62d8820625e79
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190375"
---
# <a name="_bstr_t-class"></a>_bstr_t – třída

**Specifické pro společnost Microsoft**

Objekt `_bstr_t` zapouzdřuje [datový typ BSTR](/previous-versions/windows/desktop/automat/bstr). Třída spravuje přidělování a navracení prostředků prostřednictvím volání funkcí do `SysAllocString` a `SysFreeString` a dalších `BSTR` rozhraní API, pokud je to vhodné. Třída **_bstr_t** používá počítání odkazů, aby nedocházelo k nadměrné režii.

### <a name="construction"></a>Stavbě

|||
|-|-|
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|Vytvoří objekt `_bstr_t`.|

### <a name="operations"></a>Operace

|||
|-|-|
|[Assign](../cpp/bstr-t-assign.md)|Zkopíruje `BSTR` do `BSTR` zabaleného `_bstr_t`.|
|[Attach](../cpp/bstr-t-attach.md)|Propojí `_bstr_t` obálku s `BSTR`.|
|[kopií](../cpp/bstr-t-copy.md)|Vytvoří kopii zapouzdřeného `BSTR`.|
|[Detach](../cpp/bstr-t-detach.md)|Vrátí `BSTR` zabalenou `_bstr_t` a odpojí `BSTR` od `_bstr_t`.|
|[GetAddress](../cpp/bstr-t-getaddress.md)|Odkazuje na `BSTR` zabalenou `_bstr_t`.|
|[GetBSTR](../cpp/bstr-t-getbstr.md)|Odkazuje na začátek `BSTR` zabalených `_bstr_t`.|
|[časový](../cpp/bstr-t-length.md)|Vrátí počet znaků v `_bstr_t`.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](../cpp/bstr-t-operator-equal.md)|Přiřadí novou hodnotu existujícímu objektu `_bstr_t`.|
|[operator + = – operátor](../cpp/bstr-t-operator-add-equal-plus.md)|Připojí znaky na konec objektu `_bstr_t`.|
|[+ – operátor](../cpp/bstr-t-operator-add-equal-plus.md)|Zřetězí dva řetězce.|
|[! – operátor](../cpp/bstr-t-operator-logical-not.md)|Kontroluje, zda je zapouzdřený `BSTR` řetězec s hodnotou NULL.|
|[operator = =,! =, \<, >, \<=, > =](../cpp/bstr-t-relational-operators.md)|Porovná dva objekty `_bstr_t`.|
|[operátor wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|Extrahuje ukazatele na zapouzdřený objekt Unicode nebo vícebajtový `BSTR` objekt.|

**Specifické pro konec Microsoftu**

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<comutil. h >

**Lib:** comsuppw. lib nebo comsuppwd. lib (viz [/Zc: Wchar_t (Wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) , kde najdete další informace.)

## <a name="see-also"></a>Viz také

[Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)
