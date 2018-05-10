---
title: Migrace z OpenMP do Concurrency Runtime | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 16e10287526e6b815ba56183a8e3d590102507aa
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>Migrace z OpenMP do Concurrency Runtime
Concurrency Runtime umožňuje celou řadu programovacích modelů. Tyto modely můžou překrývat nebo doplňují modely další knihovny. Dokumenty v této části porovnání [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp) do Concurrency Runtime a příklady o tom, jak migrovat existující kód OpenMP na využití modulu Concurrency Runtime.  
  
 Programovací model OpenMP je určené o otevřený standard a je dobře definovaný vazby na Fortran a C/C++ programovací jazyky. OpenMP verze 2.0 a 2.5, které jsou podporovány ve Visual C++ compiler, jsou vhodné pro paralelní algoritmy, které jsou iterativní; To znamená že provádět paralelní iterace přes pole dat. OpenMP 3.0 podporuje – iterativní úlohy kromě iterativní úlohy.  
  
 OpenMP je nejúčinnější, když stupně paralelního zpracování je předem určit a odpovídá dostupných prostředků systému. OpenMP model se zejména dobrý shodu vysoce výkonné výpočty, kde velké výpočetní problémy jsou rozmístěny v zpracování prostředků z jednoho počítače. V tomto scénáři je obecně pevná hardwarového prostředí a vývojář přiměřeně očekávat má výhradní přístup ke všem prostředkům výpočetní při algoritmus.  
  
 Však méně omezené výpočetních prostředí nemusí být funkční odpovídající OpenMP. Například jsou obtížné implementovat pomocí OpenMP 2.0 a 2.5 rekurzivní problémy (například algoritmus quicksort nebo vyhledávání stromu dat). Concurrency Runtime doplňuje tím, že poskytuje možnosti OpenMP [knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md) a [Parallel Library vzory](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). Knihovna asynchronních agentů podporuje hrubý paralelismus; knihovně PPL podporuje další podrobných paralelních úloh. Concurrency Runtime poskytuje infrastrukturu, která je nutná k provádění operací paralelně, aby se můžete soustředit na logice aplikace. Ale vzhledem k tomu Concurrency Runtime umožňuje celou řadu programovacích modelů, jeho plánování režie může být větší než jiné knihovny souběžnosti například OpenMP. Doporučujeme proto, že provedete test výkonu přírůstkově při převodu váš stávající kód OpenMP na využití modulu Concurrency Runtime.  
  
## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Při migraci z OpenMP do Concurrency Runtime  
 To může být výhodné k migraci existujícího kódu OpenMP na využití modulu Concurrency Runtime v následujících případech.  
  
|Případy|Výhody Concurrency Runtime|  
|-----------|-------------------------------------------|  
|Vyžadujete, aby rozšiřitelný rámec souběžné programování.|Mnoho funkcí v Concurrency Runtime lze rozšířit. Můžete také kombinovat stávajících funkcí, chcete-li vytvořit nové. Protože OpenMP závisí na direktivy kompilátoru, nelze snadno rozšířit.|  
|Aplikace by těžit z spolupráci blokování.|Pokud úloha zablokuje, protože vyžaduje na prostředek, který ještě není k dispozici, Concurrency Runtime můžete provádět další úlohy při první úloha čeká na prostředek.|  
|Aplikace by využívat dynamické vyrovnávání zatížení.|Concurrency Runtime používá plánování algoritmus, která se přizpůsobí přidělování výpočetních prostředků, jak změnit úlohy. V OpenMP když Plánovač přidělí výpočetních prostředků v paralelní oblasti, jsou tyto přidělení prostředků stanovená v rámci výpočet.|  
|Budete potřebovat podporu zpracování výjimek.|Knihovně PPL umožňuje zachytit výjimky uvnitř i mimo ni paralelní oblasti nebo smyčku. V OpenMP je nutné zpracovat výjimku uvnitř paralelní oblasti nebo smyčku.|  
|Vyžadujete, aby mechanismus zrušení.|Knihovně PPL umožňuje aplikacím zrušit individuální úlohy a paralelní stromy práce. OpenMP vyžaduje aplikaci implementovat vlastní mechanismus zrušení.|  
|Je potřeba dokončit v jiném kontextu, ze kterého začne paralelní kódu.|Concurrency Runtime umožňuje spuštění úlohy v jedné kontextu a potom počkejte, než nebo zrušit této úlohy v jiném kontextu. V OpenMP musíte dokončit všechny paralelní práce v kontextu, ze kterého začne.|  
|Budete potřebovat rozšířenou podporu ladění.|Visual Studio poskytuje **paralelní zásobníky** a **paralelních úloh** windows tak, aby můžete snadněji ladění vícevláknových aplikací.<br /><br /> Další informace o ladění podporu pro Concurrency Runtime najdete v tématu [používání okna úloh](/visualstudio/debugger/using-the-tasks-window), [použití okna paralelní zásobníky](/visualstudio/debugger/using-the-parallel-stacks-window), a [návod: ladění paralelní Aplikace](/visualstudio/debugger/walkthrough-debugging-a-parallel-application).|  
  
## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Když není při migraci z OpenMP do Concurrency Runtime  
 V následujících případech popisují při nemusí být vhodné pro migraci existujícího kódu OpenMP na využití modulu Concurrency Runtime.  
  
|Případy|Vysvětlení|  
|-----------|-----------------|  
|Aplikace již splňuje vaše požadavky.|Pokud budete spokojeni s výkonem aplikací a aktuální podporu ladění, nemusí být vhodný migrace.|  
|Vaše paralelní smyček málo práci.|Režii Plánovač úloh Concurrency Runtime nemusí předcházet výhody provádění těla smyčky paralelně, zejména v případě, že je poměrně malý těla smyčky.|  
|Aplikace je napsána v C.|Protože Concurrency Runtime používá mnoho funkcí C++, nemusí být vhodný při nelze psát kód, který umožňuje aplikaci C plně ho použít.|  
  
## <a name="related-topics"></a>Související témata  
 [Postupy: Převedení paralelní smyčky for v OpenMP na využití modulu Concurrency Runtime](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)  

 Danou smyčku základní, který používá OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) a [pro](../../parallel/openmp/reference/for-openmp.md) direktivy, ukazuje, jak převeďte ho na využití modulu Concurrency Runtime [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus.  

  
 [Postupy: Převedení smyčky OpenMP využívající zrušení na využití modulu Concurrency Runtime](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)  
 Vzhledem OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pro](../../parallel/openmp/reference/for-openmp.md) smyčky, který nevyžaduje všech iterací ke spuštění, ukazuje, jak převést ho na použití mechanismus zrušení Concurrency Runtime.  
  
 [Postupy: Převedení smyčky OpenMP využívající zpracování výjimek na využití modulu Concurrency Runtime](../../parallel/concrt/convert-an-openmp-loop-that uses-exception-handling.md)  
 Vzhledem OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pro](../../parallel/openmp/reference/for-openmp.md) smyčky, který provádí zpracování výjimek, ukazuje, jak převést ho na použití zpracování mechanismus výjimek Concurrency Runtime.  
  
 [Postupy: Převedení smyčky OpenMP využívající redukční proměnnou na využití modulu Concurrency Runtime](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)  
 Vzhledem OpenMP [paralelní](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pro](../../parallel/openmp/reference/for-openmp.md) smyčky, který používá [snížení](../../parallel/openmp/reference/reduction.md) klauzule, ukazuje, jak převeďte ho na využití modulu Concurrency Runtime.  
  
## <a name="see-also"></a>Viz také  
 [Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)   
 [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)   
 [Knihovna Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Knihovna asynchronních agentů](../../parallel/concrt/asynchronous-agents-library.md)

