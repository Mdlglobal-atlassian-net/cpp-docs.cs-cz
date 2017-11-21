---
title: "Použití zásobníku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c7a74abff7a2971fe66fa2df878078ac95f58fe8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stack-usage"></a>Použití zásobníku
Všechna paměť za adresu aktuální konfigurace je považován za volatile: operačního systému nebo ladicí program, mohou přepsat tuto paměť během ladicí relace uživatele nebo obslužné rutiny přerušení. Konfigurace proto musí být vždy nastaven před pokusem o čtení nebo zápis hodnot rámce zásobníku.  
  
 Tato část pojednává o přidělení zásobníku místa pro místní proměnné a **alloca –** vnitřní.  
  
-   [Přidělení zásobníku](../build/stack-allocation.md)  
  
-   [Zásobník konstrukce dynamické oblasti parametrů](../build/dynamic-parameter-stack-area-construction.md)  
  
-   [Typy funkce](../build/function-types.md)  
  
-   [malloc – zarovnání](../build/malloc-alignment.md)  
  
-   [alloca –](../build/alloca.md)  
  
## <a name="see-also"></a>Viz také  
 [x64 softwarové konvence](../build/x64-software-conventions.md)