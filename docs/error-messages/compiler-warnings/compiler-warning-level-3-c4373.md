---
title: "Kompilátoru (úroveň 3) upozornění C4373 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4373
dev_langs: C++
helpviewer_keywords: C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b8660501a679b994bfe8fa5e3ad5ff3728725667
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4373"></a>C4373 kompilátoru upozornění (úroveň 3)
'%$S': '%$pS' přepisování virtuální funkce, předchozí verze kompilátoru přepsat při parametry pouze podle const nebo volatile kvalifikátory lišil.  
  
 Vaše aplikace obsahuje metodu v odvozené třídě, který přepíše virtuální metodu v základní třídě a parametry v metodě přepsání lišit pouze [const](../../cpp/const-cpp.md) nebo [volatile](../../cpp/volatile-cpp.md) kvalifikátor z parametry virtuální metody. To znamená, kompilátor musí vytvořit vazbu funkce odkaz na metodu buď základní nebo odvozené třídy.  
  
 Verze kompilátoru před [!INCLUDE[cpp_orcas_long](../../cpp/includes/cpp_orcas_long_md.md)] metodu v základní třídě vytvořit vazbu funkce, pak zpráva s upozorněním. Další verze kompilátoru Ignorovat `const` nebo `volatile` kvalifikátor, vazbu funkce metodu v odvozené třídě a potom vydat varování `C4373`. Toto chování pozdější splňuje C++ standard.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu generuje upozornění C4373.  
  
```  
// c4373.cpp  
// compile with: /c /W3  
#include <stdio.h>  
struct Base  
{  
    virtual void f(int i) {  
        printf("base\n");  
    }  
};  
struct Derived : Base  
{  
    void f(const int i) {  // C4373  
        printf("derived\n");  
    }  
};  
void main()  
{  
    Derived d;  
    Base* p = &d;  
    p->f(1);  
}  
```  
  
```Output  
derived  
```