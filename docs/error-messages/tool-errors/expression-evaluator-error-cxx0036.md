---
title: Vyhodnocování výrazu CXX0036 chyba | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0036
dev_langs:
- C++
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a94ed846d2d4ebda2e457ee772a9f8bf081d69d6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077165"
---
# <a name="expression-evaluator-error-cxx0036"></a>Chyba při vyhodnocování výrazu CXX0036

špatný kontext {...} specifikace

Tato zpráva se může objevit některou z několika chyb používá operátor kontextu (**{}**).

- Syntaxe operátor kontextu (**{}**) byl nesprávně zadán.

   Syntaxe operátor kontextu je následující:

     {*funkce*,*modulu*,*dll*}*výraz*

   Určuje kontext *výraz*. Operátor kontextu má stejnou prioritu a použití jako přetypování.

   Na konci čárky lze vynechat. Pokud je libovolná z *funkce*, *modulu*, nebo *dll* obsahuje čárku literálu celý název je nutné uzavřít do závorek.

- Název funkce napsaný správně nebo neexistuje v zadaném modulu nebo knihovny DLL.

   Protože je velká a malá písmena jazyka C *funkce* musí být uvedené v rozlišovat velikost písmen, jak jsou definovány ve zdroji.

- Modul nebo knihovny DLL se nenašel.

   Zkontrolujte úplný název cesty zadaném modulu nebo knihovny DLL.

Tato chyba se shoduje s CAN0036.