---
title: "C4115 kompilátoru upozornění (úrovně 1 a 4) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4115
dev_langs:
- C++
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ec1c4377c2b7670b9d934d13d09bc5336fe5f30b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>C4115 kompilátoru upozornění (úrovně 1 a 4)
'type': s názvem definice typu v závorkách  
  
 Daný symbol se používá k definování struktury, sjednocení nebo výčtového typu uvnitř výraz v závorkách. Obor definice může mít neočekávané.  
  
 Definice ve volání funkce C, má globální obor. Ve volání C++ má definice stejný obor jako funkce volána.  
  
 Toto upozornění může být způsobeno deklarátory v uvozovkách (například prototypy), které nejsou výrazy se závorkami.  
  
 Toto je upozornění úrovně 1 s C++ – programy a programy C zkompilovat pod kompatibility ANSI (/Za). Jinak je úroveň 3.