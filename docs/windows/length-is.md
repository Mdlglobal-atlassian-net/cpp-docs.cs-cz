---
title: length_is – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.length_is
dev_langs:
- C++
helpviewer_keywords:
- length_is attribute
ms.assetid: 1d99b883-84bb-4b1e-b098-eb780fc94f40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1852e765ed859f95f6de5319a1e9d8fa364f7681
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207060"
---
# <a name="lengthis"></a>length_is

Určuje počet elementů pole předávají.

## <a name="syntax"></a>Syntaxe

```cpp
[ length_is(
   "expression"
) ]
```

### <a name="parameters"></a>Parametry

*Výraz*  
Jeden nebo více výrazů jazyka C. Prázdný argument sloty jsou povoleny.

## <a name="remarks"></a>Poznámky

**Length_is –** C++ atribut má stejné funkce jako [length_is –](/windows/desktop/Midl/length-is) atribut MIDL.

## <a name="example"></a>Příklad

Zobrazit [first_is –](../windows/first-is.md) příklad toho, jak zadat část pole.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Pole v **struktura** nebo **sjednocení**, rozhraní parametr, rozhraní – metoda|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[Atributy parametru](../windows/parameter-attributes.md)  
[first_is](../windows/first-is.md)  
[max_is](../windows/max-is.md)  
[last_is](../windows/last-is.md)  
[size_is](../windows/size-is.md)  