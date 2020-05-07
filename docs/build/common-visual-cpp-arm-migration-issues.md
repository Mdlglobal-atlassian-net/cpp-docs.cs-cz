---
title: Běžné problémy s migrací ARM v prostředí Visual C++
ms.date: 05/06/2019
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
ms.openlocfilehash: 2c29b4ffa5344b309622314970ce52c47a0ebd05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328799"
---
# <a name="common-visual-c-arm-migration-issues"></a>Běžné problémy s migrací ARM v prostředí Visual C++

Při použití kompilátoru jazyka Microsoft C++ (MSVC) může stejný zdrojový kód jazyka C++ vést k různým výsledkům architektury ARM než v architekturách x86 nebo x64.

## <a name="sources-of-migration-issues"></a>Zdroje problémů s migrací

Mnohé problémy, se kterými se můžete setkat při migraci kódu z architektur x86 nebo x64 do architektury ARM, souvisí s konstrukcemi zdrojového kódu, které mohou vyvolat nedefinované chování definované implementací nebo nespecifikovaným způsobem.

*Nedefinované chování* je chování, které Standard C++ nedefinuje a který je způsobený operací, která nemá rozumný výsledek: například převod hodnoty s plovoucí desetinnou čárkou na unsigned integer nebo posunutí hodnoty o několik pozic, které jsou záporné nebo překračují počet bitů v jeho propagovaném typu.

*Chování definované implementací* je chování, které Standard C++ vyžaduje, aby dodavatel kompilátoru definoval a dokumentoval. Program se může bezpečně spoléhat na chování definované implementací, i když to ale nemusí být přenosné. Mezi příklady chování definovaného implementací patří velikosti integrovaných datových typů a jejich požadavky na jejich zarovnání. Příkladem operace, která může být ovlivněna chováním definovaným implementací, je přístup k seznamu argumentů proměnných.

*Nespecifikované chování* je chování, které standardní kód jazyka C++ opustí záměrně Nedeterministický. I když se chování považuje za nedeterministické, konkrétní vyvolání nespecifikovaného chování je určeno implementací kompilátoru. Neexistuje však žádný požadavek na to, aby dodavatel kompilátoru předem určil výsledek nebo zajistil konzistentní chování mezi srovnatelnými voláními a neexistuje žádný požadavek na dokumentaci. Příkladem nespecifikovaného chování je pořadí, ve kterém jsou vyhodnoceny dílčí výrazy, které obsahují argumenty pro volání funkce.

Další problémy s migrací se dají přidružit k hardwarovým rozdílům mezi architekturami ARM a x86 nebo x64, které pracují se standardem C++ odlišně. Například model silné paměti architektury x86 a x64 poskytuje `volatile`kvalifikované proměnné některé další vlastnosti, které byly použity k usnadnění určitých druhů komunikace mezi vlákny v minulosti. Ale slabý paměťový model architektury ARM nepodporuje toto použití, ani to standard C++ to nevyžaduje.

> [!IMPORTANT]
> I `volatile` když aplikace získá některé vlastnosti, které lze použít k implementaci omezených forem komunikace mezi vlákny v systémech x86 a x64, tyto další vlastnosti nejsou dostačující k implementaci komunikace mezi vlákny obecně. Standard jazyka C++ doporučuje, aby taková komunikace byla implementována místo toho pomocí příslušných primitivních primitiv synchronizace.

Vzhledem k tomu, že různé platformy můžou tyto druhy chování vyjádřit odlišně, může být přenos softwaru mezi platformami obtížné a náchylný k chybám, pokud závisí na chování konkrétní platformy. I když mnoho z těchto druhů chování může být pozorováno a může se zdát být stabilní, spoléhá se na ně aspoň na přenosné a v případě nedefinovaného nebo nespecifikovaného chování je také chyba. I chování, které je Citováno v tomto dokumentu, by se nemělo spoléhat na a může se změnit v budoucích kompilátorech nebo implementacích procesoru.

## <a name="example-migration-issues"></a>Příklady problémů s migrací

