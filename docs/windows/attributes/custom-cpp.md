---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 227e67696e679452a9c6c0e18c04e3d918f7a93f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029431"
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
Jedinečný identifikátor.

*value*<br/>
Hodnota, která můžou být přepnuté do hodnotu typu variant.

## <a name="remarks"></a>Poznámky

**Vlastní** C++ atribut způsobí, že informace, které jde umístit do knihovny typů. Budete potřebovat nástroj, který čte vlastní hodnotu z knihovny typů.

**Vlastní** atribut má stejné funkce jako [vlastní](/windows/desktop/Midl/custom) atribut MIDL.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Non-COM **rozhraní**, **třídy**, **výčtu**s, `idl_module` metody, členy rozhraní, parametry rozhraní **typedef**s, **sjednocení**s, **struktura**s|
|**Opakovatelné**|Ano|
|**Vyžadované atributy**|**coclass** (při použití ve třídě)|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)