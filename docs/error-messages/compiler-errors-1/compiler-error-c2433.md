---
title: "C2433 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2433
dev_langs: C++
helpviewer_keywords: C2433
ms.assetid: 7079fedd-6059-4125-82ef-ebe275f1f9d1
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c5994da7e2e2dff73f7746dd0fdb2b7a20395cce
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2433"></a>C2433 chyby kompilátoru
"identifikátor": "modifikátor" není povolený v deklarace dat  
  
 `friend`, `virtual`, A `inline` Modifikátory nelze použít pro deklarace na data.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2433.  
  
```  
// C2433.cpp  
class C{};  
  
int main() {  
   inline C c;   // C2433  
}  
```