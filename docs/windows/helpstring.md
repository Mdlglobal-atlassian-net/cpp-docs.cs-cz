---
title: helpstring | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpstring
dev_langs:
- C++
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2892f957cf8937b5b030e7624bf3e39f546a7103
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437602"
---
# <a name="helpstring"></a>helpstring

Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpstring(
   "string"
) ]
```

### <a name="parameters"></a>Parametry

*string*<br/>
Textový řetězec nápovědy.

## <a name="remarks"></a>Poznámky

**Helpstring** C++ atribut má stejné funkce jako [helpstring](/windows/desktop/Midl/helpstring) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [defaultvalue](../windows/defaultvalue.md) příklad, jak používat **helpstring**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**rozhraní**, **typedef**, **třída**, metoda, vlastnost|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)<br/>
[Atributy rozhraní](../windows/interface-attributes.md)<br/>
[Atributy třídy](../windows/class-attributes.md)<br/>
[Atributy metody](../windows/method-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](../windows/helpfile.md)<br/>
[helpcontext](../windows/helpcontext.md)  