---
title: Local (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.local
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
ms.openlocfilehash: 853331ce191f8fe41d5967d2d625a3dac8543a4d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514411"
---
# <a name="local-c"></a>local (C++)

Při použití v hlavičce rozhraní umožňuje použití kompilátoru MIDL jako generátoru záhlaví. Při použití v individuální funkci určí místní proceduru, pro kterou nejsou vygenerována žádná zástupné procedury.

## <a name="syntax"></a>Syntaxe

```cpp
[local]
```

## <a name="remarks"></a>Poznámky

**Místní** C++ atribut má stejné funkce jako [místní](/windows/win32/Midl/local) atribut MIDL.

## <a name="example"></a>Příklad

Příklad použití **místní proměnné**naleznete v tématu [call_as](call-as.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**rozhraní**, metoda rozhraní|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|`dispinterface`|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[call_as](call-as.md)