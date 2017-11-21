---
title: marshal_context::marshal_context | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- msclr::interop::marshal_context::marshal_context
- marshal_context::marshal_context
- msclr.interop.marshal_context.marshal_context
- marshal_context.marshal_context
dev_langs: C++
helpviewer_keywords: marshal_context class [C++], operations
ms.assetid: 5f08c895-60b0-4f72-97ff-7ae37c68e853
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0ce4837f4e3820544852f5ca535a24ee4ed46cb0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::marshal_context
Vytvoří `marshal_context` objekt, který chcete použít pro převod data mezi spravovanými, nativními datové typy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
marshal_context();  
```  
  
## <a name="remarks"></a>Poznámky  
 Některé konverze datových vyžadují zařazování kontextu. V tématu [přehled zařazování v jazyku C++](../dotnet/overview-of-marshaling-in-cpp.md) Další informace o které překlady vyžadují kontextu a má zařazování souborů, které mají být zahrnuty do vaší aplikace.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [marshal_context::marshal_as](../dotnet/marshal-context-marshal-as.md).  
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, nebo \<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>Viz také  
 [Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)   
 [marshal_context – třída](../dotnet/marshal-context-class.md)