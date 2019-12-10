---
title: '> &lt;souhrnuC++ (dokumentační dokumentace)'
ms.date: 11/04/2016
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C++ XML tag
- summary C++ XML tag
ms.assetid: cdeeefbb-1339-45d6-9002-10042a9a2726
ms.openlocfilehash: 0620273f24573539897809b7892d46ad49b7aa57
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988583"
---
# <a name="ltsummarygt"></a>Souhrn &lt;&gt;

K popisu typu nebo členu typu by měla být použita značka \<Summary >. Pomocí [\<poznámky >](remarks-visual-cpp.md) přidat doplňující informace k popisu typu.

## <a name="syntax"></a>Syntaxe

```
<summary>description</summary>
```

#### <a name="parameters"></a>Parametry

*název*<br/>
Souhrn objektu.

## <a name="remarks"></a>Poznámky

Text > Značka \<Summary je jediným zdrojem informací o typu v technologii IntelliSense a je také zobrazen v [Prohlížeč objektů](/visualstudio/ide/viewing-the-structure-of-code) a v webové sestavě komentáře kódu.

Zkompilujte pomocí [/doc](doc-process-documentation-comments-c-cpp.md) a zpracujte dokumentační komentáře do souboru.

## <a name="example"></a>Příklad

```cpp
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
