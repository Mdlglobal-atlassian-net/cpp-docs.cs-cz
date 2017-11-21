---
title: "hlavní funkce a spuštění programu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- program startup [C++]
- entry points, program
- main function, program execution
- startup code, main function
- main function
- programs [C++], terminating
ms.assetid: 5984f1bd-072d-4e06-8640-122fb1454401
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7635595adedf961c014bf8792316ca4943dc84a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="main-function-and-program-execution"></a>main – spuštění funkce a programu
Každý program C má primární funkce (hlavní), který musí mít název **hlavní**. Pokud váš kód dodržuje programovací model znakové sady Unicode, můžete použít verzi široká charakterová **hlavní**, **wmain**. **Hlavní** funkce slouží jako výchozí bod pro spuštění programu. Obvykle řídí spuštění programu pomocí směrování volání dalších funkcí v programu. Program obvykle ukončí provádění na konci **hlavní**, i když můžete ukončovat platnost u jiných bodů programu pro celou řadu důvodů. V některých případech, například při zjištění určité chyby, lze vynutit ukončení programu. Chcete-li to provést, použijte **ukončete** funkce. Najdete v článku *referenční dokumentace běhové knihovny* informace o a příklad použití [ukončete](../c-runtime-library/reference/exit-exit-exit.md) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
main( int argc, char *argv[ ], char *envp[ ] )  
```  
  
## <a name="remarks"></a>Poznámky  
 Funkce v rámci zdrojového programu provádí jeden nebo více konkrétních úkolů. **Hlavní** tyto funkce umožňují vykonávat úkoly příslušných můžete volat funkce. Když **hlavní** volá jinou funkci, předá řízení provádění funkce, takže spuštění zahájí první příkaz ve funkci. Funkce vrátí prvek na **hlavní** při `return` spustit příkaz nebo když je dosaženo konce funkce.  
  
 Je možné deklarovat všechny funkce, včetně **hlavní**, chcete-li mít parametry. Pojem „parametr“ nebo „formální parametr“ odkazuje na identifikátor, který přijímá hodnotu předanou funkci. V tématu [parametry](../c-language/parameters.md) informace o předání argumentů parametry. Když jedna funkce volá jinou, volaná funkce přijme hodnoty svých parametrů z volající funkce. Tyto hodnoty jsou označovány jako „argumenty“. Je možné deklarovat formální parametry **hlavní** tak, aby mohl přijímat argumenty z příkazového řádku pomocí tento formát:  
  
 Pokud chcete předat informace, které **hlavní** funkce, parametry jsou tradičně pojmenované `argc` a `argv`, i když kompilátor jazyka C nevyžaduje, aby tyto názvy. Typy parametrů `argc` a `argv` jsou definovány v jazyce C. Tradičně, pokud třetí parametr předaný **hlavní**, tento parametr je pojmenován `envp`. Příklady dále v této části ukazují, jak používat tyto tři parametry pro přístup k argumentům příkazového řádku. Následující části popisují tyto parametry.  
  
 V tématu [použití funkce wmain](../c-language/using-wmain.md) popis verze široká charakterová **hlavní**.  
  
## <a name="see-also"></a>Viz také  
 [hlavní: spuštění programu](../cpp/main-program-startup.md)