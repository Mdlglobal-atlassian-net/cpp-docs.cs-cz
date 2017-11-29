---
title: "C2813 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: C2813
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1eb1d5a0175cb151735c7799d10403cf8eac4944
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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