---
title: "Chyba kompilátoru C2261 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2261
dev_langs: C++
helpviewer_keywords: C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8269b891ed899501625973b81c1823d4db2d56c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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