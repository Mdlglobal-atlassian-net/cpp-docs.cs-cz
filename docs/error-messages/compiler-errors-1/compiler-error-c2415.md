---
title: "C2415 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2415
dev_langs: C++
helpviewer_keywords: C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 68666ba203897b43fb1658525e1f342bcb923c09
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2415"></a>C2415 chyby kompilátoru
nesprávné operand typu  
  
 Opcode nepoužívá operandy tohoto typu.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Opcode nepodporuje počet operandy použít. V příručce jazyka sestavení odkaz můžete určit správný počet operandy.  
  
2.  Novější procesor podporuje pokyn s další typy. Upravit [/arch (minimální architektura procesoru)](../../build/reference/arch-minimum-cpu-architecture.md) možnost použít novější procesoru.