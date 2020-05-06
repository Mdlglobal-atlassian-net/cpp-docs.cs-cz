---
title: Deklarace ukazatelů
ms.date: 11/04/2016
helpviewer_keywords:
- pointer declarations
- declarations, pointers
- const keyword [C]
- pointers, declarations
ms.assetid: 8b3b7fc7-f44d-480d-b6f9-cebe4e5462a6
ms.openlocfilehash: 0ee6e9e78f3793cd1912ece7f8627a4be68e929c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232149"
---
# <a name="pointer-declarations"></a>Deklarace ukazatelů

*Deklarace ukazatele* Pojmenovává proměnnou ukazatele a určuje typ objektu, na který proměnná odkazuje. Proměnná deklarovaná jako ukazatel obsahuje adresu paměti.

## <a name="syntax"></a>Syntaxe

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatel na odkaz*<sub>opt</sub> *Direct – deklarátor*

*přímý – deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*RID*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *deklarátor* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor* **[** opt *-Expression*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct – deklarátor* **(** *parametr-Type-list* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor* **(** souhlas se *seznamem identifikátorů*<sub>opt</sub> **)**

*ukazatel*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*kvalifikátor typu – seznam –*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*Type-kvalifikátor – ukazatel na seznam*<sub>výslovných</sub> *pointer*

*typ – kvalifikátor – seznam*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kvalifikátor typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;kvalifikátor typu – *kvalifikátor typu* *seznamu*

*Specifikátor typu* poskytuje typ objektu, který může být jakýkoli typ základní, struktura nebo sjednocení. Proměnné ukazatelů mohou také ukazovat na funkce, pole a další ukazatele. (Informace o deklarování a interpretaci složitějších typů ukazatelů naleznete v tématu [Interpretace](../c-language/interpreting-more-complex-declarators.md)složitějších deklarátory.)

Vytvořením *specifikátoru typu* **void**lze zpozdit určení typu, na který ukazatel odkazuje. Taková položka je označována jako "ukazatel na **void**" a je zapsána jako `void *`. Proměnná deklarovaná jako ukazatel na *typ void* se dá použít k odkazování na objekt libovolného typu. Chcete-li však provést většinu operací na ukazateli nebo objektu, na který odkazuje, typ, na který odkazuje, je nutné explicitně zadat pro každou operaci. (Proměnné typu **char** <strong>\*</strong> a Type **void** <strong>\*</strong> jsou kompatibilní s přiřazením bez přetypování typu.) Takový převod lze provést s přetypováním typu (Další informace naleznete v tématu [převody přetypování](../c-language/type-cast-conversions.md) .)

*Kvalifikátor typu* může být buď **const** , nebo **volatile**, nebo obojí. Tato možnost určuje, že ukazatel nemůže být změněn samotným programem (**const**), nebo zda může být ukazatel oprávněně upraven jiným procesem nad rámec kontroly programu (**volatile**). (Další informace o **conscích** a **volatilích**naleznete v tématu [kvalifikátory typu](../c-language/type-qualifiers.md) .)

*Deklarátor* Pojmenovává proměnnou a může obsahovat modifikátor typu. Například pokud *deklarátor* představuje pole, je typ ukazatele změněn tak, aby byl ukazatelem na pole.

Před definováním struktury, sjednocení nebo výčtového typu můžete deklarovat ukazatel na typ struktury, sjednocení nebo výčtového typu. Deklarujete ukazatel pomocí značky struktury nebo sjednocení, jak je znázorněno v níže uvedených příkladech. Deklarace jsou povoleny, protože kompilátor nemusí znát velikost struktury nebo sjednocení k přidělení prostoru pro proměnnou ukazatele.

## <a name="examples"></a>Příklady

Následující příklady ilustrují deklarace ukazatelů.

```
char *message; /* Declares a pointer variable named message */
```

Ukazatel na *zprávu* odkazuje na proměnnou s typem **char** .

```
int *pointers[10];  /* Declares an array of pointers */
```

Pole s *ukazateli* má 10 prvků. Každý prvek je ukazatel na proměnnou s typem **int** .

```
int (*pointer)[10]; /* Declares a pointer to an array of 10 elements */
```

Proměnná *ukazatele* odkazuje na pole s 10 prvky. Každý prvek v tomto poli má typ **int** .

```
int const *x;      /* Declares a pointer variable, x,
                      to a constant value */
```

Ukazatel *x* lze upravit tak, aby odkazoval na jinou hodnotu typu **int** , ale hodnotu, na kterou odkazuje, nelze změnit.

```
const int some_object = 5 ;
int other_object = 37;
int *const y = &fixed_object;
int volatile *const z = &some_object;
int *const volatile w = &some_object;
```

Proměnná *y* v těchto deklaracích je deklarována jako konstantní ukazatel na hodnotu typu **int** . Hodnota, na kterou se odkazuje, se dá změnit, ale ukazatel sám musí ukazovat na stejné umístění: adresa *fixed_object*. Podobně, *z* je konstantní ukazatel, ale je také deklarován jako odkaz na typ **int** , jehož hodnotu nemůže program měnit. Další specifikátor **volatile** znamená, že i když hodnota **const int** , na kterou odkazuje objekt *z* , nemůže být programem upravována, může být oprávněně upravena procesem běžícím souběžně s programem. Deklarace *w* určuje, že program nemůže změnit hodnotu, na kterou se odkazuje, a který program nemůže změnit ukazatel.

```
struct list *next, *previous; /* Uses the tag for list */
```

Tento příklad deklaruje dvě proměnné ukazatele, *Další* a *předchozí*, které odkazují na *seznam*typu struktury. Tato deklarace se může objevit před definicí typu struktury *seznamu* (viz další příklad), pokud má definice typu *seznamu* stejnou viditelnost jako deklarace.

```
struct list
{
    char *token;
    int count;
    struct list *next;
} line;
```

Proměnná *line* má typ struktura s názvem *seznam*. Typ struktury *seznamu* má tři členy: první člen je ukazatel na hodnotu typu **char** , druhým je hodnota typu **int** a třetí je ukazatel na jinou strukturu *seznamu* .

```
struct id
{
    unsigned int id_no;
    struct name *pname;
} record;
```

*Záznam* proměnné má *ID*typu struktury. Všimněte si, že *pName* je deklarován jako ukazatel na jiný typ struktury s názvem *Name*. Tato deklarace se může vyskytovat před definováním typu *názvu* .

## <a name="see-also"></a>Viz také

[Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)
