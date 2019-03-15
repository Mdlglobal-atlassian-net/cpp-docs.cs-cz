---
title: BSCMAKE – odkaz
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, reference
- Microsoft Browse Information Maintenance Utility
- browse windows
- browse information files (.bsc), building
- .bsc files, building
- bsc files, building
- BSCMAKE
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
ms.openlocfilehash: 4303e48e3d02f0f69b177e8a888157a6f90aaa89
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822350"
---
# <a name="bscmake-reference"></a>BSCMAKE – odkaz

> [!WARNING]
> Přestože BSCMAKE je stále instalace sady Visual Studio, se už používá integrovaným vývojovým prostředím. Od verze Visual Studio 2008 je automaticky uloženy informace o procházení a symbol v soubor SDF SQL serveru ve složce řešení.

Nástroj Údržba informací procházení Microsoft (BSCMAKE. (EXE) vytvoří soubor informací o procházení (.bsc) z soubory .sbr vytvořené během kompilace. Některé nástroje třetích stran soubory .bsc použít pro analýzu kódu.

Když vytvoříte aplikaci, vytvoříte informačního souboru procházení pro váš program automaticky, pomocí nástroje BSCMAKE pro sestavení souboru. Nepotřebujete vědět, jak spustit nástroje BSCMAKE vytváření informačního souboru procházení ve vývojovém prostředí Visual C++. Můžete však chtít přečtěte si toto téma pochopit dostupné možnosti.

Pokud vytváříte program mimo vývojové prostředí, můžete stále vytvořit vlastní .bsc, které můžete zkontrolovat v prostředí. BscMake – spouštět soubory .sbr, které jste vytvořili během kompilace.

> [!NOTE]
>  Tento nástroj můžete spustit pouze z příkazového řádku pro vývojáře Visual Studio. Nelze provést toto spuštění z příkazového řádku systému nebo Průzkumníka souborů.

Tento oddíl obsahuje následující témata:

- [Sestavení souborů s informacemi o procházení: Přehled](building-browse-information-files-overview.md)

- [Sestavení souboru .bsc](building-a-dot-bsc-file.md)

- [BscMake – příkazový řádek](bscmake-command-line.md)

- [Soubor příkazů BSCMAKE](bscmake-command-file-response-file.md)

- [Možnosti BSCMAKE](bscmake-options.md)

- [BscMake – kódy ukončení](bscmake-exit-codes.md)

## <a name="see-also"></a>Viz také:

[Nástroje pro vytváření dalších MSVC](c-cpp-build-tools.md)
