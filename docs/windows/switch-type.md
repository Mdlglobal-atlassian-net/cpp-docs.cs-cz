---
title: switch_type – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.switch_type
dev_langs:
- C++
helpviewer_keywords:
- switch_type attribute
ms.assetid: e24544dc-b3bc-48ae-b249-f967db49271e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: faa2a3be7260eecb16599db967336bcb7b774c99
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200123"
---
# <a name="switchtype"></a>switch_type

Určuje typ proměnné použité jako sjednocení discriminant.

## <a name="syntax"></a>Syntaxe

```cpp
[switch_type(
type
}]
```

### <a name="parameters"></a>Parametry

*Typ*  
Typ přepínače může být typ integer, znak, logická hodnota nebo výčet.

## <a name="remarks"></a>Poznámky

**Switch_type –** C++ atribut má stejné funkce jako [switch_type –](/windows/desktop/Midl/switch-type) atribut MIDL.

Atributy C++ nepodporuje [zapouzdřené sjednocení](/windows/desktop/Midl/encapsulated-unions). [Nonencapsulated sjednocení](/windows/desktop/Midl/nonencapsulated-unions) jsou podporovány pouze v následujícím tvaru:

```cpp
// cpp_attr_ref_switch_type.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];
[ export ]
struct SizedValue2 {
   [switch_type("char"), switch_is(kind)] union {
      [case(1), string]
         wchar_t* wval;
      [default, string]
         char* val;
   };
   char kind;
};
```

## <a name="example"></a>Příklad

Najdete v článku [případ](../windows/case-cpp.md) příklad ukázkový používání **switch_type –**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Definice TypeDef**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[export](../windows/export.md)  