---
title: cpp_quote (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 905c9fc41b1b42dffe9c7b39fae0b096cdc24950
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501764"
---
# <a name="cpp_quote"></a>cpp_quote

Vygeneruje zadaný řetězec bez znaků uvozovky do generovaného souboru. idl.

## <a name="syntax"></a>Syntaxe

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>Parametry

*vydá*<br/>
Instrukce jazyka C.

## <a name="remarks"></a>Poznámky

Atribut **cpp_quote** C++ je užitečný, pokud chcete vložit direktivu preprocesoru do souboru. idl.

Můžete také použít **cpp_quote** a generovat soubor. h jako součást kompilace MIDL. Například pokud máte C++ hlavičkový soubor, který používá C++ atributy IDL, ale nemůže použít tento soubor pro určitý úkol, můžete jej zkompilovat pro vytvoření souboru. h generovaného pomocí MIDL, který byste měli mít možnost použít.

Atribut **cpp_quote** má stejné funkce jako atribut [cpp_quote](/windows/win32/Midl/cpp-quote) MIDL.

## <a name="example"></a>Příklad

Viz příklad pro [duální](dual.md) použití pro příklad použití **cpp_quote**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|Jakékoli|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)