---
title: '&lt;Hodnota&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: 6add2d7fb6676d631a03d5f6e1764ebf221b4c52
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742508"
---
# <a name="ltvaluegt-visual-c"></a>&lt;Hodnota&gt; (Visual C++)

\<Hodnota > značky umožňuje popisují vlastnosti a metody. Mějte na paměti, že při přidání vlastnosti s kódem průvodce v integrovaném vývojovém prostředí sady Visual Studio přidá [ \<summary >](../ide/summary-visual-cpp.md) značky pro novou vlastnost. Měli byste pak ručně přidat \<hodnota > značka, které popisují hodnotu, která představuje vlastnost.

## <a name="syntax"></a>Syntaxe

```
<value>property-description</value>
```

#### <a name="parameters"></a>Parametry

*property-description*<br/>
Popis pro vlastnost.

## <a name="remarks"></a>Poznámky

Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

## <a name="example"></a>Příklad

```
// xml_value_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_value_tag.dll
using namespace System;
/// Text for class Employee.
public ref class Employee {
private:
   String ^ name;
   /// <value>Name accesses the value of the name data member</value>
public:
   property String ^ Name {
      String ^ get() {
         return name;
      }
      void set(String ^ i) {
         name = i;
      }
   }
};
```

## <a name="see-also"></a>Viz také:

[Dokumentace XML](../ide/xml-documentation-visual-cpp.md)
