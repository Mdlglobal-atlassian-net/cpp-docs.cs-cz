---
title: '> oprávnění &lt;(C++ dokumentační dokumentace)'
ms.date: 11/04/2016
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C++ XML tag
- permission C++ XML tag
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
ms.openlocfilehash: e7f0a59c85e3fa28d24e44953e207151c3afa0f4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988679"
---
# <a name="ltpermissiongt"></a>&lt;oprávnění&gt;

> Značka \<oprávnění umožňuje dokumentovat přístup člena. <xref:System.Security.PermissionSet> umožňuje zadat přístup ke členu.

## <a name="syntax"></a>Syntaxe

```
<permission cref="member">description</permission>
```

#### <a name="parameters"></a>Parametry

*člen*<br/>
Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje, a překládá `member` na název kanonického prvku ve výstupním souboru XML.  Název uzavřete do jednoduchých nebo dvojitých uvozovek.

Kompilátor vydá upozornění, pokud nenajde `member`.

Informace o tom, jak vytvořit odkaz cref na obecný typ, najdete v tématu [\<](see-visual-cpp.md).

*název*<br/>
Popis přístupu ke členovi.

## <a name="remarks"></a>Poznámky

Zkompilujte pomocí [/doc](doc-process-documentation-comments-c-cpp.md) a zpracujte dokumentační komentáře do souboru.

Kompilátor MSVC se pokusí vyřešit odkazy cref v jednom průchodu pomocí dokumentačních komentářů.  Proto pokud použijete pravidla C++ vyhledávání, symbol nebyl nalezen kompilátorem, odkaz bude označen jako nevyřešený. Další informace najdete v tématu [\<seealso >](seealso-visual-cpp.md) .

## <a name="example"></a>Příklad

```cpp
// xml_permission_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_permission_tag.dll
using namespace System;
/// Text for class TestClass.
public ref class TestClass {
   /// <permission cref="System::Security::PermissionSet">Everyone can access this method.</permission>
   void Test() {}
};
```

## <a name="see-also"></a>Viz také:

[Dokumentace XML](xml-documentation-visual-cpp.md)
