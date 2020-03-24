---
title: soubor nápovědyC++ (atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 1f928fa281c99630ad52ce1fde184c44e9387263
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166975"
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

Atribut s **nápovědou** C++ má stejné funkce jako atribut s [nápovědou](/windows/win32/Midl/helpfile) .

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

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)
