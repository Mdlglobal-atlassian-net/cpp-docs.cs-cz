---
title: 'Posunutí: Diagnostika | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c6a59abc48e5a6bc2aa727508b61abe120c8425
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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