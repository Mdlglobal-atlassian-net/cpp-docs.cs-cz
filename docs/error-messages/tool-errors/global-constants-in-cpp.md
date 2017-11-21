---
title: "Globální konstanty v jazyku C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f47be9bad6cf7c8ccafac5dc8ce3786f8ada0dfb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="global-constants-in-c"></a>Globální konstanty v jazyku C++
Globální konstanty C++ mít statické propojení. Liší se od C. Pokud se pokusíte použít globální konfiguraci konstant v jazyce C++ ve více souborech získáte nerozpoznané externí chyby. Kompilátor optimalizuje globální konstanty out nezbývá vyhrazeno pro proměnnou místo.  
  
 Jeden způsob, jak tuto chybu vyřešit, je const inicializacích zahrnout soubor hlaviček a zahrnutí této hlavičky do CPP souborů, pokud je to nezbytné, stejně, jako kdyby byl prototyp funkce. Další možností je vytvořit proměnnou nekonstantní a použít odkaz na konstantní při posuzování ho.  
  
 Následující ukázka generuje C2019:  
  
```  
// global_constants.cpp  
// LNK2019 expected  
void test(void);  
const int lnktest1 = 0;  
  
int main() {  
   test();  
}  
```  
  
 A pak  
  
```  
// global_constants_2.cpp  
// compile with: global_constants.cpp  
extern int lnktest1;  
  
void test() {  
  int i = lnktest1;   // LNK2019  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Chyba linkerů LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)