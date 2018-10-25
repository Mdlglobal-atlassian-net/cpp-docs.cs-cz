---
title: Práce s vlákny (C++ COM atribut) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.threading
dev_langs:
- C++
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 85ffa775fd18b6979fccf4354ce243f017634d02
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059672"
---
# <a name="threading-c"></a>threading (C++)

Určuje model vláken pro objekt modelu COM.

## <a name="syntax"></a>Syntaxe

```cpp
[ threading(model=enumeration) ]
```

### <a name="parameters"></a>Parametry

*Model*<br/>
(Volitelné) Jeden z následujících modely dělení na vlákna:

- `apartment` (podprocesový model apartment)

- `neutral` (Součásti rozhraní .NET framework bez uživatelského rozhraní)

- `single` (jednoduché dělení na vlákna)

- `free` (bez vláken)

- `both` (objektu apartment a volných vláken)

Výchozí hodnota je `apartment`.

## <a name="remarks"></a>Poznámky

**Dělení na vlákna** C++ atribut se nezobrazují v souboru IDL vygenerovaný, ale budou použity v implementaci váš objekt modelu COM.

V projektech ATL Pokud [coclass](coclass.md) atribut je také k dispozici, model vláken určené *modelu* je předán jako parametr šablony [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) třídy , Vložit `coclass` atribut.

**Dělení na vlákna** atribut také chrání přístup k [event_source](event-source.md).

## <a name="example"></a>Příklad

Najdete v článku [licenci](licensed.md) příklad ukázkový používání **dělení na vlákna**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **– struktura**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|**coclass**|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[COM – atributy](com-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Podpora multithreadingu ve starším kódu (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[Neutrální bytů](/windows/desktop/cossdk/neutral-apartments)