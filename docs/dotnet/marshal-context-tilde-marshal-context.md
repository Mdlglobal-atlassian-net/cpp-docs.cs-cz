---
title: "marshal_context –:: ~ marshal_context | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- marshal_context::~marshal_context
- msclr.interop.marshal_context.~marshal_context
- marshal_context.~marshal_context
- msclr::interop::marshal_context::~marshal_context
- ~marshal_context
dev_langs: C++
helpviewer_keywords: marshal_context class [C++], operations
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cb052c27888bf168206c80fc06edd24034880433
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="marshalcontextmarshalcontext"></a>marshal_context::~marshal_context
Zničí `marshal_context` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
~marshal_context();  
```  
  
## <a name="remarks"></a>Poznámky  
 Některé konverze datových vyžadují zařazování kontextu. V tématu [přehled zařazování v jazyku C++](../dotnet/overview-of-marshaling-in-cpp.md) Další informace o které překlady vyžadují kontextu a má zařazování souborů, které mají být zahrnuty do vaší aplikace.  
  
 Odstranění `marshal_context` objekt zruší platnost dat převedených pomocí tohoto kontextu. Pokud chcete zachovat data po `marshal_context` zničena objektu, musíte ručně zkopírovat data do proměnné, která zachová.  
  
## <a name="requirements"></a>Požadavky  
 **Soubor hlaviček:** \<msclr\marshal.h >, \<msclr\marshal_windows.h >, \<msclr\marshal_cppstd.h >, nebo \<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>Viz také  
 [Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)   
 [marshal_context – třída](../dotnet/marshal-context-class.md)