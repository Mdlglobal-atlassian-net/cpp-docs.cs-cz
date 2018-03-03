---
title: Deklarace struktury | Microsoft Docs
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
- structure declarations
- anonymous structures
- types [C], declarations
- structure members
- embedded structures
ms.assetid: 5be3be77-a236-4153-b574-7aa77675df7f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aada86ec63ccade17577f5410ced62cb4d5cf03f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="structure-declarations"></a>Deklarace struktury
"Struktury deklarace" názvy typu a určuje pořadí proměnných hodnot (nazývané "členy" nebo "pole" struktury), které může mít různé typy. Volitelné identifikátor, s názvem "značku", poskytuje název typu Struktura a mohou být používány následující odkazy na typ struktury. Proměnné tohoto typu struktura obsahuje celého pořadí definované typu. Struktury v jazyce C jsou podobné typy označuje jako "záznamy" v dalších jazycích.  
  
## <a name="syntax"></a>Syntaxe  
 *Struktura nebo sjednocení specifikátor*:  
 *Struktura nebo sjednocení identifikátor* opt**{** *seznam struktura prohlášení* **}**  
  
 *identifikátor struktura nebo sjednocení*  
  
 *Struktura nebo sjednocení*:  
 **struct**  
  
 **sjednocení**  
  
 *seznam struktura prohlášení*:  
 *Struktura – deklarace*  
  
 *seznam struktura prohlášení struktura – deklarace*  
  
 Je definován struktura obsahu  
  
 *Struktura deklarace*:  
 *specifikátor. kvalifikátor seznamu struktura – deklarátor seznamu***;**   
  
 *specifikátor. kvalifikátor seznamu*:  
 *Specifikátor typu specifikátor kvalifikátor list* opt  
  
 *Kvalifikátor typu specifikátor kvalifikátor list* opt  
  
 *Struktura – deklarátor seznamu*:  
 *deklarátor – struktura*  
  
 *Struktura – deklarátor seznamu***,***deklarátor – struktura*   
  
 *Struktura deklarátor*:  
 `declarator`  
  
 Deklarace typu struktura není vyčleněné místa pro strukturu. Jedná pouze o šablonu pro novější deklarace proměnné struktury.  
  
 A předtím definovaný *identifikátor* (značka) slouží k odkazování na typu Struktura definovaný v jiné oblasti. V takovém případě *seznam struktura prohlášení* nelze opakovat tak dlouho, dokud definice je viditelné. Deklarace ukazatelů struktury a definice TypeDef pro typy struktur může použít struktura značky, než je definován typ struktury. Definice struktury však musí být zjištěny před použitím skutečné velikosti pole. Toto je nekompletní definici typu a typ značky. Pro tuto definici dokončit musí definice typu později zobrazí ve stejném oboru.  
  
 *Seznam struktura prohlášení* Určuje typy a názvy členů struktury. A *seznam struktura prohlášení* argument obsahuje jeden nebo více proměnné nebo pole bit deklarace.  
  
 Každá proměnná deklarované v *seznam struktura prohlášení* je definován jako člen skupiny typ struktury. Deklarace proměnných v rámci *seznam struktura prohlášení* mít stejný formát jako ostatní deklarace proměnných popsaných v této části, s tím rozdílem, že deklarací nemůže obsahovat specifikátory třídy úložiště nebo inicializátory. Členové struktury může mít všechny typy proměnných s výjimkou typu `void`, neúplné typ nebo typ funkce.  
  
 Člena nelze deklarovat tak, aby měl typ strukturu, ve kterém se zobrazí. Člen však lze deklarovat jako ukazatel na typ struktury, ve kterých se vyskytuje, pokud má tento typ struktura značky. To umožňuje vytvářet propojené seznamy struktury.  
  
 Struktury použijte stejný obor jako další identifikátory. Struktura identifikátory musí být odlišný od jiných struktury, sjednocení a výčtové tagy s stejně viditelné.  
  
 Každý *struktura deklarace* v *seznam struktura prohlášení* musí být jedinečný v rámci seznamu. Však identifikátor názvy v *seznam struktura prohlášení* nemusí být odlišný z běžné názvy proměnných nebo identifikátory v seznamech deklarace jiné struktury.  
  
 Vnořené struktury je také přístupná, jako kdyby bylo deklarováno na úrovni oboru souboru. Například uděleno toto prohlášení:  
  
