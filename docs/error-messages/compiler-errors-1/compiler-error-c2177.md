---
title: "C2177 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2177
dev_langs: C++
helpviewer_keywords: C2177
ms.assetid: 2a39a880-cddb-4d3e-a572-645a14c4c478
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 66a9e81f68e7857d12ccf31a00b18791653a0eba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2177"></a>C2177 chyby kompilátoru
Konstanta příliš velký.  
  
 Konstantní hodnota je příliš velký pro typ proměnné, které je přiřazen.  
  
 Následující ukázka generuje C2177:  
  
```  
// C2177.cpp  
int main() {  
   int a=18446744073709551616;   // C2177  
   int b=18446744073709551615;   // OK  
}  
```