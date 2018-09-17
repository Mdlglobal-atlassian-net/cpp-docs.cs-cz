---
title: Pravidla pro příkazy definice modulu | Dokumentace Microsoftu
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
ms.openlocfilehash: a31927bb1ce3667367eff8f38268b4b3b24ac82c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726476"
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

## <a name="see-also"></a>Viz také

[Soubory definice modulu (.Def)](../../build/reference/module-definition-dot-def-files.md)