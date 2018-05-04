---
title: BscMake – odkaz | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BSCMAKE, reference
- Microsoft Browse Information Maintenance Utility
- browse windows
- browse information files (.bsc), building
- .bsc files, building
- bsc files, building
- BSCMAKE
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de8e71a448c71fd18ba9cba99cb9b7347598489c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="bscmake-reference"></a>BSCMAKE – odkaz
> [!WARNING]
> I když BSCMAKE je stále nainstalován pomocí sady Visual Studio, je již používána rozhraní IDE. Od verze Visual Studio 2008 Procházet a symbol informace jsou v soubor SDF SQL serveru ve složce řešení uloženy automaticky.  
  
 Nástroj Údržba informací procházení Microsoft (BSCMAKE. Soubor EXE) vytvoří soubor informací o procházení (.bsc) z .sbr soubory vytvořené během kompilace. Některé nástroje třetích stran používají soubory .bsc pro analýzu kódu. 
  
 Při sestavování vašeho programu vytvoříte soubor procházení informace k aplikaci automaticky, použití BSCMAKE k sestavení souboru. Nemusíte vědět, jak spustit BSCMAKE, pokud vytvoříte váš soubor s informacemi o procházení ve vývojovém prostředí Visual C++. Můžete ale, přečtěte si toto téma pochopit dostupné možnosti.  
  
 Pokud sestavením programu mimo vývojového prostředí, můžete přesto vytvořit vlastní .bsc, který můžete zkontrolovat v prostředí. Spusťte BSCMAKE na .sbr soubory, které jste vytvořili během kompilace.  
  
> [!NOTE]
>  Tento nástroj můžete spustit pouze z příkazového řádku Visual Studio Developer. Nelze ji spustit z příkazového řádku systému nebo v Průzkumníku souborů.  
  
 Tento oddíl obsahuje následující témata:  
  
-   [Sestavení souborů informací o procházení: Přehled](../../build/reference/building-browse-information-files-overview.md)  
  
-   [Sestavení souboru BSC](../../build/reference/building-a-dot-bsc-file.md)  
  
-   [Příkazový řádek BSCMAKE](../../build/reference/bscmake-command-line.md)  
  
-   [Soubor příkazů BSCMAKE](../../build/reference/bscmake-command-file-response-file.md)  
  
-   [Možnosti BSCMAKE](../../build/reference/bscmake-options.md)  
  
-   [BscMake – kódy ukončení](../../build/reference/bscmake-exit-codes.md)  
  
## <a name="see-also"></a>Viz také  
 [Nástroje sestavení C/C++](../../build/reference/c-cpp-build-tools.md)