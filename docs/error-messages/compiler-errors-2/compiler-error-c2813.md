---
title: C2813 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- C2813
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 253f0d54b603c2b859f806053a906378025a39ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2813"></a>C2813 chyby kompilátoru
\#Import není podporován s /MP  
  
 C2813 jsou vydávány v příkazu kompilátoru zadáte-li **/MP** – možnost kompilátoru a dva nebo více souborů pro kompilaci a jeden nebo více souborů obsahuje[#import](../../preprocessor/hash-import-directive-cpp.md) direktivy preprocesoru. [#Import](../../preprocessor/hash-import-directive-cpp.md) – direktiva vygeneruje třídy C++ typy v knihovně zadaný typ a poté zapíše tyto třídy dva soubory hlaviček. [#Import](../../preprocessor/hash-import-directive-cpp.md) – direktiva není podporována, protože pokud několika kompilačních jednotek import stejné knihovny typů, tyto jednotky konfliktu při pokusu o zápis stejné soubory, které záhlaví ve stejnou dobu.  
  
 Tato chyba kompilátoru a **/MP** – možnost kompilátoru jsou nové v sadě Visual Studio 2008.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2813. Příkazový řádek v "kompilovat s:" komentář označuje kompilátoru používat **/MP** a **/c** – možnosti kompilátoru zkompilovat několik souborů. Obsahuje nejméně jeden ze souborů [#import](../../preprocessor/hash-import-directive-cpp.md) – direktiva. Ke stejnému souboru dvakrát z důvodu testování v tomto příkladu používáme.  
  
```  
// C2813.cpp  
// compile with: /MP /c C2813.cpp C2813.cpp  
#import "C:\windows\system32\stdole2.tlb"   // C2813  
int main()   
{  
}  
```