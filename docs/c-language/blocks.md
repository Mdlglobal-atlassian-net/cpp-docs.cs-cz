---
title: Bloky | Dokumentace Microsoftu
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
ms.openlocfilehash: 9704b499106fc59364f5cc9ae97277939e835a77
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025319"
---
# <a name="blocks"></a>Bloky

Sekvence deklarací, definic a příkazů, které jsou uzavřeny ve složených závorkách (**{}**) se nazývá "blok". Existují dva typy bloků v jazyce C. "Složený příkaz" příkaz skládá z jednoho nebo více příkazů (viz [složený příkaz](../c-language/compound-statement-c.md)), je z typů bloků. Druhý typ je „definice funkce“, která se skládá ze složeného příkazu (tělo funkce) a přidruženého „záhlaví“ funkce (název funkce, návratový typ a formální parametry). Blok v rámci jiných bloků se označuje jako „vnořený“.

I když jsou všechny složené příkazy uzavřeny ve složených závorkách, ne vše, co je uzavřeno ve složených závorkách, představuje složený příkaz. Ačkoli se například může uvnitř složených závorek objevit specifikace prvků pole, struktury nebo výčtu, nejedná se o složené příkazy.

## <a name="see-also"></a>Viz také

[Zdrojové soubory a zdrojové programy](../c-language/source-files-and-source-programs.md)