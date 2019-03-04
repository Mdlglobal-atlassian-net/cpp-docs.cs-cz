---
title: 'Návod: Použití modulu Runtime souběžnosti v aplikaci s podporou modelu COM'
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, use with COM
- COM, use with the Concurrency Runtime
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
ms.openlocfilehash: 9d306377be4a000c54fb5556b15263a15b2d4618
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278194"
---
# <a name="walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application"></a>Návod: Použití modulu Runtime souběžnosti v aplikaci s podporou modelu COM

Tento dokument popisuje způsob použití Concurrency Runtime v aplikaci, která se používá modelu COM (Component Object).

## <a name="prerequisites"></a>Požadavky

Před zahájením tohoto návodu, přečtěte si následující dokumenty:

- [Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)

- [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)

- [Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)

Další informace o modelu COM naleznete v tématu [modelu COM (Component Object)](/windows/desktop/com/component-object-model--com--portal).

## <a name="managing-the-lifetime-of-the-com-library"></a>Správa životního cyklu knihovny modelu COM

I když využívání modelu COM s modulem Runtime souběžnost ale řídí stejnými Principy jako ostatní mechanismu pro souběžnost, následující pokyny vám umožňují tyto knihovny společně efektivně používat.

- Vlákno musí volat [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex) před používá knihovnu COM.

- Vlákno může volat `CoInitializeEx` více než jednou za předpokladu, poskytuje stejné argumenty, které mají všechna volání.

- Pro každé volání `CoInitializeEx`, musíte také zavolat vlákno [CoUninitialize](/windows/desktop/api/combaseapi/nf-combaseapi-couninitialize). Jinými slovy, volání `CoInitializeEx` a `CoUninitialize` musí vyváženy.

- Přejděte z objektu apartment pro jedno vlákno do jiného vlákna musí zcela zdarma knihovny COM před voláním `CoInitializeEx` pomocí nového vlákna specifikace.

Další COM zásady platí i při použití modelu COM s modulem Runtime souběžnost. Například aplikace, která vytvoří objekt v jednovláknový apartment (STA) a zařadí tohoto objektu do jiného objektu apartment rovněž nutné poskytnout smyčky zpráv pro zpracování příchozích zpráv. Nezapomeňte taky, že zařazování objektů mezi objekty apartment může snížit výkon.

### <a name="using-com-with-the-parallel-patterns-library"></a>Používání modelu COM s knihovnou PPL

Při použití modelu COM s komponentou v paralelních vzorů knihovny (PPL), například na skupinu úloh nebo paralelního algoritmu, volání `CoInitializeEx` před použitím knihovny COM během každý úkol nebo iteraci a volání `CoUninitialize` před dokončením každý úkol nebo iterace . Následující příklad ukazuje, jak Správa životního cyklu knihovny modelu COM s [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objektu.

[!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]

Ujistěte se, že je správně uvolněn knihovny COM při zrušení úkolu nebo paralelní algoritmus, nebo pokud tělo úkolu vyvolá výjimku. Zaručit, že úloha volání `CoUninitialize` před jejím ukončení použijte `try-finally` bloku nebo *získání prostředků je inicializace* vzorek (RAII). Následující příklad používá `try-finally` bloku knihovny modelu COM uvolnit, když úloha dokončena nebo je zrušena, nebo když dojde k výjimce.

[!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]

Následující příklad používá vzor RAII pro definování `CCoInitializer` třídu, která spravuje životnost knihovny modelu COM v daném oboru.

[!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]

Můžete použít `CCoInitializer` třídy automaticky uvolnění knihovny COM při ukončení úkolu, následujícím způsobem.

[!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]

Další informace o zrušení v modulu Runtime souběžnosti, naleznete v tématu [zrušení v knihovně PPL](cancellation-in-the-ppl.md).

### <a name="using-com-with-asynchronous-agents"></a>Používání modelu COM s asynchronními agenty

Při použití modelu COM s asynchronními agenty volání `CoInitializeEx` před použitím knihovny modelu COM [concurrency::agent::run](reference/agent-class.md#run) metodu pro agenta. Poté zavolejte `CoUninitialize` před `run` metoda vrátí hodnotu. Nepoužívejte rutiny správy modelu COM v konstruktoru nebo destruktoru vašeho agenta a nesmí být přepsána [concurrency::agent::start](reference/agent-class.md#start) nebo [concurrency::agent:: provádí](reference/agent-class.md#done) metody vzhledem k tomu, že tyto metody jsou volat z jiného vlákna než `run` metody.

Následující příklad ukazuje základní agenta třídu s názvem `CCoAgent`, která spravuje knihovny modelu COM `run` metody.

[!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]

Kompletní příklad je k dispozici později v tomto názorném postupu.

### <a name="using-com-with-lightweight-tasks"></a>Používání modelu COM s prostými úlohami

Dokument [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md) popisuje využití jednoduché úlohy v modulu Runtime souběžnosti. Můžete použít modelu COM s lehký úkol, stejně jako při použití jakékoli vlákno rutiny, můžete předat `CreateThread` funkce v rozhraní Windows API. To je ukázáno v následujícím příkladu.

[!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]

## <a name="an-example-of-a-com-enabled-application"></a>Příklad aplikace s podporou modelu COM

Tato část ukazuje kompletní aplikaci podporou modelu COM, který používá `IScriptControl` rozhraní ke spuštění skriptu, který vypočítává n<sup>th</sup> Fibonacciho číslo. V tomto příkladu první volání skriptu z hlavního vlákna a potom použije PPL a agentů k volání skriptu současně.

Vezměte v úvahu následující pomocná funkce, `RunScriptProcedure`, která proceduru volá `IScriptControl` objektu.

[!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]

`wmain` Funkce vytvoří `IScriptControl` objekt, přidá kód skriptu, který vypočítá n<sup>th</sup> Fibonacciho číslo a poté zavolá `RunScriptProcedure` funkce ke spuštění tohoto skriptu.

[!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]

### <a name="calling-the-script-from-the-ppl"></a>Volání skriptu z knihovny PPL

Následující funkce `ParallelFibonacci`, používá [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmus pro volání skriptu paralelně. Tato funkce využívá `CCoInitializer` třídy pro správu životního cyklu knihovny modelu COM při každé iteraci cyklu úkolu.

[!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]

Použít `ParallelFibonacci` pracovat v příkladu, přidejte následující kód před `wmain` vrací funkce.

[!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]

### <a name="calling-the-script-from-an-agent"></a>Volání skriptu z agenta

Následující příklad ukazuje `FibonacciScriptAgent` třída, která volá proceduru skript k výpočtu n<sup>th</sup> Fibonacciho číslo. `FibonacciScriptAgent` Třída používá zprávy předávání pro příjem z hlavního programu, zadejte hodnoty do funkce skriptu. `run` Spravuje životního cyklu knihovny modelu COM v rámci úlohy.

[!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]

Následující funkce `AgentFibonacci`, vytvoří několik `FibonacciScriptAgent` objekty a používá předávání odesílat několik vstupní hodnoty na tyto objekty zprávy.

[!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]

Použít `AgentFibonacci` pracovat v příkladu, přidejte následující kód před `wmain` vrací funkce.

[!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]

### <a name="the-complete-example"></a>Kompletní příklad

Následující kód ukazuje úplný příklad, který používá paralelní algoritmy a asynchronních agentů k volání skriptu procedury, která vypočítá Fibonacciho čísla.

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

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `parallel-scripts.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

**cl.exe /EHsc parallel-scripts.cpp /link ole32.lib**

## <a name="see-also"></a>Viz také:

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Funkční paralelismus](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)<br/>
[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)
