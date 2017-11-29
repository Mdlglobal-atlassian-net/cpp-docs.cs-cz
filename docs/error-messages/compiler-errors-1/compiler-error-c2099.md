---
title: "C2099 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2099
dev_langs: C++
helpviewer_keywords: C2099
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0378426777bc7ce831eee9ecb62170baf5e906b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2099"></a>C2099 chyby kompilátoru
Inicializátor není konstanta  
  
 Tato chyba se objeví pouze kompilátorem C a dojde k jenom pro jiný automatické proměnné.  Kompilátor inicializuje bez automatické proměnné při spuštění programu a hodnoty, které jsou inicializovány s musí být konstantní.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2099.  
  
```  
// C2099.c  
int j;  
int *p;  
j = *p;   // C2099 *p is not a constant  
```  
  
## <a name="example"></a>Příklad  
 C2099 může také nastat, protože kompilátor není schopna provést konstantní skládání na výrazu v rámci **/fp: striktní** protože procedura přesnost prostředí nastavení bodu (viz [_controlfp_s –](../../c-runtime-library/reference/controlfp-s.md) pro Další informace o) se může lišit od kompilace na dobu spuštění.  
  
 Při konstantní skládání selže, kompilátor vyvolá dynamické inicializace, což není povoleno v C.  
  
 Pokud chcete tuto chybu vyřešit, kompilovat modul jako soubor sada nebo zjednodušit výraz.  
  
 Další informace najdete v tématu [/fp (zadejte Floating-Point chování)](../../build/reference/fp-specify-floating-point-behavior.md).  
  
 Následující ukázka generuje C2099.  
  
```  
// C2099_2.c  
// compile with: /fp:strict /c  
float X = 2.0 - 1.0;   // C2099  
float X2 = 1.0;   // OK  
```