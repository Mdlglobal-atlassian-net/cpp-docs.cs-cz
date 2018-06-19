---
title: Kompilátoru (úroveň 1) upozornění C4910 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34ed2ec16f579b05a572cf6bfc236cd8d5743f63
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290345"
---
# <a name="compiler-warning-level-1-c4910"></a>C4910 kompilátoru upozornění (úroveň 1)
'\<identifikátor >': '__declspec(dllexport)' a 'extern, jsou nekompatibilní na explicitní vytvoření instance  
  
 Instance explicitní šablony s názvem  *\<identifikátor >* obě je změnit `__declspec(dllexport)` a `extern` klíčová slova. Tato klíčová slova jsou však vzájemně vylučují. `__declspec(dllexport)` – Klíčové slovo znamená vytvořit instanci třídy šablony při `extern` – klíčové slovo znamená nevytvoří automaticky instanci třídy šablony.  
  
## <a name="see-also"></a>Viz také  
 [Explicitní vytvoření instance](../../cpp/explicit-instantiation.md)   
 [dllexport, dllimport](../../cpp/dllexport-dllimport.md)   
 [Obecná pravidla a omezení](../../cpp/general-rules-and-limitations.md)