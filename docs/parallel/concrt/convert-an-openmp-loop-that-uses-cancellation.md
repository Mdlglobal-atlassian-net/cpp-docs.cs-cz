---
title: 'Postupy: převedení smyčky OpenMP využívající zrušení na využití modulu Concurrency Runtime | Microsoft Docs'
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
ms.openlocfilehash: 9dae22a46d6570d7ef7abbdfc08cb2c6d76d0c08
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693260"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>Postupy: Převedení smyčky OpenMP využívající zrušení na využití modulu Concurrency Runtime
Některé paralelní smyčky nevyžadují provést všech iterací. Například můžete algoritmu, který hledá hodnotu ukončit po nalezení hodnota. OpenMP neposkytuje mechanismus pro přerušení mimo paralelní smyčky. Však můžete logickou hodnotu, nebo příznak, chcete-li povolit iterace smyčky indikující, že byl nalezen řešení. Concurrency Runtime poskytuje funkce, která umožňuje jednu úlohu zrušit dalších úlohách, které nebyly ještě nezačala.  
  
 Tento příklad ukazuje, jak převést OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pro](../../parallel/openmp/reference/for-openmp.md) smyčky, který nevyžaduje všech iterací ke spuštění používat mechanismy zrušení Concurrency Runtime.  
  
## <a name="example"></a>Příklad  

 Tento příklad používá k implementaci paralelní verzi OpenMP i Concurrency Runtime [std::any_of](../../standard-library/algorithm-functions.md#any_of) algoritmus. OpenMP verzi v tomto příkladu používá příznak ke koordinaci mezi všech iterací paralelní smyčky splnění podmínky. Používá verzi, která používá Concurrency Runtime [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) metoda zastavit celou operaci, když je splněna podmínka.  

  
 [!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]  
  
 Tento příklad vytvoří následující výstup.  
  
```Output  
Using OpenMP...  
9114046 is in the array.  
Using the Concurrency Runtime...  
9114046 is in the array.  
```  
  
 Ve verzi této používá OpenMP všechny iterace smyčky provést, i když je nastavený příznak. Kromě toho pokud úloha měla mít žádné podřízené úlohy, příznak by také mají být k dispozici pro tyto podřízené úlohy ke komunikaci zrušení. V Concurrency Runtime když byla zrušena, skupinu úloh, modul runtime zruší celý strom práce včetně podřízené úlohy. [Concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algoritmus používá úloh pro práci. Proto když jeden iteraci smyčky zruší úlohu kořenové, celý strom výpočtu je také zrušena. Když byla zrušena stromu práce, modul runtime nespustí nové úkoly. Modul runtime však umožňuje úlohy, které už začali dokončit. Proto u `parallel_for_each` algoritmus, iterací active smyčky můžete vyčistit jejich prostředky.  
  
 V obou verzích tohoto příkladu, pokud pole obsahuje více než jednu kopii hledanou hodnotu, více iterace smyčky můžete každý současně nastaví výsledek a zrušte celou operaci. Synchronizace primitivní, můžete použít například důležitý oddíl, pokud váš problém vyžaduje, že aby pouze jeden úkol provede práci, když je splněna podmínka.  
  
 Můžete použít také k zrušení úloh, které používají knihovně PPL zpracování výjimek. Další informace o zrušení najdete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).  
  
 Další informace o `parallel_for_each` a dalších paralelní algoritmy najdete v tématu [paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `concrt-omp-parallel-any-of.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc/OpenMP concrt-omp – paralelní any-of.cpp**  
  
## <a name="see-also"></a>Viz také  
 [Migrace z OpenMP do Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [Zrušení v knihovně PPL](cancellation-in-the-ppl.md)   
 [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)

