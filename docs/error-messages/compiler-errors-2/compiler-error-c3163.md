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
ms.openlocfilehash: 95fb254036d2883b6efe6b81bda54864d533c2a8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [SAL – poznámky](../../c-runtime-library/sal-annotations.md)