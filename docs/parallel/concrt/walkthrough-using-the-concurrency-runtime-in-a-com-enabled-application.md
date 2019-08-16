---
title: 'Návod: Použití Concurrency Runtime v aplikaci s podporou modelu COM'
ms.date: 04/25/2019
helpviewer_keywords:
- Concurrency Runtime, use with COM
- COM, use with the Concurrency Runtime
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
ms.openlocfilehash: 23488522287ab5767c88cd3a3e90c09392634f46
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512097"
---
# <a name="walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application"></a>Návod: Použití Concurrency Runtime v aplikaci s podporou modelu COM

Tento dokument ukazuje, jak použít Concurrency Runtime v aplikaci, která používá model COM (Component Object Model).

## <a name="prerequisites"></a>Požadavky

Než začnete tento návod, přečtěte si následující dokumenty:

- [Paralelní úkoly](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)

- [Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)

- [Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)

Další informace o modelu COM naleznete v tématu [Component Object Model (com)](/windows/win32/com/component-object-model--com--portal).

## <a name="managing-the-lifetime-of-the-com-library"></a>Správa životního cyklu knihovny modelu COM

I když použití modelu COM s Concurrency Runtime se řídí stejnými principy jako u jakéhokoli jiného mechanismu souběžnosti, následující pokyny vám mohou posloužit k efektivnímu používání těchto knihoven.

- Vlákno musí volat [funkce CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) před tím, než použije knihovnu com.

- Vlákno může volat `CoInitializeEx` vícekrát, pokud poskytuje stejné argumenty pro každé volání.

- Pro každé volání `CoInitializeEx`musí vlákno volat také [CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize). Jinými slovy, volání `CoInitializeEx` a `CoUninitialize` musí být vyváženy.

- Chcete-li přepínat z jednoho vlákna Apartment na jiný, vlákno musí zcela uvolnit knihovnu com předtím, `CoInitializeEx` než bude volat s novou specifikací vláken.

Další principy modelu COM platí při použití modelu COM s Concurrency Runtime. Například aplikace, která vytvoří objekt v jednom vlákně Apartment (STA) a zařazování tohoto objektu do jiného typu apartment, musí také poskytnout smyčku zpráv pro zpracování příchozích zpráv. Nezapomeňte také, že zařazování objektů mezi objekty Apartment může snížit výkon.

### <a name="using-com-with-the-parallel-patterns-library"></a>Používání modelu COM s knihovnou PPL

Použijete-li model COM se součástí knihovny paralelních vzorů (PPL), například skupiny úloh nebo paralelního algoritmu, zavolejte `CoInitializeEx` před použitím knihovny COM během každého úkolu nebo iterace a zavolejte `CoUninitialize` před dokončením každého úkolu nebo iterace. . Následující příklad ukazuje, jak spravovat životnost knihovny modelu COM s objektem [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) .

[!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]

Je nutné zajistit, aby knihovna COM byla správně uvolněna při zrušení úlohy nebo paralelního algoritmu nebo když tělo úlohy vyvolá výjimku. Chcete-li zaručit, že `CoUninitialize` úloha před ukončením volá, `try-finally` použijte blok nebo RAII ( *pořízení prostředku* ). Následující příklad používá `try-finally` blok k uvolnění knihovny com, pokud je úloha dokončena nebo je zrušena nebo když je vyvolána výjimka.

[!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]

Následující příklad používá vzor RAII k definování `CCoInitializer` třídy, která spravuje životnost knihovny modelu COM v daném oboru.

[!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]

`CCoInitializer` Třídu můžete použít k automatickému uvolnění knihovny com při ukončení úlohy, a to následujícím způsobem.

[!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]

Další informace o zrušení v Concurrency Runtime najdete v části [zrušení v PPL](cancellation-in-the-ppl.md).

### <a name="using-com-with-asynchronous-agents"></a>Používání modelu COM s asynchronními agenty

