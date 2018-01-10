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
ms.workload: cplusplus
ms.openlocfilehash: d6e3aa8d01dcc85b6c37684ccccaf82c84d8dfb3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="stack-usage"></a>Použití zásobníku
Všechna paměť za adresu aktuální konfigurace je považován za volatile: operačního systému nebo ladicí program, mohou přepsat tuto paměť během ladicí relace uživatele nebo obslužné rutiny přerušení. Konfigurace proto musí být vždy nastaven před pokusem o čtení nebo zápis hodnot rámce zásobníku.  
  
 Tato část pojednává o přidělení zásobníku místa pro místní proměnné a **alloca –** vnitřní.  
  
-   [Přidělení zásobníku](../build/stack-allocation.md)  
  
-   [Konstrukce dynamické oblasti zásobníku parametrů](../build/dynamic-parameter-stack-area-construction.md)  
  
-   [Typy funkcí](../build/function-types.md)  
  
-   [malloc – zarovnání](../build/malloc-alignment.md)  
  
-   [alloca](../build/alloca.md)  
  
## <a name="see-also"></a>Viz také  
 [x64 – softwarové konvence](../build/x64-software-conventions.md)