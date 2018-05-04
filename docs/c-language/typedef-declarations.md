---
title: TypeDef – deklarace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarations, typedef
- typedef declarations
- types [C], declarations
ms.assetid: e92a3b82-9269-4bc6-834a-6f431ccac83e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 192f7ab037362219261852cfdb0a5eac53e5df9f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="typedef-declarations"></a>Typedef – deklarace
Deklarace definice typedef je deklaraci s typedef jako třídy úložiště. Nový typ se změní deklarátor. Typedef – deklarace můžete použít k vytvoření kratší nebo smysluplnější názvů pro typy už definované C nebo pro typy, které mají deklarován. Názvy typedef umožňují zapouzdřit podrobnosti implementace, které se mohou změnit.  
  
 Deklaraci typedef interpretována stejným způsobem jako proměnné nebo funkce deklarace, ale identifikátor, namísto za předpokladu, že v typu zadaném pomocí deklarace, se změní na synonymum pro typ.  
  
## <a name="syntax"></a>Syntaxe  
 `declaration`:  
 *specifikátory deklarace init deklarátor list* opt **;**  
  
 *specifikátory deklarace*:  
 *specifikátor třídy úložiště specifikátory deklarace* opt  
  
 *Specifikátor typu deklarace – specifikátory* opt  
  
 *Kvalifikátor typu deklarace – specifikátory* opt  
  
 *specifikátor třídy úložiště*:  
 `typedef`  
  
 *Specifikátor typu*:  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **Podepsané**  
  
 **Bez znaménka**  
  
 *struct-or-union-specifier*  
  
 *enum – specifikátor*  
  
 *typedef-name*  
  
 *TypeDef – název*:  
 *Identifikátor*  
  
 Všimněte si, že deklaraci typedef nevytvoří typy. Vytvoří synonyma pro existující typy nebo názvy pro typy, které může být určen jinými způsoby. Pokud je jako specifikátor typu použit název typedef, lze spojovat s určitým specifikátory typu, ale jiné ne. Zahrnout přijatelné modifikátory **const** a `volatile`.  
  
 Názvy typu TypeDef sdílet s obyčejnou identifikátory obor názvů (viz [obory názvů](../c-language/name-spaces.md) Další informace). Program tedy může mít název typedef a identifikátor místního oboru se stejným názvem. Příklad:  
  
```  
typedef char FlagType;  
  
int main()  
{  
}  
  
int myproc( int )  
{  
    int FlagType;  
}  
```  
  
 Při deklarování identifikátoru místního oboru se stejným názvem jako typedef nebo při deklarování členu struktury nebo sjednocení ve stejném oboru nebo ve vnitřním oboru musí být určen specifikátor typu. Tento příklad ukazuje tato omezení:  
  
```  
typedef char FlagType;  
const FlagType x;  
```  
  
 Pro opětovné použití názvu `FlagType` pro identifikátor, člen struktury nebo člen sjednocení musí být určen typ:  
  
```  
const int FlagType;  /* Type specifier required */  
```  
  
 Nestačí říct  
  
```  
const FlagType;      /* Incomplete specification */  
```  
  
 protože `FlagType` se považuje za část typu, nikoli identifikátor, který je znovu deklarován. Tato deklarace je neplatnou jako  
  
```  
int;  /* Illegal declaration */  
```  
  
 Pomocí typedef je možné deklarovat jakýkoli typ, včetně ukazatele, funkce a typů polí. Je možné deklarovat název typedef pro ukazatel na typ struktury nebo sjednocení před definováním typu struktury nebo sjednocení, pokud má definice stejnou viditelnost jako deklarace.  
  
 Názvy typu TypeDef můžete použít ke zlepšení čitelnosti kódu. Všechny tři následující prohlášení o `signal` zadejte přesně stejného typu, nejprve bez provedení použití všechny názvy typu typedef.  
  
```  
typedef void fv( int ), (*pfv)( int );  /* typedef declarations */  
  
void ( *signal( int, void (*) (int)) ) ( int );  
fv *signal( int, fv * );   /* Uses typedef type */  
pfv signal( int, pfv );    /* Uses typedef type */  
```  
  
## <a name="examples"></a>Příklady  
 Následující příklady ilustrují typedef – deklarace:  
  
```  
typedef int WHOLE; /* Declares WHOLE to be a synonym for int */  
```  
  
 Všimněte si, že `WHOLE` může být použit v deklarace proměnné, jako `WHOLE i;` nebo `const WHOLE i;`. Ale deklaraci `long WHOLE i;` by byla neplatná.  
  
```  
typedef struct club   
{  
    char name[30];  
    int size, year;  
} GROUP;  
```  
  
 Tento příkaz deklaruje `GROUP` jako typ struktura se tři členy. Od značku struktura `club`, je zadána také, název typedef (`GROUP`) nebo struktura značky lze použít v deklaracích. Je nutné použít struct – klíčové slovo se značky a struct – klíčové slovo nelze použít s názvem typedef.  
  
```  
typedef GROUP *PG; /* Uses the previous typedef name   
                      to declare a pointer            */  
```  
  
 Typ `PG` je deklarován jako ukazatel `GROUP` typu, který naopak je definována jako typ struktury.  
  
```  
typedef void DRAWF( int, int );  
```  
  
 Tento příklad poskytuje typ `DRAWF` pro funkci vrácení žádná hodnota a přepnutím dva argumenty int. To znamená, například která deklaraci  
  
```  
DRAWF box;   
```  
  
 je ekvivalentní deklaraci  
  
```  
void box( int, int );  
```  
  
## <a name="see-also"></a>Viz také  


