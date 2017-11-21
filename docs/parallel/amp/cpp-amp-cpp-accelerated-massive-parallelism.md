---
title: C++ AMP (C++ Accelerated Massive Parallelism) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 23d93972bf077febe8497ad539ccd62ea372a384
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)
C++ AMP (C++ Accelerated Massive Parallelism) zrychluje provádění kódu C++ a využívají data paralelní hardware, který se obvykle nachází jako grafický procesor (GPU) na kartě diskrétní grafiky. Programovací model C++ AMP zahrnuje podporu pro vícerozměrná pole, indexování, přenos paměti a dlaždice. Zahrnuje taky knihovny matematické funkce. Můžete použít k řízení, jak přesunout data z procesoru na grafický procesor s rozšíření jazyka C++ AMP a zpět.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Přehled produktu C++ AMP](../../parallel/amp/cpp-amp-overview.md)|Popisuje klíčové funkce C++ AMP a matematickém knihovny.|  
|[Pomocí Lambdas, objektů funkcí a omezených funkcí](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Popisuje způsob použití výrazů lambda, objektů funkcí a omezených funkcí ve voláních [parallel_for_each –](reference/concurrency-namespace-functions-amp.md#parallel_for_each) metoda.|  
|[Pomocí dlaždice](../../parallel/amp/using-tiles.md)|Popisuje, jak zrychlit kódu C++ AMP pomocí dlaždice.|  
|[Používání akcelerátoru a objektů accelerator_view](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Popisuje, jak použít akcelerátorů k přizpůsobení provádění kódu na GPU.|  
|[Používání modelu C++ AMP v aplikacích pro Windows Store](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Popisuje způsob použití C++ AMP v [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace, které používají typy prostředí Windows Runtime.|  
|[Grafika (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Popisuje, jak na používání knihovny, C++ AMP grafiky.|  
|[Návod: Násobení matic](../../parallel/amp/walkthrough-matrix-multiplication.md)|Demonstruje násobení matic pomocí kódu C++ AMP a dlaždice.|  
|[Návod: Ladění aplikace C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Vysvětluje, jak vytvářet a ladit aplikace, která používá paralelní snížení provede součet velké pole celých čísel.|  
  
## <a name="reference"></a>Odkaz  
 [Referenční dokumentace (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)  
  
 [tile_static – klíčové slovo](../../cpp/tile-static-keyword.md)  
  
 [omezení (C++ AMP)](../../cpp/restrict-cpp-amp.md)  
  
## <a name="other-resources"></a>Další zdroje  
 [Paralelní programování v blogu nativního kódu](http://go.microsoft.com/fwlink/p/linkid=238472)  
  
 [Ukázkové projekty C++ AMP ke stažení](http://go.microsoft.com/fwlink/p/linkid=248508)  
  
 [Analýza kódu C++ AMP s vizualizér souběžnosti](http://go.microsoft.com/fwlink/linkid=253987&clcid=0x409)

