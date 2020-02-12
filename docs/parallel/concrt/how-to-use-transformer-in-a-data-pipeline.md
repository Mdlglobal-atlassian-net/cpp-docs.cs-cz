---
title: 'Postupy: Použití transformace v datovém kanálu'
ms.date: 11/04/2016
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
ms.openlocfilehash: c8cf1801d0262e3a2995d520604374ea22352fa0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141886"
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>Postupy: Použití transformace v datovém kanálu

Toto téma obsahuje základní příklad, který ukazuje, jak použít třídu [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) v datovém kanálu. Úplnější příklad, který používá datový kanál k provedení zpracování bitové kopie, naleznete v tématu [Návod: vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

*Datové kanály* jsou běžným vzorem v souběžném programování. Datový kanál se skládá z řady fází, kde každá fáze provádí práci a pak předá výsledek této práce do další fáze. `transformer` třída a klíčová komponenta v datových kanálech, protože přijímá vstupní hodnotu, provádí na této hodnotě práci a potom vytvoří výsledek pro použití jiné součásti.

## <a name="example"></a>Příklad

V tomto příkladu se pomocí následujícího datového kanálu provede řada transformací, které mají danou počáteční vstupní hodnotu:

1. První fáze vypočítá absolutní hodnotu jejího vstupu.

1. Druhá fáze vypočítá druhou odmocninu svého vstupu.

1. Třetí fáze vypočítá druhou mocninu svého vstupu.

1. V této fázi se zastavuje negace svého vstupu.

1. Pátá fáze zapíše konečný výsledek do vyrovnávací paměti zprávy.

Nakonec příklad vytiskne výsledek kanálu do konzoly.

[!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]

Tento příklad vytvoří následující výstup:

```Output
The result is -42.
```

Je běžné, že fáze v datovém kanálu má za následek výstup hodnoty, jejíž typ se liší od vstupní hodnoty. V tomto příkladu druhá fáze vezme hodnotu typu `int` jako svůj vstup a vytvoří druhou odmocninu této hodnoty (`double`) jako svůj výstup.

> [!NOTE]
> Datový kanál v tomto příkladu je určen pro ilustraci. Vzhledem k tomu, že každá operace transformace provádí menší práci, režie potřebná k provedení předání zprávy může převážit výhody používání datového kanálu.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `data-pipeline.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

> **CL. exe/EHsc data-Pipeline. cpp**

## <a name="see-also"></a>Viz také

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)
