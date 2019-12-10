---
title: '&lt;SeeAlso > (C++ dokumentační dokumentace)'
ms.date: 11/04/2016
f1_keywords:
- <seealso>
- seealso
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
ms.openlocfilehash: 698db2df462f561acd897d0d0e56b3106a915466
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988602"
---
# <a name="ltseealsogt"></a>&lt;seealso&gt;

Značka > \<SeeAlso umožňuje určit text, který se může objevit v části Viz také. Použijte [\<v části >](see-visual-cpp.md) určete odkaz z textu.

## <a name="syntax"></a>Syntaxe

```
<seealso cref="member"/>
```

#### <a name="parameters"></a>Parametry

*člen*<br/>
Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.  Název uzavřete do jednoduchých nebo dvojitých uvozovek.

Kompilátor kontroluje, zda daný prvek kódu existuje, a překládá `member` na název elementu ve výstupním souboru XML.  Kompilátor vydá upozornění, pokud nenajde `member`.

Informace o tom, jak vytvořit odkaz cref na obecný typ, najdete v tématu [\<](see-visual-cpp.md).

## <a name="remarks"></a>Poznámky

Zkompilujte pomocí [/doc](doc-process-documentation-comments-c-cpp.md) a zpracujte dokumentační komentáře do souboru.

Příklad použití \<SeeAlso > najdete v článku [> souhrnu\<](summary-visual-cpp.md) .

Kompilátor MSVC se pokusí vyřešit odkazy cref v jednom průchodu pomocí dokumentačních komentářů.  Proto pokud použijete pravidla C++ vyhledávání, symbol nebyl nalezen kompilátorem, odkaz bude označen jako nevyřešený.

## <a name="example"></a>Příklad

V následujícím příkladu je odkaz na nerozpoznaný symbol odkazován v cref. Komentář XML pro cref do B:: test bude `<seealso cref="!:B::Test" />`, zatímco odkaz na:: test je ve správném formátu `<seealso cref="M:A.Test" />`.

```cpp
// xml_seealso_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_seealso_tag.dll

/// Text for class A.
public ref struct A {
   /// <summary><seealso cref="A::Test"/>
   /// <seealso cref="B::Test"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void Test() {}
};

/// Text for class B.
public ref struct B {
   void Test() {}
};
```

## <a name="see-also"></a>Viz také:

[Dokumentace XML](xml-documentation-visual-cpp.md)
