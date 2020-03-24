---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: c9ef7ab816ec0d17b9dc0b569a6f3a43af83cc68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167690"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

C++AMP (C++ urychlení obrovských paralelismu) zrychlí provádění C++ kódu tím, že využívá hardware, který je běžně přítomen jako grafický procesor (GPU) na samostatné grafické kartě. Programovací C++ model amp zahrnuje podporu multidimenzionálních polí, indexování, přenosu paměti a dělení. Obsahuje také knihovnu matematických funkcí. Pomocí C++ rozšíření jazyka amp můžete řídit, jak se data přesunou z procesoru do GPU a zpátky.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Přehled modelu C++ AMP](../../parallel/amp/cpp-amp-overview.md)|Popisuje klíčové funkce C++ amp a matematické knihovny.|
|[Používání parametrů Lambda, objektů funkcí a omezených funkcí](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Popisuje způsob použití výrazů lambda, objektů funkcí a omezených funkcí v volání metody [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) .|
|[Používání dlaždic](../../parallel/amp/using-tiles.md)|Popisuje, jak používat dlaždice ke zrychlení kódu C++ amp.|
|[Používání akcelerátoru a objektů accelerator_view](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Popisuje, jak použít akcelerátory k přizpůsobení provádění kódu na GPU.|
|[Používání modelu C++ AMP v aplikacích pro UPW](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Popisuje, jak používat C++ amp v aplikacích Univerzální platforma Windows (UWP), které používají prostředí Windows Runtime typy.|
|[Grafické prvky (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Popisuje, jak používat knihovnu C++ grafiky amp.|
|[Návod: Násobení matic](../../parallel/amp/walkthrough-matrix-multiplication.md)|Ukazuje násobení matice pomocí C++ kódu amp a dělení.|
|[Návod: Ladění aplikace C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Vysvětluje, jak vytvořit a ladit aplikaci, která používá paralelní snížení pro Shrnutí velkého pole celých čísel.|

## <a name="reference"></a>Referenční informace

[Referenční dokumentace (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static Keyword](../../cpp/tile-static-keyword.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>Další prostředky

[Paralelní programování v blogu nativního kódu](https://go.microsoft.com/fwlink/p/?linkid=238472)<br/>
[C++Ukázkové projekty AMP ke stažení](https://go.microsoft.com/fwlink/p/?linkid=248508)<br/>
[Analýza C++ kódu amp pomocí Vizualizátor souběžnosti](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)
