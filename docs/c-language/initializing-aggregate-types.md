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
ms.openlocfilehash: f6816a6f63de262b927a3c5aeed8774ba29c2eaa
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2019
ms.locfileid: "62326076"
---
# <a name="initializing-aggregate-types"></a>Inicializace typů agregace

*Agregovaný* typ je struktura, sjednocení nebo typ pole. Pokud agregovaný typ obsahuje členy agregačních typů, pravidla inicializace se použijí rekurzivně.

## <a name="syntax"></a>Syntaxe

*inicializátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{**  *inicializátor-list*  **}** /* pro inicializaci agregace\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{**  *inicializátor-list*  **,}**

*seznam inicializátorů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inicializátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inicializátor – seznam*  **,**  *inicializátor*

*Seznam inicializátorů* je seznam inicializátorů oddělených čárkami. Každý inicializátor v seznamu je buď konstantní výraz, nebo seznam inicializátorů. Proto se seznamy inicializátorů můžou vnořovat. Tento formulář je vhodný pro inicializaci agregačních členů agregačního typu, jak je znázorněno v příkladech v této části. Pokud je však inicializátor pro automatický identifikátor jedním výrazem, nemusí být konstantní výraz; pouze musí mít odpovídající typ pro přiřazení k identifikátoru.

Pro každý seznam inicializátorů jsou hodnoty konstantních výrazů přiřazeny v pořadí podle odpovídajících členů agregační proměnné.

Pokud má *seznam inicializátorů* méně hodnot než agregovaný typ, zbývající členy nebo prvky agregačního typu jsou inicializovány na hodnotu 0. Počáteční hodnota automatického identifikátoru, který není explicitně inicializován, není definována. Pokud má *seznam inicializátorů* více hodnot než agregovaný typ, dojde k chybě. Tato pravidla platí pro každý vložený seznam inicializátorů a také pro agregaci jako celek.

Inicializátor struktury je buď výraz stejného typu, nebo seznam inicializátorů pro jeho členy uzavřený ve složených závorkách (**{}**). Nepojmenované členy bitových polí nejsou inicializovány.

Při inicializaci sjednocení musí být *seznam inicializátorů* jeden konstantní výraz. Hodnota konstantního výrazu je přiřazena prvnímu členu sjednocení.

Pokud má pole neznámou velikost, počet inicializátorů určuje velikost pole a jeho typ se změní na úplný. Neexistuje žádný způsob, jak určit opakování inicializátoru v C, nebo inicializovat element uprostřed pole bez zadání všech předcházejících hodnot. Pokud tuto operaci v programu potřebujete, zapište rutinu v jazyce sestavení.

Všimněte si, že počet inicializátorů může nastavit velikost pole:

```C
int x[ ] = { 0, 1, 2 }
```

Pokud však zadáte velikost a uvedete špatný počet inicializátorů, kompilátor vygeneruje chybu.

**Specifické pro Microsoft**

Maximální velikost pole je definována **size_t**. Definováno v hlavičkovém souboru STDDEF. H je **size_t** `unsigned int` s rozsahem 0x00000000 až 0x7CFFFFFF.

**Specifické pro konec Microsoftu**

## <a name="examples"></a>Příklady

Tento příklad ukazuje inicializátory pro pole.

```C
int P[4][3] =
{
    { 1, 1, 1 },
    { 2, 2, 2 },
    { 3, 3, 3,},
    { 4, 4, 4,},
};
```

Tento příkaz deklaruje `P` jako čtyřnásobné pole a inicializuje prvky jeho prvního řádku na hodnotu 1, prvky jeho druhého řádku na 2 atd. a to prostřednictvím čtvrtého řádku. Všimněte si, že seznam inicializátorů třetího a čtvrtého řádku obsahuje čárky za poslední konstantní výraz. Poslední seznam inicializátorů ( `{4, 4, 4,},` ) je také následován čárkou. Tyto nadbytečné čárky jsou povoleny, ale nejsou požadovány. jsou vyžadovány pouze čárky, které oddělují konstantní výrazy od sebe a ty, které oddělují jeden seznam inicializátorů z jiného.

Pokud agregační člen nemá žádný vložený seznam inicializátorů, hodnoty jsou jednoduše přiřazeny v daném pořadí pro každého člena agregace. Proto je inicializace v předchozím příkladu ekvivalentní následujícímu:

```C
int P[4][3] =
{
   1, 1, 1, 2, 2, 2, 3, 3, 3, 4, 4, 4
};
```

Složené závorky se také mohou vyskytovat kolem jednotlivých inicializátorů v seznamu a pomohou vám vysvětlit výše uvedený příklad.

Při inicializaci agregované proměnné musíte být opatrní a správně používat závorky a seznamy inicializátorů. Následující příklad ukazuje interpretaci složených závorek kompilátoru podrobněji:

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

V tomto příkladu `nlist` je deklarován jako 2 – 3 pole struktur, přičemž každá struktura má tři členy. Řádek 1 inicializace přiřadí hodnoty do prvního řádku `nlist` , jak je znázorněno níže:

1. První levá složená závorka na řádku 1 signalizuje kompilátoru, že je zahájena inicializace prvního agregačního členu `nlist` (to znamená, `nlist[0]` ).

1. Druhá levá složená závorka indikuje, že se začíná inicializovat první agregovaný člen `nlist[0]` (tj. struktura at `nlist[0][0]` ).

1. První pravá složená závorka končí inicializaci struktury `nlist[0][0]` ; následující levá složená závorka zahájí inicializaci `nlist[0][1]` .

1. Proces pokračuje až do konce řádku, kde pravá složená závorka končí inicializaci `nlist[0]` .

Řádek 2 přiřadí hodnoty k druhému řádku `nlist` podobným způsobem. Všimněte si, že jsou požadovány vnější sady složených závorek ohraničujících Inicializátory na řádcích 1 a 2. Následující konstrukce, která vynechává vnější složené závorky, by způsobila chybu:

```C
triplet nlist[2][3] =  /* THIS CAUSES AN ERROR */
{
     {  1, 2, 3 },{  4, 5, 6 },{  7, 8, 9 },   /* Line 1 */
     { 10,11,12 },{ 13,14,15 },{ 16,17,18 }    /* Line 2 */
};
```

V této konstrukci první levá složená závorka na řádku 1 spouští inicializaci `nlist[0]` , což je pole tří struktur. Hodnoty 1, 2 a 3 jsou přiřazeny třem členům první struktury. Když se vyskytne další pravá složená závorka (po hodnotě 3), inicializace `nlist[0]` je dokončená a dvě zbývající struktury v poli se třemi strukturami se automaticky inicializují na 0. Podobně `{ 4,5,6 }` inicializuje první strukturu v druhém řádku `nlist` . Zbývající dvě struktury `nlist[1]` jsou nastaveny na hodnotu 0. Když kompilátor narazí na další seznam inicializátorů ( `{ 7,8,9 }` ), pokusí se inicializovat `nlist[2]` . Vzhledem `nlist` k tomu, že má pouze dva řádky, tento pokus způsobuje chybu.

V následujícím příkladu `int` jsou tři členy `x` inicializovány na 1, 2 a 3 v uvedeném pořadí.

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

Ve `list` struktuře výše jsou tři prvky v prvním řádku pro `m` inicializovány na 4,0; prvky zbývajícího řádku ve `m` výchozím nastavení jsou inicializovány na 0,0.

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

Proměnná Union `y` v tomto příkladu je inicializovaná. První prvek sjednocení je pole, takže inicializátor je agregovaný inicializátor. Seznam inicializátorů `{'1'}` přiřadí hodnoty do prvního řádku pole. Vzhledem k tomu, že se v seznamu zobrazí pouze jedna hodnota, je prvek v prvním sloupci inicializován na znak `1` a zbývající dva prvky v řádku jsou ve výchozím nastavení inicializovány na hodnotu 0. Podobně první prvek druhého řádku `x` je inicializován na znak `4` a zbývající dva prvky na řádku jsou inicializovány na hodnotu 0.

## <a name="see-also"></a>Viz také

[Inicializace](../c-language/initialization.md)
