---
title: C2397 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- C2397
dev_langs:
- C++
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9d080450368618cc874de0ae96209e547847f8c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33196880"
---
# <a name="compiler-error-c2397"></a>C2397 chyby kompilátoru
Převod z 'type_1' do 'type_2' vyžaduje zužující převod  
  
 Při použití jednotná inicializace byl nalezen implicitní zužující převod.  
  
 Implicitní zužující převody v přiřazení a inicializace umožňuje jazyka C a C++ následuje barvy, i když neočekávané zužující příčinu chyby mnoho kódu. Chcete-li kód bezpečnější, C++ standard při zužující převod dojde v seznamu inicializace vyžaduje diagnostické zprávy. V jazyce Visual C++ je diagnostiky C2397 chyby kompilátoru při použití syntaxe podporované začátku jednotná inicializace ve Visual Studiu 2015. Kompilátor vygeneruje [upozornění kompilátoru (úroveň 1) C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) při použití seznamu nebo syntaxe inicializace agregace nepodporuje Visual Studio 2013.  
  
 Zužující převod může být v pořádku, pokud víte, že můžete začlenit možné rozsahu hodnot převedený na cíli. V takovém případě víte více než kompilátoru. Pokud provedete zužující převod záměrně, ujistěte se vaše záměry explicitní pomocí statické přetypování. Tato chybová zpráva, jinak hodnota téměř vždy indikuje, že máte ve vašem kódu chyby. Můžete ji opravit tak, že objekty, které inicializaci mít typy, které jsou pro zpracování vstupních hodnot dostatečně velké.  
  
 Následující ukázka generuje C2397 a ukazuje jeden ze způsobů a opravte ji:  
  
```  
// C2397.cpp -- C++ narrowing conversion diagnostics  
// Compile by using: cl /EHsc C2397.cpp  
#include <vector>   
  
struct S1 {  
    int m1;  
    double m2, m3;  
};  
  
void function_C2397(double d1) {  
    char c1 { 127 };          // OK  
    char c2 { 513 };          // error C2397  
  
    std::vector<S1> vS1;  
    vS1.push_back({ d1, 2, 3 }); // error C2397  
  
    // Possible fix if you know d1 always fits in an int  
    vS1.push_back({ static_cast<int>(d1), 2, 3 });   
}  
```