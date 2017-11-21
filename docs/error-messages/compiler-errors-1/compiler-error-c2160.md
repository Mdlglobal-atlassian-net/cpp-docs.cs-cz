---
title: "C2160 chyby kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2160
dev_langs: C++
helpviewer_keywords: C2160
ms.assetid: a1f694a7-fb16-4437-b7f5-a1af6da94bc5
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: caef1127e06bbf0b12480b2c10239c77ae6c0ad5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2160"></a>C2160 chyby kompilátoru
' ##' nelze provést na začátku definice makra  
  
 Definice makra začal s operátor vložení tokenu (##).  
  
 Následující ukázka generuje C2160:  
  
```  
// C2160.cpp  
// compile with: /c  
#define mac(a,b) #a   // OK  
#define mac(a,b) ##a   // C2160  
```