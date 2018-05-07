---
title: C2441 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2441
dev_langs:
- C++
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6557e913f2bd34fda9d435d44020697a925af4e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2441"></a>C2441 chyby kompilátoru
"proměnné": symbol deklarovat s __declspec(process) musí být const v/CLR: pure režimu  
  
 **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
 Ve výchozím nastavení, proměnné jsou v každé doméně aplikace v rámci **/CLR: pure**. Proměnné označené `__declspec(process)` pod **/CLR: pure** jsou náchylné na chyby, pokud je upravena v doméně jednu aplikaci a číst v jiném.  
  
 Proto kompilátor vynucuje podle procesu, proměnné se `const` pod **/CLR: pure**, provádění je číst pouze ve všech doménách aplikace.  
  
 Další informace najdete v tématu [proces](../../cpp/process.md) a [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2441.  
  
```  
// C2441.cpp  
// compile with: /clr:pure /c  
__declspec(process) int i;   // C2441  
__declspec(process) const int j = 0;   // OK  
```