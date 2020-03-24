---
title: v1_enum (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.v1_enum
helpviewer_keywords:
- v1_enum attribute
ms.assetid: 2fe92d92-81b9-4a1c-b6ce-437d0eb770ca
ms.openlocfilehash: 1a189f6f1c5ef9d4ae77df9f1eda3f3671ddaf52
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166104"
---
# <a name="v1_enum"></a>v1_enum

Směruje, že zadaný typ výčtu se přenáší jako 32ová entita, nikoli jako 16bitové výchozí hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
[v1_enum]
```

## <a name="remarks"></a>Poznámky

Atribut **v1_enum** C++ má stejné funkce jako atribut [v1_enum](/windows/win32/Midl/v1-enum) MIDL.

## <a name="example"></a>Příklad

Následující kód ukazuje použití **v1_enum**:

```cpp
// cpp_attr_ref_v1_enum.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export, v1_enum]
enum eList {
   e1 = 1, e2 = 2
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Výčtový typ|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)
