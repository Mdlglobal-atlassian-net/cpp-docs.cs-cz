---
title: Deklarace struktury
ms.date: 11/04/2016
helpviewer_keywords:
- structure declarations
- anonymous structures
- types [C], declarations
- structure members
- embedded structures
ms.assetid: 5be3be77-a236-4153-b574-7aa77675df7f
ms.openlocfilehash: a17bb996f13fdbe11bb569c8af5669a9d0c5363f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157792"
---
# <a name="structure-declarations"></a>Deklarace struktury

"Deklarace struktury" pojmenovává typ a určuje sekvenci hodnot proměnných (nazývaných "členy" nebo "pole" struktury), které mohou mít různé typy. Volitelný identifikátor, nazývaný "tag", dává název typu struktury a lze jej použít v následných odkazech na typ struktury. Proměnná typu struktury uchovává celou sekvenci definovanou tímto typem. Struktury v jazyce C jsou podobné typům, které jsou označovány jako "záznamy" v jiných jazycích.

## <a name="syntax"></a>Syntaxe

*specifikátor struct nebo Union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor ID* *struktury nebo sjednocení* –<sub>opt</sub> **{** *struct-Declaration-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor* *struktury nebo sjednocení*

*Struktura nebo sjednocení*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nemají**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sjednocovací**

*Struktura-deklarace-seznamu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct – deklarace*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura-deklarace-seznamu* *Struktura-deklarace*

*deklarace struktury*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor-kvalifikátor-list* *struct-deklarátor-list* **;**

*specifikátor – kvalifikátor – seznam*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;specifikátor *specifikátoru typu* *– kvalifikátor – seznam*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;specifikátor *kvalifikátoru typu* – *Kvalifikátor seznamu – kvalifikátor*<sub>opt</sub>

*Struktura – deklarátor-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura-deklarátor* *Struktura-deklarátor-list* **,** *struct-deklarátor*

*Struktura – deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typ – specifikátor* *deklarátor*<sub>opt</sub> **:** *konstantní výraz*

Deklarace typu struktury nenastavuje volné místo pro strukturu. Je pouze šablonou pro pozdější deklarace proměnných struktury.

Dříve definovaný *identifikátor* (tag) lze použít pro odkazování na typ struktury definovaný jinde. V takovém případě nelze *seznam struktur-Declaration-list* opakovat, dokud je definice viditelná. Deklarace ukazatelů na struktury a definice TypeDef pro typy struktur mohou používat značku struktury před definováním typu struktury. Nicméně definice struktury musí být zjištěna před jakýmkoli skutečným použitím velikosti polí. Toto je neúplná definice typu a značka typu. Aby byla tato definice dokončena, definice typu musí být uvedena později ve stejném oboru.

*Seznam struct-Declaration-list* určuje typy a názvy členů struktury. Argument *struct-Declaration-list* obsahuje jednu nebo více deklarací proměnných nebo bitového pole.

Každá Proměnná deklarovaná v *seznamu struct-Declaration-list* je definována jako člen typu struktury. Deklarace proměnných v *seznamu struct-Declaration-list* mají stejný tvar jako ostatní deklarace proměnných popsané v této části s tím rozdílem, že deklarace nemůžou obsahovat specifikátory nebo Inicializátory třídy úložiště. Členové struktury mohou mít libovolné typy proměnných kromě typu `void`, nekompletního typu nebo typu funkce.

Člen nelze deklarovat, aby měl typ struktury, ve které se vyskytuje. Člena lze však deklarovat jako ukazatel na typ struktury, ve kterém se zobrazí, pokud typ struktury má značku. To umožňuje vytvářet propojené seznamy struktur.

Struktury se řídí stejným rozsahem jako jiné identifikátory. Identifikátory struktury musí být odlišné od jiných značek struktury, sjednocení a výčtu se stejnou viditelností.

Každá *deklarace struktury* v *seznamu struct-Declaration-list* musí být v rámci seznamu jedinečná. Názvy identifikátorů v *seznamu struct-Declaration-list* ale nemusí být odlišné od běžných názvů proměnných nebo z identifikátorů v jiných seznamech deklarací struktury.

K vnořeným strukturám lze také přicházet, jako kdyby byly deklarovány na úrovni souboru. Například s ohledem na tuto deklaraci:

```C
struct a
{
    int x;
    struct b
    {
      int y;
    } var2;
} var1;
```

Tato deklarace jsou obě platná:

```C
struct a var3;
struct b var4;
```

## <a name="examples"></a>Příklady

Tyto příklady ilustrují deklarace struktury:

```C
struct employee   /* Defines a structure variable named temp */
{
    char name[20];
    int id;
    long class;
} temp;
```

`employee` Struktura má tři členy: `name`, `id`a `class`. `name` Členem je pole 20 prvků `id` a a `class` jsou jednoduché členy s `int` a **dlouhým** typem v uvedeném pořadí. Identifikátor `employee` je identifikátor struktury.

```C
struct employee student, faculty, staff;
```

Tento příklad definuje tři proměnné struktury: `student`, `faculty`a `staff`. Každá struktura má stejný seznam tří členů. Členové jsou deklarováni tak, aby měly typ `employee`struktury definovaný v předchozím příkladu.

```C
struct           /* Defines an anonymous struct and a */
{                /* structure variable named complex  */
    float x, y;
} complex;
```

`complex` Struktura má dva členy s typem **float** `x` a `y`. Typ struktury nemá žádnou značku a je proto nepojmenovaný nebo anonymní.

```C
struct sample   /* Defines a structure named x */
{
    char c;
    float *pf;
    struct sample *next;
} x;
```

Prvních dvou členů struktury je `char` proměnná a ukazatel na hodnotu **typu float** . Třetí člen, `next`, je deklarován jako ukazatel na definovaný typ struktury (`sample`).

Anonymní struktury mohou být užitečné, pokud není potřeba značka s názvem. Jedná se o případ, kdy jedna deklarace definuje všechny instance struktury. Příklad:

```C
struct
{
    int x;
    int y;
} mystruct;
```

Vložené struktury jsou často anonymní.

```C
struct somestruct
{
    struct    /* Anonymous structure */
    {
        int x, y;
    } point;
    int type;
} w;
```

**Specifické pro Microsoft**

Kompilátor umožňuje jako poslední člen struktury pole s nezvětšenou velikostí nebo nulovou velikostí. To může být užitečné, pokud se velikost konstantního pole liší při použití v různých situacích. Deklarace takové struktury vypadá takto:

**struct** *identifikátor* struktury **{** *Set-of-deklarace* – *typ* <em>pole-název</em>**\[];};**

Pole s nezměněnou velikostí se můžou vyskytovat jenom jako poslední člen struktury. Struktury obsahující deklarace pole s neurčenou velikostí mohou být vnořeny do jiných struktur, pokud nejsou deklarovány další členy v žádné ohraničující struktuře. Pole těchto struktur nejsou povolena. `sizeof` Operátor, při použití na proměnnou tohoto typu nebo na samotný typ, předpokládá 0 pro velikost pole.

Deklarace struktury lze také zadat bez deklarátor, pokud jsou členy jiné struktury nebo sjednocení. Názvy polí jsou povýšeny do ohraničující struktury. Například struktura Nameless vypadá takto:

```C
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

Informace o odkazech na strukturu najdete v tématu [Struktura a členové sjednocení](../c-language/structure-and-union-members.md) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)
