---
title: 'Postupy: Dokončení asynchronních operací s použitím knihovny WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
ms.openlocfilehash: 09c341e5e3d4f6007d5d5f66b7c06e1f0af5a65c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040222"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>Postupy: Dokončení asynchronních operací s použitím knihovny WRL

Tento dokument ukazuje, jak použít Windows Runtime C++ šablony knihovny (WRL) ke spuštění asynchronních operací a provedení práce po dokončení operací.

Tento dokument popisuje dva příklady. První příklad spustí asynchronní časovač a čeká na časovač vypršení platnosti. V tomto příkladu zadáte asynchronní akce při vytváření objektu časovače. V druhém příkladu spustí pracovní vlákno na pozadí. Tento příklad ukazuje, jak pracovat s metodu Windows Runtime, která vrátí `IAsyncInfo` rozhraní. [Zpětného volání](callback-function-wrl.md) funkce je důležitou součástí obou příkladech, protože umožňuje jim chcete-li určit obslužné rutiny události ke zpracování výsledků asynchronních operací.

Informace o jednodušší příklad, který vytvoří instanci komponenty a načte hodnotu vlastnosti, naleznete v tématu [jak: Aktivace a používání komponent prostředí Windows Runtime](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).

> [!TIP]
> Tyto příklady používají k definování tak potřebná zpětná volání výrazů lambda. Můžete použít také funkci objekty (funktory), ukazatele na funkce, nebo [std::function](../../standard-library/function-class.md) objekty. Další informace o výrazech lambda C++ naleznete v tématu [výrazy Lambda](../../cpp/lambda-expressions-in-cpp.md).

## <a name="example-working-with-a-timer"></a>Příklad: Práce s časovačem

V následujících krocích spustit asynchronní časovač a čekání na časovač vypršení platnosti. Následuje Úplný příklad.

> [!WARNING]
> I když používáte obvykle knihovna šablon C++ Windows Runtime v aplikaci pro univerzální platformu Windows (UPW), v tomto příkladu používá konzolovou aplikaci pro ilustraci. Funkce, jako například `wprintf_s` nejsou k dispozici prostřednictvím aplikace pro UPW. Další informace o typech a funkce, které můžete použít v aplikaci UWP, naleznete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) a [Win32 a COM pro aplikace pro UPW](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

1. Zahrnout (`#include`) veškeré požadované prostředí Windows Runtime, knihovny šablon jazyka C++ Windows Runtime nebo hlavičky standardní knihovny C++.

   [!code-cpp[wrl-consume-async#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]

   `Windows.System.Threading.h` deklaruje typy, které jsou nutné k použití asynchronní časovače.

   Doporučujeme využívat `using namespace` direktivy v souboru .cpp, aby byl kód čitelnější.

2. Inicializujte Windows Runtime.

   [!code-cpp[wrl-consume-async#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]

3. Vytvořit objekt factory pro aktivaci pro `ABI::Windows::System::Threading::IThreadPoolTimer` rozhraní.

   [!code-cpp[wrl-consume-async#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]

   Modul Windows Runtime používá k identifikaci typy plně kvalifikovaných názvů. `RuntimeClass_Windows_System_Threading_ThreadPoolTimer` Parametr je řetězec, který je poskytován modulu Windows Runtime a obsahuje název třídy runtime vyžaduje.

4. Vytvoření [události](event-class-wrl.md) objekt, který synchronizuje časovače zpětného volání k hlavní aplikaci.

   [!code-cpp[wrl-consume-async#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]

   > [!NOTE]
   > Tato událost je pro ukázku pouze jako součást aplikace konzoly. Tento příklad používá události k zajištění, že asynchronní operace nedokončí, před jejím ukončením. Ve většině aplikací je obvykle není počkat na dokončení asynchronních operací.

5. Vytvoření `IThreadPoolTimer` objektu, jejíž platnost vyprší po 2 sekundy. Použití `Callback` funkce k vytvoření obslužné rutiny události ( `ABI::Windows::System::Threading::ITimerElapsedHandler` objekt).

   [!code-cpp[wrl-consume-async#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]

6. Vytisknout zprávu do konzoly a počkejte časovače zpětného volání k dokončení. Všechny `ComPtr` a objekty RAII ponechte oboru a automaticky se vydávají.

   [!code-cpp[wrl-consume-async#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]

Tady je úplný příklad:

[!code-cpp[wrl-consume-async#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]

### <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li kód zkompilovat, ho zkopírujte a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `wrl-consume-async.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

`cl.exe wrl-consume-async.cpp runtimeobject.lib`

## <a name="example-working-with-a-background-thread"></a>Příklad: Práce s vlákna na pozadí

V následujících krocích spustit pracovní vlákno a definovat akce, kterou provádí toto vlákno. Následuje Úplný příklad.

> [!TIP]
> Tento příklad ukazuje, jak pracovat s `ABI::Windows::Foundation::IAsyncAction` rozhraní. Tento vzor lze použít libovolné rozhraní, která implementuje `IAsyncInfo`: `IAsyncAction`, `IAsyncActionWithProgress`, `IAsyncOperation`, a `IAsyncOperationWithProgress`.

1. Zahrnout (`#include`) veškeré požadované prostředí Windows Runtime, knihovny šablon jazyka C++ Windows Runtime nebo hlavičky standardní knihovny C++.

   [!code-cpp[wrl-consume-asyncOp#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]

   Windows.System.Threading.h deklaruje typy, které jsou nutné k použití pracovní podproces.

   Doporučujeme použít `using namespace` direktivy v souboru .cpp, aby byl kód čitelnější.

2. Inicializujte Windows Runtime.

   [!code-cpp[wrl-consume-asyncOp#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]

3. Vytvořit objekt factory pro aktivaci pro `ABI::Windows::System::Threading::IThreadPoolStatics` rozhraní.

   [!code-cpp[wrl-consume-asyncOp#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]

4. Vytvoření [události](event-class-wrl.md) objekt, který synchronizuje ukončení pracovního vlákna k hlavní aplikaci.

   [!code-cpp[wrl-consume-asyncOp#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]

   > [!NOTE]
   > Tato událost je pro ukázku pouze jako součást aplikace konzoly. Tento příklad používá události k zajištění, že asynchronní operace nedokončí, před jejím ukončením. Ve většině aplikací je obvykle není počkat na dokončení asynchronních operací.

5. Volání `IThreadPoolStatics::RunAsync` metodu pro vytvoření pracovního vlákna. Použití `Callback` funkce definujete akce.

   [!code-cpp[wrl-consume-asyncOp#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]

   `IsPrime` Funkce je definována v úplném příkladu, který následuje.

6. Vytisknout zprávu do konzoly a čekání na vlákno k dokončení. Všechny `ComPtr` a objekty RAII ponechte oboru a automaticky se vydávají.

   [!code-cpp[wrl-consume-asyncOp#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]

Tady je úplný příklad:

[!code-cpp[wrl-consume-asyncOp#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]

### <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li kód zkompilovat, ho zkopírujte a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `wrl-consume-asyncOp.cpp` a pak spusťte následující příkaz **příkazový řádek sady Visual Studio** okna.

`cl.exe wrl-consume-asyncOp.cpp runtimeobject.lib`

## <a name="see-also"></a>Viz také:

[Knihovna šablon C++ prostředí Windows Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)