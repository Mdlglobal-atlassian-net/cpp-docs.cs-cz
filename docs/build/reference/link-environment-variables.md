---
title: Proměnné prostředí LINK
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- variables, environment
- LINK tool [C++], environment variables
- LIB environment variable
- environment variables [C++], LINK
ms.assetid: 9a3d3291-0cc4-4a7d-9d50-80e351b90708
ms.openlocfilehash: 3a398787530794f5a08d6cd122e55c305e265062
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434408"
---
# <a name="link-environment-variables"></a>Proměnné prostředí LINK

Nástroj LINK používá následující proměnné prostředí:

- ODKAZ a \_odkaz\_, pokud je definována. Nástroj LINK připojí na začátek možnosti a argumenty, které jsou definovány v proměnné prostředí LINK a připojí možností a argumentů definované v \_odkaz\_ proměnnou prostředí pro argumenty příkazového řádku před zpracováním.

- LIB, pokud je definována. Nástroje pro propojení používá cesta ke KNIHOVNĚ při hledání objektu, knihovny nebo jiný soubor zadaný v příkazovém řádku nebo pomocí [/základní](../../build/reference/base-base-address.md) možnost. Cesta ke KNIHOVNĚ také používá k nalezení souboru .pdb s názvem v objektu. LIB proměnné může obsahovat jeden nebo více specifikace cesty oddělené středníky. Jedna cesta musí odkazovat na podadresáři \lib instalace sady Visual C++.

- CESTA, je-li nástroj je potřeba spustit CVTRES a nemůže najít soubor ve stejném adresáři jako samotného odkazu. (Odkaz vyžaduje CVTRES propojit soubor .res). Cesta musí odkazovat na podadresáři \bin instalace sady Visual C++.

- TMP, zadejte adresář, při propojování omf – nebo .res souborů.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
[Sestavení kódu C/C++ na příkazovém řádku](../../build/building-on-the-command-line.md)<br/>
[Nastavení cesty a proměnných prostředí pro sestavení příkazového řádku](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)
