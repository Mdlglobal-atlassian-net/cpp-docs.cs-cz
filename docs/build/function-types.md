---
title: Funkce typy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 322bd45abbfe217671fd39f0617987fde21445db
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367648"
---
# <a name="function-types"></a>Typy funkcí
V podstatě existují dva typy funkcí. Funkci, která vyžaduje rámce zásobníku se nazývá funkce rámce. Funkci, která nevyžaduje rámce zásobníku se nazývá funkce listu.  
  
 Bloková funkce je funkce, která přiděluje místo v zásobníku volání jiných funkcí, ukládá stálé registry nebo používá zpracování výjimek. Také budete potřebovat záznam tabulky funkcí. Bloková funkce vyžaduje prolog a epilog. Bloková funkce můžete dynamicky přidělit prostor zásobníku a můžete využít ukazatel na rámec. Bloková funkce má úplné možnosti tohoto volání standardní k dispozici.  
  
 Pokud bloková funkce nevolá jinou funkci, pak není požadováno zarovnání zásobníku (odkazuje v oddíle [přidělení zásobníku](../build/stack-allocation.md)).  
  
 Funkce listu je ten, který nevyžaduje záznam tabulky funkcí. Žádné stálé registry, včetně konfigurace, což znamená, že nelze volat jakékoli funkce nebo přidělit prostor v zásobníku ji nelze provádět změny. Je povoleno nechte nezarovnané zásobníku, když ji spustí.  
  
## <a name="see-also"></a>Viz také  
 [Použití zásobníku](../build/stack-usage.md)
