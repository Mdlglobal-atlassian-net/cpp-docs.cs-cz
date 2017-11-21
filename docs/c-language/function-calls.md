---
title: "Volání funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls, about function calls
- function calls
ms.assetid: 2cfa897d-3874-4820-933c-e624f75d1712
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3f04acfe9458b8a10142ef7bc12155bc8e2a9a52
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="function-calls"></a>Volání funkcí
A *volání funkce* je výraz, který předá řízení a argumenty (pokud existuje) funkce a formulář:  
  
 *výraz* (*seznam výrazů*opt)  
  
 kde *výraz* je název funkce nebo se vyhodnocuje adresu funkce a *seznam výrazů* je seznam výrazů (oddělené čárkami). Hodnoty těchto pozdějších výrazů jsou argumenty předané funkci. Pokud funkce nevrací hodnotu, pak je deklarovat, že bude funkci, která vrátí `void`.  
  
 Pokud existuje deklaraci před voláním funkce, ale je uvedeny žádné informace pro parametry, všechny nedeklarované argumenty jednoduše podstoupit obvyklé aritmetické převody.  
  
> [!NOTE]
>  Výrazy v seznamu argumentů funkce může být vyhodnocen v libovolném pořadí, tak argumenty, jejichž hodnoty mohou být změněna vedlejší účinky z jiné argument mít undefined hodnoty. Bod sekvence definované operátor volání funkce pouze zaručuje, že všechny vedlejší účinky v seznamu argumentů vyhodnocují před ovládací prvek předává do volaná funkce. (Všimněte si, že je pořadí, ve kterém jsou argumenty nabídnutých v zásobníku samostatné věci.) V tématu [body sekvence](../c-language/c-sequence-points.md) Další informace.  
  
 V žádném volání funkce Jediným požadavkem je, že adresu funkce se musí vyhodnotit výraz před závorkách. To znamená, že funkci nelze volat prostřednictvím jakýkoli výraz ukazatel na funkci.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje volat z volání funkce `switch` příkaz:  
  
```  
int main()  
{  
    /* Function prototypes */  
  
    long lift( int ), step( int ), drop( int );  
    void work( int number, long (*function)(int i) );  
  
    int select, count;  
    .  
    .  
    .  
    select = 1;  
    switch( select )   
    {  
        case 1: work( count, lift );  
                break;  
  
        case 2: work( count, step );  
                break;  
  
        case 3: work( count, drop );  
                /* Fall through to next case */  
        default:  
                break;  
    }  
}  
  
/* Function definition */  
  
void work( int number, long (*function)(int i) )  
{  
    int i;  
    long j;  
  
    for ( i = j = 0; i < number; i++ )  
            j += ( *function )( i );  
}  
```  
  
 V tomto příkladu volání funkce v `main`,  
  
```  
work( count, lift );  
```  
  
 předá proměnná typu integer `count`a adresu funkce `lift` funkce `work`. Všimněte si, že je adresa funkce předán jednoduše tím, že identifikátor funkce, protože identifikátor funkce vyhodnocen jako výraz ukazatele. Pokud chcete používat funkce identifikátor tímto způsobem, musí být funkce deklarován nebo definované před identifikátor se používá; identifikátor, jinak se nerozpoznal. V tomto případě prototypu pro `work` je uveden na začátku `main` funkce.  
  
 Parametr `function` v `work` je deklarován jako ukazatel na funkci trvá jeden `int` argument a vrací **dlouho** hodnotu. Závorky název parametru jsou požadovány; bez, by deklaraci zadejte vrácení ukazatel na funkci **dlouho** hodnotu.  
  
 Funkce `work` volá funkci vybrané z uvnitř **pro** smyčky pomocí následující volání funkce:  
  
```  
( *function )( i );  
```  
  
 Jeden argument, `i`, je předán volaná funkce.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../c-language/functions-c.md)