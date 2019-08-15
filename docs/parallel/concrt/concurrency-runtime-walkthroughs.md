---
title: Návody k Concurrency Runtime
ms.date: 11/04/2016
helpviewer_keywords:
- walkthroughs [Concurrency Runtime]
- Concurrency Runtime, walkthroughs
ms.assetid: 7374c5e9-54eb-44bf-9ed9-5e190cfd290b
ms.openlocfilehash: 7c5973f8010d7c428406a8a3f69574eab20edf82
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512835"
---
# <a name="concurrency-runtime-walkthroughs"></a>Návody k Concurrency Runtime

Témata založená na scénáři v této části ukazují, jak používat mnoho funkcí Concurrency Runtime.

## <a name="in-this-section"></a>V tomto oddílu

[Návod: Připojení pomocí úloh a žádostí XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Ukazuje, jak používat rozhraní [IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2) a [IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback) spolu s úkoly k odesílání požadavků HTTP GET a post webové službě v aplikaci Univerzální platforma Windows (UWP).

[Návod: Vytvoření aplikace založené na agentovi](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
Popisuje, jak vytvořit základní aplikaci založenou na agentech.

[Návod: Vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
Ukazuje, jak vytvořit aplikace založené na agentech, které jsou založeny na toku dat, nikoli v toku řízení.

[Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
Ukazuje, jak vytvořit síť asynchronních bloků zpráv, které provádějí zpracování imagí.

[Návod: Implementace tříd future](../../parallel/concrt/walkthrough-implementing-futures.md)<br/>
Ukazuje, jak asynchronně vypočítat hodnoty pro pozdější použití.

[Návod: Použití metody join k zabránění vzájemnému zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)<br/>
Používá obědvajících problém stravování k ilustraci, jak použít třídu [Concurrency:: JOIN](../../parallel/concrt/reference/join-class.md) , abyste zabránili zablokování ve vaší aplikaci.

[Návod: Odebrání práce z vlákna uživatelského rozhraní](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
Ukazuje, jak zlepšit výkon aplikace MFC, která vykresluje Mandelbrot Fractal.

[Návod: Použití Concurrency Runtime v aplikaci s podporou modelu COM](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)<br/>
Ukazuje, jak používat Concurrency Runtime v aplikaci, která používá model COM (Component Object Model).

[Návod: Přizpůsobení stávajícího kódu pro použití prostých úloh](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)<br/>
Ukazuje, jak upravit existující kód, který používá rozhraní Windows API k vytvoření a spuštění vlákna pro použití zjednodušené úlohy.

[Návod: Vytvoření vlastního bloku zpráv](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)<br/>
Popisuje, jak vytvořit vlastní typ bloku zpráv, který vyřadí příchozí zprávy podle priority.

## <a name="related-sections"></a>Související oddíly

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
Zavádí souběžné programovací rozhraní pro Visual C++.
