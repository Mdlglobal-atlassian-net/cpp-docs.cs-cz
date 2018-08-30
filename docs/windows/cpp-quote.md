---
title: cpp_quote – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: da9e378ff75ec67660b0c29a5765be88a2c06496
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205663"
---
# <a name="cppquote"></a>cpp_quote

Zadaný řetězec bez uvozovek znaků, vysílá do generovaného souboru.

## <a name="syntax"></a>Syntaxe

```cpp
[ cpp_quote(
   "statement"
) ];
```

### <a name="parameters"></a>Parametry

*– Příkaz*  
Instrukce C.

## <a name="remarks"></a>Poznámky

**Cpp_quote –** C++ atribut je užitečné, pokud chcete umístit direktivy preprocesoru v souboru IDL.

Můžete také použít **cpp_quote –** a generování souboru .h jako část kompilace MIDL. Například pokud máte soubor hlaviček jazyka C++, která používá C++ IDL – atributy, ale tento soubor nelze použít pro některé úlohy, pak ji můžete zkompilovat vytvořit generované MIDL. h: soubor, který byste měli použít.

**Cpp_quote –** atribut má stejné funkce jako [cpp_quote –](/windows/desktop/Midl/cpp-quote) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [duální](../windows/dual.md) příklad použití použití **cpp_quote –**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|Kdekoli|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)  
[Samostatné atributy](../windows/stand-alone-attributes.md)  