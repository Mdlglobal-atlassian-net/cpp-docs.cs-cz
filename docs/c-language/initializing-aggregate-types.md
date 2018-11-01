---
title: Inicializace typů agregace
ms.date: 11/04/2016
helpviewer_keywords:
- aggregate types [C++]
- union keyword [C], declarations
- types [C], initializing
- union keyword [C]
- aggregates [C++], initializing
ms.assetid: a8f8ed75-39db-4592-93b9-d3920d915810
ms.openlocfilehash: ebc7f6185c8115df6e6b77a034307f8998b1c2ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530299"
---
# <a name="initializing-aggregate-types"></a>Inicializace typů agregace

*Agregační* je typ struktury, sjednocení nebo typ pole. Pokud agregační typ obsahuje členy agregačních typů, inicializace pravidla se vztahují rekurzivně.

## <a name="syntax"></a>Syntaxe

*Inicializátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{***seznam inicializátorů***}** / * pro inicializace agregace \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{***seznam inicializátorů***,}**

*seznam inicializátorů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Inicializátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam inicializátorů***,***inicializátor*

*Seznam inicializátorů* je seznam inicializátorů oddělený čárkami. Každý inicializátor v seznamu je konstantní výraz nebo seznamem inicializátorů. Proto mohou být vnořené seznamy inicializátorů. Tento formulář je užitečné pro inicializace agregace členů agregační typ, jak ukazují příklady v této části. Ale pokud inicializátor pro automatickému identifikátoru je jediný výraz, se nemusí být konstantní výraz; pouze musí mít příslušného typu pro přiřazení k identifikátoru.

Pro každý seznam inicializátorů hodnoty konstantní výrazy jsou přiřazeny, v pořadí, odpovídající členů agregační proměnné.

Pokud *seznam inicializátorů* má menší počet hodnot, než požadovaný typ agregace, zbývající členy nebo prvky požadovaný typ agregace jsou inicializovány na hodnotu 0. Počáteční hodnota automatickému identifikátoru nebyly explicitně inicializovány není definována. Pokud *seznam inicializátorů* má více hodnot než agregační typ, dojde k chybě. Tato pravidla vztahují každý inicializátor vložený seznam, stejně jako agregace jako celek.

Inicializátor struktura je výraz stejného typu nebo seznam inicializátorů jeho členů uzavřený do složených závorek (**{}**). Nepojmenované členy bitových polí nejsou inicializovány.

Při inicializaci sjednocení *seznam inicializátorů* musí být jediný konstantní výraz. Hodnota konstantní výraz je přiřazena první člen sjednocení.

Pokud pole má neznámou velikost, počet inicializátory Určuje velikost pole a jeho typ je dokončen. Neexistuje žádný způsob k určení opakování inicializátor v jazyce C nebo inicializace element uprostřed pole bez zadání také všechny předchozí hodnoty. Pokud potřebujete tuto operaci ve svém programu, psát v jazyce sestavení rutiny.

Všimněte si, že počet inicializátory můžete nastavit velikost pole:

```C
int x[ ] = { 0, 1, 2 }
```

Pokud zadáte velikost a poskytnout chybný počet inicializátory, však kompilátor vygeneruje chybu.

**Specifické pro Microsoft**

Maximální velikost pole je definované **size_t**. Definovaný v souboru hlaviček STDDEF. H, **size_t** je `unsigned int` s rozsahem 0x00000000 k 0x7CFFFFFF.

**Specifické pro END Microsoft**

## <a name="examples"></a>Příklady

Tento příklad ukazuje Incializátory pole.

```C
int P[4][3] =
{
    { 1, 1, 1 },
    { 2, 2, 2 },
    { 3, 3, 3,},
    { 4, 4, 4,},
};
```

Tento příkaz deklaruje `P` jako čtyři tři pole a inicializuje prvky jeho prvního řádku na 1, prvky jeho druhého řádku na 2, a tak dále až čtvrtý řádek. Všimněte si, že v seznamu inicializátorů třetí a čtvrtý řádek obsahuje čárkami po poslední konstantní výraz. Poslední seznam inicializátorů (`{4, 4, 4,},`) také následuje čárka. Tyto dodatečné čárky jsou povolené, ale nejsou vyžadovány; pouze čárkami, které oddělují konstantní výrazy z mezi sebou a ty, které oddělují jeden seznam inicializátorů z jiného, jsou potřeba.

Pokud agregační člen nemá žádný vložený inicializátor seznamu, hodnoty jsou pouze přiřazeny, v pořadí, pro každého člena subaggregate. Inicializace v předchozím příkladu je tedy ekvivalentní následujícímu zápisu:

