---
title: uuid (C++)
ms.date: 11/04/2016
f1_keywords:
- uuid_cpp
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
ms.openlocfilehash: 09e40d38382bea0f902fda03d15d24e0cf1a627d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187801"
---
# <a name="uuid-c"></a>uuid (C++)

**Specifické pro společnost Microsoft**

Kompilátor připojí identifikátor GUID ke třídě nebo struktuře deklarované nebo definované (pouze úplné definice objektů COM) s atributem **UUID** .

## <a name="syntax"></a>Syntaxe

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>Poznámky

Atribut **UUID** bere jako argument řetězec. Tento řetězec pojmenovává identifikátor GUID v normálním formátu registru s oddělovači **{}** nebo bez něj. Příklad:

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

Tento atribut lze použít v opětovné deklaraci. To umožňuje systémovým hlavičkám dodat definice rozhraní, jako je `IUnknown`, a opětovnou deklaraci v některých dalších hlavičkách (například \<Comdef. h >) k poskytnutí identifikátoru GUID.

Klíčové slovo [__uuidof](../cpp/uuidof-operator.md) lze použít k načtení KONSTANTNÍho identifikátoru GUID připojeného k uživatelsky definovanému typu.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
