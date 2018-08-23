---
title: Obecné problémy migrace v jazyce Visual C++ ARM | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e09767927a91c61f564e2013bf1b3e0930821193
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42465474"
---
# <a name="common-visual-c-arm-migration-issues"></a>Běžné problémy s migrací ARM v prostředí Visual C++

Při použití Microsoft Visual C++ (MSVC), že stejný zdrojový kód jazyka C++ může k různým výsledkům na architektuře ARM než u x86 nebo x64 architektury.

## <a name="sources-of-migration-issues"></a>Zdroje problémy s migrací

Mnoho problémů, které se mohou vyskytnout při migrace kódu z architektury x86 nebo x64 na architekturu ARM se vztahují na zdrojový kód konstrukce, které mohou vyvolat nedefinované, definovanou implementací nebo neurčené chování.

*Nedefinované chování* je chování, které není definován standardu jazyka C++ a, který je způsobeno tím, operace, která nemá žádný rozumný výsledek: například převod hodnotu s plovoucí desetinnou čárkou na celé číslo bez znaménka, nebo hodnotu posunu počet pozic který je záporná nebo přesahuje počet bitů v jeho povýšený typ.

*Chování definované implementací* je chování, C++ standard vyžaduje dodavatel kompilátoru k definování a dokumentu. Program můžete bezpečně spolehnout na chování definované implementací, i když to uděláte tak nemusí být portable. Chování definované implementací příklady velikosti předdefinované datové typy a jejich požadavky na zarovnání. Příklad operace, které by mohly mít dopad chování definované implementací je přístup k seznamu argumentů proměnných.

*Tento parametr zadán chování* je chování, které se zasílají standardu jazyka C++ záměrně Nedeterministický. Ačkoli chování se považuje za Nedeterministický, určuje konkrétní volání neurčené chování implementace kompilátoru. Ale neexistuje žádný požadavek pro dodavatele kompilátoru určit výsledek nebo zaručit konzistenci mezi srovnatelné volání a neexistuje žádný požadavek pro dokumentaci. Příklad neurčené chování je pořadí, ve kterém jsou vyhodnoceny dílčí výrazy, které zahrnují argumenty pro volání funkce.

Další problémy s migrací lze přiřadit k hardwaru rozdíly mezi ARM a x86 nebo x64 architektury, které pracují s C++ standard odlišně. Například poskytuje silné paměťový model architektury x86 a x64 `volatile`-kvalifikovaný proměnné některé další vlastnosti, které se používají k usnadnění určité druhy komunikace mezi vlákny v minulosti. Ale model slabé paměti architektury ARM nepodporuje toto použití ani standardu jazyka C++ vyžaduje ho.

> [!IMPORTANT]
>  I když `volatile` zisky některé vlastnosti, které je možné implementovat omezený formám komunikace mezi vlákny na x86 a x64, tyto další vlastnosti nejsou dostatečná k implementaci obecně mezi vlákna komunikace. Standard jazyka C++ doporučuje, aby takovou komunikaci implementovat pomocí příslušné synchronizace primitiv.

Protože různé platformy mohou tyto druhy chování express odlišně, přenos softwaru mezi platformami může být obtížné a náchylné k chybám Pokud závisí na chování konkrétní platformy. I když mnohé z těchto druhů chování může být dodržen a může se zobrazit stabilní, spoléhání se na nich je alespoň nepřenosné a v případě neurčené nebo nedefinované chování, je také chybou. I chování, které je uvedené v tomto dokumentu nemělo spoléhat a v budoucnu změnit, jaké kompilátory a implementace procesoru.

## <a name="example-migration-issues"></a>Problémy s migrací příklad

Zbývající část tohoto dokumentu popisuje, jak různé chování těchto prvků jazyka C++ mohou přinést různé výsledky na různých platformách.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Převod s plovoucí desetinnou čárkou na celé číslo bez znaménka

V architektuře ARM nepovažuje převod na 32bitové celé číslo s plovoucí desetinnou čárkou na nejbližší hodnotu, která reprezentuje na celé číslo. Pokud s plovoucí desetinnou čárkou je mimo rozsah, která představuje celé číslo. V architekturách x86 a x64 převod cyklickému přechodu Pokud celé číslo bez znaménka, nebo je nastavený na -2147483648 Pokud podepsané celé číslo. Žádný z těchto architektury přímo nepodporuje převod hodnoty s plovoucí desetinnou čárkou na menší typy celých čísel; Místo toho převody jsou prováděny na 32 bitů a výsledky se zkrátí na menší velikost.

Pro architekturu ARM kombinace přechod sytosti a zkrácení znamená, že převod na typy bez znaménka správně nepovažuje menších typů bez znaménka při nepovažuje 32bitové celé číslo, ale vytváří zkrácený výsledek pro hodnoty, které jsou větší než menší typ může představovat ale příliš malá pro saturate úplné 32bitové celé číslo. Převod nepovažuje správně pro 32bitová celá čísla se znaménkem, ale zkrácení sytou, podepsaný celých čísel za následek pozitivně přeplněný hodnoty -1 a pro negativní přeplněný hodnoty 0. Převod na menší celé číslo se znaménkem vytváří zkrácený výsledek, které nepředvídatelné.

Pro architektury x86 a x64 kombinace obklopující chování pro převod na celé číslo bez znaménka a oceňování explicitní převody celé číslo se znaménkem na přetečení, společně s zkrácení, byly výsledky pro většinu staffhubu nepředvídatelné, pokud jsou moc velká.

Tyto platformy se také liší v jak zpracovávají NaN (Not a Number) převod na typy celých čísel. Na ARM NaN převádí na 0x00000000; na x86 a x64 převede 0x80000000.

Převody plovoucí desetinné čárky lze pouze spoléhat Pokud víte, že je hodnota v rozsahu, který je převáděn na typ integer.

