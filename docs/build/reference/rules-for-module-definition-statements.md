---
title: Pravidla pro příkazy definice modulu
ms.date: 11/04/2016
f1_keywords:
- .def
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
ms.openlocfilehash: 6d6528b81777711e52153e19a656619a2895b0d6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424753"
---
# <a name="rules-for-module-definition-statements"></a>Pravidla pro příkazy definice modulu

Následující syntaxe pravidla platí pro všechny příkazy v .def souboru. Ostatní pravidla, které se vztahují na konkrétní příkazy jsou popsané společně s každou příkazu.

- Příkazy, atribut klíčová slova a uživatelské identifikátory jsou malá a velká písmena.

- Dlouhé názvy obsahující mezery nebo středníkem (;) souborů musí být uzavřen v uvozovkách (").

- Použijte jeden nebo více mezery, tabulátory nebo znaky nového řádku oddělit příkaz klíčové slovo z jejích argumentů a samostatné příkazy od sebe navzájem. Dvojtečka (:) nebo rovná se (=), který určuje argument je obklopená nula nebo více mezery, tabulátory nebo znaky nového řádku.

- A **název** nebo **KNIHOVNY** příkazu, pokud se používá, musí předcházet všechny ostatní příkazy.

- **Oddíly** a **EXPORTY** příkazů může být více než jednou v .def souboru. Každý příkaz může trvat více specifikace, které musí být odděleny jeden nebo více mezery, tabulátory nebo znaky nového řádku. Příkaz – klíčové slovo musí být uvedena jednou před první specifikace a lze je opakovat před každá další specifikace.

- Mnoho příkazů mají ekvivalentní možnost příkazového řádku propojení. Zobrazit popis odpovídající možnosti odkaz pro další podrobnosti.

- Komentáře v souboru .def jsou označeny středníkem (;) na začátku každého řádku komentáře. Komentář nelze sdílet řádek s příkazem, ale může se objevit mezi specifikace ve víceřádkovém výrazu. (**Oddíly** a **EXPORTY** jsou víceřádkových příkazech.)

- Argumentů jsou zadané se základem 10 nebo šestnáctkové.

- Pokud jako argument řetězec odpovídá [vyhrazené slovo](../../build/reference/reserved-words.md), musí být uzavřen do dvojitých uvozovek (").

## <a name="see-also"></a>Viz také:

[Soubory definice modulu (.Def)](../../build/reference/module-definition-dot-def-files.md)
