---
title: "C2480 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2480
dev_langs: C++
helpviewer_keywords: C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 06f6c536d5756a19e28df7060373512e3e883a41
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2480"></a>C2480 chyby kompilátoru
"identifikátor": 'přístup z více vláken' platí pouze pro datové položky statický rozsah  
  
 Nelze použít `thread` atribut se automatické proměnné, nestatické datový člen, parametr funkce nebo funkce deklarace nebo definice.  
  
 Použití `thread` atribut pro globální proměnné, členy statických dat a pouze místní statické proměnné.  
  
 Následující ukázka generuje C2480:  
  
```  
// C2480.cpp  
// compile with: /c  
__declspec( thread ) void func();   // C2480  
__declspec( thread ) static int i;   // OK  
```