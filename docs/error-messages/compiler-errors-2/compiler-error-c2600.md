---
title: C2600 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2600
dev_langs:
- C++
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13b4cdf15dca9b3978f8c7855a5f1b07cc86f0b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230946"
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