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
ms.openlocfilehash: 848ea415d0638b6135c69cd14e442f45dab40237
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220358"
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

*uuid*  
Jedinečný identifikátor.

*value*  
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

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Samostatné atributy](../windows/stand-alone-attributes.md)  
[Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)  
[Atributy parametru](../windows/parameter-attributes.md)  
[Atributy metody](../windows/method-attributes.md)  
[Atributy třídy](../windows/class-attributes.md)  
[Atributy rozhraní](../windows/interface-attributes.md)  