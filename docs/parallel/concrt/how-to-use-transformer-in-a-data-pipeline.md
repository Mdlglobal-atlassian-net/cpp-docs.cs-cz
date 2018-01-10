---
title: "Postupy: použití transformace v datovém kanálu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 76c8a50bd5a58d9fe6e4a68f05d9732e50fd04e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>Postupy: Použití transformace v datovém kanálu
Toto téma obsahuje základní příklad, který ukazuje způsob použití [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) – třída v datovém kanálu. Více kompletní příklad, který používá kanálu dat k provedení zpracování obrázků, najdete v části [návod: vytváření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
 *Paralelní zpracování dat* je běžný vzor v souběžné programování. Datový kanál se skládá z řady fázích, kde každá fáze provede práci a pak předá výsledek této práce do další fáze. `transformer` Třída klíčovou komponentou v datech kanálů, protože obdrží vstupní hodnotu, provede práci na tuto hodnotu a pak vytvoří výsledek pro jiné komponenty se má použít.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá následující kanálu dat k provedení řady transformací zadaný počáteční vstupní hodnotu:  
  
1.  První fázi vypočítá absolutní hodnotu vstupem.  
  
2.  Druhou fázi vypočítá druhou odmocninu čísla vstupem.  
  
3.  Třetí fází vypočítá druhou mocninu vstupem.  
  
4.  Stanovilo fáze Neguje vstupem.  
  
5.  Páté fázi zapíše do vyrovnávací paměti zpráv konečný výsledek.  
  
 V příkladu se nakonec vytiskne výsledek kanál ke konzole.  
  
 [!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]  
  
 Tento příklad vytvoří následující výstup:  
  
```Output  
The result is -42.  
```  
  
 Je běžné pro fázi v datovém kanálu výstup hodnota, jejíž typ se liší od vstupní hodnoty. V tomto příkladu druhé fázi přebírá hodnotu typu `int` jako vstup a vytvoří druhou odmocninu čísla tuto hodnotu ( `double`) jako výstup.  
  
> [!NOTE]
>  Datový kanál v tomto příkladu je pro obrázek. Protože každý operace transformace provede málo práce, můžete převažují režie tedy požadované k provedení předávání zpráv nad výhody použití datovém kanálu.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `data-pipeline.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc data-pipeline.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)   
 [Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)

