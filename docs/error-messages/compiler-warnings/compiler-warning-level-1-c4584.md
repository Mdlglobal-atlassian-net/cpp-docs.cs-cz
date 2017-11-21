---
title: "Kompilátoru (úroveň 1) upozornění C4584 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4584
dev_langs: C++
helpviewer_keywords: C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1c17d8871d16cd2eec6b46e01d9c1779f3440398
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4584"></a>Kompilátoru (úroveň 1) upozornění C4584
"třída1": "třída2" základní třídy již základní třídy, class3.  
  
 Třídy, na kterou jste definovali dědí ze dvou tříd, z nichž jeden dědí z jiných. Příklad:  
  
```  
// C4584.cpp  
// compile with: /W1 /LD  
class A {  
};  
  
class B : public A {  
};  
  
class C : public A, public B { // C4584  
};  
```  
  
 V takovém případě by vydáno upozornění na třídě C protože dědí jak z třídy A a B, který také dědí z třídy A. Toto upozornění slouží jako připomenutí, musí plně kvalifikujte použití členy z těchto základních tříd nebo vygeneruje se chyba kompilátoru z důvodu nejednoznačnosti, které člen třídy odkazovat.