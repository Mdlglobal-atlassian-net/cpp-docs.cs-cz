---
title: "Postupy: použití filtru bloku zpráv | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- message-block filters, using [Concurrency Runtime]
- using message-block filters [Concurrency Runtime]
ms.assetid: db6b99fb-288d-4477-96dc-b9751772ebb2
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 48649931d20d344e724bd0d3ae7c64a43caa9549
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-use-a-message-block-filter"></a>Postupy: Použití filtru bloku zpráv
Tento dokument ukazuje, jak používat funkce filtru pro povolení bloku asynchronní zpráva k přijetí nebo odmítnutí zprávu na základě datovou část zprávy.  
  
 Když vytvoříte objekt bloku zpráv, jako [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), [concurrency::call](../../parallel/concrt/reference/call-class.md), nebo [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md), můžete zadat *filtrovat funkce* který určuje, zda blok zprávu přijme nebo odmítne zprávy. Funkce filtru je užitečný způsob, jak zajistit, že blok zpráv přijímá jenom určité hodnoty.  
  
 Funkce filtru jsou důležité, protože umožňují vám umožní připojit se bloky zpráv do formuláře *toku dat sítě*. Bloky zpráv v síti toku dat, řízení toku dat zpracováním pouze zprávy, které splňují určitá kritéria. Výsledky porovnejte s modelem tok řízení, které je řídí tok dat pomocí řídicí struktury například podmíněné příkazy, smyčky a tak dále.  
  
 Tento dokument obsahuje základních příkladů použití filtru zpráv. Další příklady, které používají filtry zpráv a model toku dat pro připojení bloky zpráv najdete v tématu [návod: vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md) a [návod: vytváření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md) .  
  
## <a name="example"></a>Příklad  
 Vezměte v úvahu následující funkce `count_primes`, který ukazuje základní použití bloku zpráv, který nefiltruje příchozí zprávy. Blok zpráv připojí prvočísel k [std::vector](../../standard-library/vector-class.md) objektu. `count_primes` Funkce odešle několik čísla do bloku zpráv, obdrží hodnoty výstup z bloku zpráv a vytiskne tato čísla, která jsou prime ke konzole.  
  
 [!code-cpp[concrt-primes-filter#1](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_1.cpp)]  
  
 `transformer` Objekt zpracovává všechny vstupní hodnoty; však vyžaduje pouze hodnoty, které jsou prime. I když se aplikace, může být napsaná tak, aby odesílatele zprávy odesílá pouze prvočísel, nemůže být známé vždy požadavky příjemce zprávy.  
  
## <a name="example"></a>Příklad  
 Následující funkce `count_primes_filter`, provádí stejnou úlohu, jako `count_primes` funkce. Ale `transformer` objektu v této verzi používá funkci filtru tak, aby přijímal pouze hodnoty, které jsou prime. Funkce, která provede akci pouze obdrží prvočísel; proto nemá k volání `is_prime` funkce.  
  
 Protože `transformer` objekt přijímá pouze prvočísel, `transformer` samotného objektu mohou být uloženy prvočísel. Jinými slovy `transformer` objekt v tomto příkladu není potřeba přidat prime čísla, která `vector` objektu.  
  
 [!code-cpp[concrt-primes-filter#2](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_2.cpp)]  
  
 `transformer` Objekt nyní zpracovává pouze hodnoty, které jsou prime. V předchozím příkladu `transformer` objekt zpracovává všechny zprávy. Předchozí příklad proto musí obdržet stejný počet zpráv, které odešle. Tento příklad používá výsledek [concurrency::send](reference/concurrency-namespace-functions.md#send) funkce k určení, kolik zpráv přijímat z `transformer` objektu. `send` Funkce vrátí `true` když vyrovnávací paměť zprávy přijme zprávu a `false` při vyrovnávací paměť zprávy odmítne zprávy. Počet pokusů, že vyrovnávací paměť zprávy přijímá zprávy proto odpovídá počet prvočísel.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje kompletní příklad. V příkladu volá i `count_primes` funkce a `count_primes_filter` funkce.  
  
 [!code-cpp[concrt-primes-filter#3](../../parallel/concrt/codesnippet/cpp/how-to-use-a-message-block-filter_3.cpp)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `primes-filter.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc si mosty filter.cpp**  
  
## <a name="robust-programming"></a>Robustní programování  
 Funkce filtru může být funkce lambda, ukazatel na funkci nebo funkce objektu. Každé funkce filtru má jednu z následujících podob:  
  
```Output  
bool (T)  
bool (T const &)  
```  
  
 K vyloučení nepotřebných kopírování dat, použijte druhý formulář, jestliže se agregační typu, která se přenášejí hodnotou.  
  
## <a name="see-also"></a>Viz také  
 [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)   
 [Návod: Vytvoření agenta toku dat](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)   
 [Návod: Vytvoření sítě pro zpracování obrázků](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [Třída Transformer](../../parallel/concrt/reference/transformer-class.md)
