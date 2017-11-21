---
title: "Návody k Concurrency Runtime | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- walkthroughs [Concurrency Runtime]
- Concurrency Runtime, walkthroughs
ms.assetid: 7374c5e9-54eb-44bf-9ed9-5e190cfd290b
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 42eae02b1eb789ea1333a8333e2f947457f87a41
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="concurrency-runtime-walkthroughs"></a>Návody k Concurrency Runtime
Na základě scénáře témata v této části ukazují použití mnoha funkcí Concurrency Runtime.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Návod: Připojení pomocí úloh a žádostí XML HTTP](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 Ukazuje, jak používat [IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908) a [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71) rozhraní společně s úkoly na odesílání žádostí HTTP GET a POST na webovou službu v [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace.  
  
 [Návod: Vytvoření aplikace založené na agentovi](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
 Popisuje, jak vytvořit základní aplikaci založené na agentovi.  
  
 [Návod: Vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)  
 Demonstruje postup vytvoření agenta na základě aplikací, které jsou založené na toku dat, místo na řízení toku.  
  
 [Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)  
 Ukazuje, jak vytvořit síť asynchronní bloky zpráv provádějící zpracování obrázků.  
  
 [Návod: Implementace tříd Future](../../parallel/concrt/walkthrough-implementing-futures.md)  
 Ukazuje, jak asynchronně vypočíst hodnoty pro pozdější použití.  
  
 [Návod: Použití metody join k zabránění vzájemnému zablokování](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)  
 Používá nabízet filosofů problém pro ilustraci použití [concurrency::join](../../parallel/concrt/reference/join-class.md) třídy, aby zablokování v aplikaci.  
  
 [Návod: Odstranění práce z vlákna uživatelského rozhraní](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)  
 Ukazuje, jak zlepšit výkon aplikace MFC, která nevykresluje fraktálový Mandelbrot.  
  
 [Návod: Použití Concurrency Runtime v aplikaci podporou modelu COM](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)  
 Demonstruje použití Concurrency Runtime v aplikaci, která se používá modelu COM (Component Object).  
  
 [Návod: Přizpůsobení stávajícího kódu pro použití prostých úloh](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)  
 Ukazuje, jak přizpůsobit existující kód, který používá rozhraní API systému Windows k vytvoření a provedení vlákno pro použití prostých úloh.  
  
 [Návod: Vytvoření vlastního bloku zpráv](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)  
 Popisuje, jak vytvořit vlastní zprávu typ bloku, který řadí příchozí zprávy podle priority.  
  
## <a name="related-sections"></a>Související oddíly  
 [Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)  
 Zavádí souběžných programovacím rozhraní pro Visual C++.

