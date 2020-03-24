---
title: 'Postupy: Dokončení asynchronních operací s použitím knihovny WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
ms.openlocfilehash: 8e7e52342cf73a56c6c33d4d1f998f446d632ddd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213938"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>Postupy: Dokončení asynchronních operací s použitím knihovny WRL

Tento dokument ukazuje, jak použít knihovnu šablon C++ prostředí Windows Runtime (WRL) ke spuštění asynchronních operací a provádění práce po dokončení operací.

Tento dokument popisuje dva příklady. První příklad spustí asynchronní časovač a počká, až vyprší platnost časovače. V tomto příkladu zadáte asynchronní akci při vytváření objektu Timer. Druhý příklad spustí pracovní vlákno na pozadí. Tento příklad ukazuje, jak pracovat s metodou prostředí Windows Runtime, která vrací rozhraní `IAsyncInfo`. Funkce [zpětného volání](callback-function-wrl.md) je důležitou součástí obou příkladů, protože umožňuje určit obslužnou rutinu události pro zpracování výsledků asynchronních operací.

Další základní příklad, který vytváří instanci komponenty a načítá hodnotu vlastnosti, naleznete v tématu [How to: Activate and use a prostředí Windows Runtime Component](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).

> [!TIP]
> Tyto příklady používají lambda výrazy k definování zpětných volání. Můžete také použít objekty Functions (funktory), ukazatele na funkce nebo objekty [std:: Function](../../standard-library/function-class.md) . Další informace o C++ výrazech lambda naleznete v tématu [lambda Expressions](../../cpp/lambda-expressions-in-cpp.md).

## <a name="example-working-with-a-timer"></a>Příklad: práce s časovačem

Následující kroky spouštějí asynchronní časovač a čekají na vypršení platnosti časovače. Následující příklad následuje.

