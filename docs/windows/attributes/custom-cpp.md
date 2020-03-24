---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: f51b0210fff4db5be359fa94237f4d7c77b4fef2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214887"
---
# <a name="custom-c"></a>custom (C++)

Definuje metadata pro objekt v knihovně typů.

## <a name="syntax"></a>Syntaxe

```cpp
[ custom(
   uuid,
   value
) ];
```

### <a name="parameters"></a>Parametry

*uuid*<br/>
Jedinečné ID.

*value*<br/>
Hodnota, která může být vložena do proměnné typu variant.

## <a name="remarks"></a>Poznámky

**Vlastní** C++ atribut způsobí umístění informací do knihovny typů. Budete potřebovat nástroj, který přečte vlastní hodnotu z knihovny typů.

**Vlastní** atribut má stejné funkce jako atribut [vlastního](/windows/win32/Midl/custom) MIDL.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Rozhraní**, **třídy**, **výčtové**typy, `idl_module` metody, členy rozhraní, parametry rozhraní, **definice**typu, **sjednocení**, **Struktura**s|
|**REPEATABLE**|Ano|
|**Požadované atributy**|**Coclass** (při použití ve třídě)|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)
