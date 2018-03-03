---
title: "Chybějící tělo funkce nebo proměnná | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 356d0f0a71feccee953a0b1bd7dc54bc64a0e233
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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