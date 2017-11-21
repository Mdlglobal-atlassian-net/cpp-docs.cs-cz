---
title: "Vyhodnocení tokenů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 38fe88ba1db7e602844569733046cca99c86d4b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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