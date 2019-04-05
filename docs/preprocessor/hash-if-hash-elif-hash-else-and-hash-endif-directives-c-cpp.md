---
title: '#IF, #elif, #else a #endif – direktivy (C/C++)'
ms.date: 11/04/2016
f1_keywords:
- '#else'
- '#endif'
- '#if'
- '#elif'
- defined
- __has_include
helpviewer_keywords:
- '#elif directive'
- conditional compilation, directives
- endif directive (#endif)
- preprocessor, directives
- '#else directive'
- '#endif directive'
- if directive (#if)
- else directive (#else)
- '#if directive'
- elif directive (#elif)
- defined directive
ms.assetid: c77a175f-6ca8-47d4-8df9-7bac5943d01b
ms.openlocfilehash: 90fbab45c6408c30198c2a52a42545718002cc11
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028088"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>Direktivy #if, #elif, #else a #endif (C/C++)

**#If** direktiv s **#elif**, **#else**, a **#endif** direktivy, řídí sestavování částí zdrojového souboru. Pokud výraz, který píšete (po **#if**) má nenulovou hodnotu, skupina řádku bezprostředně po **#if** – direktiva se uchovávají v jednotce překladu.

## <a name="grammar"></a>Gramatika

*Podmíněné* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*část IF části elif*<sub>optimalizované</sub> *část else*<sub>optimalizované</sub> *řádek endif*

*if-part* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*text řádku IF*

*řádek IF* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#if***konstantního výrazu.*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef***identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef***identifikátor*

*části elif* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*text řádku elif*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*části elif text řádku elif*

*řádek elif* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#elif***konstantního výrazu.*

*části else* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*text řádku else*

*řádek else* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*řádek endif* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

Každý **#if** směrnice ve zdrojovém souboru musí mít odpovídající uzavírací **#endif** směrnice. Libovolný počet **#elif** direktivy mohou objevit mezi **#if** a **#endif** direktivy, ale jedna **#else** – direktiva je povolen. **#Else** direktiva, pokud jsou k dispozici, musí být poslední direktivou před parametrem **#endif**.

**#If**, **#elif**, **#else**, a **#endif** direktiv lze vnořit do jiné části textu jiné **#if**direktivy. Každá vnořená **#else**, **#elif**, nebo **#endif** směrnice patří k nejbližší předchozí **#if** směrnice.

Všechny direktivy podmíněné kompilace, jako například **#if** a **#ifdef**, musí mít odpovídající uzavírací **#endif** direktivy před koncem souboru; jinak chyba zpráva je vygenerována. Když direktivy podmíněné kompilace jsou obsaženy v vkládané soubory, musí splňovat stejné podmínky: Musí existovat žádné neporovnané direktivy podmíněné kompilace na konci souboru začlenění.

Náhrada makra se provádí v rámci části příkazového řádku, který následuje **#elif** , takže volání makra lze použít v příkazu *konstantní výraz*.

Preprocesor vybere jeden z daných výskytů *text* k dalšímu zpracování. Blok zadaný v *text* může být libovolná sekvence textu. Může zabírat více než jeden řádek. Obvykle *text* je text programu, který má význam pro kompilátor nebo preprocesor.

Preprocesor zpracuje vybraný *text* a předá ho kompilátoru. Pokud *text* obsahuje direktivy preprocesoru, preprocesor provádí uvedené směrnice. Kompilovány jsou pouze textové bloky vybrané preprocesorem.

Preprocesor vybere jednu *text* položky vyhodnocením konstantního výrazu po každé **#if** nebo **#elif** směrnice, dokud nenajde true (nenulový) – Konstanta výraz. Vybere celý text (včetně ostatních pokynů preprocesoru počínaje **#**) až po přidružený **#elif**, **#else**, nebo **#endif** .

Pokud všechny výskyty *konstantní výraz* jsou false, nebo pokud žádná **#elif** direktivy nezobrazí, preprocesor vybere textový blok po **#else** klauzuli. Pokud **#else** klauzule je vynechána a všechny instance *konstantní výraz* v **#if** bloku jsou false, je vybrán žádný textový blok.

*Konstantního výrazu* je konstantní výraz celého čísla s těmito dalšími omezeními:

- Výrazy musí být integrálního typu a může obsahovat pouze celočíselné konstanty, znakové konstanty a **definované** operátor.

- Výraz nemůže používat `sizeof` nebo operátor přetypování.

- Cílové prostředí nemusí být schopno představovat všechny rozsahy celých čísel.

- Překlad představuje typ **int** stejný jako typ **dlouhé**, a **unsigned int** stejný jako **unsigned long**.

- Překladač může přeložit konstanty znaků do sady hodnot kódů odlišných od sady pro cílové prostředí. Pokud chcete určit vlastnosti cílového prostředí, zkontrolujte hodnoty maker z omezení. H v aplikaci sestavené pro cílové prostředí.

- Výraz nesmí vydávat žádné dotazy na prostředí a musí zůstat izolovaný od podrobností implementace v cílovém počítači.

## <a name="defined"></a>definováno

Operátor preprocesoru **definované** lze použít ve speciálních výrazech konstant, jak je znázorněno v následující syntaxi:

definovaný ( `identifier` )

definováno `identifier`

Tento konstantní výraz je považován za hodnotu true (nenulový), pokud *identifikátor* je aktuálně definován; v opačném případě je podmínka NEPRAVDA (0). Identifikátor definovaný jako prázdný text je považován za definovaný. **Definované** – direktiva je možné v **#if** a **#elif** směrnice, ale nikde jinde.

V následujícím příkladu **#if** a **#endif** určují direktivy kompilace jednoho ze třech volání funkce:

```C
#if defined(CREDIT)
    credit();
#elif defined(DEBIT)
    debit();
#else
    printerror();
#endif
```

Volání funkce `credit` se zkompiluje, pokud identifikátor `CREDIT` je definována. Pokud identifikátor `DEBIT` je definován, volání funkce `debit` je zkompilován. Pokud není definován žádný identifikátor, volání `printerror` je zkompilován. Všimněte si, že `CREDIT` a `credit` jsou odlišné identifikátory v jazyce C a C++, protože jejich případy se různí.

Příkazy podmíněné kompilace v následujícím příkladu předpokládejme dříve definovaná Symbolická konstanta s názvem `DLEVEL`.

```C
#if DLEVEL > 5
    #define SIGNAL  1
    #if STACKUSE == 1
        #define STACK   200
    #else
        #define STACK   100
    #endif
#else
    #define SIGNAL  0
    #if STACKUSE == 1
        #define STACK   100
    #else
        #define STACK   50
    #endif
#endif
#if DLEVEL == 0
    #define STACK 0
#elif DLEVEL == 1
    #define STACK 100
#elif DLEVEL > 5
    display( debugptr );
#else
    #define STACK 200
#endif
```

První **#if** bloku zobrazí dvě sady vnořených **#if**, **#else**, a **#endif** direktivy. První sada směrnic je zpracována pouze v případě `DLEVEL > 5` má hodnotu true. V opačném případě příkazy po **#else** se zpracovávají.

**#Elif** a **#else** direktivy v druhém příkladu se používají k výběru jedné ze čtyř možností na základě hodnoty z `DLEVEL`. Konstanta `STACK` je nastavena na hodnotu 0, 100 nebo 200 v závislosti na definici `DLEVEL`. Pokud `DLEVEL` je větší než 5, pak příkaz

```C
#elif DLEVEL > 5
display(debugptr);
```

je zkompilován a `STACK` není definován.

Běžným účelem pro podmíněné kompilace je zabránit vícenásobnému zahrnutí stejného souboru hlavičky. V jazyce C++, kde jsou třídy často definovány v souborech hlaviček, je možné k zabránění více definicím konstrukce, jako následující:

```cpp
/*  EXAMPLE.H - Example header file  */
#if !defined( EXAMPLE_H )
#define EXAMPLE_H

class Example
{
...
};

#endif // !defined( EXAMPLE_H )
```

Předchozí kód zkontroluje, zda Symbolická konstanta `EXAMPLE_H` je definována. Pokud ano, soubor již byl součástí a nemusí být přepracován. Pokud ne, konstanta `EXAMPLE_H` je definována k označení příklad. H jako již zpracovaného.

## <a name="hasinclude"></a>__has_include

**Visual Studio 2017 verze 15.3 nebo novější**:  Určuje, zda je k dispozici pro zahrnutí hlavičku knihovny:

```cpp
#ifdef __has_include
#  if __has_include(<filesystem>)
#    include <filesystem>
#    define have_filesystem 1
#  elif __has_include(<experimental/filesystem>)
#    include <experimental/filesystem>
#    define have_filesystem 1
#    define experimental_filesystem
#  else
#    define have_filesystem 0
#  endif
#endif
```

## <a name="see-also"></a>Viz také:

[Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)