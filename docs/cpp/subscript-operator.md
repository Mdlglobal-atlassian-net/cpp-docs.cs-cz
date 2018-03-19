---
title: "Operátor dolního indexu: | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '[]'
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fbcb3657af276cdfc9aa05d461c090b76f6de0b
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="subscript-operator"></a>Operátor dolního indexu:
## <a name="syntax"></a>Syntaxe  
  
```  
  
postfix-expression [ expression ]  
```  
  
## <a name="remarks"></a>Poznámky  
 Operátory výraz (který může být také výraz primární) následuje operátor dolního indexu, **[]**, určuje pole indexování.  
  
 Informace o spravovaných polí najdete v tématu [pole](../windows/arrays-cpp-component-extensions.md).  
  
 Obvykle hodnota reprezentována *operátory výraz* je hodnota ukazatele, jako je například identifikátorem pole a *výraz* je integrální hodnota (včetně výčtových typů). Ale všechny možnosti, které je vyžadován syntakticky jeden z výrazů se ukazatel typu a dalších být integrální typu. Proto integrální hodnotou může být v *operátory výraz* pozice a hodnota ukazatele s hodnotou může být v závorkách v *výraz* nebo dolního indexu pozice. Předpokládejme následující fragment kódu:  
  
```  
int nArray[5] = { 0, 1, 2, 3, 4 };  
cout << nArray[2] << endl;            // prints "2"  
cout << 2[nArray] << endl;            // prints "2"  
```  
  
 V předchozím příkladu výraz `nArray[2]` je stejný jako `2[nArray]`. Důvodem je, že výsledek výraz dolního indexu *e1***[** *e2* **]** je dán:  
  
 **\*( (** *e2* **)** *+* **(***e1***) )**  
  
 Adresa poskytuje podle výrazu není *e2* bajtů z adresy *e1*. Místo toho je adresu škálovat na yield další objekt v poli *e2*. Příklad:  
  
```  
double aDbl[2];  
```  
  
 Adresy `aDb[0]` a `aDb[1]` jsou od sebe 8 bajtů – velikost objekt typu **dvojité**. Škálování podle typu objektu je provedeno automaticky podle jazyka C++ a je definována v [doplňkové operátory](../cpp/additive-operators-plus-and.md) kde popsané sčítání a odečítání operandy typu ukazatele.  
  
 Výraz dolního indexu může mít také více dolních indexů následovně:  
  
 *Expression1* **[***Výraz2***] [***expression3***]**...  
  
 Výrazy dolního indexu se přiřazují zleva doprava. Krajní levé výraz dolního indexu *expression1***[***Výraz2***]**, je první vyhodnocen. Adresa, která je výsledkem přidání *expression1* a *Výraz2* forms výraz ukazatel; potom *expression3* se přidá do této ukazatele – výraz k vytvoření nové ukazatele – výraz, a tak dále, dokud se přidal poslední výraz dolního indexu. Deferenční operátor (**\***) se použijí po poslední dolního indexu výraz vyhodnocen, pokud hodnota konečné ukazatele adresy typu pole.  
  
 Výrazy s více dolní indexy odkazovat na elementy vícerozměrná pole. Vícerozměrné pole je pole, jehož prvky jsou pole. Například, první prvek trojrozměrného pole je dvourozměrné pole. Následující příklad deklaruje a inicializuje jednoduché dvourozměrná pole znaků:  
  
```  
// expre_Subscript_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
#define MAX_ROWS 2  
#define MAX_COLS 2  
  
int main() {  
   char c[ MAX_ROWS ][ MAX_COLS ] = { { 'a', 'b' }, { 'c', 'd' } };  
   for ( int i = 0; i < MAX_ROWS; i++ )  
      for ( int j = 0; j < MAX_COLS; j++ )  
         cout << c[ i ][ j ] << endl;  
}  
```  
  
## <a name="positive-and-negative-subscripts"></a>Kladné a záporné dolní indexy  
 První prvek pole je prvek 0. Rozsah C++ pole je od *pole*[0] k *pole*[*velikost* - 1]. Jazyk C++ však podporuje kladné a záporné dolní indexy. Záporné dolní indexy musí spadat do pole hranice; Pokud ne, mohou být nepředvídatelné výsledky. Následující kód ukazuje pole kladné a záporné dolní indexy:  
  
```  
#include <iostream>  
using namespace std;  
  
int main() {  
    int intArray[1024];  
    for (int i = 0, j = 0; i < 1024; i++)  
    {  
        intArray[i] = j++;  
    }  
  
    cout << intArray[512] << endl;// 512  
  
    int *midArray = &intArray[512];  // pointer to the middle of the array  
  
    cout << midArray[-256] << endl;   // 256  
  
    cout << intArray[-256] << endl; // unpredictable  
}  
```  
  
 Záporné dolní index v řádku lasta můžete vytvořit Chyba spuštění, protože odkazuje adresu nižší 256 bajtů v paměti, než je počátek pole. Ukazatele `midArray` je inicializováno středu `intArray`; proto je možné použít obě pole kladné a záporné indexy, které na ní. Chyby dolního indexu pole negenerují chyby v době kompilace, ale vedou k nepředvídatelným výsledkům.  
  
 Operátor dolního indexu je komutativní. Proto výrazy *pole*[*index*] a *pole*[*pole*] je zaručena ekvivalentní tak dlouho, dokud dolní index operátor není přetížený (viz [přetížené operátory](../cpp/operator-overloading.md)). První forma je nejběžnějším způsobem kódování, ale funguje kterákoli z nich.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy přípony](../cpp/postfix-expressions.md)   
 [Předdefinované C++ operátory, prioritu a Asociativnost](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Pole](../cpp/arrays-cpp.md)   
 [Jednorozměrná pole](../c-language/one-dimensional-arrays.md)   
 [Vícerozměrná pole](../c-language/multidimensional-arrays-c.md)