---
title: Body sekvence jazyka C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: sequence points
ms.assetid: c84885a5-4336-4eba-a643-058df4249903
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f86bd3feacbabdd11d6c8ec04b4aec96ec2f5e1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-sequence-points"></a>Body sekvence jazyka C
Mezi po sobě jdoucích "body sekvence" hodnoty objektu lze upravit pouze jednou pomocí výrazu. Jazyk C definuje toto pořadí:  
  
-   Levý operand logické – a – operátor (**&&**). Levý operand logické – operátor je zcela vyhodnotit a před pokračováním proveďte všechny vedlejší účinky. Pokud levý operand vyhodnocena jako false (0), nebude hodnocen jiných operand.  
  
-   Levý operand operátoru logické OR (`||`). Levý operand operátoru logické nebo zcela vyhodnocena a před pokračováním proveďte všechny vedlejší účinky. Pokud je výsledkem levý operand na hodnotu true (nenulové hodnoty), dalších operand, nebude hodnocen.  
  
-   Levý operand operátoru čárky. Levý operand operátoru čárkami úplně vyhodnocena a před pokračováním proveďte všechny vedlejší účinky. Oba operandy operátoru čárky jsou vždy vyhodnoceny. Všimněte si, že operátor čárky ve volání funkce nezaručuje pořadí vyhodnocení.  
  
-   Operátor volání funkce. Všechny argumenty funkce vyhodnocují a všechny vedlejší účinky dokončit před vstupem funkce. Je zadáno žádné pořadí vyhodnocení mezi argumenty.  
  
-   První operand podmíněného operátoru. První operand operátoru podmíněného úplně vyhodnocena a před pokračováním proveďte všechny vedlejší účinky.  
  
-   Konec výraz úplné inicializace (tj. výraz, který není součástí další výraz například konec inicializaci v příkazu deklarace).  
  
-   Výraz v příkazu výrazu. Příkazy výrazu obsahovat volitelné výrazu následuje středník (**;**). Vyhodnotí výraz pro jeho vedlejší efekty a je bod pořadí následující toto testování.  
  
-   Řízení výraz ve výběru (**Pokud** nebo `switch`) příkaz. Výraz je zcela vyhodnotit a všechny vedlejší účinky dokončit před provedením kód závisí na výběr.  
  
-   Kontrolní výraz `while` nebo **provést** příkaz. Výraz je zcela vyhodnotit a před všechny příkazy v další iterace dokončit všechny vedlejší účinky `while` nebo **provést** smyčky jsou spouštěny.  
  
-   Všechny tři výrazy **pro** příkaz. Výrazy úplně vyhodnocují a před všechny příkazy v další iterace dokončit všechny vedlejší účinky **pro** smyčky jsou spouštěny.  
  
-   Výraz v `return` příkaz. Výraz je zcela vyhodnotit a všechny vedlejší účinky dokončit před voláním funkce vrátí ovládací prvek.  
  
## <a name="see-also"></a>Viz také  
 [Vyhodnocení výrazu](../c-language/expression-evaluation-c.md)