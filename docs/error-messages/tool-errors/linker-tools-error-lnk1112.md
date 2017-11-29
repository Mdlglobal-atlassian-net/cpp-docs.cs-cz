---
title: "Chyba linkerů Lnk1112 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1112
dev_langs: C++
helpviewer_keywords: LNK1112
ms.assetid: 425793d8-37e6-4072-9b6e-c3d4e9c12562
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8353c8e6baf8072ee45acaa3f4635bc333c03add
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1112"></a>Chyba linkerů LNK1112
modul počítač typu 'type1' v konfliktu s cílový počítač typ 'type2'.  
  
 Zadané jako vstup objektu soubory byly zkompilovány pro typy jiného počítače.  
  
 Například pokud se pokusíte propojit soubor objektu se kompilovat s **/CLR** a soubor objektu kompilovat s **/CLR: pure** (počítač typ CEE), linkeru vygeneruje se chybová zpráva LNK1112.  
  
 Podobně pokud vytvoříte jeden modul s [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] kompilátoru a jiný modul s x86 kompilátoru a pokuste se připojit, je linkeru vygeneruje LNK1112.  
  
 Možných příčin této chyby je, pokud jsou vývoj aplikace s 64-bit, ale nenainstalovali mezi kompilátory Visual C++ 64 bitů. 64bitová verze konfigurace v takovém případě nebudete mít k dispozici. Chcete-li tento problém vyřešit, spusťte instalační program pro sadu Visual Studio a instalaci chybějících součástí C++.  
  
 Této chybě může také dojít, pokud změníte **aktivní konfigurace řešení** v **nástroje Configuration Manager** a potom se pokusíte sestavení projektu, než odstraníte soubory zprostředkující projektu. Chcete-li tuto chybu vyřešit, vyberte **znovu sestavit řešení** z **sestavení** nabídky. Můžete také vybrat **Vyčistit řešení** z **sestavení** nabídce a potom sestavení řešení.  
  
## <a name="see-also"></a>Viz také  
 [Chyby a upozornění Linkerů](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)