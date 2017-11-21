---
title: "Kompilátoru (úroveň 4) upozornění C4343 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4343
dev_langs: C++
helpviewer_keywords: C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e6c45c8a2a595d819ecc6eeb2eb8b69a3b5f864e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4343"></a>C4343 kompilátoru upozornění (úroveň 4)
\#/Og – možnost přepsání optimize("g",off) – Direktiva pragma  
  
 Toto upozornění už příště, pouze v kompilátoru procesor řady Itanium (IPF), která hlásí pragma [optimalizovat](../../preprocessor/optimize.md) overrode [/Og](../../build/reference/og-global-optimizations.md) – možnost kompilátoru.  
  
 Následující ukázka generuje C4343:  
  
```  
// C4343.cpp  
// compile with: /Og /W4 /LD  
// processor: IPF  
#pragma optimize ("g", off)   // C4343  
```