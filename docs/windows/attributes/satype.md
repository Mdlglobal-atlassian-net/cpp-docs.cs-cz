---
title: satype (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.satype
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
ms.openlocfilehash: 4619deec6d5e4e9083fbc7bcab53caee0101285c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166273"
---
# <a name="satype"></a>satype

Určuje datový typ struktury `SAFEARRAY`.

## <a name="syntax"></a>Syntaxe

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>Parametry

*data_type*<br/>
Datový typ pro `SAFEARRAY` datovou strukturu, která je předávána jako parametr metodě rozhraní.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Parametr rozhraní, metoda rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

## <a name="remarks"></a>Poznámky

Atribut **satype** C++ Určuje datový typ `SAFEARRAY`.

> [!NOTE]
> Úroveň indirekce je vyřazena z ukazatele `SAFEARRAY` v generovaném souboru IDL z toho, jak je deklarována v souboru. cpp.

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_satype.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyModule")];
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A {
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="see-also"></a>Viz také

[Atributy kompilátoru](compiler-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[id](id.md)
