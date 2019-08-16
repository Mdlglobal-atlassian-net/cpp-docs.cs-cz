---
title: Threading (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: db2940ec3536ae8ea29ba40db84ea869ecb3d0ac
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513927"
---
# <a name="threading-c"></a>threading (C++)

Určuje model dělení na vlákna pro objekt modelu COM.

## <a name="syntax"></a>Syntaxe

```cpp
[ threading(model=enumeration) ]
```

### <a name="parameters"></a>Parametry

*model*<br/>
Volitelné Jeden z následujících modelů vláken:

- `apartment`(dělení na vlákna)

- `neutral`(.NET Framework komponenty bez uživatelského rozhraní)

- `single`(jednoduché zřetězení)

- `free`(bezplatné dělení na vlákna)

- `both`(vícevláknové a bezplatné podprocesy)

Výchozí hodnota je `apartment`.

## <a name="remarks"></a>Poznámky

Atribut Threading se nezobrazí v generovaném souboru IDL, ale bude použit v implementaci objektu com. C++

V projektech ATL, pokud je současně atribut [Coclass](coclass.md) , je model vláken určený modelem předán jako parametr šablony `coclass` třídě [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) , vloženou atributem.

Atribut **vlákna** také chrání přístup k [event_source](event-source.md).

## <a name="example"></a>Příklad

Podívejte se [](licensed.md) na Vzorový příklad použití **vlákna**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|**coclass**|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[COM – atributy](com-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Podpora multithreadingu ve starším kódu (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[Neutrální objekty Apartment](/windows/win32/cossdk/neutral-apartments)