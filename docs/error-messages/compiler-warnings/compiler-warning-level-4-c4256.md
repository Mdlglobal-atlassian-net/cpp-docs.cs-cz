---
title: "Kompilátoru (úroveň 4) upozornění C4256 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4256
dev_langs: C++
helpviewer_keywords: C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4bbaec27948f061cb21eeb432446517d4f9a6b2c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4256"></a>C4256 kompilátoru upozornění (úroveň 4)
'function': konstruktor pro třídu s virtuální základů má...; volání nemusí být kompatibilní se starší verzí aplikace Visual C++  
  
 Možné nekompatibilita.  
  
 Vezměte v úvahu následující příklad kódu. Pokud definice konstruktor S2::S2 (int i,...) byl kompilován s použitím verzi Visual C++ compiler před verze 7, ale v následujícím příkladu je zkompilovat pomocí aktuální verze, volání konstruktoru pro S3 nebude fungovat správně z důvodu konvence volání změnu zvláštní případ. Pokud obě byly zkompilovány pomocí Visual C++ verze 6.0, volání nebude fungovat v pořádku buď, pokud byly předány žádné parametry pro se třemi tečkami.  
  
 Chcete-li odstranit toto upozornění  
  
1.  Nepoužívejte třemi tečkami v konstruktoru.  
  
2.  Zajistěte, aby že všechny součásti v jejich projektu jsou integrované s aktuální verzí (včetně všech knihoven, které může definovat nebo odkazovat na tuto třídu) a zakázat pomocí upozornění [upozornění](../../preprocessor/warning.md) – Direktiva pragma.  
  
 Následující ukázka generuje C4256:  
  
```  
// C4256.cpp  
// compile with: /W4  
// #pragma warning(disable : 4256)  
struct S1  
{  
};  
  
struct S2: virtual public S1  
{  
   S2( int i, ... )    // C4256  
   {  
      i = 0;  
   }  
   /*  
   // try the following line instead  
   S2( int i)  
   {  
      i = 0;  
   }  
   */  
};  
  
void func1()  
{  
   S2 S3( 2, 1, 2 );   // C4256  
   // try the following line instead  
   // S2 S3( 2 );  
}  
  
int main()  
{  
}  
```