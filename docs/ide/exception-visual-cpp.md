---
title: "&lt;výjimka&gt; (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- exception
- <exception>
dev_langs: C++
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 687d907b243e62c3fa31b93c0aaebc5180d1cc17
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltexceptiongt-visual-c"></a>&lt;výjimka&gt; (Visual C++)
\<Výjimka > značka umožňuje určit výjimek, které může být vyvolána. Tato značka se použije k definici metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odkaz na výjimku, která je k dispozici z aktuální prostředí kompilace. Pomocí pravidel vyhledávání název kompilátor ověří, že existuje výjimka a překládá `member` na element kanonický název ve výstupu XML.  Kompilátor vydá upozornění, pokud jej nenalezne `member`.  
  
 Uzavřete název v jednoduchých nebo dvojitých uvozovek.  
  
 Informace o tom, jak vytvořit cref odkaz na obecného typu najdete v tématu [ \<najdete v části >](../ide/see-visual-cpp.md).  
  
 `description`  
 Popis.  
  
## <a name="remarks"></a>Poznámky  
 Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.  
  
 Kompilátor Visual C++ se pokusí přeložit cref odkazy v jednom průchodu přes dokumentační komentáře.  Proto pokud pomocí pravidel vyhledávání C++ symbol nebyl nalezen kompilátorem odkaz budou označeny jako nevyřešené. V tématu [ \<seealso >](../ide/seealso-visual-cpp.md) Další informace.  
  
## <a name="example"></a>Příklad  
  
```  
// xml_exception_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_exception_tag.dll  
using namespace System;  
  
/// Text for class EClass.  
public ref class EClass : public Exception {  
   // class definition ...  
};  
  
/// <exception cref="System.Exception">Thrown when... .</exception>  
public ref class TestClass {  
   void Test() {  
      try {  
      }  
      catch(EClass^) {  
      }  
   }  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace XML](../ide/xml-documentation-visual-cpp.md)