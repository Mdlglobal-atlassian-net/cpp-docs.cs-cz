---
title: 'Postupy: Použití transformace v datovém kanálu'
ms.date: 11/04/2016
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
ms.openlocfilehash: 59c4854eea985b3c91fad6e7dc6c47ca9b07d333
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375584"
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>Postupy: Použití transformace v datovém kanálu

Toto téma obsahuje základní příklad, který ukazuje způsob použití [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) třídy v datovém kanálu. Úplný příklad, který používá datový kanál provádět zpracování obrázků, naleznete v tématu [názorný postup: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

*Paralelní zpracování dat* je běžný vzor v souběžné programování. Datový kanál se skládá z několika fází, kde každé fázi provádí práci a pak předá do další fáze výsledků, které pracují. `transformer` Třídy klíčovou součástí datové kanály vzhledem k tomu, že přijímá vstupní hodnoty, provede práci na tuto hodnotu a potom vytvoří výsledek pro jiné komponenty se má použít.

## <a name="example"></a>Příklad

Tento příklad používá následující datového kanálu provádět řadu transformací zadaný počáteční vstupní hodnotu:

1. První fázi vypočítá absolutní hodnotu vstup.

1. Druhá fáze vypočítá druhou odmocninu jeho vstupu.

1. Třetí fází vypočítá druhou mocninu vstup.

1. Uvedené fáze Neguje vstup.

1. Konečný výsledek páté fázi zapíše do vyrovnávací paměti zpráv.

Nakonec příklad vytiskne výsledek kanálu ke konzole.

[!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]

Tento příklad vytvoří následující výstup:

```Output
The result is -42.
```

Je běžné pro fázi v datovém kanálu pro výstup hodnota, jejíž typ se liší od jeho vstupní hodnotu. V tomto příkladu druhá fáze přebírá hodnotu typu `int` jako vstup a vytvoří druhou odmocninu tuto hodnotu ( `double`) jako výstup.

> [!NOTE]
>  Datový kanál v tomto příkladu je pro ilustraci. Vzhledem k tomu, že každá operace transformace provádí mnoho zásahů, můžou převážit režie, který je požadovaný k provedení předávání zpráv nad výhodami pomocí datového kanálu.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `data-pipeline.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc data-pipeline.cpp**

## <a name="see-also"></a>Viz také:

[Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchronní bloky zpráv](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)
