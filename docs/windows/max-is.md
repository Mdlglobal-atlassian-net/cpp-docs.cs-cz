---
title: max_is – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.max_is
dev_langs:
- C++
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e2aa0b6e3928affbd30e08030f41a0b0183e46d8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200678"
---
# <a name="maxis"></a>max_is

Určuje maximální hodnotu pro pole platný index.

## <a name="syntax"></a>Syntaxe

```cpp
[ max_is(
   "expression"
) ]
```

### <a name="parameters"></a>Parametry

*Výraz*  
Jeden nebo více výrazů jazyka C. Prázdný argument sloty jsou povoleny.

## <a name="remarks"></a>Poznámky

**Max_is –** C++ atribut má stejné funkce jako [max_is –](/windows/desktop/Midl/max-is) atribut MIDL.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Pole v **struktura** nebo **sjednocení**, rozhraní parametr, rozhraní – metoda|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|**size_is**|

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="example"></a>Příklad

Zobrazit [first_is –](../windows/first-is.md) příklad toho, jak zadat část pole.

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[Atributy parametru](../windows/parameter-attributes.md)  
[first_is](../windows/first-is.md)  
[last_is](../windows/last-is.md)  
[length_is](../windows/length-is.md)  
[size_is](../windows/size-is.md)  