---
title: atribut HelpContext (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpcontext
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
ms.openlocfilehash: 292db21e8092284a92b09ef3f889bb0475d0d886
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167001"
---
# <a name="helpcontext"></a>helpcontext

Určuje ID kontextu, které uživateli umožňuje zobrazit informace o tomto prvku v souboru **help** .

## <a name="syntax"></a>Syntaxe

```cpp
[ helpcontext(id) ]
```

### <a name="parameters"></a>Parametry

*id*<br/>
ID kontextu tématu nápovědy. Další informace o ID kontextu najdete v [nápovědě HTML: kontextová nápověda pro vaše programy](../../mfc/html-help-context-sensitive-help-for-your-programs.md) .

## <a name="remarks"></a>Poznámky

Atribut **atribut HelpContext** C++ má stejné funkce jako atribut [atribut HelpContext](/windows/win32/Midl/helpcontext) MIDL.

## <a name="example"></a>Příklad

Příklad použití **atribut HelpContext**najdete v příkladu pro [DefaultValue](defaultvalue.md) .

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**rozhraní**, **typedef**, **Třída**, metoda, vlastnost|
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
[helpfile](helpfile.md)<br/>
[helpstring](helpstring.md)
