---
title: '> hodnot &lt;(C++ dokumentační dokumentace)'
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: de84d1faca59a6c8e4f82fba3605cbd54a05bd2e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988593"
---
# <a name="ltvaluegt"></a>&lt;value&gt;

Hodnota \<> tag umožňuje popsat vlastnosti a přístupové metody vlastností. Všimněte si, že při přidání vlastnosti s průvodcem kódem v integrovaném vývojovém prostředí sady Visual Studio bude přidána značka [\<souhrnu](summary-visual-cpp.md) pro novou vlastnost. Měli byste pak ručně přidat \<Value > tag k popisu hodnoty, kterou vlastnost představuje.

## <a name="syntax"></a>Syntaxe

```
<value>property-description</value>
```

#### <a name="parameters"></a>Parametry

*property-description*<br/>
Popis vlastnosti

## <a name="remarks"></a>Poznámky

Zkompilujte pomocí [/doc](doc-process-documentation-comments-c-cpp.md) a zpracujte dokumentační komentáře do souboru.

## <a name="example"></a>Příklad

```cpp
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

[Dokumentace XML](xml-documentation-visual-cpp.md)
