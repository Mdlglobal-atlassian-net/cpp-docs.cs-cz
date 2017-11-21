---
title: "C4115 kompilátoru upozornění (úrovně 1 a 4) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4115
dev_langs: C++
helpviewer_keywords: C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a0430aae30c3a9c25b9b7fd96651a82719d9068a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>C4115 kompilátoru upozornění (úrovně 1 a 4)
'type': s názvem definice typu v závorkách  
  
 Daný symbol se používá k definování struktury, sjednocení nebo výčtového typu uvnitř výraz v závorkách. Obor definice může mít neočekávané.  
  
 Definice ve volání funkce C, má globální obor. Ve volání C++ má definice stejný obor jako funkce volána.  
  
 Toto upozornění může být způsobeno deklarátory v uvozovkách (například prototypy), které nejsou výrazy se závorkami.  
  
 Toto je upozornění úrovně 1 s C++ – programy a programy C zkompilovat pod kompatibility ANSI (/Za). Jinak je úroveň 3.