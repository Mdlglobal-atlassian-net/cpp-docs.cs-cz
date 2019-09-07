---
title: uuid (C++)
ms.date: 11/04/2016
f1_keywords:
- uuid_cpp
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
ms.openlocfilehash: c121ad99dfbe0021a263f324ccdb9a95441bba33
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740465"
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

Tento atribut lze použít v opětovné deklaraci. To umožňuje systémovým hlavičkám dodat definice rozhraní `IUnknown`, jako je a změna deklarace v některé jiné hlavičce ( \<například Comdef. h >) k poskytnutí identifikátoru GUID.

Klíčové slovo [__uuidof](../cpp/uuidof-operator.md) lze použít k načtení KONSTANTNÍho identifikátoru GUID připojeného k uživatelsky definovanému typu.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)