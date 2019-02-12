---
title: Deklarace sjednocení
ms.date: 11/04/2016
helpviewer_keywords:
- unions
- union keyword [C], declarations
- variant records
ms.assetid: 978c6165-e0ae-4196-afa7-6d94e24f62f7
ms.openlocfilehash: dbc85a467161457641dd86acf5f3720bf4e14247
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149255"
---
# <a name="union-declarations"></a>Deklarace sjednocení

"Deklarace sjednocení" Určuje sadu hodnot proměnných a volitelně také názvy sjednocení značku. Hodnoty proměnné se nazývají "členy" unie a mohou mít různé typy. Sjednocení jsou podobná "variantní záznamy" v jiných jazycích.

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

Sjednocení obsah je definován jako

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor qualifier-list* *struct-declarator-list***;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specifikátor typu* *specifikátor seznam kvalifikátorů-*<sub>optimalizované</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kvalifikátor typu* *specifikátor seznam kvalifikátorů-*<sub>optimalizované</sub>

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura declarator-list***,***deklarátor – struktura*

Proměnná s **sjednocení** typ ukládá jedna z hodnot fronty definovaných podle tohoto typu. Deklarace struktury a sjednocení se řídí stejnými pravidly. Sjednocení může mít také bitová pole.

Členové sjednocení nemůže mít nekompletní typ, zadejte `void`, nebo typ funkce. Proto členů nemůže být instancí třídy sjednocení, ale může být ukazatele na typ sjednocení, které jsou deklarované.

Deklarace typu sjednocení je pouze šablony. Dokud je proměnná deklarována není vyhrazena paměť.

> [!NOTE]
> Pokud je deklarována jako spojení dva typy a jedna hodnota je uložena, ale sjednocení je přistupováno pomocí jiného typu, nespolehlivé výsledky. Například spojení **float** a `int` je deklarována. A **float** hodnota je uložena, ale program později přistupuje k hodnotě jako `int`. V takové situaci, hodnota bude trvat, závisí na vnitřní **float** hodnoty. Celočíselná hodnota nemusí být spolehlivé.

## <a name="examples"></a>Příklady

Následují příklady sjednocení:

```C
union sign   /* A definition and a declaration */
{
    int svar;
    unsigned uvar;
} number;
```

Tento příklad definuje proměnné sjednocení s `sign` zadejte a deklaruje proměnnou s názvem `number` , který má dva členy: `svar`, celé číslo se znaménkem, a `uvar`, celé číslo bez znaménka. Tato deklarace umožňuje aktuální hodnotu `number` ukládaly jako podepsaný nebo hodnoty bez znaménka. Příznak přidružený k tomuto typu sjednocení je `sign`.

```C
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

`screen` Pole obsahuje 2 000 prvků. Každý prvek pole se jednotlivé sjednocení se dvěma členy: `window1` a `screenval`. `window1` Členů je struktura se dvěma členy bitových polí `icon` a `color`. `screenval` Člen je `int`. V daném okamžiku každý sjednocení prvek udržuje `int` reprezentována `screenval` nebo struktura reprezentována `window1`.

**Microsoft Specific**

Vnořené sjednocení mohou být deklarovány anonymně, když jsou členy jiné struktury nebo sjednocení. Toto je příklad nameless sjednocení:

```C
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

Sjednocení jsou často vnořené struktury, která obsahuje pole poskytující typu dat obsažených v sjednocení v určitém čase. Toto je příklad deklarace pro taková sjednocení:

```C
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

Zobrazit [členy struktury a sjednocení](../c-language/structure-and-union-members.md) informace o odkazování na sjednocení.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)
