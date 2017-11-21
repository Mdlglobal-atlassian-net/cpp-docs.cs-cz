---
title: "Chyba linkerů Lnk1264 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1264
dev_langs: C++
helpviewer_keywords: LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d58bad22604509546e7f1645b56594653d33b070
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1264"></a>Chyba linkerů LNK1264
/LTCG:PGINSTRUMENT zadán, ale bez generování kódu vyžaduje; instrumentace se nezdařilo  
  
 **/LTCG:PGINSTRUMENT** byl zadán ale žádné .obj byly nalezeny soubory, které byly kompilovat s [/GL](../../build/reference/gl-whole-program-optimization.md). Instrumentace nelze provést, místní a odkazu se nezdařilo. Musí existovat alespoň jeden soubor .obj na příkazovém řádku, který se zkompiluje s **/GL** tak, aby instrumentace může dojít.  
  
 Optimalizace na základě profilu (PGO) je dostupný jenom v kompilátory 64-bit.