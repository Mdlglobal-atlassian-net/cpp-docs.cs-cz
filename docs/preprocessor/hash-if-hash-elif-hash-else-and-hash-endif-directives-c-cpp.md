---
title: '#if, #elif, #else a #endif – direktivy (C/C++)'
ms.date: 08/29/2019
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
ms.openlocfilehash: 2b7ed4733dcafda793b9a945c3f40739b52e040a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220350"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>direktivy #if, #elif, #else a #endif (C/C++)

Direktiva **#if** s direktivami **#elif**, **#else**a **#endif** řídí kompilaci částí zdrojového souboru. Pokud výraz, který zapisujete (po **#if**), má nenulovou hodnotu, skupina řádků bezprostředně následující po **#if** direktivě je udržována v jednotce překladu.

## <a name="grammar"></a>Gramatika

*podmíněné* : \
&nbsp;&nbsp;&nbsp;&nbsp;*elif část if-* Parts <sub>výslovný souhlas</sub> *Else – část* <sub>výslovný souhlas</sub> *endif-line*

*if-Part* : \
&nbsp;&nbsp;&nbsp;&nbsp;*text řádku*

*řádek if-line* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *konstantní výraz*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *identifikátor*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *identifikátor*

*elif – části* : \
&nbsp;&nbsp;&nbsp;&nbsp;*text řádku elif*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif části elif – text řádku*

*elif-line* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *konstantního výrazu.*

*Else – část* : \
&nbsp;&nbsp;&nbsp;&nbsp;*text v jiném řádku*

*Else-line* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif-line* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

## <a name="remarks"></a>Poznámky

Každá direktiva **#if** ve zdrojovém souboru musí odpovídat uzavírací direktivě **#endif** . Mezi direktivami **#if** a **#endif** se může vyskytovat libovolný počet direktiv **#elif** , ale je povolená nejvýše jedna direktiva **#else** . Direktiva **#else** , pokud je k dispozici, musí být poslední direktivou před **#endif**.

Direktivy **#if**, **#elif**, **#else**a **#endif** mohou vnořovat do *textových* částí jiných direktiv **#if** . Každá vnořená direktiva **#else**, **#elif**nebo **#endif** patří do nejbližší předchozí direktivy **#if** .

Všechny direktivy podmíněné kompilace, například **#if** a **#ifdef**, se musí shodovat s direktivou ukončení **#endif** před koncem souboru. V opačném případě se vygeneruje chybová zpráva. Pokud jsou direktivy podmíněné kompilace obsaženy v zahrnutých souborech, musí splňovat stejné podmínky: Na konci souboru include nesmí existovat žádné nespárované direktivy podmíněné kompilace.

Nahrazení makra je provedeno v rámci řádku, který následuje **#elif** příkaz, takže volání makra lze použít v *konstantním výrazu*.

Preprocesor vybere jeden z daných výskytů *textu* pro další zpracování. Blok zadaný v *textu* může být libovolná sekvence textu. Může zabírat více než jeden řádek. Obvykle *text* je text programu, který má význam pro kompilátor nebo preprocesor.

Preprocesor zpracuje vybraný *text* a předá ho kompilátoru. Pokud *text* obsahuje direktivy preprocesoru, preprocesor tyto směrnice provede. Kompilovány jsou pouze textové bloky vybrané preprocesorem.

Preprocesor vybere jednu položku *textu* vyhodnocením konstantního výrazu po každé **#if** nebo direktivě **#elif** , dokud nenajde konstantní (nenulový) konstantní výraz. Vybere celý text (včetně dalších direktiv **#** preprocesoru počínaje) až do jeho přidruženého **#elif**, **#else**nebo **#endif**.

Pokud jsou všechny výskyty *konstantního výrazu* false nebo pokud se nezobrazí žádné direktivy **#elif** , preprocesor vybere blok textu za klauzulí **#else** . Pokud není k dispozici žádná klauzule **#else** a všechny instance *konstantního výrazu* v bloku **#if** jsou false, není vybrán žádný textový blok.

