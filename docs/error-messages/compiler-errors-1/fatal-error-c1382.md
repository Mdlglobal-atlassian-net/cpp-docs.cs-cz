---
title: Závažná chyba C1382 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1382
dev_langs:
- C++
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07c6af1209faface96585224cbd08b4e35101478
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229252"
---
# <a name="fatal-error-c1382"></a>Závažná chyba C1382
soubor PCH 'file' byla znovu sestavena od vygenerování 'obj'. Změňte prosím tento objekt  
  
 Při použití [/ltgc](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil souboru .pch, která je novější než .obj souboru CIL, který odkazuje na ni. Informace v souboru .obj CIL je zastaralý. Znovu sestavte objekt.  
  
 C1382 může také dojít, když kompilujete s **/Yc**, ale také předat více zdrojové soubory kódu kompilátoru.  Pokud chcete vyřešit, nepoužívejte **/Yc** při předávání více zdrojové soubory kódu kompilátoru.  Další informace najdete v tématu [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md).