---
title: '&lt;oprávnění&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C++ XML tag
- permission C++ XML tag
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
ms.openlocfilehash: ecf027600b23a640d1dc0cd68b75ffa5eb1b3659
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744620"
---
# <a name="ltpermissiongt-visual-c"></a>&lt;oprávnění&gt; (Visual C++)

\<Oprávnění > značky umožňuje dokumentu přístup člena. <xref:System.Security.PermissionSet> Umožňuje určit přístup ke členu.

## <a name="syntax"></a>Syntaxe

```
<permission cref="member">description</permission>
```

#### <a name="parameters"></a>Parametry

*Člen*<br/>
Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje a přeloží `member` k názvu canonical prvku ve výstupním souboru XML.  Název uzavřete do jednoduchých nebo dvojitých uvozovek.

Kompilátor vyvolá upozornění, pokud se nenajde `member`.

Informace o tom, jak vytvořit cref odkaz na obecný typ, naleznete v tématu [ \<naleznete v tématu >](../ide/see-visual-cpp.md).

*description*<br/>
Popis přístup ke členu.

## <a name="remarks"></a>Poznámky

Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.

Kompilátor Visual C++ se pokusí přeložit odkazy cref v jednom průchodu přes komentáře k dokumentaci.  Proto pokud pomocí pravidel vyhledávání C++ symbol nebyl nalezen kompilátorem odkaz bude označen jako nevyřešené. Zobrazit [ \<seealso >](../ide/seealso-visual-cpp.md) Další informace.

## <a name="example"></a>Příklad

```
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

[Dokumentace XML](../ide/xml-documentation-visual-cpp.md)
