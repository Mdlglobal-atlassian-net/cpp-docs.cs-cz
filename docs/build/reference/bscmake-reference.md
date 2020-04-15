---
title: BSCMAKE – odkaz
ms.date: 05/06/2019
helpviewer_keywords:
- BSCMAKE, reference
- Microsoft Browse Information Maintenance Utility
- browse windows
- browse information files (.bsc), building
- .bsc files, building
- bsc files, building
- BSCMAKE
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
ms.openlocfilehash: f95e34b9599de628463b9f92ebf8f01036237891
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320740"
---
# <a name="bscmake-reference"></a>BSCMAKE – odkaz

> [!WARNING]
> Přestože BSCMAKE je stále nainstalován s Visual Studio, je již používán ide. Od aplikace Visual Studio 2008 jsou informace o procházení a symbolech automaticky uloženy v souboru SQL Server .sdf ve složce řešení.

Nástroj Pro procházení informací společnosti Microsoft (BSCMAKE. EXE) vytvoří informační soubor procházení (.bsc) ze souborů .sbr vytvořených během kompilace. Některé nástroje jiných výrobců používají soubory BSC pro analýzu kódu.

Při vytváření programu můžete vytvořit informační soubor procházení pro váš program automaticky pomocí BSCMAKE k vytvoření souboru. Není nutné vědět, jak spustit BSCMAKE, pokud vytvoříte soubor informací proprocházení ve vývojovém prostředí sady Visual Studio. Můžete si však přečíst toto téma, abyste porozuměli dostupným možnostem.

Pokud vytvoříte program mimo vývojové prostředí, můžete stále vytvořit vlastní .bsc, který můžete prozkoumat v prostředí. Spusťte BSCMAKE na souboru .sbr, které jste vytvořili během kompilace.

> [!NOTE]
> Tento nástroj lze spustit pouze z příkazového řádku aplikace Visual Studio Developer. Nelze jej spustit ze systémového příkazového řádku nebo z Průzkumníka souborů.

Tento oddíl obsahuje následující témata:

- [Sestavení souborů informací o procházení: Přehled](building-browse-information-files-overview.md)

- [Vytváření souboru BSC](building-a-dot-bsc-file.md)

- [Příkazový řádek BSCMAKE](bscmake-command-line.md)

- [Soubor příkazů BSCMAKE](bscmake-command-file-response-file.md)

- [Možnosti BSCMAKE](bscmake-options.md)

- [Ukončovací kódy BSCMAKE](bscmake-exit-codes.md)

## <a name="see-also"></a>Viz také

[Další nástroje pro sestavení msvc](c-cpp-build-tools.md)
