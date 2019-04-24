---
title: Návody k Concurrency Runtime
ms.date: 11/04/2016
helpviewer_keywords:
- walkthroughs [Concurrency Runtime]
- Concurrency Runtime, walkthroughs
ms.assetid: 7374c5e9-54eb-44bf-9ed9-5e190cfd290b
ms.openlocfilehash: d176049bb3b03ae0f55170e45e20e7c2c0e322ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296487"
---
# <a name="concurrency-runtime-walkthroughs"></a>Návody k Concurrency Runtime

Založené na scénářích témata v této části ukazují použití mnoha funkcí modulu Runtime souběžnosti.

## <a name="in-this-section"></a>V tomto oddílu

[Návod: Připojení pomocí úloh a žádostí XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Ukazuje způsob použití [IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2) a [IXMLHTTPRequest2Callback](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2callback) spolu s úkoly odesílajícími požadavky HTTP GET a POST na webovou službu v aplikaci pro univerzální platformu Windows (UPW).

[Návod: Vytvoření aplikace založené na agentovi](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
Popisuje, jak vytvořit základní aplikaci založené na agentovi.

[Návod: Vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
Ukazuje, jak vytvářet aplikace pro systém agenta, které jsou založeny na toku dat, místo v toku řízení.

[Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
Ukazuje, jak vytvořit síť asynchronní bloky zpráv, které provádějí zpracování obrázků.

[Návod: Implementace tříd future](../../parallel/concrt/walkthrough-implementing-futures.md)<br/>
Ukazuje, jak asynchronně vypočíst hodnoty pro pozdější použití.

[Návod: Použití metody join k zabránění vzájemnému zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)<br/>
Problém obědvajících filozofů využívá pro ilustraci použití [concurrency::join](../../parallel/concrt/reference/join-class.md) třídy, aby se zabránilo zablokování v aplikaci.

[Návod: Odebrání práce z vlákna uživatelského rozhraní](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
Ukazuje, jak zvýšit výkon, který vykreslí fraktálový Mandelbrot aplikace knihovny MFC.

[Návod: Použití Concurrency Runtime v aplikaci s podporou modelu COM](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)<br/>
Popisuje způsob použití Concurrency Runtime v aplikaci, která se používá modelu COM (Component Object).

[Návod: Přizpůsobení stávajícího kódu pro použití prostých úloh](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)<br/>
Ukazuje, jak přizpůsobit existující kód, který používá rozhraní Windows API k vytvoření a spuštění vlákna používal prostou úlohu.

[Návod: Vytvoření vlastního bloku zpráv](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)<br/>
Popisuje, jak vytvořit typ bloku vlastní zprávy, který řadí příchozích zprávy podle priority.

## <a name="related-sections"></a>Související oddíly

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
Představuje souběžnému programovacímu pro Visual C++.
