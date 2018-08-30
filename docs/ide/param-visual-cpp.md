---
title: '&lt;Param&gt; (Visual C++) | Dokumentace Microsoftu'
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
ms.openlocfilehash: 1f8fae2d8af1b7121290bfbd42b2668afc50034c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217250"
---
# <a name="ltparamgt-visual-c"></a>&lt;Param&gt; (Visual C++)
\<Param > značky byste měli použít ve komentář pro deklaraci metody, popisující jeden z parametrů pro metodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<param name='name'>description</param>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Název parametru metody.  Název uzavřete do jednoduchých nebo dvojitých uvozovek.  Kompilátor vyvolá upozornění, pokud se nenajde `name`.  
  
 `description`  
 Popis pro parametr.  
  
## <a name="remarks"></a>Poznámky  
 Text \<param > značky se zobrazí v IntelliSense, [prohlížeče objektů](https://msdn.microsoft.com/f89acfc5-1152-413d-9f56-3dc16e3f0470)a v sestavě webového kódu komentář.  
  
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