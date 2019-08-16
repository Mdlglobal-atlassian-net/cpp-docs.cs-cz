---
title: nevytvořitelné (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.noncreatable
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
ms.openlocfilehash: e855497cb6f619ecdaa6aedf16a04f045a60faa7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514565"
---
# <a name="noncreatable"></a>noncreatable

Definuje objekt, který nemůže být vytvořen sám sebou.

## <a name="syntax"></a>Syntaxe

```cpp
[noncreatable]
```

## <a name="remarks"></a>Poznámky

Netvářený C++ atribut má stejné funkce jako nevytvořitelné [](/windows/win32/Midl/noncreatable) MIDL atribut a automaticky se předává do generovaného. Soubor IDL kompilátorem.

Při použití tohoto atributu v projektu, který používá ATL, se chování atributu změní. Kromě výše uvedeného chování atribut také vloží [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) makro. Toto makro indikuje knihovně ATL, že objekt nelze vytvořit externě.

## <a name="example"></a>Příklad

```cpp
// cpp_attr_ref_noncreatable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("11111111-1111-1111-1111-111111111111")]
__interface A
{
};

[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]
class CMyClass : public A
{
   HRESULT xx();
};
```

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

[IDL – atributy](idl-attributes.md)<br/>
[Atributy třídy](class-attributes.md)
