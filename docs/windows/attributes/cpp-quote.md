---
title: cpp_quote – (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.cpp_quote
dev_langs:
- C++
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e67b839b487f7bb457eeadb0f4d0385b025ebc3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080595"
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