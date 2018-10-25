---
title: místní (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: e510e4faa707c954c52ae9daae4c4dc0d4c800dd
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50057150"
---
# <a name="local-c"></a>local (C++)

Při použití v záhlaví rozhraní, můžete pomocí kompilátoru MIDL jako generátor záhlaví. Při použití jednotlivých funkcí, určuje místní postupu, pro které jsou generovány žádné zástupné procedury.

## <a name="syntax"></a>Syntaxe

```cpp
[local]
```

## <a name="remarks"></a>Poznámky

**Místní** C++ atribut má stejné funkce jako [místní](/windows/desktop/Midl/local) atribut MIDL.

## <a name="example"></a>Příklad

Zobrazit [call_as](call-as.md) příklad, jak používat **místní**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**rozhraní**, rozhraní – metoda|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|`dispinterface`|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[call_as](call-as.md)