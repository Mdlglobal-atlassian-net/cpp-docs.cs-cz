---
title: "Závažná chyba C1382 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1382
dev_langs: C++
helpviewer_keywords: C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ddb016e14b01b3bc1dfd45c7d5a8ad1aa489ac3a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1382"></a>Závažná chyba C1382
soubor PCH 'file' byla znovu sestavena od vygenerování 'obj'. Změňte prosím tento objekt  
  
 Při použití [/ltgc](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil souboru .pch, která je novější než .obj souboru CIL, který odkazuje na ni. Informace v souboru .obj CIL je zastaralý. Znovu sestavte objekt.  
  
 C1382 může také dojít, když kompilujete s **/Yc**, ale také předat více zdrojové soubory kódu kompilátoru.  Pokud chcete vyřešit, nepoužívejte **/Yc** při předávání více zdrojové soubory kódu kompilátoru.  Další informace najdete v tématu [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md).