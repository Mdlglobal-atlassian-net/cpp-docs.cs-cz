---
title: Přizpůsobení zpracování příkazového řádku jazyka C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _setenvp
- _setargv
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e2691ba3b83cd536c6f0a152bf4de2a855f81e0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="customizing-c-command-line-processing"></a>Přizpůsobení zpracování příkazového řádku jazyka C++
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Pokud aplikace nepřijímá argumenty příkazového řádku, je možné ušetřit malé množství místa potlačením použití rutiny knihovny, která vykonává zpracování příkazového řádku. Tato rutina se nazývá **_setargv –** který je popsán v [rozšíření zástupného znaku](../cpp/wildcard-expansion.md). Chcete-li potlačit jeho použití, definovat rutiny, která nemá žádnou v soubor obsahující **hlavní** funkce a pojmenujte ji **_setargv –**. Volání **_setargv –** pak splňují vaše definice **_setargv –**, a není načtený knihovní verze.  
  
 Podobně pokud máte nikdy přístup k tabulce prostředí prostřednictvím `envp` argument, můžete zadat vlastní prázdný rutiny má být použit místo **_setenvp –**, rutiny zpracování prostředí. Jenom jako s **_setargv –** funkce, **_setenvp –** musí být deklarována jako **extern "C"**.  
  
 Váš program může volat **spawn** nebo `exec` rodiny rutin v běhové knihovny jazyka C. Jde-li o tento případ, neměla by být rutina zpracování prostředí potlačena, protože slouží k předání prostředí z nadřazeného procesu podřízenému procesu.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [main: spuštění programu](../cpp/main-program-startup.md)