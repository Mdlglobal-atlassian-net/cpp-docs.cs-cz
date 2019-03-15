---
title: '&lt;SeeAlso > (C++ dokumentačních komentářů)'
ms.date: 11/04/2016
f1_keywords:
- <seealso>
- seealso
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
ms.openlocfilehash: ea399e98723a265ef3c17f2282b7c81299b4abc5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823117"
---
# <a name="ltseealsogt"></a>&lt;seealso&gt;

\<Seealso > značky umožňuje zadat text, který chcete zobrazit v části Viz také. Použití [ \<naleznete v tématu >](see-visual-cpp.md) zadat odkaz v rámci textu.

## <a name="syntax"></a>Syntaxe

```
<seealso cref="member"/>
```

#### <a name="parameters"></a>Parametry

*Člen*<br/>
Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.  Název uzavřete do jednoduchých nebo dvojitých uvozovek.

Kompilátor kontroluje, zda daný prvek kódu existuje a odstraňuje `member` do názvu prvku ve výstupním souboru XML.  Kompilátor vyvolá upozornění, pokud se nenajde `member`.

Informace o tom, jak vytvořit cref odkaz na obecný typ, naleznete v tématu [ \<naleznete v tématu >](see-visual-cpp.md).

## <a name="remarks"></a>Poznámky

Kompilovat s [/doc](doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

Zobrazit [ \<summary >](summary-visual-cpp.md) pro příklad použití \<seealso >.

Kompilátor MSVC pokusila přeložit odkazy cref v jednom průchodu přes komentáře k dokumentaci.  Proto pokud pomocí pravidel vyhledávání C++ symbol nebyl nalezen kompilátorem odkaz bude označen jako nevyřešené.

## <a name="example"></a>Příklad

V následujícím příkladu odkazuje cref nevyřešeného symbolu. Komentář XML u cref k B::Test bude `<seealso cref="!:B::Test" />`, že je odkaz na A::Test ve správném formátu `<seealso cref="M:A.Test" />`.

```
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
