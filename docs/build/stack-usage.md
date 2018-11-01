---
title: Použití zásobníku
ms.date: 11/04/2016
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
ms.openlocfilehash: 5ee9da50a03e1137ed6543cd349481148c9127d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452218"
---
# <a name="stack-usage"></a>Použití zásobníku

Všechny paměti větší než aktuální adresu RSP se považuje za volatile: operačního systému nebo ladicího programu, mohou přepsat tuto paměť během uživatelské relace ladění nebo obslužné rutiny přerušení. RSP proto musí být vždycky nastavená před pokusem o čtení nebo zápisu hodnot do bloku zásobníku.

Tato část pojednává o přidělení zásobníku prostoru pro místní proměnné a **alloca** vnitřní.

- [Přidělení zásobníku](../build/stack-allocation.md)

- [Konstrukce dynamické oblasti zásobníku parametrů](../build/dynamic-parameter-stack-area-construction.md)

- [Typy funkcí](../build/function-types.md)

- [malloc – zarovnání](../build/malloc-alignment.md)

- [alloca](../build/alloca.md)

## <a name="see-also"></a>Viz také

[x64 – softwarové konvence](../build/x64-software-conventions.md)