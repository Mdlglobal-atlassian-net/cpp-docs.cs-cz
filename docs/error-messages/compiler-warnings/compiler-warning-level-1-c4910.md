---
title: "Kompilátoru (úroveň 1) upozornění C4910 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f758e2e15d5492724e9b819622202831d4e9f5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4910"></a>C4910 kompilátoru upozornění (úroveň 1)
'\<identifikátor >': '__declspec(dllexport)' a 'extern, jsou nekompatibilní na explicitní vytvoření instance  
  
 Instance explicitní šablony s názvem  *\<identifikátor >* obě je změnit `__declspec(dllexport)` a `extern` klíčová slova. Tato klíčová slova jsou však vzájemně vylučují. `__declspec(dllexport)` – Klíčové slovo znamená vytvořit instanci třídy šablony při `extern` – klíčové slovo znamená nevytvoří automaticky instanci třídy šablony.  
  
## <a name="see-also"></a>Viz také  
 [Explicitní vytvoření instance](../../cpp/explicit-instantiation.md)   
 [dllexport, dllimport](../../cpp/dllexport-dllimport.md)   
 [Obecná pravidla a omezení](../../cpp/general-rules-and-limitations.md)