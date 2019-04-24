---
title: 1. Úvod
ms.date: 01/16/2019
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
ms.openlocfilehash: 8c735408bdf9f9a13693bd0ad25df185bb1db42a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236447"
---
# <a name="1-introduction"></a>1. Úvod

Tento dokument určuje kolekci direktivy kompilátoru knihovních funkcí a proměnných prostředí, které můžete použít k určení paralelismu sdílené paměti v aplikacích jazyka C a C++. Funkce popsané v tomto dokumentu se souhrnně říká *OpenMP – C/C++ rozhraní API (Application Program)*. Cílem této specifikace je k poskytnutí modelu pro paralelní programování umožňuje aplikaci mít přenosné mezi architekturami sdílené paměti od různých dodavatelů. Kompilátory z mnoho dodavatelů podporují rozhraní API OpenMP – C/C++. Další informace o OpenMP, včetně *OpenMP až po Fortran Application Program Interface*, najdete na následujícím webu:

[https://www.openmp.org](https://www.openmp.org)

Direktivy, knihovních funkcí a proměnných prostředí definovaných v tomto dokumentu umožňují vytvářet a spravovat paralelních programů zároveň umožní přenositelnost. Direktivy rozšíření C a C++ sekvenční programovací model s jeden program, který vytvoří více dat (SPMD), konstrukce pro sdílení práce a konstrukce synchronizace. Podporují také sdílení a privatizace data. Kompilátory, které podporují OpenMP – C a C++ API zahrnují možnost příkazového řádku pro kompilátor, který aktivuje a umožňuje výklad všechny direktivy OpenMP kompilátoru.

## <a name="11-scope"></a>1.1 Rozsah

Tato specifikace obsahuje pouze uživatel přesměruje paralelizace, ve které explicitně definovat, jaké akce kompilátor a za běhu systému provést paralelní spuštění programu. Implementace OpenMP – C a C++ se nevyžadují pro vyhledání závislostí, je v konfliktu, zablokování, časování nebo jiné problémy, jejichž výsledkem nesprávné programu. Jste zodpovědní za zajištění, že aplikace konstrukce OpenMP – C a C++ API pomocí provádí správně. Vygenerovaný kompilátorem automatickou paralelizaci a direktivy kompilátoru pomáhat takové paralelizace nejsou zahrnuté v tomto dokumentu.

## <a name="12-definition-of-terms"></a>1.2 definice pojmů

V tomto dokumentu se používají následující termíny:

- barrier

  Bod synchronizace, který se po dosažení všechna vlákna v týmu.  Každé vlákno čeká, dokud všechna vlákna v týmu v tuto chvíli přicházejí. Existují explicitní překážky direktivy a implicitní překážky, které jsou vytvořené v implementaci.

- Konstrukce

  Konstrukce je příkaz. Skládá se z direktivu, za nímž následuje strukturovaný blok. Některé direktivy nejsou součástí konstrukci. (Viz *openmp – direktiva* v [dodatku C](c-openmp-c-and-cpp-grammar.md)).

- – Direktiva

  C nebo C++ `#pragma` následovaný `omp` identifikátor, další text a nový řádek. Direktiva určuje chování programu.

- dynamický rozsah

  Všechny příkazy ve *lexikální rozsah*, plus všechny výroku uvnitř funkce, která se spustí v důsledku spuštění příkazů v rámci lexikální rozsah. Dynamické míry se také označuje jako *oblasti*.

- Lexikální rozsah

  Příkazy lexikálně uchovávat ve *strukturovaný blok*.

- hlavní vlákno

  Vlákno, které vytvoří tým při *paralelní oblasti* zadání.

- paralelní oblasti

  Příkazy, které svázat paralelní konstrukce OpenMP a mohou být provedeny podle několika vlákny.

- private

  Soukromá proměnná názvy blok úložiště, které je jedinečné pro vlákno odkazu. Existuje několik způsobů, jak určit, že proměnná je privátní: definici v rámci paralelní oblasti `threadprivate` směrnice, `private`, `firstprivate`, `lastprivate`, nebo `reduction` klauzuli, nebo použijte proměnnou jako `for`smyčky řídicí proměnná v `for` ihned po smyčce `for` nebo `parallel for` – direktiva.

- oblast

  Dynamický rozsah.

- oblast sériového portu

  Příkazy spustit pouze *hlavní vlákno* mimo rozsah dynamické žádné *paralelní oblasti*.

- Serializace

  Ke spuštění paralelní konstrukce pomocí:

  - tým vláken, který se skládá z pouze jedno vlákno (což je hlavní vlákno pro tato paralelní konstrukce),

  - sériový pořadí zpracování pro příkazy v rámci strukturovaný blok (stejné pořadí jakoby bloku nejsou součástí paralelní konstrukce), a

  - žádný vliv na hodnotu vrácenou příkazem `omp_in_parallel()` (kromě účinků žádné vnořené paralelní konstrukce pro).

- shared

  Sdílené proměnné názvy jeden blok úložiště. Všechna vlákna v týmu, které k této proměnné přístup také přístup k této jeden blok úložiště.

- strukturovaný blok

  Strukturovaný blok je příkaz (jednoduchá nebo složené), který má jednu položku a jeden výstup. Při přechodu do nebo z něj příkaz, který tento příkaz je strukturovaný blok. (Toto pravidlo obsahuje volání `longjmp`(3C) nebo použití `throw`, i když volání `exit` je povolená.) Pokud provádění vždy začíná na otevření `{` a vždy končí uzavírací `}`, složený příkaz je strukturovaný blok. Příkaz výrazu, příkaz výběru, příkazu iterace nebo `try` blok je strukturovaný blok, pokud odpovídající složený příkaz získali ve kterém je obsažená v `{` a `}` by být strukturovaný blok. Příkaz skoku, příkaz s popiskem nebo příkazu deklarace není strukturovaný blok.

- Tým

  Jedno nebo více vláken spolupracující při provádění konstruktoru.

- vlákno

  Spuštění entity s Sériový tok řízení, sada privátních proměnných a přístup ke sdílené proměnné.

- proměnná

  Identifikátor, volitelně kvalifikované názvy oborů názvů, která pojmenuje objekt.

## <a name="13-execution-model"></a>1.3 model spouštění

OpenMP – používá model forku spojení paralelní spuštění. Ačkoli tento model forku spojení mohou být užitečné při řešení potíží s různými, je přizpůsobené pro velké aplikace založené na pole. OpenMP – slouží k podpoře programy, které jsou spuštěny správně také jako paralelních programů (podpora několika vlákny a úplné OpenMP – knihovny). Je také pro programy, které jsou spuštěny správně sekvenční programy (direktivy ignorována a jednoduché OpenMP – knihovny zástupné procedury). Nicméně je možné a umožnit vývoj program, který nebude chovat správně při prováděny postupně. Kromě toho různým stupněm paralelizace může způsobit různých číselných výsledků z důvodu změn v přidružení škály číselných operací. Například sériového portu přidání snížení může mít různé vzor přidružení přidání než paralelní redukci. Tyto jiné přidružení může změnit výsledky s plovoucí desetinnou čárkou sčítání.

Program napsané pomocí rozhraní API pro C/C++ OpenMP zahájí provádění spuštění označované jako jedno vlákno *hlavní vlákno*. Hlavní vlákno provádí v oblasti sériového portu, dokud se zjistil první paralelní konstrukce. V rozhraní API OpenMP C/C++ `parallel` směrnice představuje paralelní konstrukce. Vyskytne paralelní konstrukce hlavní vlákno vytvoří tým vláken a se stává hlavní týmu. Každé vlákno v týmu provede příkazy na dynamický rozsah paralelní oblasti, s výjimkou konstrukce pro sdílení práce. Všechna vlákna v týmu musí nastat konstrukce pro sdílení práce ve stejném pořadí a jeden nebo více vláken spouští příkazy v rámci přidružené strukturovaný blok. Překážkou implicitní na konci konstruktoru work-sharing bez `nowait` klauzule se spouštějí všemi vlákny v týmu.

Pokud vlákno upraví objekt sdílené, ovlivní to pouze svou vlastní spouštěcí prostředí, ale také ty ostatní vlákna v programu. Změna je zaručeno, že na dokončení, z hlediska jiného vlákna, v dalším bodě pořadí (podle definice v základní jazyk) pouze v případě, že objekt je deklarován jako volatile. V opačném případě úpravy je zaručeno, že na dokončení po první úprava vlákna. Ostatní vlákna pak (nebo souběžně) najdete v článku `flush` směrnice, který určuje objekt (implicitně nebo explicitně). Když `flush` direktivy, které jsou odvozené od jiné direktivy OpenMP nezaručují, správné seřazení vedlejší účinky, zodpovídá programátor slouží k poskytování dalších, explicitní `flush` direktivy.

Po dokončení paralelní konstrukce synchronizaci vláken v týmu na implicitní bariéry a pouze hlavní vlákno pokračuje v provádění kódu. V jediném programu můžete zadat libovolný počet paralelní konstrukce pro. V důsledku toho může program vytvořit fork a připojte se k během provádění v mnoha případech.

Rozhraní API OpenMP – C/C++ umožňuje programátorům ve funkcích volaných z v rámci paralelní konstrukce pro použití direktivy. Direktivy, které nejsou zobrazeny v lexikálním rozsahu paralelní konstrukce, ale můžou být v rozsahu dynamické se nazývají *osamocené* direktivy. S osamocené direktivy je programátoři paralelně s minimální změny sekvenční program spustit hlavní části tohoto programu. Pomocí této funkce můžete kód paralelní konstrukce v nejvyšší úrovně stromu volání aplikace a použít direktivy k řízení provádění v některém z volané funkce.

Nesynchronizované volání jazyka C a C++ výstupních funkcí, které se zapisovat do stejného souboru může vést k výstupu, ve kterém se zobrazí data napsané v různých vláknech popořadě nedeterministická. Nesynchronizované volání k zadání funkce, které čtou ze stejného souboru obdobně může číst data v nedeterministická pořadí. Nesynchronizované použití vstupně-výstupních operací, tak, aby každé vlákno má přístup k jiný soubor, vytvoří stejné výsledky jako sériové provádění funkcí vstupně-výstupních operací.

## <a name="14-compliance"></a>1.4 Kompatibilita

Je implementace rozhraní API pro C/C++ OpenMP *CLS OpenMP* pokud rozpozná a zachovává sémantiku ze všech prvků této specifikace, který je uveden v kapitoly 1, 2, 3, 4, a dodatky C. dodatku A, B, D, E a F jsou určené pro informace mají jenom a nejsou součástí specifikace. Implementace, které zahrnují jenom podmnožinu rozhraní API nejsou kompatibilní s OpenMP.

OpenMP – C a C++ API je rozšířením základní jazyk, který podporuje implementaci. Pokud základní jazyk nepodporuje konstrukce jazyka nebo rozšíření, které se zobrazí v tomto dokumentu, implementace OpenMP není vyžadována pro její podporu.

Všechny standardní funkce knihovny C a C++ a předdefinované funkce (to znamená, funkce, které kompilátor nemá specifické znalosti) musí být bezpečné pro vlákna. Nesynchronizované použití těchto funkcí bezpečné pro vlákna v různých vláknech uvnitř paralelní oblasti nemá za následek nedefinované chování. Chování však nemusí být stejný jako v sériových oblastech. (Náhodné číslo funkce generování je příklad).

Rozhraní API jazyka C/C++ OpenMP – Určuje, že určité chování *definované implementací.* Vyhovující implementace OpenMP – je potřeba definovat a dokumentovat jeho chování v těchto případech. Seznam chování definované implementací najdete v tématu [příloha E:](e-implementation-defined-behaviors-in-openmp-c-cpp.md).

## <a name="15-normative-references"></a>1.5 normativní odkazy

- ISO/IEC 9899:1999 *informace technologie – programovací jazyky – C*. Tato specifikace rozhraní API OpenMP odkazuje na 9899:1999 ISO/IEC jako C99.

- ISO/IEC 9899: 1990, *informace technologie – programovací jazyky – C*. Tato specifikace rozhraní API OpenMP odkazuje na ISO/IEC 9899: 1990 jako C90.

- ISO/IEC 14882:1998 *informace technologie – programovací jazyky – C++*. Tato specifikace rozhraní API OpenMP odkazuje na 14882:1998 ISO/IEC jako C++.

Pokud tato specifikace rozhraní API OpenMP odkazuje na C, se odkazuje na základní jazyk podporováno implementací.

## <a name="16-organization"></a>1.6 Organizace

- [Funkce knihovny run-time](3-run-time-library-functions.md)
- [Proměnné prostředí](4-environment-variables.md)
- [Chování definované implementací v OpenMP – C/C++](e-implementation-defined-behaviors-in-openmp-c-cpp.md)
- [Nové funkce v OpenMP – C/C++ verze 2.0](f-new-features-and-clarifications-in-version-2-0.md)
