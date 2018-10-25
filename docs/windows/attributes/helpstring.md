---
title: helpstring (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: 8cca35d151d0f28c7273c84643662b442afbd3a3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056981"
---
# <a name="helpstring"></a>helpstring

Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpstring("string") ]
```

### <a name="parameters"></a>Parametry

*string*<br/>
Textový řetězec nápovědy.

## <a name="remarks"></a>Poznámky

**Helpstring** C++ atribut má stejné funkce jako [helpstring](/windows/desktop/Midl/helpstring) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [defaultvalue](defaultvalue.md) příklad, jak používat **helpstring**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**rozhraní**, **typedef**, **třída**, metoda, vlastnost|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpcontext](helpcontext.md)