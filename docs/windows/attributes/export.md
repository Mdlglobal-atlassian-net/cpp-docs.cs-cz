---
title: Exportovat (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 5ffa4283b8a2b265809d06b72be96e217cf8bf9f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023604"
---
# <a name="export"></a>export

Způsobí, že datová struktura budou umístěny v souboru IDL.

## <a name="syntax"></a>Syntaxe

```cpp
[export]
```

## <a name="remarks"></a>Poznámky

**Exportovat** C++ atribut způsobí, že datová struktura, budou umístěny v souboru IDL a poté bude k dispozici v knihovně typů ve formátu binárně kompatibilní, který je k dispozici pro použití v libovolném jazyce.

Nelze použít **exportovat** atribut třídy i v případě, že třída má pouze veřejné členy (ekvivalent **struktura**).

Pokud exportujete nepojmenované **výčtu** nebo **struktura**, se klíči přiřadí název, který začíná **__unnamed**<em>x</em>, kde *x* je pořadové číslo.

Platné pro export definice TypeDef jsou základních typů, struktur, sjednocení, výčty, nebo zadejte identifikátory.  Zobrazit [typedef](/windows/desktop/Midl/typedef) Další informace.

## <a name="example"></a>Příklad

Následující kód ukazuje způsob použití **exportovat** atribut:

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

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**sjednocení**, **typedef**, **výčtu**, **struktura**, nebo **rozhraní**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[Atributy kompilátoru](compiler-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)