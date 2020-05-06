---
title: Deklarace sjednocení
ms.date: 11/04/2016
helpviewer_keywords:
- unions
- union keyword [C], declarations
- variant records
ms.assetid: 978c6165-e0ae-4196-afa7-6d94e24f62f7
ms.openlocfilehash: dbc85a467161457641dd86acf5f3720bf4e14247
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291038"
---
# <a name="union-declarations"></a>Deklarace sjednocení

Deklarace Union určuje sadu hodnot proměnných a volitelně také značku pro pojmenování sjednocení. Proměnné hodnoty se nazývají "Členové" sjednocení a mohou mít různé typy. Sjednocení jsou podobná "variantům záznamů" v jiných jazycích.

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

Obsah sjednocení je definovaný jako

*deklarace struktury*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor-kvalifikátor-list* *struct-deklarátor-list*  **;**

*specifikátor – kvalifikátor – seznam*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;specifikátor *specifikátoru typu* *– kvalifikátor – seznam*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;specifikátor *kvalifikátoru typu* – *Kvalifikátor seznamu – kvalifikátor*<sub>opt</sub>

*Struktura – deklarátor-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struktura – deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura – deklarátor-list*  **,**  *struct – deklarátor*

Proměnná s typem **sjednocení** ukládá jednu z hodnot definovaných tímto typem. Stejná pravidla řídí deklarace struktury a sjednocení. Sjednocení mohou mít také bitová pole.

Členové sjednocení nemohou mít nekompletní typ, typ `void`ani typ funkce. Proto členové nemohou být instancí sjednocení, ale mohou být ukazateli deklarovaného typu sjednocení.

Deklarace typu sjednocení je pouze šablona. Paměť není vyhrazena, dokud není deklarována proměnná.

> [!NOTE]
> Pokud je deklarováno sjednocení dvou typů a je uložena jedna hodnota, ale sjednocení je dostupné s jiným typem, výsledky jsou nespolehlivé. Například sjednocení typu **float** a `int` je deklarováno. Hodnota **typu float** je uložena, ale program později k hodnotě přistupuje jako `int`. V takové situaci bude hodnota záviset na interním úložišti hodnot **float** . Celočíselná hodnota by nebyla spolehlivá.

## <a name="examples"></a>Příklady

Následují příklady sjednocení:

```C
union sign   /* A definition and a declaration */
{
    int svar;
    unsigned uvar;
} number;
```

Tento příklad definuje proměnnou sjednocení s `sign` typem a deklaruje proměnnou s názvem `number` , která má dva členy: `svar`, celé číslo se znaménkem `uvar`a unsigned integer. Tato deklarace umožňuje uložení aktuální hodnoty `number` buď jako znaménko, nebo jako hodnotu bez znaménka. Značka přidružená k tomuto typu sjednocení `sign`je.

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

`screen` Pole obsahuje 2 000 prvků. Každý prvek pole je individuální sjednocení se dvěma členy: `window1` a. `screenval` `window1` Člen je struktura se dvěma členy bitových polí `icon` a `color`. `screenval` Člen je `int`. V každém okamžiku obsahuje každý prvek sjednocení buď `int` reprezentované, `screenval` nebo strukturou reprezentovanou. `window1`

**Specifické pro Microsoft**

Vnořené sjednocení lze deklarovat anonymně, pokud jsou členy jiné struktury nebo sjednocení. Toto je příklad Nameless sjednocení:

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

Sjednocení jsou často vnořena do struktury, která obsahuje pole poskytující typ dat obsažených v sjednocení v určitou dobu. Toto je příklad deklarace pro toto sjednocení:

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

Informace o referenčních sjednoceních naleznete v tématu [Struktura a členové sjednocení](../c-language/structure-and-union-members.md) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Deklarátor a deklarace proměnné](../c-language/declarators-and-variable-declarations.md)
