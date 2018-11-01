---
title: Podtečení hodnot s plovoucí desetinnou čárkou
ms.date: 11/04/2016
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
ms.openlocfilehash: cd4aadc5ab006b79a43e31348fa101d40e8ca03a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477360"
---
# <a name="underflow-of-floating-point-values"></a>Podtečení hodnot s plovoucí desetinnou čárkou

**ANSI 4.5.1** Určuje, zda matematické funkce nastaví celočíselný výraz `errno` hodnotu makra `ERANGE` chybách podtečení rozsahu

Podtečení čísla s plovoucí desetinnou čárkou nenastaví výraz `errno` na hodnotu `ERANGE`. Pokud se hodnota blíží nule a nakonec dojde k podtečení, je hodnota nastavena na nulu.

## <a name="see-also"></a>Viz také

[Funkce knihovny](../c-language/library-functions.md)