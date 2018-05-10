---
title: C++ AMP (C++ Accelerated Massive Parallelism) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98ae6b6a5cd24a1ea146cca7ccb30fcbdc93ae75
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)
C++ AMP (C++ Accelerated Massive Parallelism) zrychluje provádění kódu C++ a využívají data paralelní hardware, který se obvykle nachází jako grafický procesor (GPU) na kartě diskrétní grafiky. Programovací model C++ AMP zahrnuje podporu pro vícerozměrná pole, indexování, přenos paměti a dlaždice. Zahrnuje taky knihovny matematické funkce. Můžete použít k řízení, jak přesunout data z procesoru na grafický procesor s rozšíření jazyka C++ AMP a zpět.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Přehled modelu C++ AMP](../../parallel/amp/cpp-amp-overview.md)|Popisuje klíčové funkce C++ AMP a matematickém knihovny.|  
|[Používání parametrů Lambda, objektů funkcí a omezených funkcí](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Popisuje způsob použití výrazů lambda, objektů funkcí a omezených funkcí ve voláních [parallel_for_each –](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metoda.|  
|[Používání dlaždic](../../parallel/amp/using-tiles.md)|Popisuje, jak zrychlit kódu C++ AMP pomocí dlaždice.|  
|[Používání akcelerátoru a objektů accelerator_view](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Popisuje, jak použít akcelerátorů k přizpůsobení provádění kódu na GPU.|  
|[Používání modelu C++ AMP v aplikacích pro UPW](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Popisuje způsob použití C++ AMP v aplikacích univerzální platformu Windows (UWP), které používají typy prostředí Windows Runtime.|  
|[Grafické prvky (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Popisuje, jak na používání knihovny, C++ AMP grafiky.|  
|[Návod: Násobení matic](../../parallel/amp/walkthrough-matrix-multiplication.md)|Demonstruje násobení matic pomocí kódu C++ AMP a dlaždice.|  
|[Návod: Ladění aplikace C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Vysvětluje, jak vytvářet a ladit aplikace, která používá paralelní snížení provede součet velké pole celých čísel.|  
  
## <a name="reference"></a>Odkaz  
 [Referenční dokumentace (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)  
  
 [tile_static Keyword](../../cpp/tile-static-keyword.md)  
  
 [restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)  
  
## <a name="other-resources"></a>Další zdroje  
 [Paralelní programování v blogu nativního kódu](http://go.microsoft.com/fwlink/p/?linkid=238472)  
  
 [Ukázkové projekty C++ AMP ke stažení](http://go.microsoft.com/fwlink/p/?linkid=248508)  
  
 [Analýza kódu C++ AMP s vizualizér souběžnosti](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)

