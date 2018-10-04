---
title: Exportovat (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.export
dev_langs:
- C++
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a636b7d4c943896bcd1e5e7b3580c2d3f7410fc8
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789339"
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

## <a name="see-also"></a>Viz také

[Atributy kompilátoru](compiler-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)  