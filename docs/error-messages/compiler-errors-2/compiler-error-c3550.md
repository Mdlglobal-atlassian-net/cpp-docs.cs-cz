---
title: "C3550 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3550
dev_langs: C++
helpviewer_keywords: C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 52b3e3323bac9ad55ff10481b3504e4e054ba874
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3550"></a>C3550 chyby kompilátoru
v tomto kontextu je povoleno pouze prostý 'decltype(auto).  
  
 Pokud `decltype(auto)` slouží jako zástupný symbol pro návratový typ funkce, musíte ho použít samostatně. Nelze zadat jako součást deklaraci ukazatele (`decltype(auto*)`), odkaz na prohlášení (`decltype(auto&)`), nebo jakékoli jiné takové kvalifikace.  
  
## <a name="see-also"></a>Viz také  
 [automaticky](../../cpp/auto-cpp.md)