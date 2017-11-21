---
title: "Chybějící tělo funkce nebo proměnná | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba591b6bba935ff5ee6669dd0feb62fb9bd05177
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="missing-function-body-or-variable"></a>Chybějící tělo funkce nebo proměnná
S právě funkce prototyp kompilátor můžete pokračovat bez chyby, ale linkeru nemůže vyřešit volání na adresu, protože není žádný kód funkce nebo proměnná místa vyhrazeného. Tato chyba se se nezobrazí, dokud vytvoříte volání funkce, která musíte vyřešit linkeru.  
  
## <a name="example"></a>Příklad  
 Volání funkce v hlavní způsobí LNK2019, protože prototyp, umožníte kompilátoru myslíte, že funkce existuje.  Linkeru zjistí, že nepodporuje.  
  
```  
// LNK2019_MFBV.cpp  
// LNK2019 expected  
void DoSomething(void);  
int main() {  
   DoSomething();  
}  
```  
  
## <a name="example"></a>Příklad  
 V jazyce C++ Ujistěte se, jestli jste zahrnuli implementace konkrétní funkce pro třídy a ne jenom prototyp v definici třídy. Pokud jsou definice třídy mimo soubor hlaviček, nezapomeňte použít název třídy před funkce (`Classname::memberfunction`).  
  
```  
// LNK2019_MFBV_2.cpp  
// LNK2019 expected  
struct A {  
   static void Test();  
};  
  
// Should be void A::Test() {}  
void Test() {}  
  
int main() {  
   A AObject;  
   AObject.Test();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Chyba linkerů LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)