Použijete-li com s asynchronními agenty, zavolejte `CoInitializeEx` před použitím knihovny COM v metodě [Concurrency:: Agent:: Run](reference/agent-class.md#run) pro vašeho agenta. Pak zavolejte `CoUninitialize` `run` před vrácením metody. Nepoužívejte rutiny správy modelu COM v konstruktoru nebo destruktoru vašeho agenta a nepřepisujte [Concurrency:: Agent:: Start](reference/agent-class.md#start) nebo [Concurrency:: Agent::d jednu z](reference/agent-class.md#done) těchto metod, protože tyto metody jsou volány z jiného vlákna než `run` metoda.

Následující příklad ukazuje základní třídu agenta s názvem `CCoAgent`, která spravuje knihovnu com `run` v metodě.

[!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]

Kompletní příklad najdete později v tomto návodu.

### <a name="using-com-with-lightweight-tasks"></a>Používání modelu COM s prostými úlohami

Dokument [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md) popisuje roli zjednodušených úloh v Concurrency Runtime. Model COM můžete použít s odlehčenou úlohou stejným způsobem jako u jakékoli rutiny vlákna, kterou předáte `CreateThread` do funkce v rozhraní API systému Windows. To je ukázáno v následujícím příkladu.

[!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]

## <a name="an-example-of-a-com-enabled-application"></a>Příklad aplikace s podporou modelu COM

V této části se zobrazuje kompletní aplikace s podporou modelu COM, `IScriptControl` která používá rozhraní ke spuštění skriptu, který počítá n-<sup>tý</sup> Fibonacci číslo. Tento příklad nejprve volá skript z hlavního vlákna a poté používá PPL a agenty pro volání skriptu souběžně.

Vezměte v úvahu následující pomocnou `RunScriptProcedure`funkci, která volá proceduru `IScriptControl` v objektu.

[!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]

Funkce vytvoří objekt, přidá do něj kód skriptu, který vypočítá `RunScriptProcedure` n-tý Fibonacci číslo, a potom zavolá funkci pro spuštění tohoto skriptu.<sup></sup> `wmain` `IScriptControl`

[!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]

### <a name="calling-the-script-from-the-ppl"></a>Volání skriptu z knihovny PPL

Následující funkce `ParallelFibonacci`používá algoritmus [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) k volání skriptu paralelně. Tato funkce používá `CCoInitializer` třídu ke správě životnosti knihovny modelu COM během každé iterace úlohy.

[!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]

Chcete-li `ParallelFibonacci` použít funkci s příkladem, přidejte následující kód `wmain` před vrácením funkce.

[!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]

### <a name="calling-the-script-from-an-agent"></a>Volání skriptu z agenta

Následující příklad ukazuje `FibonacciScriptAgent` třídu, která volá proceduru skriptu, aby vypočítala n-<sup>tý</sup> Fibonacci číslo. `FibonacciScriptAgent` Třída používá předávání zprávy z hlavního programu do funkce skriptu. `run` Metoda spravuje životnost knihovny COM v rámci úlohy.

[!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]

Následující funkce `AgentFibonacci`vytvoří několik `FibonacciScriptAgent` objektů a použije předávání zpráv k odeslání několika vstupních hodnot těmto objektům.

[!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]

Chcete-li `AgentFibonacci` použít funkci s příkladem, přidejte následující kód `wmain` před vrácením funkce.

[!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]

### <a name="the-complete-example"></a>Kompletní příklad

Následující kód ukazuje kompletní příklad, který používá paralelní algoritmy a asynchronní agenty k volání procedury skriptu, která vypočítá Fibonacci čísla.

[!code-cpp[concrt-parallel-scripts#14](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_14.cpp)]

Příklad vytvoří následující vzorový výstup.

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

Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo ho vložte do souboru s názvem `parallel-scripts.cpp` a potom spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

**CL. exe/EHsc Parallel-Scripts. cpp/Link Ole32. lib**

## <a name="see-also"></a>Viz také:

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Paralelní úkoly](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)<br/>
[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)
