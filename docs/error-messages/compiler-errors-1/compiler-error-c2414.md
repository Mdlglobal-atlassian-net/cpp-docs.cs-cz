---
title: "C2414 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2414
dev_langs: C++
helpviewer_keywords: C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f3b532fdb8448f616916adcaf047dc83923f62c0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2414"></a>C2414 chyby kompilátoru
Neplatný počet operandy  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Opcode nepodporuje počet operandy použít. V příručce jazyka sestavení odkaz můžete určit správný počet operandy.  
  
2.  Novější procesor podporuje pokyn s různým počtem operandy. Upravit [/arch (minimální architektura procesoru)](../../build/reference/arch-minimum-cpu-architecture.md) možnost použít novější procesoru.