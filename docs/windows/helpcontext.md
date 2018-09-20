---
title: HelpContext | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.helpcontext
dev_langs:
- C++
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d9c2efecf34e5d58f633bc21e62801157b1b8955
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388586"
---
# <a name="helpcontext"></a>helpcontext

Určuje ID kontextu, který umožňuje uživateli zobrazit informace o tomto elementu v **pomáhají** souboru.

## <a name="syntax"></a>Syntaxe

```cpp
[ helpcontext(
   id
) ]
```

### <a name="parameters"></a>Parametry

*id*<br/>
ID kontextu téma nápovědy. Zobrazit [HTML Help: Context-Sensitive Help for Your Programs](../mfc/html-help-context-sensitive-help-for-your-programs.md) Další informace o kontextu ID.

## <a name="remarks"></a>Poznámky

**Helpcontext** C++ atribut má stejné funkce jako [helpcontext](/windows/desktop/Midl/helpcontext) atribut MIDL.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [defaultvalue](../windows/defaultvalue.md) příklad, jak používat **helpcontext**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**rozhraní**, **typedef**, **třída**, metoda, vlastnost|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).

## <a name="see-also"></a>Viz také

[IDL – atributy](../windows/idl-attributes.md)<br/>
[Atributy rozhraní](../windows/interface-attributes.md)<br/>
[Atributy třídy](../windows/class-attributes.md)<br/>
[Atributy metody](../windows/method-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](../windows/typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](../windows/helpfile.md)<br/>
[helpstring](../windows/helpstring.md)  