### <a name="shift-operator---behavior"></a>Operátor posunutí (\< \< >>) chování

V architektuře ARM hodnotu lze přesunout left nebo right až 255 bits ještě před zahájením modelu opakování. V architekturách x86 a x64 vzor se opakuje v každé násobek 32 Pokud zdroj vzor je proměnná 64-bit; v takovém případě vzor se opakuje v každé násobkem 64 na x 64 a každý násobek 256 na x86, kde pracuje implementaci softwaru. Pro 32bitové proměnné, která má hodnotu 1 posunuta doleva o 32 pozice, na ARM výsledkem je 0, například na x86 výsledek je 1 a na x64 vrácená hodnota je také 1. Ale pokud je zdroj hodnoty proměnné 64-bit, pak výsledek na všech třech platformách 4294967296, a hodnota nebude "obtékat kolem" dokud posunula 64 pozice na x64 nebo 256 pozice na ARM a x86.

Vzhledem k tomu, že výsledek operace posunutí, která překračuje počet bitů v zdrojový typ není definován, kompilátor nemusí mít konzistentní chování ve všech situacích. Například pokud jsou oba operandy posunu znám v době kompilace, kompilátor může optimalizovat program pomocí rutiny interní předpočítání výsledek shift a potom nahraďte výsledek místo operaci posunutí. Pokud hodnota shift je příliš velká, nebo záporný, výsledkem vnitřní rutina může být jiný než výsledek stejný výraz shift jako provedl procesoru.

### <a name="variable-arguments-varargs-behavior"></a>Chování proměnné argumenty (vararg)

V architektuře ARM podléhají parametry ze seznamu argumenty proměnných, které jsou předány v zásobníku zarovnání. Například je 64-bit parametr zarovnáno na hranici 64-bit. Na x86 a x64 argumenty, které jsou předány v zásobníku nejsou v souladu s zarovnání a aktualizací Service pack úzce. Tento rozdíl může způsobit variadické funkce, jako je `printf` číst adresy paměti, které byly určeny jako odsazení v ARM Pokud je očekávané rozložení seznamu proměnné argumenty, se neshoduje přesně, i v případě, že může fungovat pro podmnožinu některé hodnoty v x86 nebo x64 architektury. Podívejte se například:

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will “parse” the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

V takovém případě chyby může být opraveno a ujistěte se, že specifikace správný formát se používá tak, aby se považuje za zarovnání argumentu. Tento kód je správný:

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Pořadí vyhodnocení argumentu

Protože ARM, x 86 a x64 procesorů se tak liší, můžou poskytnout různé požadavky pro implementace kompilátoru a také různé možnosti optimalizace. Z tohoto důvodu spolu s jinými faktory jako nastavení konvence volání a optimalizace, kompilátor může vyhodnotit argumentů v jiném pořadí na různé architektury nebo při změně dalších faktorů. To může způsobit chování aplikace, která závisí na konkrétní evaluationorder neočekávaně změnit.

Předejít těmto chybám může dojít, pokud argumenty funkce mají vedlejší účinky, které mají vliv ostatních argumentů pro funkce ve stejném volání. Obvykle je snadné se vyhnout, tento druh závislosti, ale to může v některých případech být skryty závislosti, které je obtížné rozpoznat nebo přetížení operátoru. Vezměte v úvahu tento příklad kódu:

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

To vypadá jasně definované, avšak v tom případě `->` a `*` jsou přetížené operátory, potom tento kód se přeloží na něco, co vypadá takto:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

A pokud neexistuje závislost mezi `operator->(memory_handle)` a `operator*(p)`, může kód závisí na konkrétní evaluationorder, i když původní kód vypadá neexistuje žádná závislost je to možné.

### <a name="volatile-keyword-default-behavior"></a>volatile – klíčové slovo výchozí chování

Kompilátor MSVC podporuje dvě různé interpretaci `volatile` kvalifikátor úložiště, který určíte pomocí přepínače kompilátoru. [/Volatile:ms](../build/reference/volatile-volatile-keyword-interpretation.md) přepínač vybere rozšířená volatile sémantiku, která zaručí silné řazení, protože byl z důvodu model silného paměti na tyto architektury tradiční případ x86 a x64 společnosti Microsoft. [/Volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) přepínač vybere striktní C++ standardní volatile sémantiku, která nezaručují silné řazení.

V architektuře ARM, výchozí hodnota je **/volatile:iso** protože slabě řazení paměti modelu mají procesory ARM a ARM softwaru nemá starší verze sady spoléhat na rozšířené sémantika **/volatile:ms**  a nemá obvykle rozhraní s software, který nemá. Je však stále někdy vhodné nebo dokonce muset kompilovat aplikace ARM k používání sémantiky rozšířené. Například může být příliš drahé port programu k používání sémantiky ISO C++ nebo ovladač může být nutné splnit tradiční sémantiku fungovat správně. V těchto případech můžete použít **/volatile:ms** přepínače; znovu vytvořit tradiční volatile sémantiky pro cíle ARM, však kompilátor musí vložit překážky paměti kolem každé čtení nebo zápis `volatile` proměnné k vynucení silné řazení, který může mít negativní dopad na výkon.

V architekturách x86 a x64, výchozí hodnota je **/volatile:ms** vzhledem k tomu, že velká část softwaru, který již byl vytvořen pro tyto architektury s využitím MSVC spoléhá na ně. Při kompilaci programů x86 a x64 můžete zadat **/volatile:iso** přepínače, která pomáhá zabránit zbytečným umožňující tradiční volatile sémantiku a zvýšení úrovně přenositelnost.

## <a name="see-also"></a>Viz také:

[Konfigurace Visual C++ pro procesory ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md)  
