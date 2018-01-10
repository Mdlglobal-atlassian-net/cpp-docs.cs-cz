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
ms.workload: cplusplus
ms.openlocfilehash: 923cc957dd136147a6c749f5ebf9508ca7e2052d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1382"></a>Závažná chyba C1382
soubor PCH 'file' byla znovu sestavena od vygenerování 'obj'. Změňte prosím tento objekt  
  
 Při použití [/ltgc](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil souboru .pch, která je novější než .obj souboru CIL, který odkazuje na ni. Informace v souboru .obj CIL je zastaralý. Znovu sestavte objekt.  
  
 C1382 může také dojít, když kompilujete s **/Yc**, ale také předat více zdrojové soubory kódu kompilátoru.  Pokud chcete vyřešit, nepoužívejte **/Yc** při předávání více zdrojové soubory kódu kompilátoru.  Další informace najdete v tématu [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md).