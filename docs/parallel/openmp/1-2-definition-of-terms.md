---
title: 1.2 definice pojmů | Microsoft Docs
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
ms.openlocfilehash: 8563bb757ad8d30f1639f017769bfd6c4084efa0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="12-definition-of-terms"></a>1.2 Definice pojmů
V tomto dokumentu se používají následující termíny:  
  
 barrier  
 Bod synchronizace, který musí být dosaženo pomocí všechna vlákna v týmu.  Každé vlákno počká, až všechna vlákna v týmu dorazí v tomto okamžiku. Existují explicitní překážky identifikovaný direktivy a implicitní překážek vytvořené implementace.  
  
 konstrukce  
 Konstrukce, které je prohlášení. Obsahuje direktivu a následné strukturovaných bloku. Všimněte si, že některé direktivy nejsou součástí konstrukt. (Viz *openmp – direktiva* v [příloha C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)).  
  
 – Direktiva  
 C nebo C++ **#pragma** následuje **omp –** identifikátor, další text a nový řádek. Direktiva určuje chování programu.  
  
 dynamické rozsahu  
 Všechny příkazy ve *lexikální rozsah*, plus s příkazy uvnitř funkce, která je provést v důsledku provádění příkazů v rámci lexikální rozsah. Dynamické rozsah se také označuje jako *oblast*.  
  
 Lexikální rozsahu  
 Příkazy lexikálně obsažené v *strukturovaných bloku*.  
  
 hlavní vlákno  
 Vlákno, které vytvoří tým při *paralelní oblast* zadána.  
  
 paralelní oblast  
 Příkazy, které vytvořit vazbu OpenMP paralelní konstrukce a mohou být prováděny více vláken.  
  
 private  
 Soukromé proměnné názvy blok úložiště, které jsou jedinečné pro provedení odkaz na vlákno. Všimněte si, že jsou několik způsobů, jak určit, že je soukromé proměnné: a definice v rámci paralelní oblasti **threadprivate** – direktiva, **privátní**, **firstprivate**, **lastprivate**, nebo **snížení** klauzuli, nebo použijte jako proměnnou **pro**řídicí proměnná smyčky v **pro** smyčky hned za **pro** nebo **paralelní pro** – direktiva.  
  
 oblast  
 Dynamické rozsah.  
  
 sériové oblast  
 Spustit pouze pomocí příkazů *hlavní vlákno* mimo rozsah dynamické žádné *paralelní oblast*.  
  
 serializace  
 Provést paralelní konstrukce s týmem vláken, který se skládá z pouze jedno vlákno (což je hlavní vlákno pro tento paralelní konstrukce), s sériové pořadí zpracování pro příkazy v bloku strukturovaných (stejné pořadí jako v případě, že bloku nebyly součástí z paralelní konstrukce) a bez vlivu na hodnoty vrácené **omp_in_parallel()** (kromě důsledky všechny vnořené paralelní konstrukce).  
  
 shared  
 Sdílené proměnné názvy jeden blok úložiště. Všechna vlákna v týmu, která přistupují k této proměnné budou přistupovat k této jeden blok úložiště.  
  
 strukturované bloku  
 Strukturované blok je příkaz (jednoduchá nebo složené), který má jeden záznam a jeden ukončení. Žádný příkaz je strukturovaných blok, pokud je přechod do nebo z tohoto příkazu (včetně volání **longjmp**(3 C) nebo použití **throw**, ale volání **ukončete** jsou povoleny). Složený příkaz je blok strukturovaných, pokud jeho spuštění vždy začíná na otevření **{** a vždy končí ukončovací **}**. Příkaz výrazu, výběr příkaz, příkaz iterace nebo **zkuste** blok je blok strukturovaných, pokud příkaz odpovídající složené získali uveden v **{** a **}** by strukturovaných blok. Přechod příkaz, příkaz s popiskem nebo příkaz deklarace není strukturovaných blok.  
  
 Tým  
 Jeden nebo více podprocesů spolupracující při provádění konstrukt.  
  
 vlákno  
 Provádění entity s Sériový tok řízení, sadu soukromé proměnné a přístup ke sdílené proměnné.  
  
 proměnná  
 Identifikátor, volitelně kvalifikovaný názvy oborů názvů, který názvy objekt.