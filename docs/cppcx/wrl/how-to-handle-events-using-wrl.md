---
title: 'Postupy: Zpracování událostí s použitím knihovny WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
ms.openlocfilehash: 959a85d6cf6de666ae56d09035acefe9a3828ae8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033174"
---
# <a name="how-to-handle-events-using-wrl"></a>Postupy: Zpracování událostí s použitím knihovny WRL

Tento dokument ukazuje, jak použít Windows Runtime C++ šablony knihovny (WRL) přihlásit k odběru a zpracování událostí objekt prostředí Windows Runtime.

Informace o jednodušší příklad, který vytvoří instanci této součásti a načte hodnotu vlastnosti, naleznete v tématu [jak: Aktivace a používání komponent prostředí Windows Runtime](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).

## <a name="subscribing-to-and-handling-events"></a>Přihlášení k odběru a zpracování událostí

Následující kroky spuštění `ABI::Windows::System::Threading::IDeviceWatcher` objektu a sledovat průběh pomocí obslužných rutin událostí. `IDeviceWatcher` Rozhraní umožňuje výčet zařízení asynchronně, nebo na pozadí a obdržení oznámení při přidání, odebrání nebo změně zařízení. [Zpětného volání](callback-function-wrl.md) funkce je důležitou součástí tohoto příkladu, protože umožňuje určit obslužné rutiny událostí, které zpracovávají výsledky operace na pozadí. Následuje Úplný příklad.

> [!WARNING]
> I když používáte obvykle knihovna šablon C++ Windows Runtime v aplikaci pro univerzální platformu Windows, tento příklad používá konzolovou aplikaci pro ilustraci. Funkce, jako například `wprintf_s` nejsou k dispozici z aplikace pro univerzální platformu Windows. Další informace o typech a funkce, které můžete použít v aplikaci pro univerzální platformu Windows najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) a [Win32 a COM pro aplikace pro UPW](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

1. Zahrnout (`#include`) veškeré požadované prostředí Windows Runtime, knihovny šablon jazyka C++ Windows Runtime nebo hlavičky standardní knihovny C++.

   [!code-cpp[wrl-consume-event#2](../codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]

   `Windows.Devices.Enumeration.h` deklaruje typy, které jsou nutné k vytvoření výčtu zařízení.

   Doporučujeme využívat `using namespace` direktivy v souboru .cpp, aby byl kód čitelnější.

2. Deklarování lokálních proměnných pro aplikaci. V tomto příkladu obsahuje počet počet výčtu zařízení a registračních tokenů, které je povolují později zrušit odběr události.

   [!code-cpp[wrl-consume-event#7](../codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]

3. Inicializujte Windows Runtime.

   [!code-cpp[wrl-consume-event#3](../codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]

4. Vytvoření [události](event-class-wrl.md) objekt, který synchronizuje dokončení procesu výčet k hlavní aplikaci.

   [!code-cpp[wrl-consume-event#4](../codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]

   > [!NOTE]
   > Tato událost je pro ukázku pouze jako součást aplikace konzoly. Tento příklad používá události k zajištění, že asynchronní operace nedokončí, před jejím ukončením. Ve většině aplikací je obvykle není počkat na dokončení asynchronních operací.

5. Vytvořit objekt factory pro aktivaci pro `IDeviceWatcher` rozhraní.

   [!code-cpp[wrl-consume-event#5](../codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]

   Modul Windows Runtime používá k identifikaci typy plně kvalifikovaných názvů. `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation` Parametr je řetězec, který je poskytován modulu Windows Runtime a obsahuje název třídy runtime vyžaduje.

6. Vytvořte `IDeviceWatcher` objektu.

   [!code-cpp[wrl-consume-event#6](../codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]

7. Použití `Callback` funkce pro přihlášení k odběru `Added`, `EnumerationCompleted`, a `Stopped` události.

   [!code-cpp[wrl-consume-event#8](../codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]

   `Added` Obslužná rutina události zvýší počet výčtu zařízení. Zastaví proces výčtu až deset zařízení se nacházejí.

   `Stopped` Obslužná rutina události odstraní obslužné rutiny událostí a nastaví událost dokončení.

   `EnumerationCompleted` Obslužná rutina události zastaví proces výčtu. My se postaráme tuto událost v případě, že jsou míň než deset zařízení.

   > [!TIP]
   > Tento příklad používá výraz lambda k definování tak potřebná zpětná volání. Můžete použít také funkci objekty (funktory), ukazatele na funkce, nebo [std::function](../../standard-library/function-class.md) objekty. Další informace o výrazech lambda naleznete v tématu [výrazy Lambda](../../cpp/lambda-expressions-in-cpp.md).

8. Spusťte proces výčtu.

   [!code-cpp[wrl-consume-event#9](../codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]

9. Počkejte na dokončení a poté vytiskněte zprávu procesu výčtu. Všechny `ComPtr` a objekty RAII ponechte oboru a automaticky se vydávají.

   [!code-cpp[wrl-consume-event#10](../codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]

Tady je úplný příklad:

[!code-cpp[wrl-consume-event#1](../codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li kód zkompilovat, ho zkopírujte a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `wrl-consume-events.cpp` a pak spusťte následující příkaz **příkazový řádek sady Visual Studio** okna.

`cl.exe wrl-consume-events.cpp runtimeobject.lib`

## <a name="see-also"></a>Viz také:

[Knihovna šablon C++ prostředí Windows Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)