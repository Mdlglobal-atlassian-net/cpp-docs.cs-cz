---
title: Vlastní (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.custom
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5a491c120dff7f8f505878d6887498eb5f05fb22
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789393"
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

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Atributy parametru](parameter-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)  