---
title: "C3533 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3533
dev_langs: C++
helpviewer_keywords: C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e7bcd9c710ac5cdd50b966a72291918459d984be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3533"></a>C3533 chyby kompilátoru
'type': Parametr nemůže mít typ, který obsahuje 'auto'  
  
 Parametr metody nebo šablony nelze deklarovat s `auto` – klíčové slovo Pokud výchozí [/Zc: Auto](../../build/reference/zc-auto-deduce-variable-type.md) – možnost kompilátoru je v platnosti.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Odeberte `auto` – klíčové slovo z deklarací parametrů.  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá C3535, protože deklaruje parametr funkce s `auto` – klíčové slovo a je kompilovat s **/Zc: Auto**.  
  
```  
// C3533a.cpp  
// Compile with /Zc:auto  
void f(auto j){} // C3533  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá C3535, protože deklaruje parametr šablony s `auto` – klíčové slovo a je kompilovat s **/Zc: Auto**.  
  
```  
// C3533b.cpp  
// Compile with /Zc:auto  
template<auto T> class C{}; // C3533  
```  
  
## <a name="see-also"></a>Viz také  
 [Auto – klíčové slovo](../../cpp/auto-keyword.md)   
 [/ Zc: Auto (odvození typu proměnné)](../../build/reference/zc-auto-deduce-variable-type.md)