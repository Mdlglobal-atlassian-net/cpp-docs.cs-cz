---
title: "C3862 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3862
dev_langs:
- C++
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 63fa12348ee2ab58782fad02719918bfe7929ff8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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