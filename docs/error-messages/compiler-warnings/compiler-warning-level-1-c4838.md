---
title: "Kompilátoru (úroveň 1) upozornění C4838 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4838
dev_langs: C++
helpviewer_keywords: C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 227af1840fe5aee63545e35456fe09749f00de1d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4838"></a>C4838 kompilátoru upozornění (úroveň 1)
Převod z 'type_1' do 'type_2' vyžaduje zužující převod  
  
 Při použití agregační nebo seznamu inicializace byl nalezen implicitní zužující převod.  
  
 Implicitní zužující převody v přiřazení a inicializace umožňuje jazyka C a C++ následuje barvy, i když neočekávané zužující příčinu chyby mnoho kódu. Chcete-li kód bezpečnější, C++ standard při zužující převod dojde v seznamu inicializace vyžaduje diagnostické zprávy. V jazyce Visual C++, diagnostiky je [C2397 Chyba kompilátoru](../../error-messages/compiler-errors-1/compiler-error-c2397.md) při použití syntaxe jednotná inicializace podporované od ve Visual Studiu 2015. Kompilátor vygeneruje upozornění C4838 pomocí seznamu nebo syntaxe inicializace agregace nepodporuje Visual Studio 2013.  
  
 Zužující převod může být v pořádku, pokud víte, že můžete začlenit možné rozsahu hodnot převedený na cíli. V takovém případě víte více než kompilátoru. Pokud provedete zužující převod záměrně, ujistěte se vaše záměry explicitní pomocí statické přetypování. Jinak hodnota tuto zprávu upozornění téměř vždy označuje, že máte ve vašem kódu chyby. Můžete ji opravit tak, že objekty, které inicializaci mít typy, které jsou pro zpracování vstupních hodnot dostatečně velké.  
  
 Následující ukázka generuje C4838 a ukazuje jeden ze způsobů a opravte ji:  
  
```  
// C4838.cpp -- C++ narrowing conversion diagnostics  
// Compile by using: cl /EHsc C4838.cpp  
  
struct S1 {  
    int m1;  
    double m2, m3;  
};  
  
void function_C4838(double d1) {  
    double ad[] = { 1, d1 }; // OK  
    int ai[] = { 1, d1 };    // warning C4838  
    S1 s11 = { 1, 2, d1 };   // OK  
    S1 s12 { d1, 2, 3 };     // warning C4838  
    S1 s13 { static_cast<int>(d1), 2, 3 }; // possible fix for C4838  
}  
```