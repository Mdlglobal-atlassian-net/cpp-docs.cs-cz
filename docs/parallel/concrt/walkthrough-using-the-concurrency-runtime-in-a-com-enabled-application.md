---
title: 'Návod: Použití Concurrency Runtime v aplikaci podporou modelu COM | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, use with COM
- COM, use with the Concurrency Runtime
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1fd9f665f77ca5ae5311b034ee7afef6241ac489
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692545"
---
# <a name="walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application"></a>Návod: Použití Concurrency Runtime v aplikaci s podporou modelu COM
Tento dokument ukazuje, jak používat Concurrency Runtime v aplikaci, která používá modelu COM (Component Object).  
  
## <a name="prerequisites"></a>Požadavky  
 Přečtěte si následující dokumenty, než začnete Tento názorný postup:  
  
- [Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
- [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)  
  
- [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)  
  
- [Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)  
  
 Další informace o modelu COM, najdete v části [modelu COM (Component Object)](http://msdn.microsoft.com/library/windows/desktop/ms680573).  
  
## <a name="managing-the-lifetime-of-the-com-library"></a>Správa životního cyklu knihovny modelu COM  
 I když použití COM s komponentou Concurrency Runtime řídí stejnými zásadami jako ostatní souběžnosti mechanismus, následující pokyny vám pomohou při používání těchto knihoven společně efektivně.  
  
-   Vlákno musí volat [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) předtím, než použije knihovny COM.  
  
-   Můžete volat vlákno `CoInitializeEx` několikrát, dokud poskytuje stejné argumenty pro každé volání.  
  
-   Pro každé volání `CoInitializeEx`, musíte také zavolat vlákno [CoUninitialize](http://msdn.microsoft.com/library/windows/desktop/ms688715). Jinými slovy, volá, aby se `CoInitializeEx` a `CoUninitialize` musí vyváženy.  
  
-   Přepnutí z objektu apartment jedno vlákno na jiný, vlákno musí zcela bez knihovny COM zavolá `CoInitializeEx` s novým dělení na vlákna specifikace.  
  
 Platí jiné zásady COM při použití modelu COM s komponentou Concurrency Runtime. Například aplikace, která vytvoří objekt single-threaded apartment (STA) a zařazuje do jiného objektu apartment tento objekt musíte taky zadat smyčku zprávu zpracovat příchozí zprávy. Nezapomeňte taky, že zařazování objektů mezi Apartment může snížit výkon.  
  
### <a name="using-com-with-the-parallel-patterns-library"></a>Používání modelu COM s knihovnou PPL  
 Při použití modelu COM pomocí součásti v paralelní vzory knihovna PPL (), například skupina úkolů nebo paralelní algoritmus volání `CoInitializeEx` dříve, než použijete knihovny COM během jednotlivých úloh nebo iterace a volání `CoUninitialize` před dokončení každé úlohy nebo iterace . Následující příklad ukazuje, jak spravovat dobu životnosti knihovnu COM s [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objektu.  
  
 [!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]  
  
 Musí se ujistěte, že je správně uvolněno knihovny COM při zrušení úloh nebo paralelní algoritmus, nebo když text úloh vyvolá výjimku. Chcete-li zaručit, že úloha volá `CoUninitialize` předtím, než se bude používat `try-finally` bloku nebo *prostředků pořízení je inicializace* vzoru (RAII). Následující příklad používá `try-finally` bloku na uvolnění knihovny COM, když dokončí úlohu nebo je zrušena, nebo když je vyvolána výjimka.  
  
 [!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]  
  
 Následující příklad používá k definování vzoru RAII `CCoInitializer` třída, která spravuje životnost knihovny COM v daném oboru.  
  
 [!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]  
  
 Můžete použít `CCoInitializer` třída automaticky uvolnit knihovny COM při ukončení úlohy, následujícím způsobem.  
  
 [!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]  
  
 Další informace o zrušení v Concurrency Runtime najdete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).  
  
### <a name="using-com-with-asynchronous-agents"></a>Používání modelu COM s asynchronními agenty  

 Pokud používáte COM s asynchronních agentů, volání `CoInitializeEx` dříve, než použijete knihovny COM v [concurrency::agent::run](reference/agent-class.md#run) metoda pro agenta. Potom zavolejte `CoUninitialize` před `run` metoda vrátí. Nepoužívejte rutiny správy COM v konstruktoru nebo destruktor agenta a přepsat [concurrency::agent::start](reference/agent-class.md#start) nebo [concurrency::agent:: provádí](reference/agent-class.md#done) metody vzhledem k tomu, že jsou tyto metody volá se z jiného vlákna než `run` metoda.  

  
 Následující příklad ukazuje třídu základní agenta s názvem `CCoAgent`, který spravuje knihovny COM v `run` metoda.  
  
 [!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]  
  
 Úplný příklad je k dispozici dále v tomto návodu.  
  
### <a name="using-com-with-lightweight-tasks"></a>Používání modelu COM s prostými úlohami  
 Dokument [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md) popisuje roli prosté úlohy v Concurrency Runtime. Prosté úlohy můžete použít COM, stejně jako s všechny rutiny přístup z více vláken, která je předat do `CreateThread` funkce v rozhraní API systému Windows. To je ukázáno v následujícím příkladu.  
  
 [!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]  
  
## <a name="an-example-of-a-com-enabled-application"></a>Příklad aplikace s podporou modelu COM  
 Tato část uvádí dokončení aplikace podporou modelu COM, která používá `IScriptControl` rozhraní pro spuštění skriptu, který vypočítá z n<sup>tý</sup> Fibonacciho číslo. Tento příklad nejprve volá skript z hlavního vlákna a pak použije PPL a agenty současně volat skript.  
  
 Vezměte v úvahu následující podpůrná funkce `RunScriptProcedure`, která volá proceduru `IScriptControl` objektu.  
  
 [!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]  
  
 `wmain` Funkce vytvoří `IScriptControl` objektu, přidá kód skriptu k němu, která vypočítá z n<sup>tý</sup> Fibonacciho číslo a poté zavolá `RunScriptProcedure` funkce ke spuštění skriptu.  
  
 [!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]  
  
### <a name="calling-the-script-from-the-ppl"></a>Volání skriptu z knihovny PPL  

 Následující funkce `ParallelFibonacci`, používá [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus volat skript paralelně. Tato funkce používá `CCoInitializer` třída spravovat dobu životnosti knihovny COM při každé iteraci úlohy.  

  
 [!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]  
  
 Použít `ParallelFibonacci` fungovat na příklad, přidejte následující kód, než `wmain` funkce vrátí.  
  
 [!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]  
  
### <a name="calling-the-script-from-an-agent"></a>Volání skriptu z agenta  
 Následující příklad ukazuje `FibonacciScriptAgent` třídy, která volá skript postup výpočetní z n<sup>tý</sup> Fibonacciho číslo. `FibonacciScriptAgent` Třída používá zpráva předávání přijímat z hlavní aplikace, zadejte hodnoty pro funkci skriptu. `run` Metoda spravuje životnost knihovny COM v rámci úlohy.  
  
 [!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]  
  
 Následující funkce `AgentFibonacci`, vytvoří několik `FibonacciScriptAgent` objekty a používá zpráva předávání odeslat několik vstupní hodnoty k těmto objektům.  
  
 [!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]  
  
 Použít `AgentFibonacci` fungovat na příklad, přidejte následující kód, než `wmain` funkce vrátí.  
  
 [!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]  
  
### <a name="the-complete-example"></a>Kompletní příklad  
 Následující kód ukazuje dokončení příkladu, který používá paralelní algoritmy a asynchronních agentů k volání procedury skriptu, která vypočítá Fibonacciho čísla.  
  
 [!code-cpp[concrt-parallel-scripts#14](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_14.cpp)]  
  
 Tento příklad vytvoří následující ukázkový výstup.  
  
```Output  
Main Thread:  
fib(15) = 610  
 
Parallel Fibonacci:  
fib(15) = 610  
fib(10) = 55  
fib(16) = 987  
fib(18) = 2584  
fib(11) = 89  
fib(17) = 1597  
fib(19) = 4181  
fib(12) = 144  
fib(13) = 233  
fib(14) = 377  
 
Agent Fibonacci:  
fib(30) = 832040  
fib(22) = 17711  
fib(10) = 55  
fib(12) = 144  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `parallel-scripts.cpp` a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 **cl.exe /EHsc/Link paralelní scripts.cpp ole32.lib**  
  
## <a name="see-also"></a>Viz také  
 [Návody k Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)   
 [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)   
 [Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Zrušení v knihovně PPL](cancellation-in-the-ppl.md)   
 [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)

