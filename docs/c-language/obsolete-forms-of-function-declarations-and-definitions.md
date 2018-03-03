---
title: "Zastaralé formy deklarací a definic funkcí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- old style function declarations
ms.assetid: 67c5038f-0529-4f29-9d0f-c27580977b50
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c7de356abb7078b7dd50f0d90bf4ecb0a046945b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="obsolete-forms-of-function-declarations-and-definitions"></a>Zastaralé formy deklarací a definic funkcí
Deklarace a definice funkcí starého typu používají mírně odlišná pravidla pro deklarování parametrů než syntaxe doporučená standardem ANSI jazyka C. Za prvé, deklarace starého typu nemají seznam parametrů. Za druhé, parametry jsou uvedeny v definici funkce, ale jejich typy nejsou deklarovány v seznamu parametrů. Deklarace typů předcházejí složený příkaz tvořící tělo funkce. Syntaxe starého typu je zastaralá a neměla by se v novém kódu používat. Ačkoli kód používající syntaxi starého typu je nadále podporován. Tento příklad ukazuje zastaralé tvary deklarací a definicí:  
  
```  
double old_style();           /* Obsolete function declaration */  
  
double alt_style( a , real )  /* Obsolete function definition */  
    double *real;   
    int a;   
{  
    return ( *real + a ) ;  
}  
```  
  
 Funkce, která vrátí celé číslo nebo ukazatel se stejnou velikostí jako typ `int`, nemusí mít deklaraci, i když je deklarace doporučena.  
  
 Z důvodu dodržení standardu ANSI jazyka C staré typy deklarací funkce používající tři tečky nyní vygenerují chybu při kompilaci s možnosti /Za a upozornění úrovně 4 při kompilaci s možností /Ze. Příklad:  
  
```  
void funct1( a, ... )  /* Generates a warning under /Ze or */  
int a;                 /* an error when compiling with /Za */  
{  
}  
```  
  
 Tuto deklaraci byste měli přepsat jako prototyp:  
  
```  
void funct1( int a, ... )  
{  
}  
```  
  
 Deklarace funkce starého typu také vygenerují upozornění, pokud následně deklarujete nebo definujete stejnou funkci se třemi tečkami nebo parametr typu, který není stejný jako jeho povýšený typ.  
  
 V další části [definice funkcí jazyka C](../c-language/c-function-definitions.md), ukazuje syntaxi pro definice funkcí, včetně syntaxe starého. Je nonterminal pro seznam parametrů v syntaxi starého *seznam identifikátorů*.  
  
## <a name="see-also"></a>Viz také  
 [Přehled funkcí](../c-language/overview-of-functions.md)