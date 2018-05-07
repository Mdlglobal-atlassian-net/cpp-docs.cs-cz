---
title: Chyba linkerů Lnk1264 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1264
dev_langs:
- C++
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ed21327028fc9849f6e0694bb82ae34c6084842
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1264"></a>Chyba linkerů LNK1264
/LTCG:PGINSTRUMENT zadán, ale bez generování kódu vyžaduje; instrumentace se nezdařilo  
  
 **/LTCG:PGINSTRUMENT** byl zadán ale žádné .obj byly nalezeny soubory, které byly kompilovat s [/GL](../../build/reference/gl-whole-program-optimization.md). Instrumentace nelze provést, místní a odkazu se nezdařilo. Musí existovat alespoň jeden soubor .obj na příkazovém řádku, který se zkompiluje s **/GL** tak, aby instrumentace může dojít.  
  
 Optimalizace na základě profilu (PGO) je dostupný jenom v kompilátory 64-bit.