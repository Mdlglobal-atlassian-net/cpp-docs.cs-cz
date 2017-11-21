---
title: "Deklarace ukazatelů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- pointer declarations
- declarations, pointers
- const keyword [C]
- pointers, declarations
ms.assetid: 8b3b7fc7-f44d-480d-b6f9-cebe4e5462a6
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e7d8b351f7cc58d37d4da8bc273d8541aee54446
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="pointer-declarations"></a>Deklarace ukazatelů
"Ukazatel prohlášení" názvy proměnné ukazatele a určuje typ objektu, na kterou odkazuje proměnná. Proměnná definovaná jako ukazatel obsahuje adresu paměti.  
  
## <a name="syntax"></a>Syntaxe  
 *deklarátor*:  
 &nbsp;&nbsp;*ukazatel*<sub>opt</sub> *přímo deklarátor*  
  
 *deklarátor přímo*:  
 &nbsp;&nbsp;*identifikátor*  
  
 &nbsp;&nbsp;**(** *deklarátor* **)**  
  
 &nbsp;&nbsp;*deklarátor přímo* **[** *konstantní výraz*<sub>opt</sub> **]**  
  
 &nbsp;&nbsp;*deklarátor přímo* **(** *seznam parametrů typu* **)**  
  
 &nbsp;&nbsp;*deklarátor přímo* **(** *seznam identifikátorů*<sub>opt</sub> **)**  
  
 *ukazatel*:  
 &nbsp;&nbsp;**\****seznam typů kvalifikátor*<sub>opt</sub>  
  
 &nbsp;&nbsp;**\****seznam typů kvalifikátor*<sub>opt</sub> *ukazatele*  
  
 *seznam typů kvalifikátor*:  
 &nbsp;&nbsp;*Kvalifikátor typu*  
  
 &nbsp;&nbsp;*seznam typů kvalifikátor* *kvalifikátor typu*  
  
 *Specifikátor typu* dává typ objektu, který může být všechny základní, struktura nebo typu union. Proměnné ukazatele může taky ukazovat na funkce, pole a jiné ukazatele. (Informace o deklarace a výklad složitějších typy ukazatelů, najdete v části [interpretace další složité Deklarátory](../c-language/interpreting-more-complex-declarators.md).)  
  
 Tím, že *specifikátor typu* **void**, můžete počkat, specifikace typu, na který odkazuje ukazatele. Tyto položky se označuje jako "ukazatel na **void**" a je zapsán jako `void *`. Proměnná definovaná jako ukazatel na *void* lze použít tak, aby odkazoval na objekt libovolného typu. Však provádějí většinu operací na ukazatele nebo na objektu, na kterou odkazuje, na kterou odkazuje typ musí být explicitně zadáno pro každou operaci. (Proměnné typu **char \***  a typ **void \***  jsou kompatibilní s přiřazení bez typu přetypování.) Takový převod lze provést pomocí typu přetypování (viz [převody přetypování](../c-language/type-cast-conversions.md) Další informace).  
  
 *Kvalifikátor typu* může být buď **const** nebo **volatile**, nebo obojí. Tyto specifikují, zda je ukazatel nelze změnit pomocí této aplikace (**const**), nebo který ukazatele lze upravit legálně proces mimo kontrolu programu (**volatile**). (Viz [kvalifikátory typu](../c-language/type-qualifiers.md) Další informace o **const** a **volatile**.)  
  
 *Deklarátor* názvy proměnnou a může obsahovat modifikátor typu. Například pokud *deklarátor* představuje pole, typ ukazatele je upravit tak, aby se ukazatel myši na pole.  
  
 Ukazatel na strukturu, union nebo výčtového typu můžou deklarovat, než můžete definovat struktury, sjednocení nebo výčtového typu. Pomocí značky struktury nebo sjednocení, jak je znázorněno v následujících příkladech je deklarovat ukazatele. Tato prohlášení jsou povolena, protože kompilátor není nutné znát velikost struktury nebo sjednocení k přidělení místa pro proměnné ukazatele.  
  
## <a name="examples"></a>Příklady  
 Následující příklady znázorňují deklarace ukazatelů.  
  
```  
char *message; /* Declares a pointer variable named message */  
```  
  
 *Zpráva* ukazatel ukazuje proměnné se **char** typu.  
  
```  
int *pointers[10];  /* Declares an array of pointers */  
```  
  
 *Ukazatele* pole má 10 elementy; každý prvek je ukazatel na proměnná s **int** typu.  
  
```  
int (*pointer)[10]; /* Declares a pointer to an array of 10 elements */  
```  
  
 *Ukazatel* proměnná ukazuje na pole s 10 elementy. Každý prvek toto pole má **int** typu.  
  
```  
int const *x;      /* Declares a pointer variable, x,  
                      to a constant value */   
```  
  
 Ukazatele *x* lze upravit tak, aby odkazoval na jiný **int** hodnotu, ale hodnota, na která se nemůže být upraven body.  
  
```  
const int some_object = 5 ;  
int other_object = 37;  
int *const y = &fixed_object;  
int volatile *const z = &some_object;  
int *const volatile w = &some_object;  
```  
  
 Proměnná *y* v těchto deklaracích je deklarován jako konstantní ukazatel **int** hodnotu. Je možné upravit hodnotu odkazuje, ale ukazatel sám sebe musí vždy přejděte do stejného umístění: adresa *fixed_object*. Podobně *z* konstantní ukazatel, ale je také deklarovaný tak, aby odkazoval **int** jehož hodnota nemůže být upraven program. Další specifikátor **volatile** znamená, že i když hodnota **const int** na kterou odkazuje *z* nemůže být upravena programem, může to legálně být upravit proces, který běží souběžně program. Prohlášení o *w* Určuje, že tento program nelze změnit hodnotu ukazuje, že program nelze změnit, ukazatele.  
  
```  
struct list *next, *previous; /* Uses the tag for list */  
```  
  
 Tento příklad deklaruje dvě proměnné ukazatele *Další* a *předchozí*, které odkazují na typ struktury *seznamu*. Toto prohlášení se může zobrazit před definice *seznamu* struktura zadejte (viz další příklad), tak dlouho, dokud *seznamu* definice typu jsou stejně viditelné jako deklaraci.  
  
```  
struct list   
{  
    char *token;  
    int count;  
    struct list *next;  
} line;  
```  
  
 Proměnná *řádku* má typ struktury s názvem *seznamu*. *Seznamu* typ struktury má tři členy: první člen je ukazatel na **char** je druhá hodnota, **int** hodnota a třetí je ukazatel na jiné *seznamu* struktura.  
  
```  
struct id   
{  
    unsigned int id_no;  
    struct name *pname;  
} record;  
```  
  
 Proměnná *záznam* má typ struktury *id*. Všimněte si, že *pname* je deklarován jako ukazatel na jiný typ struktura s názvem *název*. Toto prohlášení se může zobrazit před *název* je definovaný typ.  
  
## <a name="see-also"></a>Viz také  
 [Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)