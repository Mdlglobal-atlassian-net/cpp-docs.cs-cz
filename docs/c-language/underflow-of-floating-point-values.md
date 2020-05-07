---
title: Podtečení hodnot s plovoucí desetinnou čárkou
ms.date: 11/04/2016
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
ms.openlocfilehash: 93230b50b81ede44a9c55406db1566df2660c1ba
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344063"
---
# <a name="underflow-of-floating-point-values"></a>Podtečení hodnot s plovoucí desetinnou čárkou

**ANSI 4.5.1** Bez ohledu na to, zda matematické funkce `errno` nastavují celočíselný výraz `ERANGE` na hodnotu makra na základě chyb v podtečení rozsahu

Podtečení čísla s plovoucí desetinnou čárkou nenastaví výraz `errno` na hodnotu `ERANGE`. Pokud se hodnota blíží nule a nakonec dojde k podtečení, je hodnota nastavena na nulu.

## <a name="see-also"></a>Viz také

[Funkce knihovny](../c-language/library-functions.md)
