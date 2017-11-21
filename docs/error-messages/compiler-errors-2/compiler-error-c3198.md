---
title: "C3198 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3198
dev_langs: C++
helpviewer_keywords: C3198
ms.assetid: ec4ecf61-0067-4aa4-b443-a91013a1e59d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 56325b1410e2d7255eec599cdb73f52710bbe1c1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3198"></a>C3198 chyby kompilátoru
Neplatné použití s plovoucí desetinnou čárkou direktivy: fenv_access – Direktiva pragma funguje pouze v režimu přesné  
  
 [fenv_access –](../../preprocessor/fenv-access.md) – Direktiva pragma byl použitý v rámci [/fp](../../build/reference/fp-specify-floating-point-behavior.md) nastavení jiné než **/fp: přesné**.  
  
 Následující ukázka generuje C3198:  
  
```  
// C3198.cpp  
// compile with: /fp:fast  
#pragma fenv_access(on)   // C3198  
```