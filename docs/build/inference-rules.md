---
title: "Odvozená pravidla | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 932aad860cd2b78208857ca7b028e35cd96d481e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="inference-rules"></a>Odvozená pravidla
Odvozená pravidla zadat příkazy aktualizaci cíle a odvození závislé objekty pro cíle. Rozšíření v pravidle odvození shodovat s jedním cílem a závislé, které mají stejné základní název. Odvozená pravidla jsou definované uživatelem nebo předdefinované; můžete jej předefinovat předdefinovaná pravidla.  
  
 Pokud má zastaralé závislostí žádné příkazy a pokud [. PŘÍPONY](../build/dot-directives.md) obsahuje závislé na rozšíření, NMAKE používá pravidla, jejichž rozšíření odpovídají cíl a existující soubor v adresáři zadané nebo aktuální. Pokud existující soubory, odpovídá více než jedno pravidlo **. PŘÍPONY** seznamu určuje, který se použije; seznamu priority descends zleva doprava. Pokud závislý soubor neexistuje a není uvedena jako cíl v jiném popis bloku, odvozené pravidlo můžete vytvořit chybějící závislé z jiného souboru se stejným názvem základní. Pokud cílový blok popis nemá žádné závislosti nebo příkazy, můžete aktualizovat pravidlo odvození cíl. Odvozená pravidla můžete vytvořit cíl příkazového řádku, i v případě, že neexistuje žádný popis blok. NMAKE může vyvolat pravidlo pro odvozené závislé, i když je zadaný explicitní závislé.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
 [Definice pravidla](../build/defining-a-rule.md)  
  
 [Pravidla dávkového režimu](../build/batch-mode-rules.md)  
  
 [Předdefinovaná pravidla](../build/predefined-rules.md)  
  
 [Odvozené závislé objekty a pravidla](../build/inferred-dependents-and-rules.md)  
  
 [Priorita odvozených pravidel](../build/precedence-in-inference-rules.md)  
  
## <a name="see-also"></a>Viz také  
 [NMAKE – referenční zdroje](../build/nmake-reference.md)