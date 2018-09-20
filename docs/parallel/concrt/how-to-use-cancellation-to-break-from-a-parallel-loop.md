---
title: 'Postupy: přerušení paralelní smyčky pomocí zrušení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9172132f0bdaabea9d6959a3f947d7b50d5261da
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417329"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>Postupy: Přerušení paralelní smyčky pomocí zrušení

Tento příklad ukazuje způsob použití zrušení k implementaci základní paralelního vyhledávacího algoritmu.

## <a name="example"></a>Příklad

Následující příklad používá zrušení vyhledat prvek v poli. `parallel_find_any` Funkce používá [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus a [concurrency::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) funkce pro hledání pozice, který obsahuje zadanou hodnotu. Paralelní smyčka najde hodnotu, volá [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) metoda zrušit budoucí práci.

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

[Concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus funguje souběžně. Proto se neprovádí operace v předem určeném pořadí. Pokud pole obsahuje více instancí hodnotu, výsledek může být jedna z jeho pozice.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `parallel-array-search.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc paralelní pole search.cpp**

## <a name="see-also"></a>Viz také

[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for – funkce](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source – třída](../../parallel/concrt/reference/cancellation-token-source-class.md)
