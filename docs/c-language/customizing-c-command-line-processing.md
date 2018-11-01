---
title: Přizpůsobení zpracování příkazového řádku jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- _spawn functions
- command line, processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line, processing arguments
- suppressing environment processing
- _exec function
ms.assetid: c20fa11d-b35b-4f3e-93b6-2cd5a1c3c993
ms.openlocfilehash: 9f7bc78c20aee4b91bf00fefd2615ba1a6611010
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623593"
---
# <a name="customizing-c-command-line-processing"></a>Přizpůsobení zpracování příkazového řádku jazyka C

Pokud aplikace nepřijímá argumenty příkazového řádku, je možné ušetřit malé množství místa potlačením použití rutiny knihovny, která vykonává zpracování příkazového řádku. Tato rutina se nazývá **_setargv** (nebo **_wsetargv** v prostředí širokých znaků), jak je popsáno v [rozbalení argumentů zástupných znaků](../c-language/expanding-wildcard-arguments.md). Pro potlačení je třeba definovat rutinu, která nemá žádný účinek v obsahující soubor **hlavní** fungovat a pojmenujte ho **_setargv** (nebo **_wsetargv** v širokého znaku prostředí). Volání **_setargv** nebo **_wsetargv** je následně splněno definicí **_setargv** nebo **_wsetargv** , a je knihovní verze Nelze načíst.

Podobně pokud nikdy přístup k tabulce prostředí skrze `envp` argument, můžete poskytnout vlastní prázdnou rutinu, který se má použít místo **_setenvp** (nebo **_wsetenvp**), rutiny zpracování prostředí.

Pokud váš program provede volání **_spawn** nebo **_exec** řadu rutin v knihovny run-time jazyka C, by neměla potlačení rutiny zpracování prostředí, protože tato rutina slouží k předání prostředí z procesu trdliště novému procesu.

## <a name="see-also"></a>Viz také

[main – spuštění funkce a programu](../c-language/main-function-and-program-execution.md)