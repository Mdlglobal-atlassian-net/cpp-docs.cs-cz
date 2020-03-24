---
title: Chyba při vyhodnocování výrazu CXX0036
ms.date: 11/04/2016
f1_keywords:
- CXX0036
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
ms.openlocfilehash: 164fd9ee00071e218e5bb4f3ab00febc618725a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195497"
---
# <a name="expression-evaluator-error-cxx0036"></a>Chyba při vyhodnocování výrazu CXX0036

Chybný kontext {...} specifikace

Tato zpráva může být generována některou z několika chyb v použití operátoru kontextu ( **{}** ).

- Syntaxe operátoru kontextu ( **{}** ) byla nesprávně zadána.

   Syntaxe operátoru kontextu je:

     {*Function*,*Module*,*DLL*} *výraz*

   Určuje kontext *výrazu*. Operátor kontextu má stejnou prioritu a využití jako přetypování typu.

   Koncové čárky lze vynechat. Pokud některá z *funkcí*, *modulů*nebo *knihoven DLL* obsahuje literální čárku, musíte uzavřít celý název do závorek.

- Název funkce byl nesprávně zadán nebo neexistuje v zadaném modulu nebo v knihovně DLL.

   Vzhledem k tomu, že C je jazyk citlivý na velká a malá písmena, musí být *funkce* uvedena v přesném případě, jak je definována ve zdroji.

- Modul nebo knihovna DLL se nepodařilo najít.

   Zkontroluje úplný název cesty zadaného modulu nebo knihovny DLL.

Tato chyba je shodná s CAN0036.
