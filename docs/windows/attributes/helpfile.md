---
title: soubor nápovědy (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpfile
helpviewer_keywords:
- helpfile attribute
ms.assetid: d75161c1-1363-4019-ae09-e7e3b8a3971e
ms.openlocfilehash: 7aff6addffb13d2d45953d190eeaac518fe48d6d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409561"
---
# <a name="helpfile"></a>helpfile

Nastaví název souboru nápovědy pro knihovnu typů.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpfile("filename") ]
```

### <a name="parameters"></a>Parametry

*Název souboru*<br/>
Název souboru, který obsahuje témata nápovědy.

## <a name="remarks"></a>Poznámky

**HelpFile –** C++ atribut má stejné funkce jako [HelpFile –](/windows/desktop/Midl/helpfile) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [modulu](module-cpp.md) příklad, jak používat **HelpFile –**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**rozhraní**, **typedef**, **třídy**, metoda, **vlastnost**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádný|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy rozhraní](interface-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy metody](method-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)