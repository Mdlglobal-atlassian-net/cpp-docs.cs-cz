---
title: "C2600 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2600
dev_langs: C++
helpviewer_keywords: C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1fe5383e17212b21c11394c6b987e92aacbe637e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2600"></a>C2600 chyby kompilátoru
'function': nelze definovat generované kompilátorem speciální členské funkce (musí být deklarován v třídě nejprve)  
  
 Před člen, které funkce jako je například konstruktory nebo destruktory lze definovat pro třídu musí být deklarován v třídě. Kompilátor může vygenerovat výchozí konstruktory a destruktorů (nazývané speciální členské funkce), pokud žádný jsou deklarované v třídě. Ale pokud definujete jednu z těchto funkcí bez odpovídající deklarace ve třídě, kompilátor zjistí konflikt.  
  
 Odstranění této chyby v deklaraci třídy, deklarujte každý člen funkce, které definujete mimo deklaraci třídy.  
  
 Následující ukázka generuje C2600:  
  
```  
// C2600.cpp  
// compile with: /c  
class C {};  
C::~C() {}   // C2600  
  
class D {  
   D::~D();  
};  
  
D::~D() {}  
```