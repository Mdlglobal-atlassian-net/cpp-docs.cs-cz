---
title: Vyhodnocení tokenů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: baebf5c7b00dc069a1b0f97a9bc5ffb54f856980
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383050"
---
# <a name="evaluation-of-tokens"></a>Vyhodnocení tokenů
Při interpretaci tokenů kompilátor před přechodem na další token zahrne do jednoho tokenu co nejvíce znaků. Vlivem tohoto chování kompilátor možná nebude interpretovat tokeny zamýšleným způsobem, pokud nejsou správně odděleny prázdným znakem. Vezměte v úvahu následující výraz:  
  
```  
i+++j  
```  
  
 V tomto příkladu kompilátor nejprve ze tří znamének plus utvoří nejdelší možný operátor (`++`) a poté zpracuje zbývající znaménko plus jako operátor sčítání (`+`). Výraz je proto interpretován jako výraz `(i++) + (j)`, nikoli `(i) + (++j)`. V tomto a podobných případech se použitím prázdných znaků a závorek vyhněte víceznačnosti a zajistěte správné vyhodnocení výrazu.  
  
 **Konkrétní Microsoft**  
  
 Kompilátor jazyka C zpracovává znak CTRL+Z jako indikátor konce souboru. Veškerý text za znakem CTRL+Z je ignorován.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Tokeny jazyka C](../c-language/c-tokens.md)