---
title: C2585 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2585
dev_langs:
- C++
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ab812a4b6621acb28a4df636056598047f5c21e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2585"></a>C2585 chyby kompilátoru
explicitní převod na "typ" je nejednoznačný  
  
 Převod typů může vytvářet více než jeden výsledek.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Převod z typu třídu nebo strukturu podle vícenásobná dědičnost. Pokud typ dědí stejnou základní třídu více než jednou, musíte použít funkci pro převod nebo operátor řešení rozsahu (`::`) Chcete-li určit, které zděděné třídy použít v převodu.  
  
2.  Operátor převodu a konstruktor nebyly definovány provedení stejné převod.