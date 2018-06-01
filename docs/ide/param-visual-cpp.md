---
title: '&lt;Param&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- param
- <param>
dev_langs:
- C++
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 01add77f68ac35b4c669391504461dd516b55d3d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33325380"
---
# <a name="ltparamgt-visual-c"></a>&lt;Param&gt; (Visual C++)
\<Param > Značka je třeba používat v komentář pro deklaraci metody k popisu jeden z parametrů pro metodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<param name='name'>description</param>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Název parametru metody.  Uzavřete název v jednoduchých nebo dvojitých uvozovek.  Kompilátor vydá upozornění, pokud jej nenalezne `name`.  
  
 `description`  
 Popis parametru.  
  
## <a name="remarks"></a>Poznámky  
 Text pro \<param > Značka se zobrazí v technologii IntelliSense, [Prohlížeč objektů](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470)a v sestavě webové komentář kódu.  
  
 Kompilovat s [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
  
```  
// xml_param_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_param_tag.dll  
/// Text for class MyClass.  
public ref class MyClass {  
   /// <param name="Int1">Used to indicate status.</param>  
   void MyMethod(int Int1) {  
   }  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace XML](../ide/xml-documentation-visual-cpp.md)