Zbývající část tohoto dokumentu popisuje, jak různé chování těchto elementů jazyka C++ může na různých platformách způsobit různé výsledky.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Převod plovoucí desetinné čárky na unsigned integer

V architektuře ARM je převod hodnoty s plovoucí desetinnou čárkou na 32 celé číslo se sytostí na nejbližší hodnotu, kterou může celé číslo představovat, pokud je hodnota s plovoucí desetinnou čárkou mimo rozsah, jehož celé číslo může představovat. V architekturách x86 a x64 se převod zalamuje kolem, pokud je celé číslo bez znaménka, nebo je nastaveno na-2147483648, pokud je celé číslo podepsáno. Žádná z těchto architektur přímo nepodporuje převod hodnot s plovoucí desetinnou čárkou na menší celočíselné typy; místo toho jsou převody provedeny na 32 bitů a výsledky jsou zkráceny na menší velikost.

V případě architektury ARM je kombinace sytosti a zkrácení znamená, že převod na typy bez znaménka správně navýší menší typy bez znaménka, pokud dojde k sytosti 32 celé číslo, ale výsledkem je zkrácený výsledek pro hodnoty, které jsou větší, než menší typ, může představovat, ale je příliš malý, aby bylo možné sytost celého čísla 32. Převod je také správně sytost u celých čísel se znaménkem (32), ale zkrácením nasycených celých čísel je hodnota-1 pro kladné hodnoty a 0 pro hodnoty s negativní sytostí. Převod na menší celé číslo se znaménkem vytvoří zkrácený výsledek, který nelze předvídat.

V architekturách x86 a x64 je kombinace chování při obtékání unsigned integer a explicitního oceňování pro převody s celými čísly při přetečení spolu se zkrácením povede k nepředvídatelným výsledkům pro většinu posunů, pokud jsou příliš velké.

Tyto platformy se také liší v tom, jak zpracovávají převod NaN (ne-a-Number) na celočíselné typy. V ARM se hodnota NaN převede na 0x00000000; v x86 a x64 se převede na 0x80000000.

Konverze s plovoucí desetinnou čárkou se dá spoléhat jenom v případě, že víte, že hodnota spadá do rozsahu typu Integer, na který se převádí.

### <a name="shift-operator---behavior"></a>Chování operátoru\< \< Shift ( >>)

V architektuře ARM může být hodnota posunutá doleva nebo doprava až 255 bitů, než se vzorek začne opakovat. V architekturách x86 a x64 se vzor opakuje v každé násobce 32, pokud zdroj vzorce je 64 proměnná; v takovém případě se vzor opakuje v každé násobce 64 na x64 a v každé násobce 256 v x86, kde se používá implementace softwaru. Například pro 32 proměnnou, která má hodnotu 1 posunutou doleva o 32 pozic, je výsledek 0, v x86 je výsledkem 1 a v případě x64 je výsledkem také 1. Pokud je však zdrojem hodnoty 64 bitová proměnná, pak výsledek na všech třech platformách je 4294967296 a hodnota nebude "obtékat", dokud nebude 64 přesunuta do polohy x64 nebo na 256 pozic na ARM a x86.

Vzhledem k tomu, že výsledek operace posunutí, který překračuje počet bitů ve zdrojovém typu, není definován, kompilátor nemusí mít ve všech situacích konzistentní chování. Například pokud jsou oba operandy Shift známy v době kompilace, kompilátor může optimalizovat program pomocí interní rutiny k předběžnému výpočtu výsledku posunu a následným nahrazením výsledku operace posunutí. Pokud je hodnota posunutí příliš velká nebo záporná, výsledek interní rutiny může být jiný než výsledek stejného výrazu Shift, který je spuštěný PROCESORem.

### <a name="variable-arguments-varargs-behavior"></a>Chování proměnných argumentů (varargs)

