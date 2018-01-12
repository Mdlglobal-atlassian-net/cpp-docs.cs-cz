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
ms.workload: cplusplus
ms.openlocfilehash: 407598a68df37aa130ce26e4f02e98de975ab527
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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