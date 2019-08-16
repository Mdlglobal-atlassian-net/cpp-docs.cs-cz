---
title: soubor nápovědyC++ (atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 538cdbb38ac525cfee03a641f3e62e22a69f8e2b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501541"
---
# <a name="helpfile"></a>helpfile

Nastaví název souboru s nápovědu pro knihovnu typů.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpfile("filename") ]
```

### <a name="parameters"></a>Parametry

*Bitmap*<br/>
Název souboru, který obsahuje témata nápovědy.

## <a name="remarks"></a>Poznámky

Atribut C++ s nápovědou má stejné funkce jako atribut [](/windows/win32/Midl/helpfile) s nápovědou.

## <a name="example"></a>Příklad

Příklad použití funkce soubor **nápovědy**naleznete v příkladu pro [modul](module-cpp.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**rozhraní**, **typedef**, **Třída**, metoda, **vlastnost**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)