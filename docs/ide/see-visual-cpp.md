---
title: "&lt;v tématu&gt; (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <see>
- see
dev_langs: C++
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15e1aedefe6d20c181ff208f76a61f49e15f5214
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ltseegt-visual-c"></a>&lt;v tématu&gt; (Visual C++)
\<Najdete v části > značka umožňuje zadat odkaz z v textu. Použití [ \<seealso >](../ide/seealso-visual-cpp.md) označíte, text, který chcete zobrazit v části Viz také.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.  Uzavřete název v jednoduchých nebo dvojitých uvozovek.  
  
 Kompilátor zkontroluje, zda existuje element daného kódu a přeloží `member` k názvu elementu ve výstupu XML.  Kompilátor vydá upozornění, pokud jej nenalezne `member`.  
  
## <a name="remarks"></a>Poznámky  
 Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.  
  
 V tématu [ \<souhrnné >](../ide/summary-visual-cpp.md) příklad použití \<najdete v části >.  
  
 Kompilátor Visual C++ se pokusí přeložit cref odkazy v jednom průchodu přes dokumentační komentáře.  Proto pokud pomocí pravidel vyhledávání C++ symbol nebyl nalezen kompilátorem odkaz budou označeny jako nevyřešené. V tématu [ \<seealso >](../ide/seealso-visual-cpp.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak provést cref odkaz na obecného typu tak, aby kompilátor vyřeší odkaz.  
  
```  
// xml_see_cref_example.cpp  
// compile with: /LD /clr /doc  
// the following cref shows how to specify the reference, such that,  
// the compiler will resolve the reference  
/// <see cref="C{T}">  
/// </see>  
ref class A {};  
  
// the following cref shows another way to specify the reference,   
// such that, the compiler will resolve the reference  
/// <see cref="C < T >"/>  
  
// the following cref shows how to hard-code the reference  
/// <see cref="T:C`1">  
/// </see>  
ref class B {};  
  
/// <see cref="A">  
/// </see>  
/// <typeparam name="T"></typeparam>  
generic<class T>  
ref class C {};  
```  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace XML](../ide/xml-documentation-visual-cpp.md)