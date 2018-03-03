---
title: "Posunutí: Diagnostika | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 10349357fa0411357b702ff48ff9407c1f5b91e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="translation-diagnostics"></a>Posunutí: diagnostika
**ANSI 2.1.1.3** jak identifikovat Diagnostika  
  
 Jazyk Microsoft C generuje chybové zprávy v následujícím tvaru:  
  
```  
  
filename( line-number ) : diagnostic Cnumbermessage  
```  
  
 kde *filename* je název zdrojového souboru, ve které došlo k chybě; *číslo řádku* je číslo řádku, na které kompilátor zjistil chybu. `diagnostic` "Chyba" nebo "upozornění"; `number` jedinečný čtyři číslice (před sebou **C**, jak je uvedeno v syntaxi) identifikující chyby nebo upozornění; `message` je vysvětlující zpráva.  
  
## <a name="see-also"></a>Viz také  
 [Chování definované implementací](../c-language/implementation-defined-behavior.md)