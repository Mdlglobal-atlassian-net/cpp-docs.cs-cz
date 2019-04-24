---
title: '&lt;Souhrn > (C++ dokumentačních komentářů)'
ms.date: 11/04/2016
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C++ XML tag
- summary C++ XML tag
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
ms.openlocfilehash: 68bb8b7c269b3406438e5cf21dde7179f7e67646
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318183"
---
# <a name="ltsummarygt"></a>&lt;Souhrn&gt;

\<Summary > Značka by měla sloužit k popisu typu nebo člena typu. Použití [ \<remarks >](remarks-visual-cpp.md) přidat doplňující informace pro popis typu.

## <a name="syntax"></a>Syntaxe

```
<summary>description</summary>
```

#### <a name="parameters"></a>Parametry

*description*<br/>
Přehled objektu.

## <a name="remarks"></a>Poznámky

Text \<summary > značku je jediný zdroj informací o typu v IntelliSense a zobrazí se také v [Prohlížeč objektů](/visualstudio/ide/viewing-the-structure-of-code) a v sestavě webového kódu komentář.

Kompilovat s [/doc](doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

## <a name="example"></a>Příklad

```
// xml_summary_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_summary_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary>MyMethod is a method in the MyClass class.
   /// <para>Here's how you could make a second paragraph in a description. <see cref="System::Console::WriteLine"/> for information about output statements.</para>
   /// <seealso cref="MyClass::MyMethod2"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void MyMethod2() {}
};
```

## <a name="see-also"></a>Viz také:

[Dokumentace XML](xml-documentation-visual-cpp.md)
