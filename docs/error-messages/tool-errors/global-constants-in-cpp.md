---
title: Globální konstanty v jazyku C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- global constants
- constants, global
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f1ee5fdf3d50f30e02bd48fe3664c10d26a8449
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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