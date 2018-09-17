---
title: Proměnné prostředí LINK | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- variables, environment
- LINK tool [C++], environment variables
- LIB environment variable
- environment variables [C++], LINK
ms.assetid: 9a3d3291-0cc4-4a7d-9d50-80e351b90708
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e88ac63ace95ac0b9874dc3376210f3f5b4af320
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716649"
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
