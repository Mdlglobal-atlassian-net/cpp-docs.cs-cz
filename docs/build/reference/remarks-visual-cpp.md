---
title: '&lt;REMARKS > (C++ dokumentačních komentářů)'
ms.date: 11/04/2016
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
ms.openlocfilehash: 0d0c63d55de80f498498a6873dacb5e83fc956b7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823157"
---
# <a name="ltremarksgt"></a>&lt;Poznámky&gt;

\<Remarks > Značka se používá k přidání informací o typu, doplňující informace zadaným [ \<summary >](summary-visual-cpp.md). Tyto informace se zobrazují v [prohlížeče objektů](/visualstudio/ide/viewing-the-structure-of-code) a v sestavě webového kódu komentář.

## <a name="syntax"></a>Syntaxe

```
<remarks>description</remarks>
```

#### <a name="parameters"></a>Parametry

*description*<br/>
Popis člena.

## <a name="remarks"></a>Poznámky

Kompilovat s [/doc](doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

## <a name="example"></a>Příklad

```
// xml_remarks_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_remarks_tag.dll

using namespace System;

/// <summary>
/// You may have some primary information about this class.
/// </summary>
/// <remarks>
/// You may have some additional information about this class.
/// </remarks>
public ref class MyClass {};
```

## <a name="see-also"></a>Viz také:

[Dokumentace XML](xml-documentation-visual-cpp.md)
