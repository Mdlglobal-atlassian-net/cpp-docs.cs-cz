---
title: C3862 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3862
dev_langs:
- C++
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25b0a344eaafedc2f7c0eb60141e3a07fd86c6af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3862"></a>C3862 chyby kompilátoru
'function': Nelze kompilovat nespravované funkce s volbou/CLR: pure nebo/CLR: safe  
  
 **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
 Kompilace pomocí **/CLR: pure** nebo **/CLR: safe** vytvoří MSIL jedinou bitovou kopii, bitovou kopii s žádné nativního kódu (nespravovaný).  Proto nelze použít `unmanaged` – Direktiva pragma v **/CLR: pure** nebo **/CLR: safe** kompilace.  
  
 Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [spravované, nespravované](../../preprocessor/managed-unmanaged.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3862:  
  
```  
// C3862.cpp  
// compile with: /clr:pure /c  
#pragma unmanaged  
void f() {}   // C3862  
```