---
title: Příkaz výrazu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d94acdfff2fdea2cc35d0856940270ba82e131af
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405253"
---
# <a name="expression-statement"></a>Příkaz výrazu
Příkazy výrazů způsobí vyhodnocení výrazů. Není proveden žádný přenos řízení nebo iterace jako výsledek příkazu výrazu.  
  
 Syntaxe pro příkaz výrazu je jednoduše  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[expression ] ;  
```  
  
## <a name="remarks"></a>Poznámky  
 Před provedením dalšího příkazu jsou všechny výrazy v příkazu výrazu vyhodnoceny a dokončeny všechny vedlejší účinky. Nejčastěji používané příkazy výrazů jsou přiřazení a volání funkce.  Jelikož je výraz nepovinný, je samotný středník považován za prázdný příkaz výrazu, označuje jako [null](../cpp/null-statement.md) příkazu.  
  
## <a name="see-also"></a>Viz také:  
 [Přehled příkazů jazyka C++](../cpp/overview-of-cpp-statements.md)