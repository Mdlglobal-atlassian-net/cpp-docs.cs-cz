---
title: "Návratový typ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function return types
- return values [C++], function procedures
- function return types, syntax
- return values [C++]
- data types [C++], function return types
- return keyword [C++], function return types
- functions [C++], return types
ms.assetid: 3e5b8a97-b341-48c5-8be8-8986980ef586
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9768baa53e39f1b3243aba24385d592010c3d81a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="return-type"></a>Návratový typ
Návratový typ funkce vytváří velikost a typ hodnoty vrácené funkcí a odpovídá specifikátor typu níže uvedené syntaxe:  
  
## <a name="syntax"></a>Syntaxe  
 *definice funkce*:  
 *specifikátory deklarace* vyjádřit výslovný*atribut seq* opt*deklarátor deklarace list* opt*složené – příkaz*  
  
 /\**atribut seq* je specifické pro Microsoft * /  
  
 *specifikátory deklarace*:  
 *specifikátor třídy úložiště specifikátory deklarace* opt  
  
 *Specifikátor typu deklarace – specifikátory* opt  
  
 *Kvalifikátor typu deklarace – specifikátory* opt  
  
 *Specifikátor typu*:  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **podepsané**  
  
 **bez znaménka**  
  
 *Struktura nebo sjednocení – specifikátor*  
  
 *enum – specifikátor*  
  
 *Název definice TypeDef*  
  
 *Specifikátor typu* můžete zadat všechny základní struktura nebo typu union. Pokud neuvedete *specifikátor typu*, návratový typ `int` se předpokládá.  
  
 Návratový typ zadaný v definici funkce musí odpovídat návratový typ v deklaracích funkce v programu. Funkce vrátí hodnotu při `return` je spustit příkaz, který obsahuje výraz. Vyhodnotí výraz převést na typ vrácené hodnoty, pokud potřebné a vrácený do bodu, kdy byla zavolána funkce. Pokud je funkce deklarovat s návratovým typem `void`, návratový příkazu, který obsahuje výraz generuje upozornění a výraz, nebude hodnocen.  
  
 Následující příklady znázorňují návratové hodnoty funkce.  
  
```  
typedef struct    
{  
    char name[20];  
    int id;  
    long class;  
} STUDENT;  
  
/* Return type is STUDENT: */  
  
STUDENT sortstu( STUDENT a, STUDENT b )  
{  
    return ( (a.id < b.id) ? a : b );  
}  
```  
  
 Tento příklad definuje `STUDENT` zadejte s `typedef` deklarace a definuje funkci `sortstu` tak, aby měl `STUDENT` návratovým typem. Funkce vybere a vrátí jeden z jeho struktura dva argumenty. V následující volání funkce kompilátoru zkontroluje, zkontrolujte, zda jsou typy argumentů `STUDENT`.  
  
> [!NOTE]
>  Efektivita by vylepšit pomocí předání ukazatele struktura, nikoli celý struktury.  
  
```  
char *smallstr( char s1[], char s2[] )  
{  
    int i;  
  
    i = 0;  
    while ( s1[i] != '\0' && s2[i] != '\0' )  
        i++;  
    if ( s1[i] == '\0' )  
        return ( s1 );  
    else  
        return ( s2 );  
}  
```  
  
 Tento příklad definuje funkci vrácení ukazatele na pole znaků. Funkce přebírá dva znaková pole (řetězce) jako argumenty a vrací ukazatel na kratší dvou řetězců. Ukazatel na pole odkazuje na první prvků pole a má typ; proto návratový typ funkce je ukazatel na typ `char`.  
  
 Není nutné deklarovat funkce s `int` návratový typ před voláním, i když prototypy se doporučuje, aby správný typ kontrola argumenty a návratové hodnoty je povolen.  
  
## <a name="see-also"></a>Viz také  
 [Definice funkcí jazyka C](../c-language/c-function-definitions.md)