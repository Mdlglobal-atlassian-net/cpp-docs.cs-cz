---
title: Funkce typů | Dokumentace Microsoftu
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
ms.openlocfilehash: 6dfb36dc9e177fdb9ad196c0e2a8ad0f352d5f2d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709563"
---
# <a name="function-types"></a>Typy funkcí

V podstatě existují dva typy funkcí. Funkce, která vyžaduje rámec zásobníku je volána funkce rámce. Funkce, která nevyžaduje blok zásobníku je volána funkce typu list.

Funkce rámce je funkce, která přiděluje místo v zásobníku volání dalších funkcí, ukládá stálé registry a používá zpracování výjimek. Také vyžaduje záznam tabulky funkcí. Funkce rámce vyžaduje prologu a epilogu. Bloková funkce můžete dynamicky přidělit místo v zásobníku a můžete použít ukazatel na rámec. Funkce rámce obsahuje všechny funkce tohoto volání standardní k dispozici.

Pokud funkce rámce nevolá jinou funkci, není to nutné k zarovnání zásobníku (odkazováno v oddíle [přidělení zásobníku](../build/stack-allocation.md)).

Funkce typu list je ten, který nevyžaduje, aby záznam tabulky funkcí. Ho nemůže provádět změny libovolné stálé registry, včetně RSP, což znamená, že nelze volat jakékoli funkce nebo přidělit místo v zásobníku. Je povoleno ji nechte nezarovnaných zásobníku během provádění.

## <a name="see-also"></a>Viz také

[Použití zásobníku](../build/stack-usage.md)
