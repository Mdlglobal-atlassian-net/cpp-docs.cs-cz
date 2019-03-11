---
title: '&lt;Poznámky&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- <remarks> C++ XML tag
- remarks C++ XML tag
ms.assetid: c820083b-3192-40ab-9ec8-1472c55b4247
ms.openlocfilehash: 2a897b20cbee797bd1e9a7477e30460f2ed4064c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748980"
---
# <a name="ltremarksgt-visual-c"></a>&lt;Poznámky&gt; (Visual C++)

\<Remarks > Značka se používá k přidání informací o typu, doplňující informace zadaným [ \<summary >](../ide/summary-visual-cpp.md). Tyto informace se zobrazují v [prohlížeče objektů](/visualstudio/ide/viewing-the-structure-of-code) a v sestavě webového kódu komentář.

## <a name="syntax"></a>Syntaxe

```
<remarks>description</remarks>
```

#### <a name="parameters"></a>Parametry

*description*<br/>
Popis člena.

## <a name="remarks"></a>Poznámky

Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

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

[Dokumentace XML](../ide/xml-documentation-visual-cpp.md)
