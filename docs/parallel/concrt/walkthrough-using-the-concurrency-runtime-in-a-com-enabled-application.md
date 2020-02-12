---
title: 'Návod: Použití Concurrency Runtime v aplikaci s podporou modelu COM'
ms.date: 04/25/2019
helpviewer_keywords:
- Concurrency Runtime, use with COM
- COM, use with the Concurrency Runtime
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
ms.openlocfilehash: faa072ab2b5973ace0f0ca138dcedffa56044213
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140625"
---
# <a name="walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application"></a>Návod: Použití Concurrency Runtime v aplikaci s podporou modelu COM

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

- Vlákno může volat `CoInitializeEx` víckrát, pokud poskytuje stejné argumenty pro každé volání.

- Pro každé volání `CoInitializeEx`musí vlákno volat také [CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize). Jinými slovy, volání `CoInitializeEx` a `CoUninitialize` musí být vyváženy.

- Chcete-li přepínat z jednoho vlákna Apartment na jiný, vlákno musí zcela uvolnit knihovnu COM před voláním `CoInitializeEx` s novou specifikací vláken.

Další principy modelu COM platí při použití modelu COM s Concurrency Runtime. Například aplikace, která vytvoří objekt v jednom vlákně Apartment (STA) a zařazování tohoto objektu do jiného typu apartment, musí také poskytnout smyčku zpráv pro zpracování příchozích zpráv. Nezapomeňte také, že zařazování objektů mezi objekty Apartment může snížit výkon.

### <a name="using-com-with-the-parallel-patterns-library"></a>Používání modelu COM s knihovnou PPL

Použijete-li model COM se součástí knihovny paralelních vzorů (PPL), například skupinu úloh nebo paralelní algoritmus, zavolejte `CoInitializeEx` před použitím knihovny COM během každého úkolu nebo iterace a zavolejte `CoUninitialize` před dokončením každého úkolu nebo iterace. Následující příklad ukazuje, jak spravovat životnost knihovny modelu COM s objektem [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) .

[!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]

Je nutné zajistit, aby knihovna COM byla správně uvolněna při zrušení úlohy nebo paralelního algoritmu nebo když tělo úlohy vyvolá výjimku. Chcete-li zaručit, že úloha před ukončením `CoUninitialize` volá, použijte blok `try-finally` nebo RAII ( *pořízení prostředku* ). Následující příklad používá blok `try-finally` k uvolnění knihovny COM, pokud je úloha dokončena nebo je zrušena nebo když je vyvolána výjimka.

[!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]

Následující příklad používá vzor RAII k definování třídy `CCoInitializer`, která spravuje životnost knihovny modelu COM v daném oboru.

[!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]

Třídu `CCoInitializer` můžete použít k automatickému uvolnění knihovny COM při ukončení úlohy, a to následujícím způsobem.

[!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]

Další informace o zrušení v Concurrency Runtime najdete v části [zrušení v PPL](cancellation-in-the-ppl.md).

### <a name="using-com-with-asynchronous-agents"></a>Používání modelu COM s asynchronními agenty

Použijete-li COM s asynchronními agenty, zavolejte `CoInitializeEx` před použitím knihovny COM v metodě [Concurrency:: Agent:: Run](reference/agent-class.md#run) pro vašeho agenta. Poté zavolejte `CoUninitialize` před vrácením metody `run`. Nepoužívejte rutiny správy modelu COM v konstruktoru nebo destruktoru vašeho agenta a nepřepište metody [Concurrency:: Agent:: Start](reference/agent-class.md#start) nebo [Concurrency:: Agent::d jednu](reference/agent-class.md#done) z těchto metod, protože tyto metody jsou volány z jiného vlákna než z metody `run`.

Následující příklad ukazuje základní třídu agenta s názvem `CCoAgent`, která spravuje knihovnu COM v metodě `run`.

[!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]

Kompletní příklad najdete později v tomto návodu.

### <a name="using-com-with-lightweight-tasks"></a>Používání modelu COM s prostými úlohami

Dokument [Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md) popisuje roli zjednodušených úloh v Concurrency Runtime. Model COM můžete použít s odlehčenou úlohou stejným způsobem jako u jakékoli rutiny vlákna, kterou předáte do funkce `CreateThread` v rozhraní API systému Windows. To je ukázáno v následujícím příkladu.

[!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]

## <a name="an-example-of-a-com-enabled-application"></a>Příklad aplikace s podporou modelu COM

V této části se zobrazuje kompletní aplikace s podporou modelu COM, která používá rozhraní `IScriptControl` ke spuštění skriptu, který počítá n-<sup>tý</sup> Fibonacci číslo. Tento příklad nejprve volá skript z hlavního vlákna a poté používá PPL a agenty pro volání skriptu souběžně.

Vezměte v úvahu následující pomocnou funkci `RunScriptProcedure`, která volá proceduru v objektu `IScriptControl`.

[!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]

Funkce `wmain` vytvoří objekt `IScriptControl`, přidá do něj kód skriptu, který vypočítá n-<sup>tý</sup> Fibonacci číslo, a potom zavolá funkci `RunScriptProcedure` pro spuštění tohoto skriptu.

[!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]

### <a name="calling-the-script-from-the-ppl"></a>Volání skriptu z knihovny PPL

Následující funkce, `ParallelFibonacci`, používá algoritmus [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) k volání skriptu paralelně. Tato funkce používá třídu `CCoInitializer` ke správě životního cyklu knihovny modelu COM během každé iterace úlohy.

[!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]

Chcete-li použít funkci `ParallelFibonacci` s příkladem, přidejte následující kód před vrácením `wmain` funkce.

[!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]

### <a name="calling-the-script-from-an-agent"></a>Volání skriptu z agenta

Následující příklad ukazuje třídu `FibonacciScriptAgent`, která volá proceduru skriptu pro výpočet n-<sup>tého</sup> Fibonacci čísla. Třída `FibonacciScriptAgent` používá předávání zprávy z hlavního programu do funkce skriptu. Metoda `run` spravuje životnost knihovny COM v rámci úlohy.

[!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]

Následující funkce, `AgentFibonacci`, vytvoří několik objektů `FibonacciScriptAgent` a používá předávání zpráv k odeslání několika vstupních hodnot těmto objektům.

[!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]

Chcete-li použít funkci `AgentFibonacci` s příkladem, přidejte následující kód před vrácením `wmain` funkce.

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

> **CL. exe/EHsc Parallel-Scripts. cpp/Link Ole32. lib**

## <a name="see-also"></a>Viz také

[Návody pro Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Paralelní úkoly](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Paralelní algoritmy](../../parallel/concrt/parallel-algorithms.md)<br/>
[Asynchronní agenti](../../parallel/concrt/asynchronous-agents.md)<br/>
[Zpracování výjimek](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Zrušení v knihovně PPL](cancellation-in-the-ppl.md)<br/>
[Plánovač úloh](../../parallel/concrt/task-scheduler-concurrency-runtime.md)
