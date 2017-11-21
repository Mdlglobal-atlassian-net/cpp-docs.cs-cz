---
title: "C2379 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2379
dev_langs: C++
helpviewer_keywords: C2379
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 69be5132451269f7eba9c2e9186a9c25d4629ae7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2379"></a>C2379 chyby kompilátoru
formální parametr číslo je jiného typu povýšení  
  
 Typ zadaného parametru není kompatibilní, prostřednictvím výchozí povýšení s typem v předchozí deklaraci. Jedná se o chybu v ANSI C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) a upozornění s rozšíření Microsoft (**/Ze**).  
  
 Následující ukázka generuje C2379:  
  
```  
// C2379.c  
// compile with: /Za  
void func();  
void func(char);   // C2379, char promotes to int  
```