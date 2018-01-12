---
title: "C3163 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3163
dev_langs: C++
helpviewer_keywords: C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4d3cbb5c5c3e8391b3a549fc0c34661dc86b492c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3163"></a>C3163 chyby kompilátoru
'vytvořit': atributy, které jsou konzistentní s předchozí deklarace  
  
 Atributy, které se použijí pro definici v konfliktu s atributy, které se použijí pro deklaraci.  
  
 Jeden způsob, jak vyřešit C3163 je odstranit atributy na deklaraci předat dál. Všechny atributy v deklaraci dopředného by měla být menší než atributy v definici nebo maximálně roven do je.  
  
 Možnou příčinou této chyby C3163 zahrnuje jazyk Microsoft zdrojového kódu poznámky (SAL). Makra SAL nebudou rozbaleny pokud zkompilujete váš projekt pomocí **/ analyze** příznak. Program, který se zkompiluje řádně bez / analyze může vyvolat C3163, pokud se pokusíte znovu zkompiluje ho pomocí / analyze – možnost. Další informace o SAL najdete v tématu [poznámek SAL](../../c-runtime-library/sal-annotations.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3163.  
  
```  
// C3163.cpp  
// compile with: /clr /c  
using namespace System;  
  
[CLSCompliant(true)] void f();  
[CLSCompliant(false)] void f() {}   // C3163  
// try the following line instead  
// [CLSCompliant(true)] void f() {}  
```  
  
## <a name="see-also"></a>Viz také  
 [Poznámky SAL](../../c-runtime-library/sal-annotations.md)