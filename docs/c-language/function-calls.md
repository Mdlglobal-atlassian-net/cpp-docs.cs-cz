---
title: Volání funkcí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls, about function calls
- function calls
ms.assetid: 2cfa897d-3874-4820-933c-e624f75d1712
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8849cd932bd44b5dd7094d05470a4a97f58b08cb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755488"
---
# <a name="function-calls"></a>Volání funkcí
A *volání funkce* je výraz, který předává řízení a argumenty (pokud existuje) na funkci a má formát:  
  
*výraz* (*seznam výrazů*<sub>optimalizované</sub>)  
  
kde *výraz* je název funkce nebo vyhodnotí na adresu funkce a *seznam výrazů* je seznamem výrazů (oddělený čárkami). Hodnoty těchto pozdějších výrazů jsou argumenty předané funkci. Pokud funkce nevrací hodnotu, pak se deklaruje jako funkce, která vrátí `void`.  
  
Pokud existuje deklarace před voláním funkce, ale žádné údaje o parametrech, procházejí argumentů nedeklarovaný jednoduše obvyklé aritmetické převody.  
  
> [!NOTE]
>  Výrazy v seznamu argumentů funkce mohou být vyhodnoceny v libovolném pořadí, proto mít argumenty, jejichž hodnoty mohou být změněna vedlejším účinkům z jiného argumentu nedefinované hodnoty. Tento bod sekvence určené operátor volání funkce pouze zaručuje, že všechny vedlejší účinky jsou v seznamu argumentů se vyhodnocují před řízení se předá do volané funkce. (Všimněte si, že pořadí, ve kterém jsou argumenty posunuto v zásobníku je samostatný otázkou.) Zobrazit [body sekvence](../c-language/c-sequence-points.md) Další informace.  
  
V žádném volání funkce Jediným požadavkem je, že výraz před závorky se musí vyhodnotit na adresu funkce. To znamená, že funkce lze volat přes libovolný výraz ukazatele na funkce.  
  
## <a name="example"></a>Příklad  
Tento příklad znázorňuje volání funkce volána z `switch` – příkaz:  
  
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
  
předá proměnná typu integer `count`a adresu funkce `lift` funkci `work`. Všimněte si, že je adresa funkce předán jednoduše tak, že udělíte identifikátor funkce, protože identifikátor funkce je vyhodnocen jako výraz ukazatele. Tímto způsobem použít identifikátor funkce, musí být funkce deklarované nebo definované předtím, než se používá identifikátor; v opačném případě identifikátor nebyl rozpoznán. V tomto případě prototyp `work` dostane na začátku `main` funkce.  
  
Parametr `function` v `work` je deklarováno jako ukazatel na funkci s jeden `int` argument a vrátí **dlouhé** hodnotu. Závorky kolem názvu parametru jsou povinné; bez nich deklaraci zadáte vrací ukazatel na funkci **dlouhé** hodnotu.  
  
Funkce `work` volá funkci vybrané z uvnitř **pro** smyčky s použitím následující volání funkce:  
  
```  
( *function )( i );  
```  
  
Jeden argument, `i`, je předán do volané funkce.  
  
## <a name="see-also"></a>Viz také  
[Funkce](../c-language/functions-c.md)