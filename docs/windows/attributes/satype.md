---
title: satype – (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.satype
helpviewer_keywords:
- satype attribute
ms.assetid: 1716590b-6bcb-4aba-b1bc-82f7335f02c3
ms.openlocfilehash: 7588e8d855d648309c46d981898cfbbf7888f4c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407299"
---
# <a name="satype"></a>satype

Určuje datový typ `SAFEARRAY` struktury.

## <a name="syntax"></a>Syntaxe

```cpp
[ satype(data_type) ]
```

### <a name="parameters"></a>Parametry

*data_type*<br/>
Datový typ `SAFEARRAY` datová struktura, která je předána jako parametr metody rozhraní.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Rozhraní parametrů, metody rozhraní|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádný|

## <a name="remarks"></a>Poznámky

**Satype –** C++ atribut určuje datový typ `SAFEARRAY`.

> [!NOTE]
> Z je vyřadit určitou úroveň dereference `SAFEARRAY` ukazatel v souboru IDL vygenerovaný v tom, jak je deklarován v souboru .cpp.

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

## <a name="see-also"></a>Viz také:

[Atributy kompilátoru](compiler-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[id](id.md)