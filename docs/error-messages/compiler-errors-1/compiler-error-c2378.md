---
title: "C2378 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2378
dev_langs: C++
helpviewer_keywords: C2378
ms.assetid: 507a91c6-ca72-48df-b3a4-2cf931c86806
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 279a6c8c5de43f6ac0a9438e06f93b5d3b4294b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2378"></a>C2378 chyby kompilátoru
"identifikátor": předefinování; symbol nemohou být přetíženy s definice typu  
  
 Identifikátor byl předefinovat jako `typedef`.  
  
 Následující ukázka generuje C2378:  
  
```  
// C2378.cpp  
// compile with: /c  
int i;  
typedef int i;   // C2378  
typedef int b;   // OK  
```