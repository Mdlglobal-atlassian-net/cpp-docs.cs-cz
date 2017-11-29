---
title: "C3320 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3320
dev_langs: C++
helpviewer_keywords: C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fbc375682bb42070d49dd08b711926462c17f32b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3320"></a>C3320 chyby kompilátoru
'type': typ nemůže mít stejný název jako vlastnost 'name' module  
  
Exportovaný uživatelem definovaný typ (UDT), které by mohly být struktura, třídu, výčet nebo union, nemůže mít stejný název jako parametr předaný [modulu](../../windows/module-cpp.md) vlastnost název atributu.  
  
## <a name="example"></a>Příklad  
Následující ukázka generuje C3320:  
  
```cpp  
// C3320.cpp  
#include "unknwn.h"  
[module(name="xx")];  
  
[export] struct xx {   // C3320  
// Try the following line instead  
// [export] struct yy {  
   int i;  
};  
```