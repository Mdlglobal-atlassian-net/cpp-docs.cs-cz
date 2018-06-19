---
title: Sestavení pro vydání | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3ae18c5e2dcdb735880509fd158dac4ccaa1462
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376647"
---
# <a name="release-builds"></a>Sestavení pro vydání
Sestavení pro vydání používá optimalizace. Použijete-li optimalizace vytvořit sestavení pro vydání, nebude kompilátor vytvořit symbolické ladicí informace. Neexistence symbolické ladicí informace, společně s fakt, že kód není vygenerovat pro trasování a ASSERT volá, znamená to, že se snižuje velikost spustitelného souboru a proto bude rychlejší.  
  
 V této části naleznete informace o proč a kdy chcete změnit z sestavení ladicí verze na sestavení pro vydání. Popisuje také některé problémy, se můžete setkat při změně ladění na sestavení pro vydání:  
  
-   [Vytváření sestavení pro vydání](../../build/reference/how-to-create-a-release-build.md)  
  
-   [Běžné problémy při vytváření sestavení pro vydání](../../build/reference/common-problems-when-creating-a-release-build.md)  
  
-   [Oprava problémů se sestavením pro vydání](../../build/reference/fixing-release-build-problems.md)  
  
    -   [Zkoumání ASSERT – příkazy](../../build/reference/using-verify-instead-of-assert.md)  
  
    -   [Přepisování paměti použitím ladění sestavení ke kontrole](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)  
  
    -   [Ladění sestavení pro vydání](../../build/reference/how-to-debug-a-release-build.md)  
  
    -   [Kontrola přepisů paměti](../../build/reference/checking-for-memory-overwrites.md)  
  
## <a name="see-also"></a>Viz také  
 [Sestavení projektů C++ v sadě Visual Studio](../../ide/building-cpp-projects-in-visual-studio.md)   
 [Referenční zdroje k sestavení programu v jazyce C/C++](../../build/reference/c-cpp-building-reference.md)