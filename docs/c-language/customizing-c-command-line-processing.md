---
title: "Přizpůsobení zpracování příkazového řádku jazyka C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 60f0c14382190cb724c4e4a84488006c54813558
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="customizing-c-command-line-processing"></a>Přizpůsobení zpracování příkazového řádku jazyka C
Pokud aplikace nepřijímá argumenty příkazového řádku, je možné ušetřit malé množství místa potlačením použití rutiny knihovny, která vykonává zpracování příkazového řádku. Tato rutina se nazývá **_setargv –** (nebo **_wsetargv** v prostředí široká charakterová), jak je popsáno v [rozbalení argumentů zástupných znaků](../c-language/expanding-wildcard-arguments.md). Chcete-li potlačit jeho použití, definovat rutiny, která nemá žádnou v soubor obsahující **hlavní** funkce a pojmenujte ji **_setargv –** (nebo **_wsetargv** znakem celou prostředí). Volání **_setargv –** nebo **_wsetargv** pak splňují vaše definice **_setargv –** nebo **_wsetargv** , a je knihovní verze není načtená.  
  
 Podobně pokud máte nikdy přístup k tabulce prostředí prostřednictvím `envp` argument, můžete zadat vlastní prázdný rutiny má být použit místo **_setenvp –** (nebo **_wsetenvp**), rutiny zpracování prostředí.  
  
 Pokud váš program volá **_spawn** nebo **_exec** řadu rutiny v běhové knihovny jazyka C jste neměli potlačit rutiny zpracování prostředí vzhledem k tomu, že tato rutina slouží k předávání prostředí z procesu trdliště nový proces.  
  
## <a name="see-also"></a>Viz také  
 [main – spuštění funkce a programu](../c-language/main-function-and-program-execution.md)