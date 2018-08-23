---
title: místní (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.local
dev_langs:
- C++
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a19e58e68b7f03269c002072859c2410a38c397b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597615"
---
# <a name="local-c"></a>local (C++)

Při použití v záhlaví rozhraní, můžete pomocí kompilátoru MIDL jako generátor záhlaví. Při použití jednotlivých funkcí, určuje místní postupu, pro které jsou generovány žádné zástupné procedury.

## <a name="syntax"></a>Syntaxe

```cpp
[local]
```

## <a name="remarks"></a>Poznámky

**Místní** C++ atribut má stejné funkce jako [místní](http://msdn.microsoft.com/library/windows/desktop/aa367071) atribut MIDL.

## <a name="example"></a>Příklad

Zobrazit [call_as](../windows/call-as.md) příklad, jak používat **místní**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**rozhraní**, rozhraní – metoda|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|`dispinterface`|

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Atributy rozhraní](../windows/interface-attributes.md)  
[Atributy metody](../windows/method-attributes.md)  
[call_as](../windows/call-as.md)  