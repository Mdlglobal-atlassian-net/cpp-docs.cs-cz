---
title: Deklarace ukazatelů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- pointer declarations
- declarations, pointers
- const keyword [C]
- pointers, declarations
ms.assetid: 8b3b7fc7-f44d-480d-b6f9-cebe4e5462a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f7e5f8933aabe36362938a23c28ed1cd562a579
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205390"
---
# <a name="pointer-declarations"></a>Deklarace ukazatelů
"Deklarace ukazatelů" název proměnné ukazatele a určuje typ objektu, na kterou ukazuje proměnná. Proměnná deklarovaná jako ukazatel obsahuje adresu paměti.  
  
## <a name="syntax"></a>Syntaxe

*deklarátor*:  
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatel*<sub>optimalizované</sub> *direct-declarator*  

*přímé declarator*:  
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*  
&nbsp;&nbsp;&nbsp;&nbsp;**(** *deklarátor* **)**  
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **[** *konstantní výraz*<sub>optimalizované</sub> **]**  
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **(** *seznam parametrů typu* **)**  
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **(** *seznam identifikátorů*<sub>optimalizované</sub> **)**  

*ukazatel*:  
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *seznam typů kvalifikátor*<sub>optimalizované</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *seznam typů kvalifikátor*<sub>optimalizované</sub> *ukazatele*  

*seznam typů kvalifikátor*:  
&nbsp;&nbsp;&nbsp;&nbsp;*Kvalifikátor typu*  
&nbsp;&nbsp;&nbsp;&nbsp;*seznam typů kvalifikátor* *kvalifikátor typu*  
  
 *Specifikátor typu* poskytuje typ objektu, který může být jakýkoli základní, struktury nebo sjednocení. Proměnné ukazatele může poukazovat na funkce, polí a dalšími ukazateli. (Informace o deklarování a interpretace složitějších typy ukazatelů, [interpretace složitějších Deklarátorů](../c-language/interpreting-more-complex-declarators.md).)  
  
 Tím, že *specifikátor typu* **void**, můžete odložit určení typu, na který ukazatel odkazuje. Tyto položky se označuje jako "ukazatel na **void**" a je zapsán jako `void *`. Proměnná deklarovaná jako ukazatel na *void* můžete použít tak, aby odkazoval na objekt jakéhokoli typu. Však provádějí většinu operací na ukazatel myši nebo na objekt, na kterou odkazuje, na kterou odkazuje typ musí být explicitně zadán pro každou operaci. (Proměnné typu **char** <strong>\*</strong> a typ **void** <strong>\*</strong> jsou kompatibilní s přiřazení bez typu přetypování.) Takový převod lze provést pomocí přetypování typu (viz [převody přetypování](../c-language/type-cast-conversions.md) Další informace).  
  
 *Kvalifikátor typu* může být buď **const** nebo **volatile**, nebo obojí. Tyto určit, v uvedeném pořadí, že program sám nemůže upravit ukazatel (**const**), nebo kterou ukazatele lze upravovat oprávněně některé procesem mimo kontrolu program (**volatile**). (Viz [kvalifikátory typu](../c-language/type-qualifiers.md) Další informace o **const** a **volatile**.)  
  
 *Deklarátor* názvy proměnných a může obsahovat modifikátor typu. Například pokud *deklarátor* představuje pole, typ ukazatele je upravit tak, aby se ukazatel na pole.  
  
 Před definováním struktury, sjednocení nebo Výčtový typ. je možné deklarovat ukazatel na strukturu, sjednocení nebo výčtového typu. Deklarovat ukazatel pomocí značky struktury nebo sjednocení, jak je znázorněno v následujících příkladech. Takové deklarace jsou povolená, protože není potřeba znát velikost struktury nebo sjednocení k přidělení místa pro proměnnou ukazatel kompilátor.  
  
## <a name="examples"></a>Příklady  
 Následující příklady znázorňují deklarace ukazatelů.  
  
```  
char *message; /* Declares a pointer variable named message */  
```  
  
 *Zpráva* ukazatel odkazuje na proměnnou s **char** typu.  
  
```  
int *pointers[10];  /* Declares an array of pointers */  
```  
  
 *Ukazatele* pole obsahuje 10 prvků; každý element je ukazatel na proměnnou s **int** typu.  
  
```  
int (*pointer)[10]; /* Declares a pointer to an array of 10 elements */  
```  
  
 *Ukazatel* proměnná ukazuje na pole s 10 prvků. Každý prvek v tomto poli má **int** typu.  
  
```  
int const *x;      /* Declares a pointer variable, x,  
                      to a constant value */   
```  
  
 Ukazatel *x* lze upravit tak, aby odkazoval na jiný **int** hodnotou, ale skutečná hodnota, na který se nemůže modifikovat body.  
  
```  
const int some_object = 5 ;  
int other_object = 37;  
int *const y = &fixed_object;  
int volatile *const z = &some_object;  
int *const volatile w = &some_object;  
```  
  
 Proměnná *y* v tyto deklarace je deklarován jako konstantní ukazatel **int** hodnotu. Odkazuje na hodnotu lze upravit, ale ukazatel sám musí vždy odkazovat do stejného umístění: adresa *fixed_object*. Podobně *z* konstantní ukazatel, ale je také deklarován tak, aby odkazovala na **int** jehož hodnota se nemůže modifikovat programem. Další specifikátor **volatile** znamená, že i když hodnota **const int** odkazované *z* nemůže být upraven programem, může oprávněně být upravit proces spuštěný současně program. Deklarace *w* Určuje, že program nelze změnit hodnotu na, že program nelze změnit, ukazatel.  
  
```  
struct list *next, *previous; /* Uses the tag for list */  
```  
  
 Tento příklad deklaruje dvě proměnné ukazatele *Další* a *předchozí*, které odkazují na typ struktury *seznamu*. Tato deklarace se může objevit před definici *seznamu* typ struktury (viz následující příklad), tak dlouho, dokud *seznamu* definice typu má stejnou viditelnost jako deklarace.  
  
```  
struct list   
{  
    char *token;  
    int count;  
    struct list *next;  
} line;  
```  
  
 Proměnná *řádku* má typ struktury s názvem *seznamu*. *Seznamu* typ struktury má tři členy: první člen je ukazatel na **char** druhá hodnota, je **int** hodnoty a třetí je ukazatel na jiný *seznamu* struktury.  
  
```  
struct id   
{  
    unsigned int id_no;  
    struct name *pname;  
} record;  
```  
  
 Proměnná *záznam* má typ struktury *id*. Všimněte si, že *pname* je deklarována jako ukazatel na jiný typ struktury s názvem *název*. Tato deklarace se může objevit před *název* je typ definován.  
  
## <a name="see-also"></a>Viz také  
 [Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)