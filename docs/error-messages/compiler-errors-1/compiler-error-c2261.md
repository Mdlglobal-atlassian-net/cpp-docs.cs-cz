---
title: Chyba kompilátoru C2261 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2261
dev_langs:
- C++
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45050daf3149cd813fb23b5814be5fe49c375f03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170463"
---
# <a name="compiler-error-c2261"></a>Chyba kompilátoru C2261
'řetězec': odkaz na sestavení je neplatný a nelze jej přeložit  
  
 Hodnotu nebyla platná.  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> slouží k určení přátelského sestavení. Například pokud a.dll chce určit b.dll jako přátelského sestavení, zadali byste (v a.dll): InternalsVisibleTo("b"). Modul runtime pak umožňuje b.dll všechno ve a.dll (s výjimkou privátní typy) přístup.  
  
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