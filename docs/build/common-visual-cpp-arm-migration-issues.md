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

Při použití kompilátoru Microsoft C++ (MSVC) může stejný zdrojový kód jazyka C++ vést k různým výsledkům na architektuře ARM než na architekturách x86 nebo x64.

## <a name="sources-of-migration-issues"></a>Zdroje otázek migrace

Mnoho problémů, které se mohou vyskytnou při migraci kódu z architektury x86 nebo x64 na architekturu ARM, souvisí s konstrukcemi zdrojového kódu, které mohou vyvolat nedefinované, definované implementace nebo nespecifikované chování.

*Nedefinované chování* je chování, které standard Jazyka C++ nedefinuje a které je způsobeno operací, která nemá žádný rozumný výsledek: například převod hodnoty s plovoucí desetinnou hodnotou na nepodepsané celé číslo nebo posun hodnoty o počet pozic, které jsou záporné nebo překračují počet bitů v jeho propagovaném typu.

*Chování definované implementací* je chování, které standard C++ vyžaduje, aby dodavatel kompilátoru definoval a dokumentoval. Program může bezpečně spoléhat na chování definované implementací, i když to nemusí být přenosné. Příklady chování definované implementací zahrnují velikosti předdefinovaných datových typů a jejich požadavky na zarovnání. Příkladem operace, která může být ovlivněna chováním definovaným implementací, je přístup k seznamu argumentů proměnných.

*Nespecifikované chování* je chování, které standard Jazyka C++ ponechává záměrně nedeterministické. Přestože chování je považováno za nedeterministické, zejména vyvolání nespecifikované chování jsou určeny implementací kompilátoru. Neexistuje však žádný požadavek na dodavatele kompilátoru předem určit výsledek nebo zaručit konzistentní chování mezi srovnatelné vyvolání a neexistuje žádný požadavek na dokumentaci. Příkladem nespecifikovaného chování je pořadí, ve kterém jsou vyhodnocovány dílčí výrazy, které obsahují argumenty pro volání funkce.

Další problémy s migrací lze připsat hardwarovým rozdílům mezi architekturami ARM a x86 nebo x64, které interagují se standardem C++odlišně. Například model silné paměti architektury x86 a x64 poskytuje `volatile`-qualified proměnné některé další vlastnosti, které byly použity k usnadnění určité druhy komunikace mezi vlákny v minulosti. Ale model slabé paměti architektury ARM nepodporuje toto použití, ani standard C++ to nevyžaduje.

> [!IMPORTANT]
> Přestože `volatile` získá některé vlastnosti, které lze použít k implementaci omezené formy komunikace mezi vlákny na x86 a x64, tyto další vlastnosti nejsou dostatečné k implementaci komunikace mezi vlákny obecně. Standard Jazyka C++ doporučuje, aby byla tato komunikace implementována pomocí vhodných synchronizačních primitiv.

Vzhledem k tomu, že různé platformy mohou vyjádřit tyto druhy chování odlišně, přenos softwaru mezi platformami může být obtížný a náchylný k chybám, pokud závisí na chování konkrétní platformy. Ačkoli mnoho z těchto druhů chování lze pozorovat a může se zdát stabilní, spoléhání se na ně je alespoň nepřenosné a v případě nedefinované nebo nespecifikované chování, je také chyba. Dokonce i chování, které je citováno v tomto dokumentu by neměla být spoléhal a může změnit v budoucích kompilátorů nebo implementace procesoru.

## <a name="example-migration-issues"></a>Příklad problémů s migrací

Zbytek tohoto dokumentu popisuje, jak různé chování těchto prvků jazyka C++ může způsobit různé výsledky na různých platformách.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Převod plovoucí desetinné na nepodepsané celé číslo

