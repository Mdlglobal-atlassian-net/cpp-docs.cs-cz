---
title: "Kompilátoru (úroveň 4) upozornění C4212 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4212
dev_langs: C++
helpviewer_keywords: C4212
ms.assetid: df781ea1-182d-4f9f-9a31-55b6ce80c711
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bffec0b612bbf815eb3579e78104dd8e3599bdb5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4212"></a>C4212 kompilátoru upozornění (úroveň 4)
nestandardní rozšíření používané: deklarace funkce používá třemi tečkami  
  
 Prototyp funkce má proměnný počet argumentů. V definici funkce neexistuje.  
  
 Následující ukázka generuje C4212:  
  
```  
// C4212.c  
// compile with: /W4 /Ze /c  
void f(int , ...);  
void f(int i, int j) {}  
```