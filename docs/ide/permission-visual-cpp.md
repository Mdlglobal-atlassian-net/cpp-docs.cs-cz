---
title: '&lt;oprávnění&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- permission
- <permission>
dev_langs:
- C++
helpviewer_keywords:
- <permission> C++ XML tag
- permission C++ XML tag
ms.assetid: 537ee2bc-95bd-48e4-9ce6-3420c3da87f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e13824780a5c73d4423bd544a97108b45d1b770a
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33324080"
---
# <a name="ltpermissiongt-visual-c"></a>&lt;oprávnění&gt; (Visual C++)
\<Oprávnění > značka umožňuje dokumentu přístup člena. <xref:System.Security.PermissionSet> Umožňuje zadat přístup k členem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor zkontroluje, zda existuje element daného kódu a překládá `member` na element kanonický název ve výstupu XML.  Uzavřete název v jednoduchých nebo dvojitých uvozovek.  
  
 Kompilátor vydá upozornění, pokud jej nenalezne `member`.  
  
 Informace o tom, jak vytvořit cref odkaz na obecného typu najdete v tématu [ \<najdete v části >](../ide/see-visual-cpp.md).  
  
 `description`  
 Popis přístup ke členu.  
  
## <a name="remarks"></a>Poznámky  
 Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.  
  
 Kompilátor Visual C++ se pokusí přeložit cref odkazy v jednom průchodu přes dokumentační komentáře.  Proto pokud pomocí pravidel vyhledávání C++ symbol nebyl nalezen kompilátorem odkaz budou označeny jako nevyřešené. V tématu [ \<seealso >](../ide/seealso-visual-cpp.md) Další informace.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Dokumentace XML](../ide/xml-documentation-visual-cpp.md)