---
title: Makra proměnné prostředí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, environment variable macros
- environment variables, macros in NMAKE
- macros, environment-variable
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cebb544b1d8fc8489de298bf7512cc612a6dfef2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701165"
---
# <a name="environment-variable-macros"></a>Makra proměnné prostředí

NMAKE dědí definice maker pro proměnné prostředí, které existují před zahájením relace. Pokud proměnná byla nastavena v prostředí operačního systému, je k dispozici jako makra NMAKE. Zděděné názvy jsou převedeny na velká písmena. Vyvolá se před předzpracování dědičnosti. Pomocí možnosti /E způsobit maker zděděno z proměnné prostředí pro přepsání jakékoli makro se stejným názvem v souboru pravidel.

Makra proměnné prostředí lze redefinovat v relaci, a tím změní příslušné proměnné prostředí. Můžete také změnit proměnných prostředí pomocí příkazu SET. Chcete-li změnit proměnné prostředí v relaci pomocí příkazu SET nezmění odpovídající – makro, ale.

Příklad:

```
PATH=$(PATH);\nonesuch

all:
    echo %PATH%
```

V tomto příkladu mění `PATH` změní příslušné proměnné prostředí `PATH`; přidá `\nonesuch` do cesty.

Pokud proměnná prostředí je definovaný jako řetězec, který by byla syntaxe chybná v souboru pravidel, žádné – makro se vytvoří a je generována bez upozornění. Pokud hodnota proměnné obsahuje znak dolaru ($), NMAKE interpretovat jako začátek volání makra. Použití makra může způsobit neočekávané chování.

## <a name="see-also"></a>Viz také

[Speciální makra NMAKE](../build/special-nmake-macros.md)