---
title: "Kompilátoru (úroveň 4) upozornění C4710 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4710
dev_langs:
- C++
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0464d924c21a029a97a8f03d30f88127f3aea6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4710"></a>C4710 kompilátoru upozornění (úroveň 4)
'function': není vložená funkce  
  
 Danou funkci byla vybrána pro vložené rozšíření, ale kompilátor nebyla provedena vložené.  
  
 Vložené provádí uvážení kompilátoru. **Vložené** – klíčové slovo, například **zaregistrovat** – klíčové slovo, slouží jako nápovědu pro kompilátor. Kompilátor používá heuristiku k určení, pokud by měl vložené určitou funkci pro urychlení kód při kompilaci pro rychlost, nebo pokud by měl vložené určitou funkci zmenšit kód při kompilaci pro prostor. Kompilátor bude pouze vložené při kompilaci pro prostor velmi malé funkce.  
  
 V některých případech kompilátor není vložené určitou funkci mechanických důvodů. V tématu [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) seznam příčiny kompilátor může vložené funkce.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.