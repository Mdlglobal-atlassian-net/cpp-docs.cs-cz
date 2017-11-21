---
title: "Deklarace sjednocení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- unions
- union keyword [C], declarations
- variant records
ms.assetid: 978c6165-e0ae-4196-afa7-6d94e24f62f7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 57e7db99e90e68e71dae4fc00f271b3831a5fc39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="union-declarations"></a>Deklarace sjednocení
"Union prohlášení" Určuje sadu hodnot proměnných a volitelně značku pojmenování sjednocení. Hodnoty proměnné se nazývají "členové" sjednocení a může mít různé typy. Sjednocení se podobá "variantní záznamy" v dalších jazycích.  
  
## <a name="syntax"></a>Syntaxe  
 *Struktura nebo sjednocení specifikátor*:  
 *Struktura nebo sjednocení identifikátor* opt**{** *seznam struktura prohlášení* **}**  
  
 *identifikátor struktura nebo sjednocení*  
  
 *Struktura nebo sjednocení*:  
 **Struktura**  
  
 **sjednocení**  
  
 *seznam struktura prohlášení*:  
 *Struktura – deklarace*  
  
 *seznam struktura prohlášení struktura – deklarace*  
  
 Je definován union obsahu  
  
 *Struktura deklarace*:  
 *specifikátor. kvalifikátor seznamu struktura – deklarátor seznamu***;**   
  
 *specifikátor. kvalifikátor seznamu*:  
 *Specifikátor typu specifikátor kvalifikátor list* opt  
  
 *Kvalifikátor typu specifikátor kvalifikátor list* opt  
  
 *Struktura – deklarátor seznamu*:  
 *deklarátor – struktura*  
  
 *Struktura – deklarátor seznamu***,***deklarátor – struktura*   
  
 Proměnná s **sjednocení** typ ukládá jednu z hodnot fronty definovaných podle typu. Stejná pravidla řídí struktury a sjednocení deklarace. Sjednocení může mít také bit pole.  
  
 Členové sjednocení nemůže mít typ nekompletní, zadejte `void`, nebo typ funkce. Členy proto nemůže být instanci sjednocení ale může být ukazatelé na typ union se deklarovat.  
  
 Deklarace typu union je pouze šablony. Paměti není vyhrazena, dokud je deklarovaná proměnnou.  
  
> [!NOTE]
>  Pokud je deklarovaná spojení dvou typů a jedna hodnota je uložena, ale sjednocení přistupuje s jiným typem, nespolehlivé výsledky. Například spojení **float** a `int` je deklarován. A **float** hodnota je uložena, ale tento program později přistupuje k hodnotě jako `int`. V takové situaci by hodnota závisí na interní úložiště **float** hodnoty. Celočíselná hodnota, nebudou spolehlivé.  
  
## <a name="examples"></a>Příklady  
 Následují příklady sjednocení:  
  
```  
union sign   /* A definition and a declaration */  
{  
    int svar;  
    unsigned uvar;  
} number;  
```  
  
 Tento příklad definuje union proměnná s `sign` zadejte a deklaruje proměnné s názvem `number` , má dva členy: `svar`, znaménkem, a `uvar`, celé číslo bez znaménka. Toto prohlášení umožňuje aktuální hodnota `number` ukládaly jako přihlášeni nebo hodnotu bez znaménka. Značka přidružené tomuto typu union je `sign`.  
  
```  
union               /* Defines a two-dimensional */  
{                   /*  array named screen */  
    struct      
    {   
      unsigned int icon : 8;    
      unsigned color : 4;  
    } window1;  
    int screenval;  
} screen[25][80];  
```  
  
 `screen` Pole obsahuje 2 000 prvků. Každý element pole je jednotlivých – typ union s dva členy: `window1` a `screenval`. `window1` Člen je struktura s dva členy pole bit `icon` a `color`. `screenval` Člen `int`. V každém okamžiku každý union prvek obsahuje buď `int` reprezentována `screenval` nebo struktura reprezentována `window1`.  
  
 **Konkrétní Microsoft**  
  
 Vnořené sjednocení lze deklarovat anonymně, když jsou členy jiné struktura nebo union. Jedná se o příklad nameless unie:  
  
```  
struct str  
{  
    int a, b;  
    union            / * Unnamed union */  
    {  
      char c[4];  
      long l;  
      float f;  
   };  
   char c_array[10];  
} my_str;  
.  
.  
.  
my_str.l == 0L;  /* A reference to a field in the my_str union */  
```  
  
 Sjednocení jsou často vnořené ve strukturu, která obsahuje pole, udělíte typ dat ve sjednocení konkrétní kdykoli. Toto je příklad deklarace pro takové spojení:  
  
```  
struct x  
{  
    int type_tag;  
    union  
    {  
      int x;  
      float y;  
    }  
}  
```  
  
 V tématu [členové struktury a sjednocení](../c-language/structure-and-union-members.md) informace o odkazování na sjednocení.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)