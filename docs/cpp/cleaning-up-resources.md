---
title: "Vymazání prostředků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- termination handlers [C++], cleaning up resources
- exception handling [C++], cleaning up resources
- C++ exception handling, termination handlers
- resources [C++], cleaning up
- exception handling [C++], cleanup code
- try-catch keyword [C++], termination handlers
ms.assetid: 65753efe-6a27-4750-b90c-50635775c1b6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1e2f8e8c5fb170d68b28383ae7280be410ee73ce
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cleaning-up-resources"></a>Vymazání prostředků
Při provádění obslužné rutiny ukončení nemusíte před voláním rutiny ukončení vědět, které prostředky jsou ve skutečnosti přiděleny. Je možné, že blok příkazu `__try` byl přerušen dříve, než byly veškeré prostředky přiděleny, takže ne všechny prostředky byly otevřeny.  
  
 Proto byste dříve, než přikročíte k zpracování vyčištění při ukončení, měli z důvodu bezpečnosti zkontrolovat, které prostředky jsou skutečně otevřené. Doporučený postup je:  
  
1.  Inicializovat popisovače na hodnotu NULL.  
  
2.  Přidělit prostředky v bloku příkazu `__try`. Pokud je prostředek přidělen, jsou popisovače nastaveny na kladné hodnoty.  
  
3.  V bloku příkazu `__finally` uvolněte každý prostředek, jehož odpovídající popisovač nebo proměnná příznaku je nenulová nebo není NULL.  
  
## <a name="example"></a>Příklad  
 Například, následující kód používá popisovač ukončení pro uzavření tří souborů a bloku paměti, které byly přiděleny v příkazu `__try`. Před vyčištěním prostředků kód nejprve zkontroluje, zda tyto prostředky byly přiděleny.  
  
```  
// exceptions_Cleaning_up_Resources.cpp  
#include <stdlib.h>  
#include <malloc.h>  
#include <stdio.h>  
#include <windows.h>  
  
void fileOps() {  
   FILE  *fp1 = NULL,  
         *fp2 = NULL,  
         *fp3 = NULL;  
   LPVOID lpvoid = NULL;  
   errno_t err;  
  
   __try {  
      lpvoid = malloc( BUFSIZ );  
  
      err = fopen_s(&fp1, "ADDRESS.DAT", "w+" );  
      err = fopen_s(&fp2, "NAMES.DAT", "w+" );  
      err = fopen_s(&fp3, "CARS.DAT", "w+" );  
   }  
   __finally {  
      if ( fp1 )  
         fclose( fp1 );  
      if ( fp2 )  
         fclose( fp2 );  
      if ( fp3 )  
         fclose( fp3 );  
      if ( lpvoid )  
         free( lpvoid );  
   }  
}  
  
int main() {  
   fileOps();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Zápis obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md)   
 [Strukturované zpracování (C/C++) výjimek](../cpp/structured-exception-handling-c-cpp.md)