---
title: '&lt;c > (C++ dokumentačních komentářů)'
ms.date: 11/04/2016
f1_keywords:
- <c>
helpviewer_keywords:
- <c> C++ XML tag
- c C++ XML tag
ms.assetid: 3b23fc0f-e10d-4dd0-b197-48a46cbddd9f
ms.openlocfilehash: 43e1417e5a749f2ea51346bbf6db235ba08a7bcf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823040"
---
# <a name="ltcgt"></a>&lt;c&gt;

\<c > značka označuje, že text v popisu musí být označené jako kód. Použití [ \<kód >](code-visual-cpp.md) k označení jako kódu více řádků.

## <a name="syntax"></a>Syntaxe

```
<c>text</c>
```

#### <a name="parameters"></a>Parametry

*Text*<br/>
Text, který chcete určit jako kód.

## <a name="remarks"></a>Poznámky

Kompilovat s [/doc](doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

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

## <a name="see-also"></a>Viz také:

[Dokumentace XML](xml-documentation-visual-cpp.md)
