---
title: Příkaz výrazu | Microsoft Docs
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
ms.openlocfilehash: 60879ca8792e3259a69b7a9a3de6cd83dce0d6d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="expression-statement"></a>Příkaz výrazu
Příkazy výrazů způsobí vyhodnocení výrazů. Není proveden žádný přenos řízení nebo iterace jako výsledek příkazu výrazu.  
  
 Syntaxe pro příkaz výrazu je jednoduše  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[expression ] ;  
```  
  
## <a name="remarks"></a>Poznámky  
 Před provedením dalšího příkazu jsou všechny výrazy v příkazu výrazu vyhodnoceny a dokončeny všechny vedlejší účinky. Nejčastěji používané příkazy výrazů jsou přiřazení a volání funkce.  Vzhledem k tomu, že ve výrazu je volitelné, samostatně středníkem je považován za příkaz prázdný výrazu, označuje jako [null](../cpp/null-statement.md) příkaz.  
  
## <a name="see-also"></a>Viz také  
 [Přehled příkazů jazyka C++](../cpp/overview-of-cpp-statements.md)