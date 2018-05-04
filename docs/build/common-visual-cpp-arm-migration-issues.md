---
title: Běžné problémy s migrací ARM Visual C++ | Microsoft Docs
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
ms.openlocfilehash: 04253b5d71de75f6a06f2934dae24df2e6d4e3e2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="common-visual-c-arm-migration-issues"></a>Běžné problémy s migrací ARM v prostředí Visual C++

Pokud používáte Microsoft Visual C++ (MSVC), ze stejného zdrojového kódu C++ může mít různé výsledky na architektuře ARM, než u x86 nebo x64 architektury.

## <a name="sources-of-migration-issues"></a>Zdroje problémy s migrací

Mnohé problémy, které se můžete setkat při migraci kód z architektury x86 nebo x64 s architekturou ARM souvisí s konstrukce zdrojového kódu, které může vyvolat nedefinované, definované implementací nebo nezadanou chování.

*Není definována chování* je chování, které C++ standard nedefinuje a je příčinou operace, která nemá žádný přiměřené výsledek: například převodu hodnot s plovoucí desetinnou čárkou celé číslo bez znaménka nebo s posunem hodnotu podle počet pozic který záporné nebo překračuje počet bitů v jeho propagovaných typu.

*Chování definované implementací* je chování, které C++ standard vyžaduje dodavatele kompilátoru definovat a dokumentů. Program můžete bezpečně spoléhají na chování definované implementací, i když to proto nemusí být přenosná. Chování definované implementací příklady velikosti předdefinované datové typy a jejich požadavky na zarovnání. Příklad operace, která může být ovlivněn chování definované implementací je přístup k seznamu proměnné argumenty.

*Neurčené chování* je chování, které C++ standard opustí záměrně není deterministický. I když chování považuje za Nedeterministický, konkrétní volání neurčené chování určuje implementace kompilátoru. Ale není potřeba pro dodavatele kompilátoru předem nastavit výsledek nebo zaručit konzistenci mezi porovnatelný z hlediska volání a není potřeba pro dokumentaci. Pořadí, ve kterém jsou vyhodnocovány dílčí výrazy, které obsahují argumenty pro volání funkce, je například neurčené chování.

Další problémy migrace je spojena hardwaru rozdíly mezi ARM a x86 nebo x64 architektury, které pracují se standardní C++ jinak. Například poskytuje model silné paměti architektury x86 a x64 `volatile`-kvalifikovaný proměnné některé další vlastnosti, které byly použity pro usnadnění určité druhy komunikace mezi vláken v minulosti. Ale modelu slabé paměti architektura ARM nepodporuje tuto použijte ani C++ standard nevyžaduje ho.

> [!IMPORTANT]
>  I když `volatile` zvýšení některé vlastnosti, které lze použít k implementaci omezené forem komunikace mezi vlákna na x86 a x64, tyto další vlastnosti nejsou dostatečná k implementaci obecně mezi vláken komunikace. Standardní C++ doporučuje, aby takovou komunikaci implementovat pomocí příslušné synchronizace primitiv.

Protože tyto druhy chování může express různých platformách jinak, portování softwaru mezi platformami může být obtížné a chyb náchylné Pokud je závislý na chování konkrétní platformu. I když mnohé z těchto druhů chování může být dodržen a může se objevit stabilní, spoléhat na jejich je alespoň bez přenositelností a v případech chování definován nebo není zadán, je také k chybě. I chování, které je uvedené v tomto dokumentu by neměl být spoléhali na a může v budoucnu měnit kompilátory nebo implementace procesoru.

## <a name="example-migration-issues"></a>Příklad problémy s migrací

Zbytek tohoto dokumentu popisuje, jak různé chování těchto prvků jazyka C++, může mít různé výsledky na různých platformách.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Převod s plovoucí desetinnou čárkou na celé číslo bez znaménka

V architektuře ARM nepovažuje převod s plovoucí desetinnou čárkou hodnoty 32bitové celé číslo na nejbližší hodnotu, která představuje na celé číslo. Pokud hodnota s plovoucí desetinnou čárkou je mimo rozsah, který může představovat na celé číslo. Na x86 a x64 architektury převod obtéká Pokud celé číslo bez znaménka nebo je nastavena na -2147483648, pokud je podepsaný na celé číslo. Žádný z těchto architektury přímo nepodporuje převod hodnot s plovoucí desetinnou čárkou menší typy celého čísla; Místo toho se provádí převody 32bitová verze a výsledky se zkrátí na menší velikost.

Kombinace sytost a zkrácení pro architekturu ARM, znamená, že převod na typy bez znaménka správně nepovažuje menší typy bez znaménka nepovažuje 32bitové celé číslo, ale vytvoří zkrácený výsledek hodnot, které jsou větší než menší typ může představovat ale příliš malá pro saturate úplné 32bitové celé číslo. Převod nepovažuje správně pro 32bitová podepsaná celá čísla, ale zkrácení nasycených, podepsaný celých čísel za následek -1 pro hodnoty u nasyceno a 0 pro negativní nasyceno hodnoty. Převod na menší znaménkem vytvoří zkrácený výsledek, který předpovědět.

Pro x86 a x64 architektury kombinace obklopující chování celé číslo bez znaménka převody a explicitní ohodnocení pro číslo se znaménkem převody na přetečení společně s zkrácení, zkontrolujte výsledky pro většinu posuny nepředvídatelným, pokud jsou příliš velký.

Tyto platformy se také liší v jak budou pracovat s převod NaN (není a-Number) typy celého čísla. Na ARM NaN převede na 0x00000000; na x86 a x64 převede ji na 0x80000000.

Převody plovoucí desetinné čárky pouze jsou spolehlivé Pokud víte, že se hodnota v rozsahu celým číslem, který je převáděn na.

