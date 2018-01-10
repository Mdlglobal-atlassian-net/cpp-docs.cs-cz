---
title: "Výklad složitějších deklarací | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- complex declarators
- interpreting complex declarators
ms.assetid: dd5b7019-c86d-4645-a5cc-21f834de6f4a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 67d66667d169a95ae4d62ccadd2b56a136cd0a76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="interpreting-more-complex-declarators"></a>Výklad složitějších deklarací
Je-li uzavřít všechny deklarátor v závorkách zadat konkrétní výklad "komplexní deklarátor". Komplexní deklarátor je identifikátor kvalifikovaný více než jeden pole, ukazatel nebo modifikační funkce. Můžete použít různé kombinace pole, ukazatelů a funkce modifikátory na jediný identifikátor. Obecně `typedef` lze zjednodušit deklarace. V tématu [Typedef – deklarace](../c-language/typedef-declarations.md).  
  
 V výklad složitých deklarátorů a složené závorky (tedy modifikátory napravo od identifikátoru) mají přednost před hvězdičky (tedy modifikátory nalevo od identifikátor). A složené závorky mají stejnou prioritu a přidružit zleva doprava. Po deklarátor byla plně interpretovat, specifikátor typu se použije jako poslední krok. Pomocí závorek můžete přepsat výchozí pořadí přidružení a vynutit konkrétní interpretace. Nikdy nepoužívejte závorky, ale kolem název identifikátoru samostatně. To může dojít k nesprávné interpretaci jako seznam parametrů.  
  
 Jednoduchý způsob, jak interpretovat složité deklarátory je čtení je "z uvnitř out" pomocí následující čtyři kroky:  
  
1.  Začínat identifikátor a podívejte se přímo na pravé závorky nebo závorky (pokud existuje).  
  
2.  Interpretovat tyto závorky nebo kulaté závorky a podívejte se na levé straně pro hvězdičky.  
  
3.  Pokud narazíte na pravé závorky v jakékoli fázi, přejděte zpět a použít pravidla 1 a 2 pro všechna data v závorkách.  
  
4.  Použijte specifikátor typu.  
  
    ```  
    char *( *(*var)() )[10];  
     ^   ^  ^ ^ ^   ^    ^  
     7   6  4 2 1   3    5  
    ```  
  
 Kroky v tomto příkladu jsou číslované v pořadí a jde interpretovat následujícím způsobem:  
  
1.  Identifikátor `var` je deklarován jako  
  
2.  ukazatele na  
  
3.  funkce vrácení  
  
4.  ukazatele na  
  
5.  pole 10 elementů, které jsou  
  
6.  ukazatele na  
  
7.  `char`hodnoty.  
  
## <a name="examples"></a>Příklady  
 Následující příklady ilustrují jiné komplexní deklarace a zobrazit vliv význam deklaraci závorek.  
  
```  
int *var[5]; /* Array of pointers to int values */  
```  
  
 Modifikátor pole má vyšší prioritu než modifikátor ukazatele, takže `var` je deklarován jako pole. Modifikátor ukazatel platí pro typ prvků pole; proto elementy pole jsou ukazatele na `int` hodnoty.  
  
```  
int (*var)[5]; /* Pointer to array of int values */  
```  
  
 V tomto prohlášení pro `var`, kulaté závorky poskytnout ukazatel modifikátor vyšší prioritu než modifikátor pole, a `var` je deklarován jako ukazatel na pole pět `int` hodnoty.  
  
```  
long *var( long, long ); /* Function returning pointer to long */  
```  
  
 Modifikátory funkce proto také mají vyšší prioritu než ukazatel modifikátory tuto deklaraci pro `var` deklaruje `var` být vrácení ukazatel na funkci **dlouho** hodnotu. Funkce je deklarovaná provést dvě **dlouho** hodnoty jako argumenty.  
  
```  
long (*var)( long, long ); /* Pointer to function returning long */  
```  
  
 V tomto příkladu je podobný předchozímu. Závorky poskytnout ukazatel modifikátor vyšší prioritu než modifikátor funkce, a `var` je deklarován jako ukazatel na funkci, která vrátí **dlouho** hodnotu. Znovu, funkce přebírá dva **dlouho** argumenty.  
  
```  
struct both       /* Array of pointers to functions */  
{                 /*   returning structures         */  
    int a;  
    char b;  
} ( *var[5] )( struct both, struct both );  
```  
  
 Prvky pole nemůže být funkce, ale tuto deklaraci ukazuje, jak místo deklarovat pole ukazatelé na funkce. V tomto příkladu `var` je deklarován jako pole pět ukazatele na funkce, které vrací struktur s dva členy. Argumenty, které mají funkce, které jsou deklarované jako dvě struktury stejného typu Struktura `both`. Všimněte si, že závorky kolem `*var[5]` jsou povinné. Bez, je deklaraci k neplatnému pokusu deklarovat řadu funkcí, jak je uvedeno níže:  
  
```  
/* ILLEGAL */  
struct both *var[5](struct both, struct both);  
```  
  
 Následující příkaz deklaruje pole ukazatele.  
  
```  
unsigned int *(* const *name[5][10] ) ( void );  
```  
  
 `name` Pole má 50 elementy, které jsou uspořádány do multidimenzionálního pole. Elementy jsou ukazatele na ukazatele, který je konstanta. Ukazatel this konstantní odkazuje na funkci, která nemá žádné parametry a vrátí ukazatel na typ bez znaménka.  
  
 Tento další příklad je funkce vrácení ukazatele na pole tři **dvojité** hodnoty.  
  
```  
double ( *var( double (*)[3] ) )[3];  
```  
  
 V tomto prohlášení funkce vrátí ukazatel na pole, od funkcí vracejících pole jsou neplatné. Zde `var` je deklarován jako funkci vrácení ukazatele na pole tři **dvojité** hodnoty. Funkce `var` přijímá jeden argument. Argument jako návratová hodnota, je zde ukazatel na tři pole **dvojité** hodnoty. Typ argumentu je dán komplexní *abstraktní deklarátor*. Závorky se tedy hvězdička v typ argumentu jsou požadovány; typ argumentu bez, bude pole tři ukazatele na **dvojité** hodnoty. Se zabývat a příklady deklarátory abstraktu jazyka najdete v tématu [deklarátory abstraktu jazyka](../c-language/c-abstract-declarators.md).  
  
```  
union sign         /* Array of arrays of pointers */  
{                  /* to pointers to unions       */  
     int x;  
     unsigned y;  
} **var[5][5];  
```  
  
 Výše uvedený příklad ukazuje, ukazatel může ukazovat na jiné ukazatele a pole může obsahovat pole jako elementy. Zde `var` je pole pět elementů. Každý prvek je pět element pole ukazatelů na ukazatele k sjednocení s dva členy.  
  
```  
union sign *(*var[5])[5]; /* Array of pointers to arrays  
                             of pointers to unions        */  
```  
  
 Tento příklad ukazuje, jak umístění závorkách změní význam deklaraci. V tomto příkladu `var` je pěti element pole ukazatele na pět element pole ukazatele na sjednocení. Příklady, jak používat `typedef` nechcete komplexní deklarace, najdete v části [Typedef – deklarace](../c-language/typedef-declarations.md).  
  
## <a name="see-also"></a>Viz také  
 [Deklarace a typy](../c-language/declarations-and-types.md)