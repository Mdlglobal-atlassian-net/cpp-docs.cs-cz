---
title: "C3554 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3554
dev_langs: C++
helpviewer_keywords: C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2a05ebf4333b1642aaedc5967b0bfd0979cbac21
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3554"></a>C3554 chyby kompilátoru
'decltype, nelze kombinovat s jakékoli jiné – specifikátor typu  
  
 Nelze kvalifikaci `decltype()` – klíčové slovo s všechny specifikace typu. Například následující fragment kódu vypočítá chyba C3554.  
  
```  
int x;  
unsigned decltype(x); // C3554  
```