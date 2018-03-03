---
title: "Chyba kompilátoru C2261 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2261
dev_langs:
- C++
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3907a1d270de11af82462815ce87398e10c50513
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2261"></a>Chyba kompilátoru C2261
'řetězec': odkaz na sestavení je neplatný a nelze jej přeložit  
  
 Hodnotu nebyla platná.  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>slouží k určení přátelského sestavení. Například pokud a.dll chce určit b.dll jako přátelského sestavení, zadali byste (v a.dll): InternalsVisibleTo("b"). Modul runtime pak umožňuje b.dll všechno ve a.dll (s výjimkou privátní typy) přístup.  
  
 Další informace o správné syntaxi při zadávání přátelských sestavení najdete v tématu [přátelských sestavení (C++)](../../dotnet/friend-assemblies-cpp.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2261.  
  
```  
// C2261.cpp  
// compile with: /clr /c  
using namespace System::Runtime::CompilerServices;  
[assembly: InternalsVisibleTo("a,a,a")];   // C2261  
[assembly: InternalsVisibleTo("a.a")];   // OK  
[assembly: InternalsVisibleTo("a")];   // OK  
```