> [!WARNING]
> I když obvykle používáte knihovnu šablon C++ prostředí Windows Runtime v aplikaci Univerzální platforma Windows (UWP), v tomto příkladu se pro ilustraci používá aplikace konzoly. Funkce, jako například `wprintf_s`, nejsou k dispozici z aplikace pro UWP. Další informace o typech a funkcích, které můžete použít v aplikaci pro UWP, najdete v tématu [funkce CRT nepodporované v aplikacích Univerzální platforma Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) a [Win32 a com pro aplikace UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

1. Zahrnout (`#include`) všechny požadované prostředí Windows Runtime, prostředí Windows Runtime C++ knihovny šablon nebo C++ standardní hlavičky knihovny.

   [!code-cpp[wrl-consume-async#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]

   `Windows.System.Threading.h` deklaruje typy, které jsou požadovány pro použití asynchronního časovače.

   Doporučujeme, abyste v souboru. cpp využili direktivu `using namespace`, abyste mohli kód čitelnější.

2. Inicializujte prostředí Windows Runtime.

   [!code-cpp[wrl-consume-async#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]

3. Vytvořte továrnu aktivace pro rozhraní `ABI::Windows::System::Threading::IThreadPoolTimer`.

   [!code-cpp[wrl-consume-async#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]

   Prostředí Windows Runtime používá k identifikaci typů plně kvalifikované názvy. Parametr `RuntimeClass_Windows_System_Threading_ThreadPoolTimer` je řetězec, který je poskytován prostředí Windows Runtime a obsahuje požadovaný název běhové třídy.

4. Vytvořte objekt [události](event-class-wrl.md) , který synchronizuje zpětné volání časovače s hlavní aplikací.

   [!code-cpp[wrl-consume-async#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]

   > [!NOTE]
   > Tato událost je určena pouze pro účely ukázky jako součást konzolové aplikace. V tomto příkladu se používá událost k zajištění, aby se asynchronní operace dokončila před ukončením aplikace. Ve většině aplikací obvykle nečekáte na dokončení asynchronních operací.

5. Vytvořte objekt `IThreadPoolTimer`, jehož platnost vyprší po dvou sekundách. K vytvoření obslužné rutiny události (objekt `ABI::Windows::System::Threading::ITimerElapsedHandler`) použijte funkci `Callback`.

   [!code-cpp[wrl-consume-async#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]

6. Vytiskněte zprávu do konzoly a počkejte, než se dokončí zpětné volání časovače. Všechny objekty `ComPtr` a RAII připouštějí rozsah a automaticky se vydávají.

   [!code-cpp[wrl-consume-async#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]

Tady je kompletní příklad:

[!code-cpp[wrl-consume-async#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]

### <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li zkompilovat kód, zkopírujte jej a vložte jej do projektu aplikace Visual Studio nebo jej vložte do souboru s názvem `wrl-consume-async.cpp` a poté spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

`cl.exe wrl-consume-async.cpp runtimeobject.lib`

## <a name="example-working-with-a-background-thread"></a>Příklad: práce s vláknem na pozadí

Následující kroky spouštějí pracovní vlákno a definují akci, kterou provede toto vlákno. Následující příklad následuje.

> [!TIP]
> Tento příklad ukazuje, jak pracovat s rozhraním `ABI::Windows::Foundation::IAsyncAction`. Tento model můžete použít pro jakékoli rozhraní, které implementuje `IAsyncInfo`: `IAsyncAction`, `IAsyncActionWithProgress`, `IAsyncOperation`a `IAsyncOperationWithProgress`.

1. Zahrnout (`#include`) všechny požadované prostředí Windows Runtime, prostředí Windows Runtime C++ knihovny šablon nebo C++ standardní hlavičky knihovny.

   [!code-cpp[wrl-consume-asyncOp#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]

   Windows. System. Threading. h deklaruje typy, které jsou požadovány pro použití pracovního vlákna.

   Doporučujeme, abyste v souboru. cpp použili direktivu `using namespace`, abyste mohli kód čitelnější.

2. Inicializujte prostředí Windows Runtime.

   [!code-cpp[wrl-consume-asyncOp#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]

3. Vytvořte továrnu aktivace pro rozhraní `ABI::Windows::System::Threading::IThreadPoolStatics`.

   [!code-cpp[wrl-consume-asyncOp#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]

4. Vytvořte objekt [události](event-class-wrl.md) , který synchronizuje dokončení pracovního vlákna s hlavní aplikací.

   [!code-cpp[wrl-consume-asyncOp#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]

   > [!NOTE]
   > Tato událost je určena pouze pro účely ukázky jako součást konzolové aplikace. V tomto příkladu se používá událost k zajištění, aby se asynchronní operace dokončila před ukončením aplikace. Ve většině aplikací obvykle nečekáte na dokončení asynchronních operací.

5. Chcete-li vytvořit pracovní vlákno, zavolejte metodu `IThreadPoolStatics::RunAsync`. Akci definujte pomocí funkce `Callback`.

   [!code-cpp[wrl-consume-asyncOp#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]

   Funkce `IsPrime` je definována v úplném příkladu, který následuje.

6. Vytiskněte zprávu do konzoly a počkejte, než se vlákno dokončí. Všechny objekty `ComPtr` a RAII připouštějí rozsah a automaticky se vydávají.

   [!code-cpp[wrl-consume-asyncOp#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]

Tady je kompletní příklad:

[!code-cpp[wrl-consume-asyncOp#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]

### <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li zkompilovat kód, zkopírujte jej a vložte jej do projektu aplikace Visual Studio nebo jej vložte do souboru s názvem `wrl-consume-asyncOp.cpp` a poté spusťte následující příkaz v okně **příkazového řádku sady Visual Studio** .

`cl.exe wrl-consume-asyncOp.cpp runtimeobject.lib`

## <a name="see-also"></a>Viz také

[Knihovna šablon C++ prostředí Windows Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)
