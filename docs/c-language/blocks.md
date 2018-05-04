---
title: Bloky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function definitions, blocks in code
- blocks
- compound statements
- statements, compound
ms.assetid: be231a92-c712-464e-ae25-a4becb20f7f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 309e6c017587a2dd3cdc80cd55ffec82751dedd3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="blocks"></a>Bloky
Pořadí deklarací, definice a příkazy uzavřený do složených závorek (**{}**) se označuje jako "blokem". Existují dva typy bloků v C. Příkaz "složený příkaz," skládá z jednoho nebo více příkazů (najdete v části [The složený příkaz](../c-language/compound-statement-c.md)), je jeden typ bloku. Druhý typ je „definice funkce“, která se skládá ze složeného příkazu (tělo funkce) a přidruženého „záhlaví“ funkce (název funkce, návratový typ a formální parametry). Blok v rámci jiných bloků se označuje jako „vnořený“.  
  
 I když jsou všechny složené příkazy uzavřeny ve složených závorkách, ne vše, co je uzavřeno ve složených závorkách, představuje složený příkaz. Ačkoli se například může uvnitř složených závorek objevit specifikace prvků pole, struktury nebo výčtu, nejedná se o složené příkazy.  
  
## <a name="see-also"></a>Viz také  
 [Zdrojové soubory a zdrojové programy](../c-language/source-files-and-source-programs.md)