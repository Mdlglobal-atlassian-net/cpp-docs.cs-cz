---
title: "C2585 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2585
dev_langs: C++
helpviewer_keywords: C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cb0720c7fa9cde9a735c4353bb6bf1d8714ff0fd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2585"></a>C2585 chyby kompilátoru
explicitní převod na "typ" je nejednoznačný  
  
 Převod typů může vytvářet více než jeden výsledek.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Převod z typu třídu nebo strukturu podle vícenásobná dědičnost. Pokud typ dědí stejnou základní třídu více než jednou, musíte použít funkci pro převod nebo operátor řešení rozsahu (`::`) Chcete-li určit, které zděděné třídy použít v převodu.  
  
2.  Operátor převodu a konstruktor nebyly definovány provedení stejné převod.