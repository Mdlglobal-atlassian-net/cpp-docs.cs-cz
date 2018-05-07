---
title: Kompilátoru (úroveň 4) upozornění C4289 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4289
dev_langs:
- C++
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f7f09bd85d3740d43b6e4b6a80ed562f8cc2261
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4289"></a>C4289 kompilátoru upozornění (úroveň 4)
používá nestandardní rozšíření: 'var': řídicí proměnná smyčky deklarovaná ve smyčce For je použita mimo rozsah smyčky For  
  
 Při kompilaci s [/Ze](../../build/reference/za-ze-disable-language-extensions.md) a **/Zc:forScope-**, proměnná definovaná v [pro](../../cpp/for-statement-cpp.md) smyčky byl použit po **pro**-cykly oboru.  
  
 V tématu [/Zc:forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) informace o tom, jak zadat standardní chování v **pro** cyklu s **/Ze**.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
 Následující ukázka generuje C4289:  
  
```  
// C4289.cpp  
// compile with: /W4 /Zc:forScope-  
#pragma warning(default:4289)  
int main() {  
   for (int i = 0 ; ; )   // C4289  
      break;  
   i++;  
}  
```