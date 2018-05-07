---
title: C4115 kompilátoru upozornění (úrovně 1 a 4) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4115
dev_langs:
- C++
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2edfdc84ee38e20f7193d720eab0ccb58d30790b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>C4115 kompilátoru upozornění (úrovně 1 a 4)
'type': s názvem definice typu v závorkách  
  
 Daný symbol se používá k definování struktury, sjednocení nebo výčtového typu uvnitř výraz v závorkách. Obor definice může mít neočekávané.  
  
 Definice ve volání funkce C, má globální obor. Ve volání C++ má definice stejný obor jako funkce volána.  
  
 Toto upozornění může být způsobeno deklarátory v uvozovkách (například prototypy), které nejsou výrazy se závorkami.  
  
 Toto je upozornění úrovně 1 s C++ – programy a programy C zkompilovat pod kompatibility ANSI (/Za). Jinak je úroveň 3.