### <a name="shift-operator---behavior"></a>Operátor posunutí (\< \< >>) chování

V architektuře ARM hodnotu lze přesunout doleva nebo doprava až 255 bits ještě před zahájením vzor opakování. Na x86 a x64 architektury vzorek opakuje na každých několik 32 Pokud zdroj vzor je proměnná 64-bit; v takovém případě vzor opakuje v každé násobkem 64 na x 64 a každý násobkem 256 na x86, kde implementace software pracuje. Pro 32bitové proměnné, která má hodnotu 1 zapuštěno zanechaný 32 pozic, na ARM výsledkem je 0, například na x86 výsledkem je 1 a na x64 výsledek je také 1. Ale pokud je zdroj hodnoty proměnné 64-bit, pak výsledek na všech platformách tři 4294967296, a hodnota nemá "obtékat kolem" dokud ho na x64 nebo 256 pozic na ARM a x86 posunula 64 pozic.

Protože výsledek operace shift, která překračuje počet bitů v typ zdroje není definovaný, kompilátor není potřeba mít konzistentní chování ve všech situacích. Například pokud oba operandy shift známé v době kompilace, kompilátor může optimalizovat program pomocí interní rutiny předpočítání výsledek k posunu a poté nahraďte výsledek místo operaci shift. Pokud velikost posunutí je příliš velký, nebo záporná, může být výsledkem vnitřní rutiny jiný než výsledek stejný výraz shift provedený procesoru.

### <a name="variable-arguments-varargs-behavior"></a>Chování proměnné argumenty (vararg)

V architektuře ARM parametry ze seznamu proměnné argumenty, které se předávají v zásobníku se vztahují zarovnání. Například 64-bit parametr je zarovnán na hranici 64-bit. Na x86 a x64 argumenty, které se předávají v zásobníku se nevztahuje zarovnání a pack úzce. Tento rozdíl může způsobit variadická funkce jako `printf` číst adres paměti, které byly určeny jako odsazení v ARM pokud očekávaný rozložení seznamu proměnné argumenty neodpovídá přesně, i když může fungovat pro podmnožinu některé hodnoty na x86 nebo x64 architektury. Vezměte v úvahu v tomto příkladu:

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will “parse” the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

V takovém případě můžete opravit chybě tím, že zajistí, že se používá specifikace správný formát tak, aby který je považován za zarovnání argumentu. Tento kód není správný:

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Argument pořadí vyhodnocení

Protože ARM, x 86 a x64 procesorů se tak liší, můžou poskytnout jiné požadavky implementace kompilátoru a také různé možnosti optimalizace. Z toho důvodu spolu s jinými faktory jako nastavení konvence volání a optimalizace, kompilátor může vyhodnotit argumenty funkce v jiném pořadí na různé architektury nebo kdy se změnil dalších faktorů. To může způsobit chování aplikace, které jsou závislé na konkrétní vyhodnocení pořadí chcete změnit neočekávaně.

Tento druh chyby může nastat, pokud argumenty pro funkci vedlejší účinky, které mají vliv další argumenty funkce ve stejném volání. Obvykle je snadné se vyhnout, tento druh závislostí, ale je může v některých případech být skryté závislosti, které je obtížné rozpoznat nebo přetížení operátoru. Vezměte v úvahu tento příklad kódu:

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Se zobrazuje dobře definovaný, avšak v tom případě `->` a `*` se přetížené operátory, pak tento kód je přeložená na jinou hodnotu, která vypadá takto:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

A pokud je závislosti mezi `operator->(memory_handle)` a `operator*(p)`, může kód závisí na konkrétní vyhodnocení pořadí, i když původní kód vypadá jako neexistuje žádná možné závislost.

### <a name="volatile-keyword-default-behavior"></a>výchozí chování volatile – klíčové slovo

Podporuje dvě různé interpretace z kompilátoru MSVC `volatile` kvalifikátor úložiště, které můžete zadat pomocí přepínače kompilátoru. [/Volatile:ms](../build/reference/volatile-volatile-keyword-interpretation.md) přepínač vybere Microsoft rozšířené volatile sémantikou, které zaručit silné řazení, protože byl tradiční případ x86 a x64 z důvodu modelu silné paměti na tyto architektury. [/Volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) přepínač vybere striktní C++ standardní volatile sémantiky který nezaručují silné řazení.

Na architektuře ARM, výchozí hodnota je **/volatile:iso** protože procesory ARM slabě seřazené modelu paměti, a protože ARM softwaru nemá starší verze systému spoléhat na rozšířené sémantika **/volatile:ms**  a nemá obvykle rozhraní s software, který nemá. Je však stále někdy pohodlný nebo i vyžaduje kompilátor ARM k používání sémantiky rozšířené. Například může být příliš nákladná k portu program k používání sémantiky ISO C++, nebo ovladač softwaru může mít řídit tradiční sémantiku fungovat správně. V těchto případech můžete použít **/volatile:ms** přepínač; však k opětovnému vytvoření tradiční volatile sémantiku na ARM cíle, třeba kompilátor vložit paměti překážek kolem každé pro čtení nebo zápis `volatile` proměnná k vynucení silné řazení, která může mít negativní dopad na výkon.

Na x86 a x64 architektury, výchozí hodnota je **/volatile:ms** vzhledem k tomu většinu software, který již byl vytvořen pro tyto architektury pomocí MSVC závisí na ně. Když zkompilujete x86 a x64 programy, můžete zadat **/volatile:iso** přepínače, abyste se vyhnuli nepotřebné spoléhat na tradiční volatile sémantiku a ke zvýšení úrovně přenositelnost.

## <a name="see-also"></a>Viz také

[Konfigurace Visual C++ pro procesory ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md)  
