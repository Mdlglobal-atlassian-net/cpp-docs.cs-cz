---
title: Export (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 771bfdfe4eab2acf31e97a606795066e8938a8a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501606"
---
# <a name="export"></a>export

Způsobí, že datová struktura bude umístěna v souboru. idl.

## <a name="syntax"></a>Syntaxe

```cpp
[export]
```

## <a name="remarks"></a>Poznámky

Atribut **Export** C++ způsobí, že datová struktura bude umístěna v souboru. idl a pak bude k dispozici v knihovně typů v binárním formátu, který je k dispozici pro použití s jakýmkoli jazykem.

Atribut **exportu** nelze použít pro třídu, i když má třída pouze veřejné členy (ekvivalent **struktury**).

Pokud exportujete nepojmenované **výčty** nebo **struktury**, bude mu přidělen název začínající na **__unnamed**<em>x</em>, kde *x* je sekvenční číslo.

Definice typedef platný pro export jsou základní typy, struktury, sjednocení, výčty nebo identifikátory typů.  Další informace naleznete v tématu [typedef](/windows/win32/Midl/typedef) .

## <a name="example"></a>Příklad

Následující kód ukazuje, jak použít atribut **Export** :

```cpp
// cpp_attr_ref_export.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Union**, **typedef**, **Enum**, **struct**nebo **Interface**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[Atributy kompilátoru](compiler-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)