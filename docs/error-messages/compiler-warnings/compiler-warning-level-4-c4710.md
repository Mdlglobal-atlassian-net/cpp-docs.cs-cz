---
title: Kompilátoru (úroveň 4) upozornění C4710 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4710
dev_langs:
- C++
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c1cc77d8ee5393fe600ceadd9c1335d76e32efe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4710"></a>C4710 kompilátoru upozornění (úroveň 4)
'function': není vložená funkce  
  
 Danou funkci byla vybrána pro vložené rozšíření, ale kompilátor nebyla provedena vložené.  
  
 Vložené provádí uvážení kompilátoru. **Vložené** – klíčové slovo, například **zaregistrovat** – klíčové slovo, slouží jako nápovědu pro kompilátor. Kompilátor používá heuristiku k určení, pokud by měl vložené určitou funkci pro urychlení kód při kompilaci pro rychlost, nebo pokud by měl vložené určitou funkci zmenšit kód při kompilaci pro prostor. Kompilátor bude pouze vložené při kompilaci pro prostor velmi malé funkce.  
  
 V některých případech kompilátor není vložené určitou funkci mechanických důvodů. V tématu [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) seznam příčiny kompilátor může vložené funkce.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.