V architektuře ARM se parametry ze seznamu argumentů proměnné, které jsou předány v zásobníku, vztahují na zarovnání. Například parametr 64-bit je zarovnán na 64 bitové hranici. V x86 a x64 argumenty, které jsou předány v zásobníku, nejsou předmětem zarovnání a balení těsně. Tento rozdíl může způsobit variadické funkci, jako `printf` je čtení adres paměti, které byly určeny jako odsazení na ARM, pokud očekávané rozložení seznamu argumentů proměnných neodpovídá přesně, i když může fungovat pro podmnožinu některých hodnot v architekturách x86 nebo x64. Vezměte v úvahu tento příklad:

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will "parse" the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

V takovém případě může být chyba opravena tím, že zajistí, že se použije správná specifikace formátu, aby bylo zváženo zarovnání argumentu. Tento kód je správný:

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Pořadí vyhodnocení argumentů

Vzhledem k tomu, že procesory ARM, x86 a x64 jsou rozdílné, mohou představovat různé požadavky na implementace kompilátoru a také různé příležitosti pro optimalizace. Z tohoto důvodu může kompilátor vyhodnotit argumenty funkce v jiném pořadí v různých architekturách nebo v případě, že jsou jiné faktory změněny. To může způsobit neočekávané změny chování aplikace, která spoléhá na konkrétní pořadí vyhodnocování.

Tento druh chyby může nastat, pokud argumenty funkce mají vedlejší účinky, které mají vliv na ostatní argumenty funkce ve stejném volání. Tento druh závislosti se většinou snadno vyhne, ale může být někdy zakrytý závislostmi, které jsou obtížné nerozlišuje, nebo přetěžováním operátorů. Vezměte v úvahu tento příklad kódu:

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Zobrazí se dobře definované, ale pokud `->` a `*` jsou přetížené operátory, pak je tento kód přeložen na něco, co se podobá tomuto:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

A pokud existuje závislost mezi `operator->(memory_handle)` a `operator*(p)`, může se kód spoléhat na konkrétní pořadí vyhodnocování, i když původní kód vypadá jako, že neexistuje žádná možná závislost.

### <a name="volatile-keyword-default-behavior"></a>nestálé výchozí chování klíčových slov

Kompilátor MSVC podporuje dvě různé interprety kvalifikátoru `volatile` úložiště, které lze zadat pomocí přepínačů kompilátoru. Přepínač [/volatile: MS](reference/volatile-volatile-keyword-interpretation.md) vybírá nestálou sémantiku od společnosti Microsoft, která zaručuje silné řazení, stejně jako tradiční scénář pro x86 a x64, protože se jedná o model silné paměti v těchto architekturách. Přepínač [/volatile: ISO](reference/volatile-volatile-keyword-interpretation.md) vybere striktně standardní nestálé sémantiky C++, které nezaručují silné řazení.

V architektuře ARM je výchozím nastavením **/volatile: ISO** , protože procesory ARM mají slabě seřazený paměťový model a protože software ARM nemá starší verzi, která by se měla spoléhat na rozšířenou sémantiku **/volatile: MS** a obvykle nemá k dispozici rozhraní s tímto softwarem. Někdy je však stále pohodlné nebo dokonce nutné zkompilovat program ARM, aby používal rozšířenou sémantiku. Například může být příliš nákladný, aby mohl program použít sémantiku ISO C++, nebo aby software ovladače mohl správně fungovat, aby fungovala tradiční sémantika. V těchto případech můžete použít přepínač **/volatile: MS** ; Chcete-li však znovu vytvořit tradiční nestálou sémantiku pro cíle ARM, kompilátor musí vložit bariéry paměti kolem každého čtení nebo zápisu `volatile` proměnné, aby vynutilo silné řazení, což může mít negativní vliv na výkon.

V architekturách x86 a x64 je výchozí hodnota **/volatile: MS** , protože většina softwaru, který už je pro tyto architektury vytvořená, používá MSVC, spoléhá na ně. Při kompilaci programů x86 a x64 můžete zadat přepínač **/volatile: ISO** , který vám umožní vyhnout se zbytečnému spoléhání na tradiční nestálou sémantiku a zvýšit přenositelnost.

## <a name="see-also"></a>Viz také

[Konfigurace Visual C++ pro procesory ARM](configuring-programs-for-arm-processors-visual-cpp.md)