Na architektuře ARM převod hodnoty s plovoucí desetinnou desetinnou hodnotou na 32bitové celé číslo nasytí na nejbližší hodnotu, kterou může představovat celé číslo, pokud je hodnota s plovoucí desetinnou hodnotou mimo rozsah, který může představovat celé číslo. Na architekturách x86 a x64 se převod obtéká, pokud je celé číslo nepodepsané, nebo je nastaveno na -2147483648, pokud je celé číslo podepsáno. Žádná z těchto architektur přímo nepodporuje převod hodnot s plovoucí desetinnou desetinnou desetinnou hodnotou na menší celočíselné typy; místo toho převody jsou prováděny na 32 bitů a výsledky jsou zkráceny na menší velikost.

Pro architekturu ARM kombinace sytosti a zkrácení znamená, že převod na nepodepsané typy správně nasytí menší nepodepsané typy, když nasycuje 32bitové celé číslo, ale vytvoří zkrácený výsledek pro hodnoty, které jsou větší než menší typ, může představovat, ale příliš malý na to, aby nasytil celé 32bitové celé číslo. Převod také správně nasytí pro 32bitová podepsaná celá čísla, ale zkrácení nasycených, podepsaných celočísel má za následek -1 pro kladně nasycené hodnoty a 0 pro záporně nasycené hodnoty. Převod na menší podepsané celé číslo vytvoří zkrácený výsledek, který je nepředvídatelný.

Pro architektury x86 a x64 kombinace obtékání chování pro nepodepsané celočíselné převody a explicitní ocenění pro podepsané celočíselné převody na přetečení, spolu s zkrácením, aby výsledky pro většinu směn nepředvídatelné, pokud jsou příliš velké.

Tyto platformy se také liší v tom, jak zpracovávají převod NaN (Not-a-Number) na celočíselné typy. Na ARM NaN převede na 0x00000000; na x86 a x64, převede na 0x8000000.

Převod s plovoucí desetinnou desetinnou hodnotou lze spoléhat pouze v případě, že víte, že hodnota je v rozsahu celočíselného typu, na který je převáděn.

### <a name="shift-operator---behavior"></a>Chování operátoru shift ( >>)\< \<

Na architektuře ARM hodnota může být posunuta doleva nebo doprava až na 255 bitů před vzor začne opakovat. Na architekturách x86 a x64 se vzorek opakuje na každém násobku 32, pokud není zdrojem vzoru 64bitová proměnná; v takovém případě se vzor opakuje na každém násobku 64 na x64 a každý násobek 256 na x86, kde je použita implementace softwaru. Například pro 32bitovou proměnnou, která má hodnotu 1 posunutou doleva o 32 pozic, na ARM je výsledek 0, na x86 výsledek je 1 a na x64 výsledek je také 1. Pokud je však zdrojem hodnoty 64bitová proměnná, výsledek na všech třech platformách je 4294967296 a hodnota se "neobtéká", dokud se neposune o 64 pozic na x64 nebo 256 pozicích na ARM a x86.

Vzhledem k tomu, že výsledek operace shift, která přesahuje počet bitů ve zdrojovém typu, není definován, kompilátor nemusí mít konzistentní chování ve všech situacích. Například pokud oba operandy shift jsou známy v době kompilace, kompilátor může optimalizovat program pomocí interní rutiny předem vypočítat výsledek shift a potom nahrazení výsledku v místě operace shift. Pokud je částka směny příliš velká nebo záporná, může se výsledek interní rutiny lišit od výsledku stejného výrazu shift, který byl proveden procesorem.

### <a name="variable-arguments-varargs-behavior"></a>Chování proměnných argumentů (varargs)

Na architektuře ARM parametry ze seznamu proměnných argumentů, které jsou předány v zásobníku podléhají zarovnání. Například 64bitový parametr je zarovnán na hranici 64 bitů. Na x86 a x64 argumenty, které jsou předány v zásobníku nejsou předmětem zarovnání a balení pevně. Tento rozdíl může způsobit variadické funkce, jako `printf` je čtení adres paměti, které byly určeny jako odsazení na ARM, pokud očekávané rozložení seznamu proměnných argumentů není přesně uzavřeno, i když může fungovat pro podmnožinu některých hodnot na architekturách x86 nebo x64. Vezměme si tento příklad:

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will "parse" the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

