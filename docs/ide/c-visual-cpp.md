---
title: '&lt;c&gt; (Visual C++) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <c>
dev_langs:
- C++
helpviewer_keywords:
- <c> C++ XML tag
- c C++ XML tag
ms.assetid: 3b23fc0f-e10d-4dd0-b197-48a46cbddd9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74e2fdd2f970ca3c1f177dd8d7ea565757a03a4b
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44312997"
---
# <a name="ltcgt-visual-c"></a>&lt;c&gt; (Visual C++)

\<c > značka označuje, že text v popisu musí být označené jako kód. Použití [ \<kód >](../ide/code-visual-cpp.md) k označení jako kódu více řádků.

## <a name="syntax"></a>Syntaxe

```
<c>text</c>
```

#### <a name="parameters"></a>Parametry

*Text*<br/>
Text, který chcete určit jako kód.

## <a name="remarks"></a>Poznámky

Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

## <a name="example"></a>Příklad

```cpp
// xml_c_tag.cpp
// compile with: /doc /LD
// post-build command: xdcmake xml_c_tag.xdc

/// Text for class MyClass.
class MyClass {
public:
   int m_i;
   MyClass() : m_i(0) {}

   /// <summary><c>MyMethod</c> is a method in the <c>MyClass</c> class.
   /// </summary>
   int MyMethod(MyClass * a) {
      return a -> m_i;
   }
};
```

## <a name="see-also"></a>Viz také

[Dokumentace XML](../ide/xml-documentation-visual-cpp.md)