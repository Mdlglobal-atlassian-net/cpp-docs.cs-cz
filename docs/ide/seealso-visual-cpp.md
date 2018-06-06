---
title: '&lt;Viz také&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <seealso>
- seealso
dev_langs:
- C++
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a726a2fa1694fd346a6632fdc5e40bd53547fc8
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33334305"
---
# <a name="ltseealsogt-visual-c"></a>&lt;Viz také&gt; (Visual C++)
\<Seealso > značka umožňuje zadat text, který chcete zobrazit v části Viz také. Použití [ \<najdete v části >](../ide/see-visual-cpp.md) zadat odkaz z v textu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace.  Uzavřete název v jednoduchých nebo dvojitých uvozovek.  
  
 Kompilátor zkontroluje, zda existuje element daného kódu a přeloží `member` k názvu elementu ve výstupu XML.  Kompilátor vydá upozornění, pokud jej nenalezne `member`.  
  
 Informace o tom, jak vytvořit cref odkaz na obecného typu najdete v tématu [ \<najdete v části >](../ide/see-visual-cpp.md).  
  
## <a name="remarks"></a>Poznámky  
 Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.  
  
 V tématu [ \<souhrnné >](../ide/summary-visual-cpp.md) příklad použití \<seealso >.  
  
 Kompilátor Visual C++ se pokusí přeložit cref odkazy v jednom průchodu přes dokumentační komentáře.  Proto pokud pomocí pravidel vyhledávání C++ symbol nebyl nalezen kompilátorem odkaz budou označeny jako nevyřešené.  
  
## <a name="example"></a>Příklad  
 V následující ukázce nerozpoznané symbol odkazuje cref. Komentáře kódu XML pro cref k B::Test bude `<seealso cref="!:B::Test" />`, že je odkaz na A::Test ve správném formátu `<seealso cref="M:A.Test" />`.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Dokumentace XML](../ide/xml-documentation-visual-cpp.md)