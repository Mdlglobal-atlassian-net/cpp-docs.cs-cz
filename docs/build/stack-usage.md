---
title: Použití zásobníku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 827a129c0b7a444cc5b48ba68a3e360712e1c08e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721536"
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