V tomto případě lze chybu opravit tím, že se ujistíte, že je použita správná specifikace formátu, aby bylo zváženo zarovnání argumentu. Tento kód je správný:

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Pořadí vyhodnocení argumentů

Vzhledem k tomu, že procesory ARM, x86 a x64 se tak liší, mohou představovat různé požadavky na implementace kompilátoru a také různé příležitosti pro optimalizace. Z tohoto důvodu spolu s dalšími faktory, jako je konvence volání a nastavení optimalizace kompilátoru může vyhodnotit argumenty funkce v jiném pořadí na různých architekturách nebo při změně ostatních faktorů. To může způsobit neočekávanou změnu chování aplikace, která závisí na určitém pořadí hodnocení.

Tento druh chyby může dojít, když argumenty funkce mají vedlejší účinky, které mají vliv na jiné argumenty funkce ve stejném volání. Obvykle tento druh závislosti je snadné se vyhnout, ale může být někdy zakryta závislosti, které jsou obtížně rozpoznatelné, nebo přetížení operátorem. Vezměme si tento příklad kódu:

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

To se zdá být `->` dobře `*` definované, ale pokud a jsou přetížené operátory, pak tento kód je přeložen na něco, co se podobá toto:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

A pokud existuje závislost mezi `operator->(memory_handle)` `operator*(p)`a , kód může spoléhat na konkrétní pořadí hodnocení, i když původní kód vypadá, že neexistuje žádná možná závislost.

### <a name="volatile-keyword-default-behavior"></a>výchozí chování těkavých klíčových slov

Kompilátor MSVC podporuje dvě různé `volatile` interpretace kvalifikátoru úložiště, které můžete zadat pomocí přepínačů kompilátoru. Přepínač [/volatile:ms](reference/volatile-volatile-keyword-interpretation.md) vybere rozšířenou těkavou sémantiku společnosti Microsoft, která zaručuje silné řazení, jako tomu bylo u x86 a x64 z důvodu modelu silné paměti na těchto architekturách. Přepínač [/volatile:iso](reference/volatile-volatile-keyword-interpretation.md) vybere striktní standardní těkavou sémantiku jazyka C++, která nezaručuje silné řazení.

Na architektuře ARM je výchozí **hodnota /volatile:iso,** protože procesory ARM mají slabě uspořádaný paměťový model a protože software ARM nemá starší odkaz spoléhání se na rozšířenou sémantiku **/volatile:ms** a obvykle nemá rozhraní se softwarem, který nemá. Je však někdy pohodlné nebo dokonce nutné zkompilovat program ARM pro použití rozšířené sémantiky. Například může být příliš nákladné portovat program používat iso c++ sémantiku nebo software ovladače může mít dodržovat tradiční sémantiku fungovat správně. V těchto případech můžete použít **přepínač /volatile:ms;** však znovu tradiční těkavé sémantiky na cíle ARM, kompilátor musí `volatile` vložit bariéry paměti kolem každé čtení nebo zápis proměnné vynutit silné řazení, což může mít negativní dopad na výkon.

Na architekturách x86 a x64 je výchozí hodnota **/volatile:ms,** protože na nich závisí velká část softwaru, který již byl vytvořen pro tyto architektury pomocí nástroje MSVC. Při kompilaci programů x86 a x64 můžete zadat přepínač **/volatile:iso,** který zabrání zbytečnému spoléhání se na tradiční těkavou sémantiku a podpoří přenositelnost.

## <a name="see-also"></a>Viz také

[Konfigurace Visual C++ pro procesory ARM](configuring-programs-for-arm-processors-visual-cpp.md)
