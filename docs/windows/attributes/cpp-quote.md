---
title: cpp_quote – (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 5a281f9f88412df4d3ee18bff1302b19433e07f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466947"
---
# <a name="cppquote"></a>cpp_quote

Zadaný řetězec bez uvozovek znaků, vysílá do generovaného souboru.

## <a name="syntax"></a>Syntaxe

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>Parametry

*– Příkaz*<br/>
Instrukce C.

## <a name="remarks"></a>Poznámky

**Cpp_quote –** C++ atribut je užitečné, pokud chcete umístit direktivy preprocesoru v souboru IDL.

Můžete také použít **cpp_quote –** a generování souboru .h jako část kompilace MIDL. Například pokud máte soubor hlaviček jazyka C++, která používá C++ IDL – atributy, ale tento soubor nelze použít pro některé úlohy, pak ji můžete zkompilovat vytvořit generované MIDL. h: soubor, který byste měli použít.

**Cpp_quote –** atribut má stejné funkce jako [cpp_quote –](/windows/desktop/Midl/cpp-quote) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [duální](dual.md) příklad použití použití **cpp_quote –**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Kdekoli|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[IDL – atributy](idl-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)