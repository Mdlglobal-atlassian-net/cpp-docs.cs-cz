---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: f8ac71023f66868a66fb8c54a5e86678225378a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613171"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

C++ AMP (C++ Accelerated Massive Parallelism) zrychlí provádění kódu jazyka C++ využitím hardwaru paralelizovaného pro data, která je běžně přítomen jako grafický procesor (GPU) na samostatné grafické kartě. Model programování C++ AMP zahrnuje podporu vícerozměrných polí, indexování, paměťového přenosu a dělení na bloky. Také obsahuje knihovnu matematických funkcí. Můžete použít rozšíření jazyka C++ AMP řídit, jak jsou data přenášena z procesoru do GPU a zpět.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Přehled modelu C++ AMP](../../parallel/amp/cpp-amp-overview.md)|Popisuje klíčové funkce jazyka C++ AMP a matematické knihovny.|
|[Používání parametrů Lambda, objektů funkcí a omezených funkcí](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Popisuje způsob použití výrazů lambda, objektů funkcí a omezených funkcí ve voláních [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metody.|
|[Používání dlaždic](../../parallel/amp/using-tiles.md)|Popisuje způsob použití bloků k urychlení kódu C++ AMP.|
|[Používání akcelerátoru a objektů accelerator_view](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Popisuje použití akcelerátorů k přizpůsobení provádění kódu na GPU.|
|[Používání modelu C++ AMP v aplikacích pro UPW](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Popisuje způsob použití jazyka C++ AMP v aplikacích pro univerzální platformu Windows (UPW), které používají typy Windows Runtime.|
|[Grafické prvky (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Popisuje použití grafické knihovny C++ AMP.|
|[Návod: Násobení matic](../../parallel/amp/walkthrough-matrix-multiplication.md)|Demonstruje násobení matic pomocí kódu C++ AMP a bloků.|
|[Návod: Ladění aplikace C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Vysvětluje, jak vytvářet a ladit aplikaci používající paralelní redukci pro součet velkého pole celých čísel.|

## <a name="reference"></a>Odkaz

[Referenční dokumentace (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static Keyword](../../cpp/tile-static-keyword.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>Další zdroje

[Paralelní programování v blogu nativního kódu](http://go.microsoft.com/fwlink/p/?linkid=238472)<br/>
[Ukázkové projekty jazyka C++ AMP ke stažení](http://go.microsoft.com/fwlink/p/?linkid=248508)<br/>
[Analýza kódu C++ AMP pomocí Vizualizéru souběžnosti](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)