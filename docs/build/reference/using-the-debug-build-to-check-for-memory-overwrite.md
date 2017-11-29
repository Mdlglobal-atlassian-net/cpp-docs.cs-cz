---
title: "Přepisování paměti použitím ladění sestavení kontrola | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7b8fc223a1e4e1162ce99bb3275152c49828aa99
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>Kontrola přepisování paměti použitím ladění sestavení
Chcete-li kontrola přepisování paměti pomocí sestavení ladicí verze, musíte nejprve znovu sestavte projekt pro ladění. Potom přejděte na samém začátku vaší aplikace `InitInstance` funkce a přidejte následující řádek:  
  
```  
afxMemDF |= checkAlwaysMemDF;  
```  
  
 Přidělení paměti ladění převádí ochrana bajtů kolem všechny přidělení paměti. Ale tyto ochrana bajtů žádné dobré nedělají nic, pokud jste zkontrolujte, zda nebyly změněny (což může naznačovat přepisování paměti). Jinak hodnota právě poskytuje vyrovnávací paměť, která ve skutečnosti může umožňují rychle získat s přepisování paměti.  
  
 Zapnutím `checkAlwaysMemDF`, vynutí MFC aby volání `AfxCheckMemory` funkce při každém volání **nové** nebo **odstranit** Přišla žádost. Pokud byl zjištěn přepisování paměti, vygeneruje zpráva trasování, který vypadá podobně jako následující:  
  
```  
Damage Occurred! Block=0x5533  
```  
  
 Pokud se zobrazí některá z těchto zpráv, budete muset krokovat kód k určení, kde došlo k poškození. Izolace, přesněji kde přepisování paměti došlo k chybě, můžete provést explicitní volání do `AfxCheckMemory` sami. Příklad:  
  
```  
ASSERT(AfxCheckMemory());  
    DoABunchOfStuff();  
    ASSERT(AfxCheckMemory());  
```  
  
 Pokud se podaří první ASSERT a druhý selže, znamená to, že přepisování paměti musí mít došlo k chybě ve funkci mezi dvěma volání.  
  
 V závislosti na povaze vaší aplikace, můžete zjistit, že `afxMemDF` způsobí, že program spustit příliš pomalu i otestovat. `afxMemDF` Způsobí, že proměnná `AfxCheckMemory` lze volat pro každé volání nové a odstraňovat. V takovém případě by měl bodový vlastní volání `AfxCheckMemory`() jako v příkladu nahoře a pokuste se izolovat paměť přepsat tímto způsobem.  
  
## <a name="see-also"></a>Viz také  
 [Oprava problémů se sestavením pro vydání](../../build/reference/fixing-release-build-problems.md)