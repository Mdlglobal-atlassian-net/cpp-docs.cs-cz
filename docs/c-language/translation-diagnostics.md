---
title: "Posunutí: Diagnostika | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bb7f826be88ebec640a6f3b40b38478eea91ed36
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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