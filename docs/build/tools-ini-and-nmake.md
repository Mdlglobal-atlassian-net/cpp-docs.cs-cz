---
title: Tools.ini a příkaz NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
ms.openlocfilehash: 1a8673741cb49c504855fb1af00dbdc06379210d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654412"
---
# <a name="toolsini-and-nmake"></a>Tools.ini a příkaz NMAKE

NMAKE přečte Tools.ini předtím, než se načte soubory pravidel, pokud se nepoužije/r. Hledá Tools.ini nejprve v aktuálním adresáři a potom do adresáře určené proměnnou prostředí INIT. V části Nastavení NMAKE v souboru inicializace začíná `[NMAKE]` a může obsahovat jakékoli informace o souboru pravidel. Zadejte komentář na samostatný řádek začínající znakem čísla (#).

## <a name="see-also"></a>Viz také

[Spuštění příkazu NMAKE](../build/running-nmake.md)