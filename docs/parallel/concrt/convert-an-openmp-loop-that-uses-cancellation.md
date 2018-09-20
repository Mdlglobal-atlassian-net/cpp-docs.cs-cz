---
title: 'Postupy: převedení smyčky OpenMP využívající zrušení na využití modulu Concurrency Runtime | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3cb0d57edae11acd076a9be2bfed18ec2140bb7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373539"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>Postupy: Převedení smyčky OpenMP využívající zrušení na využití modulu Concurrency Runtime

Některé paralelních smyček nevyžadují provést všech iterací. Například algoritmus, který vyhledá hodnotu můžete ukončit po nalezení hodnoty. OpenMP – neposkytuje mechanismus pro přerušení mimo paralelní smyčky. Však můžete logickou hodnotu nebo příznak, pokud chcete povolit iteraci smyčky k označení, že byla nalezena řešení. Modul Concurrency Runtime poskytuje funkce, která umožňuje jednoho úkolu zrušit dalších úlohách, které ještě nebyly spuštěny.

Tento příklad ukazuje, jak převést OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pro](../../parallel/openmp/reference/for-openmp.md) smyčku, která nevyžaduje ke spuštění všech iterací použití mechanismu zrušení Concurrency Runtime.

## <a name="example"></a>Příklad

Tento příklad používá k implementaci paralelní verze OpenMP a modulu Runtime souběžnosti [std::any_of](../../standard-library/algorithm-functions.md#any_of) algoritmus. OpenMP – verze tohoto příkladu příznak, který používá ke koordinaci mezi všech iteracích paralelní smyčky, že byly splněny podmínky. Používá verzi, která používá modulu Runtime souběžnosti [Concurrency::structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) metoda zastaví celkovou operaci, pokud je splněna podmínka.

[!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]

Tento příklad vytvoří následující výstup.

```Output
Using OpenMP...
9114046 is in the array.
Using the Concurrency Runtime...
9114046 is in the array.
```

Ve verzi, který používá OpenMP všech iterací smyčky provést, i když je příznak nastaven. Kromě toho pokud mají všechny podřízené úkoly úlohy, příznak by také musí být k dispozici pro tyto podřízené úlohy ke komunikaci zrušení. V modulu Runtime souběžnosti při zrušení skupiny úloh, modul runtime zruší celý strom práci, včetně podřízených úloh. [: Concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus používá úkoly k provedení práce. Proto při jedné iterace smyčky zruší úlohu kořenové, celý strom výpočtu je také zrušeno. Při zrušení strom pracovní modul runtime nelze spustit nové úkoly. Modul runtime však umožňuje úlohy, které jste už začali dokončit. Proto v případě třídy `parallel_for_each` algoritmus, aktivní průchod cyklem můžete vyčistit své zdroje.

V obou verzích tohoto příkladu, pokud pole obsahuje více než jednu kopii hodnoty vyhledat, více iterací smyčky můžete každý současně nastaví výsledek a zrušit celkovou operaci. Synchronizace primitiv, můžete použít například kritický oddíl, pokud váš problém vyžaduje, že aby pouze jeden úkol provádí práci, když je splněna podmínka.

Můžete také použít zpracování výjimek pro zrušení úloh, které používají PPL. Další informace o zrušení naleznete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).

Další informace o `parallel_for_each` a jiné paralelní algoritmy, naleznete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `concrt-omp-parallel-any-of.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe/EHsc/OpenMP concrt-omp – paralelní any – of.cpp**

## <a name="see-also"></a>Viz také

[Migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)

