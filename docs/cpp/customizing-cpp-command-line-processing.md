---
title: Přizpůsobení zpracování příkazového řádku jazyka C++
ms.date: 11/04/2016
f1_keywords:
- _setenvp
- _setargv
helpviewer_keywords:
- command line [C++], processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line [C++], processing arguments
- suppressing environment processing
- _setenvp function
ms.assetid: aae01cbb-892b-48b8-8e1f-34f22421f263
ms.openlocfilehash: da1b3bdd6392b144f9315add4c19de14c1d14d41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582686"
---
# <a name="customizing-c-command-line-processing"></a>Přizpůsobení zpracování příkazového řádku jazyka C++

## <a name="microsoft-specific"></a>Specifické pro Microsoft

Pokud aplikace nepřijímá argumenty příkazového řádku, je možné ušetřit malé množství místa potlačením použití rutiny knihovny, která vykonává zpracování příkazového řádku. Tato rutina se nazývá `_setargv` a je popsána v [rozšíření zástupného znaku](../cpp/wildcard-expansion.md). Chcete-li potlačení je třeba definovat rutinu, která nemá žádný účinek v soubor obsahující `main` fungovat a pojmenujte ho `_setargv`. Volání `_setargv` je následně splněno definicí `_setargv`, a verze knihovny není načtena.

Podobně pokud nikdy přístup k tabulce prostředí skrze `envp` argument, můžete poskytnout vlastní prázdnou rutinu, který se má použít místo `_setenvp`, rutiny zpracování prostředí. Stejně jako u `_setargv` funkci `_setenvp` musí být deklarována jako **extern "C"**.

Váš program může volat `spawn` nebo `exec` řadu rutin v knihovně C Runtime. Jde-li o tento případ, neměla by být rutina zpracování prostředí potlačena, protože slouží k předání prostředí z nadřazeného procesu podřízenému procesu.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[main: spuštění programu](../cpp/main-program-startup.md)