```C
int P[4][3] =
{
   1, 1, 1, 2, 2, 2, 3, 3, 3, 4, 4, 4
};
```

Složené závorky se může zobrazit i po jednotlivých inicializátory v seznamu a by pomohou vyjasnit výše uvedený příklad.

Když inicializujete proměnnou agregace, musíte použít složené závorky a seznamy inicializátorů správně. Následující příklad ukazuje kompilátoru interpretaci složených závorek podrobněji:

```C
typedef struct
{
    int n1, n2, n3;
} triplet;

triplet nlist[2][3] =
{
    { {  1, 2, 3 }, {  4, 5, 6 }, {  7, 8, 9 } },  /* Row 1 */
    { { 10,11,12 }, { 13,14,15 }, { 16,17,18 } }   /* Row 2 */
};
```

V tomto příkladu `nlist` je deklarován jako 2 3 pole struktur, každá struktura s tři členy. Řádek 1 inicializace přiřadí první řádek hodnot `nlist`, následujícím způsobem:

1. První levou složenou závorku na řádek 1 signalizuje kompilátoru, že inicializace prvního člena agregační `nlist` (to znamená `nlist[0]`) je začátek.

1. Druhý levou složenou závorku označuje, že inicializace prvního člena agregační `nlist[0]` (to znamená, že struktura v `nlist[0][0]`) je začátek.

1. Inicializace struktury končí první pravou složenou závorku `nlist[0][0]`; další levou složenou závorku spuštění inicializace `nlist[0][1]`.

1. Proces bude pokračovat až do konce řádku, kde končí pravou složenou závorku správné inicializace `nlist[0]`.

Řádek 2 přiřadí hodnoty do druhého řádku `nlist` podobným způsobem. Všimněte si, že se vyžadují vnější sady složené závorky uzavírající inicializátory řádky 1 a 2. Následující konstrukce, která vynechává vnější závorky, způsobí chybu:

```C
triplet nlist[2][3] =  /* THIS CAUSES AN ERROR */
{
     {  1, 2, 3 },{  4, 5, 6 },{  7, 8, 9 },   /* Line 1 */
     { 10,11,12 },{ 13,14,15 },{ 16,17,18 }    /* Line 2 */
};
```

V této konstrukce spustí první levou složenou závorku na řádek 1 inicializace `nlist[0]`, což je pole tři konstrukcí. Hodnoty 1, 2 a 3 jsou přiřazeny k tři členy struktury první. Pokud je další pravou složenou závorku (po hodnotu 3) došlo k chybě inicializace `nlist[0]` se dokončí, a dvě zbývající struktury struktura tři pole jsou automaticky inicializovány na hodnotu 0. Obdobně `{ 4,5,6 }` inicializuje první struktury, ve druhém řádku `nlist`. Zbývající dvě struktury `nlist[1]` jsou nastaveny na hodnotu 0. Když kompilátor narazí na další seznam inicializátorů ( `{ 7,8,9 }` ), pokusí se inicializovat `nlist[2]`. Protože `nlist` má pouze dva řádky, tento pokus způsobí chybu.

V tomto dalším příkladu tři `int` členy `x` jsou inicializovány na hodnotu 1, 2 a 3, v uvedeném pořadí.

```C
struct list
{
    int i, j, k;
    float m[2][3];
} x = {
        1,
        2,
        3,
       {4.0, 4.0, 4.0}
      };
```

V `list` strukturu výše, tři prvky v prvním řádku `m` jsou inicializovány na hodnotu 4.0; prvky řádku zbývající `m` jsou ve výchozím nastavení inicializována na hodnotu 0,0.

```C
union
{
    char x[2][3];
    int i, j, k;
} y = { {
            {'1'},
            {'4'}
        }
      };
```

Proměnné sjednocení `y`, v tomto příkladu je inicializován. První prvek sjednocení je pole, takže inicializátoru je souhrnných inicializátorů. Seznam inicializátorů `{'1'}` přiřadí hodnoty na první řádek pole. Vzhledem k tomu, že v seznamu se zobrazí pouze jedna hodnota, elementu v prvním sloupci je inicializován na znak `1`, a zbývající dva prvky v řádku jsou ve výchozím nastavení inicializována na hodnotu 0. Podobně, první prvek druhého řádku `x` je inicializován na znak `4`, a zbývající dva prvky v řádku jsou inicializovány na hodnotu 0.

## <a name="see-also"></a>Viz také

[Inicializace](../c-language/initialization.md)