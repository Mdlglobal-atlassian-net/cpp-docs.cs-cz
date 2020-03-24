---
title: verze (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: e5fcf80ef753a869b8798d6ab9c8e9f8ecff16fd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165987"
---
# <a name="version-c"></a>version (C++)

Identifikuje konkrétní verzi z více verzí třídy.

## <a name="syntax"></a>Syntaxe

```cpp
[ version("version") ]
```

### <a name="parameters"></a>Parametry

*version*<br/>
Číslo verze `coclass`. Pokud není zadán, 1,0 bude umístěn v souboru. idl.

## <a name="remarks"></a>Poznámky

Atribut **Version** C++ má stejné funkce jako atribut MIDL [verze](/windows/win32/Midl/version) a je předán do generovaného souboru. idl.

## <a name="example"></a>Příklad

Ukázku použití **verze**najdete v příkladu s možností [vazby](bindable.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|**coclass**|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[Atributy kompilátoru](compiler-attributes.md)<br/>
[Atributy třídy](class-attributes.md)
