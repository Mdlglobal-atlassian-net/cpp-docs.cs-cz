---
title: neprocházetelné (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonbrowsable
helpviewer_keywords:
- nonbrowsable attribute
ms.assetid: e71a98e7-4b65-454a-9829-342b9f2a84be
ms.openlocfilehash: 8b1849aa75e61ea5e369a277cab0b1327f48a28a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514382"
---
# <a name="nonbrowsable"></a>nonbrowsable

Indikuje, že by se člen rozhraní neměl zobrazovat v prohlížeči vlastností.

## <a name="syntax"></a>Syntaxe

```cpp
[nonbrowsable]
```

## <a name="remarks"></a>Poznámky

Atribut, který nelze **Procházet** , má stejné funkce jako atribut MIDL, který nelze [Procházet.](/windows/win32/Midl/nonbrowsable) C++

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_nonbrowsable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, helpstring("help string"), helpstringcontext(1),
uuid="11111111-1111-1111-1111-111111111111"]
__interface IMyI
{
   [nonbrowsable] HRESULT xx();
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Metoda rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy metody](method-attributes.md)