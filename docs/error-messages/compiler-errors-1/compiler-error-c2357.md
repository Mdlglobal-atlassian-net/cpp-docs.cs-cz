---
title: "C2357 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2357
dev_langs: C++
helpviewer_keywords: C2357
ms.assetid: d1083945-0ea2-4385-9e66-8c665978806c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b3804f0ee55284aabcd46b0f45c557ccc79cbb8a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2357"></a>C2357 chyby kompilátoru
"identifikátor": musí být funkce typu "typ"  
  
 Váš kód deklaruje verzi `atexit` funkce, která neodpovídá verzi kompilátor deklarovaná interně. Deklarovat `atexit` následujícím způsobem:  
  
```  
int __cdecl atexit(void (__cdecl *)());  
```  
  
 Další informace najdete v tématu [init_seg –](../../preprocessor/init-seg.md).  
  
 Následující ukázka generuje C2357:  
  
```  
// C2357.cpp  
// compile with: /c  
// C2357 expected  
#pragma warning(disable : 4075)  
// Uncomment the following line to resolve.  
// int __cdecl myexit(void (__cdecl *)());  
#pragma init_seg(".mine$m",myexit)  
```