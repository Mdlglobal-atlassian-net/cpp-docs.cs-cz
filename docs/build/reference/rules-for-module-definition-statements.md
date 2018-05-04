---
title: Pravidla pro příkazy definice modulu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- .def
dev_langs:
- C++
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f8de42480dae9be203a132561d722c18d6952c1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="rules-for-module-definition-statements"></a>Pravidla pro příkazy definice modulu
Následující syntaxe pravidla platí pro všechny příkazy v souboru .def. Další pravidla, která se vztahují na konkrétní příkazy jsou popsány se každý příkaz.  
  
-   Příkazy, atribut klíčová slova a zadat uživatele identifikátory se velká a malá písmena.  
  
-   Dlouhé názvy obsahující mezery nebo středníkem (;) souborů musí být uzavřena v uvozovkách (").  
  
-   Použijte jeden nebo více mezery, tabulátory nebo znaky nového řádku k oddělení příkaz klíčové slovo z jeho argumenty a jednotlivé příkazy od sebe navzájem. Dvojtečkou (:) nebo rovná (=), který určuje argument je obklopená nula nebo další mezery, tabulátory nebo znaky nového řádku.  
  
-   A **název** nebo **KNIHOVNY** příkaz, pokud se používá, musí předcházet jiné příkazy.  
  
-   **Části** a **EXPORTUJE** příkazy může vyskytovat více než jednou v souboru .def. Každý příkaz může trvat několik specifikace, které musí být odděleny jeden nebo více mezery, tabulátory nebo znaky nového řádku. Klíčové slovo příkazu musí být jednou před první specifikaci a lze je opakovat před každou další specifikace.  
  
-   Mnoho příkazů mít ekvivalentní možnost příkazového řádku odkaz. Naleznete v popisu odpovídající možnost odkazu pro další podrobnosti.  
  
-   Komentáře v souboru .def jsou určené středníkem (;) na začátku každého řádku komentář. Komentář nemohou sdílet řádek s příkazem, ale může se objevit mezi specifikace ve výpisu víceřádkový. (**Části** a **EXPORTUJE** jsou příkazy víceřádkový.)  
  
-   Číselné argumenty jsou zadané v základní 10 nebo hexadecimální.  
  
-   Pokud odpovídá argument řetězce [vyhrazené slovo](../../build/reference/reserved-words.md), musí být uzavřena v uvozovkách (").  
  
## <a name="see-also"></a>Viz také  
 [Soubory definice modulu (.Def)](../../build/reference/module-definition-dot-def-files.md)  