*Konstantní výraz* je celočíselný konstantní výraz s těmito dodatečnými omezeními:

- Výrazy musí být integrálního typu a můžou obsahovat jenom celočíselné konstanty, znakové konstanty a **definovaný** operátor.

- Výraz nemůže být použit `sizeof` nebo operátor přetypování typu.

- Cílové prostředí nemusí být schopné zastupovat všechny rozsahy celých čísel.

- Překlad představuje typ **int** stejným způsobem jako typ **Long**a **unsigned int** stejným způsobem jako **bez znaménka Long**.

- Překladatel může přeložit znakové konstanty na sadu hodnot kódu, které se liší od sady pro cílové prostředí. K určení vlastností cílového prostředí použijte aplikaci vytvořenou pro toto prostředí pro kontrolu hodnot *omezení. Makro H* .

- Výraz nesmí být prostředím dotazu a musí zůstat izolované z podrobností implementace v cílovém počítači.

## <a name="preprocessor-operators"></a>Operátory preprocesoru

### <a name="defined"></a>definováno

**Definovaný** operátor preprocesoru lze použít ve zvláštních konstantních výrazech, jak je znázorněno v následující syntaxi:

> **definováno (** *identifikátor* **)** \
> **definováno** *identifikátor*

Tento konstantní výraz je považován za true (nenulový), pokud je *identifikátor* aktuálně definován. V opačném případě je podmínka NEPRAVDA (0). Identifikátor definovaný jako prázdný text je považován za definovaný. **Definovaný** operátor lze použít v **#if** a direktivě **#elif** , ale nikde else.

V následujícím příkladu direktivy **#if** a **#endif** řídí kompilaci jednoho ze tří volání funkce:

```C
#if defined(CREDIT)
    credit();
#elif defined(DEBIT)
    debit();
#else
    printerror();
#endif
```

Volání funkce je zkompilováno, je- `credit` li definován identifikátor. `CREDIT` Pokud je definován `DEBIT` identifikátor, `debit` volání funkce je zkompilováno. Pokud není definován žádný identifikátor, volání `printerror` je zkompilováno. A jsou odlišné identifikátory v C a, C++ protože se liší jejich případy. `credit` `CREDIT`

Příkazy podmíněné kompilace v následujícím příkladu předpokládají dříve definovanou symbolický konstantu s názvem `DLEVEL`.

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

První blok **#if** zobrazuje dvě sady vnořených **#if**, **#else**a direktivy **#endif** . První sada direktiv je zpracována pouze v případě `DLEVEL > 5` , že má hodnotu true. Jinak se zpracují příkazy po **#else** .

Direktivy **#elif** a **#else** ve druhém příkladu slouží k vytvoření jedné ze čtyř možností na základě hodnoty `DLEVEL`. Konstanta `STACK` je nastavena na 0, 100 nebo 200 v závislosti na `DLEVEL`definici. Pokud `DLEVEL` je větší než 5, pak příkaz

```C
#elif DLEVEL > 5
display(debugptr);
```

je zkompilován a `STACK` není definován.

Běžné použití pro podmíněnou kompilaci je zabránit vícenásobnému zahrnutí stejného hlavičkového souboru. V C++, kde jsou třídy často definovány v hlavičkových souborech, lze pomocí tohoto typu zabránit více definicím:

```cpp
/*  EXAMPLE.H - Example header file  */
#if !defined( EXAMPLE_H )
#define EXAMPLE_H

class Example
{
    //...
};

#endif // !defined( EXAMPLE_H )
```

Předchozí kód zkontroluje, zda je symbolická konstanta `EXAMPLE_H` definována. Pokud ano, soubor již byl zahrnut a nepotřebuje znovu zpracovat. V takovém případě je `EXAMPLE_H` konstanta definována jako příklad. H, jak již bylo zpracováno.

### <a name="__has_include"></a>__has_include

**Visual Studio 2017 verze 15,3 a novější**:  Určuje, zda je k dispozici hlavička knihovny pro zahrnutí:

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

[Direktivy preprocesoru](../preprocessor/preprocessor-directives.md)
