---
title: '&lt;Příklad > (C++ dokumentačních komentářů)'
ms.date: 11/04/2016
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C++ XML tag
- example C++ XML tag
ms.assetid: c821aaa7-7ea7-4bee-9922-6705ad57f877
ms.openlocfilehash: 69e4ad8315948c9c77e99f6ebece4debbe3831b5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823041"
---
# <a name="ltexamplegt"></a>&lt;Příklad&gt;

\<Příklad > značky vám umožní určit příklad použití metody nebo jiný člen knihovny. Obvykle to by také zahrnovat použití [ \<kód >](code-visual-cpp.md) značky.

## <a name="syntax"></a>Syntaxe

```
<example>description</example>
```

#### <a name="parameters"></a>Parametry

*description*<br/>
Popis ukázky kódu.

## <a name="remarks"></a>Poznámky

Kompilovat s [/doc](doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

## <a name="example"></a>Příklad

```
// xml_example_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_example_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary>
   /// GetZero method
   /// </summary>
   /// <example> This sample shows how to call the GetZero method.
   /// <code>
   /// int main()
   /// {
   ///    return GetZero();
   /// }
   /// </code>
   /// </example>
   static int GetZero() {
      return 0;
   }
};
```

## <a name="see-also"></a>Viz také:

[Dokumentace XML](xml-documentation-visual-cpp.md)
