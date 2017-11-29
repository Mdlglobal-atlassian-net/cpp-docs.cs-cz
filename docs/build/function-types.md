---
title: Funkce typy | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d43daef2095fb63bd79644c940627754e00e199b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="function-types"></a>Typy funkcí
V podstatě existují dva typy funkcí. Funkci, která vyžaduje rámce zásobníku se nazývá funkce rámce. Funkci, která nevyžaduje rámce zásobníku se nazývá funkce listu.  
  
 Bloková funkce je funkce, která přiděluje místo v zásobníku volání jiných funkcí, ukládá stálé registry nebo používá zpracování výjimek. Také budete potřebovat záznam tabulky funkcí. Bloková funkce vyžaduje prolog a epilog. Bloková funkce můžete dynamicky přidělit prostor zásobníku a můžete využít ukazatel na rámec. Bloková funkce má úplné možnosti tohoto volání standardní k dispozici.  
  
 Pokud bloková funkce nevolá jinou funkci, pak není požadováno zarovnání zásobníku (odkazuje v oddíle [přidělení zásobníku](../build/stack-allocation.md)).  
  
 Funkce listu je ten, který nevyžaduje záznam tabulky funkcí. Žádné stálé registry, včetně konfigurace, což znamená, že nelze volat jakékoli funkce nebo přidělit prostor v zásobníku ji nelze provádět změny. Je povoleno nechte nezarovnané zásobníku, když ji spustí.  
  
## <a name="see-also"></a>Viz také  
 [Použití zásobníku](../build/stack-usage.md)