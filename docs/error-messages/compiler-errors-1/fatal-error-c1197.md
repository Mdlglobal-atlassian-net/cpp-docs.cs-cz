---
title: "Závažná chyba C1197 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1197
dev_langs: C++
helpviewer_keywords: C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1658e55a9298df703051b856bb9b10dd02d8cc68
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1197"></a>Závažná chyba C1197
nemůže odkazovat 'mscorlib.dll_1', jak program již odkázal 'mscorlib.dll_2.  
  
 Kompilátor odpovídá verzi modulu CLR.  Chcete-li verzi běžné souborů modulu runtime jazyka z předchozí verze byl však proveden pokus o.  
  
 Pokud chcete tuto chybu vyřešit, odkazovat jenom soubory z verze modul common language runtime, který se dodává s verzí aplikace Visual C++ jsou kompilujete s.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C1197:  
  
```  
// C1197.cpp  
// compile with: /clr /c  
// processor: x86  
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197  
// try the following line instead  
// #using "mscorlib.dll"  
```