---
title: 1.2 definice pojmů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fcaa8eb8-bbbf-4a24-ad0e-e299c442db79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e95ad940aac14892ac14e8d56ba64f49d0bbf7c0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423829"
---
# <a name="12-definition-of-terms"></a>1.2 Definice pojmů

V tomto dokumentu se používají následující termíny:

- barrier

   Bod synchronizace, který musí být dosažitelný všemi vlákny v týmu.  Každé vlákno čeká, dokud všechna vlákna v týmu v tuto chvíli přicházejí. Existují explicitní překážky direktivy a implicitní překážky, které jsou vytvořené v implementaci.

- Konstrukce

   Konstrukce je příkaz. Zahrnuje směrnice a následné strukturovaný blok. Všimněte si, že některé direktivy nejsou součástí konstruktoru. (Viz *openmp – direktiva* v [dodatku C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)).

- – Direktiva

   C nebo C++ **#pragma** následovaný **omp** identifikátor, další text a nový řádek. Direktiva určuje chování programu.

- dynamický rozsah

   Všechny příkazy ve *lexikální rozsah*, plus všechny výroku uvnitř funkce, která se spustí v důsledku spuštění příkazů v rámci lexikální rozsah. Dynamické míry se také označuje jako *oblasti*.

- Lexikální rozsah

   Příkazy lexikálně obsažené *strukturovaný blok*.

-  hlavní vlákno

   Vlákno, které vytvoří tým při *paralelní oblasti* zadání.

- paralelní oblasti

   Příkazy, které svázat paralelní konstrukce OpenMP a mohou být provedeny ve víc vláknech.

- private

   Soukromá proměnná názvy blok úložiště, které je jedinečné pro vlákno odkazu. Všimněte si, že existuje několik způsobů, jak určit, že proměnná je privátní: definici v rámci paralelní oblasti **threadprivate** směrnice, **privátní**, **firstprivate**, **lastprivate**, nebo **snížení** klauzuli, nebo použijte proměnnou jako **pro**řídicí proměnná smyčky for v **pro** smyčky přímo za **pro** nebo **paralelní pro** směrnice.

- oblast

   Dynamický rozsah.

- oblast sériového portu

   Příkazy spustit pouze *hlavní vlákno* mimo rozsah dynamické žádné *paralelní oblasti*.

- Serializace

   Ke spuštění paralelní konstrukce s týmem vláken, který se skládá z pouze jedno vlákno (což je hlavní vlákno pro tato paralelní konstrukce), pomocí sériového portu pořadí zpracování pro příkazy v rámci strukturovaný blok (stejné pořadí, jako kdyby byly bloku není součástí paralelní konstrukce) a bez vlivu na hodnotu vrácenou příkazem **omp_in_parallel()** (kromě účinků žádné vnořené paralelní konstrukce pro).

- shared

   Sdílené proměnné názvy jeden blok úložiště. Všechna vlákna v týmu, které k této proměnné přístup bude mít přístup k této jeden blok úložiště.

- strukturovaný blok

   Strukturovaný blok je příkaz (jednoduchá nebo složené), který má jednu položku a jeden výstup. Žádný příkaz je strukturovaný blok v případě přechod do nebo z něj, který tento příkaz (včetně volání **longjmp**(3 C) nebo použití **throw**, ale volání **ukončit** smí obsahovat). Složený příkaz je strukturovaný blok, pokud jeho spuštění vždy začíná na otevření **{** a vždy končí uzavírací **}**. Příkaz výrazu, příkaz výběru, příkazu iterace nebo **zkuste** blok je strukturovaný blok, pokud odpovídající složený příkaz získali ve kterém je obsažená v **{** a **}** by být strukturovaný blok. Příkaz skoku, příkaz s popiskem nebo příkazu deklarace není strukturovaný blok.

-  Tým

   Jedno nebo více vláken spolupracující při provádění konstruktoru.

- vlákno

   Spuštění entity s Sériový tok řízení, sada privátních proměnných a přístup ke sdílené proměnné.

- proměnná

   Identifikátor, volitelně kvalifikované názvy oborů názvů, která pojmenuje objekt.
