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

"Struktury deklarace" název typu a určuje pořadí hodnot proměnných (označované jako "členy" nebo "pole" struktury), které mohou mít různé typy. Volitelný identifikátor, s názvem "značku", obsahuje název typu struktury a lze použít v následných odkazů na typ struktury. Proměnná tohoto typu struktury obsahuje celé sekvenci definovaný podle tohoto typu. Struktury v jazyce C jsou podobné typy, které jsou známé jako "záznamů" v jiných jazycích.

## <a name="syntax"></a>Syntaxe

*struct-or-union-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura nebo sjednocení* *identifikátor*<sub>optimalizované</sub> **{** *struct-declaration-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura nebo sjednocení* *identifikátor*

*struct-or-union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**– Struktura**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sjednocení**

*struct-declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace struktury*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration-list* *struct-declaration*

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor qualifier-list* *struct-declarator-list* **;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specifikátor typu* *specifikátor seznam kvalifikátorů-*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kvalifikátor typu* *specifikátor seznam kvalifikátorů-*<sub>optimalizované</sub>

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura declarator* *struct-declarator-list* **,** *deklarátor – struktura*

*struct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specifikátor typu* *deklarátor*<sub>optimalizované</sub> **:** *konstantního výrazu.*

Deklaraci typu struktury nenastaví vyhrazené místo pro strukturu. Je jenom šablony pro pozdější deklaraci proměnné struktury.

Dříve definovaná *identifikátor* (značky) slouží k odkazování na typ struktury definované jinde. V takovém případě *struct-declaration-list* nelze opakovat za předpokladu, definice není viditelný. Deklarace ukazatelů na struktury a definice TypeDef pro typy struktur lze použít značku struktury předtím, než je typ struktury definován. Definice struktury musí však došlo k před veškeré jeho používání skutečná velikost polí. Toto je neúplná definice pro typ a typ značky. Pro tuto definici k dokončení definice typu musí být uvedena dále ve stejném oboru.

*Struct-declaration-list* Určuje typy a názvy členů struktury. A *struct-declaration-list* argument obsahuje jednu nebo více proměnné nebo deklarace bitového pole.

Každá proměnná deklarovaná ve *struct-declaration-list* je definován jako člen typu Struktura. Deklarace proměnných v rámci *struct-declaration-list* mají stejné formuláře jako další deklarace proměnných popsaných v této části s tím rozdílem, že deklarace nemůže obsahovat specifikátory třídy úložiště nebo inicializátory. Členy struktury mohou mít všechny tyto typy proměnných s výjimkou typu `void`, neúplný typ nebo typ funkce.

Člen nejde použít deklaraci typu struktury, ve kterém se zobrazí. Člena ale mohou být deklarovány jako ukazatel na typ struktury, ve kterém se zobrazí, dokud typ struktury je značka. To umožňuje vytvářet propojené seznamy struktur.

Struktury, postupujte podle stejného rozsahu jako další identifikátory. Struktura identifikátory musí být odlišný od jiných struktury, sjednocení a výčtu značky se stejnou viditelností.

Každý *struct-declaration* v *struct-declaration-list* musí být jedinečný v rámci seznamu. Nicméně názvy identifikátor v *struct-declaration-list* nemusí být odlišný od běžné názvy proměnných nebo identifikátory v seznamech deklaraci struktury.

Vnořené struktury lze rovněž přistupovat, jako kdyby byly deklarovány na úrovni rozsahu souboru. Mějme například tuto deklaraci:

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

Tyto deklarace jsou platné:

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

`employee` Struktura obsahuje tři členy: `name`, `id`, a `class`. `name` Člen je pole 20 prvcích a `id` a `class` jsou jednoduché členy s `int` a **dlouhé** zadejte v uvedeném pořadí. Identifikátor `employee` je identifikátor struktury.

```C
struct employee student, faculty, staff;
```

Tento příklad definuje tři proměnné struktury: `student`, `faculty`, a `staff`. Každá struktura má stejný seznam tří členů. Členů jsou deklarovány mít typ struktury `employee`definovaná v předchozím příkladu.

```C
struct           /* Defines an anonymous struct and a */
{                /* structure variable named complex  */
    float x, y;
} complex;
```

`complex` Struktura obsahuje dva členy s **float** typ `x` a `y`. Typ struktury nemá žádnou značku a proto je nepojmenovaný nebo anonymní.

```C
struct sample   /* Defines a structure named x */
{
    char c;
    float *pf;
    struct sample *next;
} x;
```

První dva členy struktury jsou `char` proměnné a ukazatel **float** hodnotu. Třetí členské `next`, je deklarována jako ukazatel na typ struktury definované (`sample`).

Anonymní struktury může být užitečné, když není potřeba značku s názvem. To je případ, kdy jedna deklarace definuje všechny instance struktury. Příklad:

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

**Microsoft Specific**

Kompilátor umožňuje jako poslední člen struktury pole bez velikosti nebo s nulovou velikostí. To může být užitečné, pokud se velikost pole s konstantní liší při použití v různých situacích. Deklarace takové struktury vypadá takto:

**Struktura** *identifikátor* **{** *sada deklarací* *typ* <em>název pole</em> **\[]; };**

Poli netříděnými podle velikosti se může zobrazit pouze jako poslední člen struktury. Struktury obsahující pole nesetříděné podle velikosti deklarace mohou být vnořené v jiných strukturách, za předpokladu, žádní další členové jsou deklarovány v libovolné nadřazené struktury. Pole těchto struktur nejsou povoleny. `sizeof` Při použití proměnné tohoto typu nebo typ, samotný operátoru předpokládá 0 pro velikost pole.

Deklarace struktury lze také zadat bez deklarátorem nejsou členy jiné struktury nebo sjednocení. Názvy polí jsou povýšeny do nadřazené struktury. Nepojmenované struktury bude vypadat takto:

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

Zobrazit [členy struktury a sjednocení](../c-language/structure-and-union-members.md) informace o odkazech na strukturu.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)
