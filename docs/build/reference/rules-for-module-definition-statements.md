---
title: "Pravidla pro příkazy definice modulu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .def
dev_langs: C++
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 50d382b8f6dbb8c6468bba3bcb2d5c65607de99d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Definice modulu (. Soubory def)](../../build/reference/module-definition-dot-def-files.md)  