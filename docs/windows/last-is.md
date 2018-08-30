---
title: last_is – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.last_is
dev_langs:
- C++
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e7b699f5b6aa023473416b822a94d9b3a91c2b07
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221116"
---
# <a name="lastis"></a>last_is

Určuje index posledního prvku pole předávají.

## <a name="syntax"></a>Syntaxe

```cpp
[ last_is(
   "expression"
) ]
```

### <a name="parameters"></a>Parametry

*Výraz*  
Jeden nebo více výrazů jazyka C. Prázdný argument sloty jsou povoleny.

## <a name="remarks"></a>Poznámky

**Last_is –** C++ atribut má stejné funkce jako [last_is –](/windows/desktop/Midl/last-is) atribut MIDL.

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
[length_is](../windows/length-is.md)  
[size_is](../windows/size-is.md)  