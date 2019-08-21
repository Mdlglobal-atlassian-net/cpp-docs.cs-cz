---
title: 'Postupy: Převést smyčku OpenMP, která používá zrušení k použití Concurrency Runtime'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
ms.openlocfilehash: df55a58617b802f24e4caf13784ac080222b93bc
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631532"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>Postupy: Převést smyčku OpenMP, která používá zrušení k použití Concurrency Runtime

Některé paralelní smyčky nevyžadují, aby byly provedeny všechny iterace. Například algoritmus, který vyhledává hodnotu, může skončit po nalezení hodnoty. OpenMP neposkytuje mechanismus pro přerušení paralelní smyčky. Můžete však použít logickou hodnotu nebo příznak pro povolení iterace smyčky, která označuje, že řešení bylo nalezeno. Concurrency Runtime poskytuje funkce, které umožňují, aby jedna úloha zrušila jiné úlohy, které ještě nebyly spuštěny.

Tento příklad ukazuje, jak převést [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)metodu OpenMP[pro](../../parallel/openmp/reference/for-openmp.md) smyčku, která nevyžaduje, aby všechny iterace běžely k použití mechanismu Concurrency Runtime zrušení.

## <a name="example"></a>Příklad

V tomto příkladu je použita direktiva OpenMP i Concurrency Runtime k implementaci paralelní verze algoritmu [std:: any_of](../../standard-library/algorithm-functions.md#any_of) . Verze OpenMP v tomto příkladu používá příznak ke koordinaci mezi všemi cykly paralelní smyčky, u kterých byla podmínka splněna. Verze, která používá Concurrency Runtime, používá metodu [Concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) k zastavení celkové operace, pokud je splněna podmínka.

[!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Using OpenMP...
9114046 is in the array.
Using the Concurrency Runtime...
9114046 is in the array.
```

Ve verzi nástroje, která používá OpenMP, se spustí všechny iterace smyčky, a to i v případě, že je nastaven příznak. Kromě toho, pokud by měl úkol mít jakékoli podřízené úlohy, příznak by měl být také k dispozici pro tyto podřízené úlohy pro účely sdělení zrušení. V Concurrency Runtime při zrušení skupiny úloh modul runtime zruší celý strom práce, včetně podřízených úloh. [Arallel_for_each algoritmus concurrency::p](reference/concurrency-namespace-functions.md#parallel_for_each) používá úkoly k provedení práce. Proto když jedna iterace smyčky zruší kořenovou úlohu, celý strom výpočtu se také zruší. Když je strom práce zrušen, modul runtime nespustí nové úlohy. Modul runtime však umožňuje dokončení úloh, které již byly zahájeny. V případě `parallel_for_each` algoritmu proto mohou iterace aktivní smyčky vyčistit své prostředky.

V obou verzích tohoto příkladu, pokud pole obsahuje více než jednu kopii hledané hodnoty, může každá iterace smyčky každý současně nastavit výsledek a zrušit celkovou operaci. Můžete použít primitivní prostředí synchronizace, jako je například kritická část, pokud váš problém vyžaduje, aby při splnění podmínky prováděla práci pouze jedna úloha.

Zpracování výjimek lze také použít k zrušení úloh, které používají PPL. Další informace o zrušení naleznete v tématu [zrušení v PPL](cancellation-in-the-ppl.md).

Další informace o `parallel_for_each` a dalších paralelních algoritmech naleznete v tématu [Parallel](../../parallel/concrt/parallel-algorithms.md)Algorithms.

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `concrt-omp-parallel-any-of.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

**cl.exe /EHsc /openmp concrt-omp-parallel-any-of.cpp**

## <a name="see-also"></a>Viz také:

[Migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)
