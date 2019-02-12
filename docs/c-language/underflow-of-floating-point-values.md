---
title: Podtečení hodnot s plovoucí desetinnou čárkou
ms.date: 11/04/2016
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
ms.openlocfilehash: 93230b50b81ede44a9c55406db1566df2660c1ba
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149922"
---
# <a name="underflow-of-floating-point-values"></a>Podtečení hodnot s plovoucí desetinnou čárkou

**ANSI 4.5.1** Určuje, zda matematické funkce nastaví celočíselný výraz `errno` hodnotu makra `ERANGE` chybách podtečení rozsahu

Podtečení čísla s plovoucí desetinnou čárkou nenastaví výraz `errno` na hodnotu `ERANGE`. Pokud se hodnota blíží nule a nakonec dojde k podtečení, je hodnota nastavena na nulu.

## <a name="see-also"></a>Viz také:

[Funkce knihovny](../c-language/library-functions.md)