```  
struct a  
{  
    int x;  
    struct b  
    {  
      int y;  
    } var2;  
} var1;  
```  
  
 Tyto deklarace jsou obě právní:  
  
```  
struct a var3;  
struct b var4;  
```  
  
## <a name="examples"></a>Příklady  
 Tyto příklady ilustrují deklarace struktury:  
  
```  
struct employee   /* Defines a structure variable named temp */  
{  
    char name[20];  
    int id;  
    long class;  
} temp;  
```  
  
 `employee` Struktura má tři členy: `name`, `id`, a `class`. `name` Člen je 20 element pole, a `id` a `class` jsou jednoduché členy s `int` a **dlouho** typ, v uvedeném pořadí. Identifikátor `employee` je identifikátor struktura.  
  
```  
struct employee student, faculty, staff;  
```  
  
 Tento příklad definuje tři proměnné struktury: `student`, `faculty`, a `staff`. Každá struktura má stejný seznam tři členy. Členy jsou deklarovány tak, aby měl typ struktury `employee`definovaná v předchozím příkladu.  
  
```  
struct           /* Defines an anonymous struct and a */  
{                /* structure variable named complex  */  
    float x, y;  
} complex;  
```  
  
 `complex` Struktura má dva členy s **float** typu, `x` a `y`. Typ struktury nemá značku a je proto nepojmenovaný nebo anonymní.  
  
```  
struct sample   /* Defines a structure named x */  
{  
    char c;  
    float *pf;  
    struct sample *next;  
} x;  
```  
  
 První dva členové struktury jsou `char` proměnnou a odkazy **float** hodnotu. Třetí člen `next`, je deklarován jako ukazatel na strukturu typ definovaný (`sample`).  
  
 Anonymní struktury může být užitečné, když není potřeba značky s názvem. To je případ, kdy všechny instance struktura definuje jednu deklaraci. Příklad:  
  
```  
struct  
{  
    int x;  
    int y;  
} mystruct;  
```  
  
 Vložené struktury jsou často anonymní.  
  
```  
struct somestruct  
{  
    struct    /* Anonymous structure */  
    {  
        int x, y;  
    } point;  
    int type;  
} w;  
```  
  
 **Konkrétní Microsoft**  
  
 Kompilátor umožňuje nenastavenou velikostí nebo nulovou velikostí pole jako člen této struktury. To může být užitečné, pokud při použití v různých situacích se liší velikost konstantní pole. Prohlášení o tato struktura vypadá takto:  
  
 `struct`*identifikátor***{** *sadu deklarace* *zadejte název pole***[];};**  
  
 Polí s nenastavenou velikostí může se objevit pouze jako člen této struktury. Struktury obsahující deklarace nenastavenou velikostí pole lze začlenit do jiné struktury tak dlouho, dokud žádné další členy, které jsou deklarované v jakékoli nadřazených struktury. Pole takové struktury nejsou povoleny. `sizeof` Operátor, při použití proměnné tohoto typu nebo typ sebe, se předpokládá, 0 pro velikost pole.  
  
 Deklarace struktury můžete také zadat bez deklarátor když jsou členy jiné struktura nebo union. Názvy polí povýšené do nadřazených struktury. Nameless struktura například vypadá takto:  
  
```  
struct s  
{  
    float y;  
    struct  
    {  
        int a, b, c;  
    };  
    char str[10];  
} *p_s;  
.  
.  
.  
p_s->b = 100;  /* A reference to a field in the s structure */  
```  
  
 V tématu [členové struktury a sjednocení](../c-language/structure-and-union-members.md) informace o struktuře odkazy.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)