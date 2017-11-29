---
title: "Typy propojení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- no linkage
- linkage [C++], none
- linkage [C++], types of
- types [C++], linkage
- internal linkage, types of linkage
- external linkage, linkage types
ms.assetid: 41326c7f-4602-4bad-a648-697604858ba0
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 154c6a1694055a65eed262055997ba88aa07b18c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="types-of-linkage"></a>Typy propojení
Způsob, jakým jsou názvy objektů a funkcí sdíleny mezi jednotkami překladu, se nazývá propojení. Tyto názvy mohou mít:  
  
-   Vnitřní propojení, při kterém odkazují pouze na prvky programu uvnitř jejich vlastních jednotek překladu. Nejsou sdíleny s ostatními jednotkami.  
  
     Stejný název v jiné jednotce překladu může odkazovat na jiný objekt nebo jinou třídu. O názvech s vnitřním propojením se někdy říká, že jsou lokální vzhledem ke svým jednotkám překladu.  
  
     Příklad deklarace názvu s vnitřním propojením:  
  
    ```  
    static int i;   // The static keyword ensures internal linkage.  
    ```  
  
-   Vnější propojení, u něhož se odkazuje na prvky programu v libovolné jednotce překladu programu – prvek programu je sdílen mezi jednotkami.  
  
     Je zaručeno, že stejný název v jiné jednotce překladu odkazuje na stejný objekt nebo třídu. Názvy s vnějším propojením se někdy označují jako globální.  
  
     Příklad deklarace názvu s vnějším propojením:  
  
    ```  
    extern int i;  
    ```  
  
-   Bez propojení, kdy se odkazuje na jedinečné entity. Stejný název v jiném oboru nemusí odkazovat na stejný objekt. Příkladem je výčet. (Ukazatel na objekt lze však předat bez propojení. Tím je objekt zpřístupněn i v ostatních jednotkách překladu.)  
  
## <a name="see-also"></a>Viz také  
 [Program a propojení](../cpp/program-and-linkage-cpp.md)