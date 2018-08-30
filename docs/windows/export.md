---
title: Export | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: d5da3f03500ccaadb4cff3be0226592e36ed3160
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200886"
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

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[Atributy kompilátoru](../windows/compiler-attributes.md)  
[Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)  