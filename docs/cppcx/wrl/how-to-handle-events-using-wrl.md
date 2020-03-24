---
title: 'Postupy: Zpracování událostí s použitím knihovny WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
ms.openlocfilehash: 0e13212d7cb481bc72a903a31fb170fd1ff8b7ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213925"
---
# <a name="how-to-handle-events-using-wrl"></a>Postupy: Zpracování událostí s použitím knihovny WRL

Tento dokument ukazuje, jak použít knihovnu šablon C++ prostředí Windows Runtime (WRL) k přihlášení k odběru a zpracování událostí objektu prostředí Windows Runtime.

Další základní příklad, který vytváří instanci této komponenty a načítá hodnotu vlastnosti, naleznete v tématu [How to: Activate and use a prostředí Windows Runtime Component](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).

## <a name="subscribing-to-and-handling-events"></a>Přihlášení k odběru a zpracování událostí

Následující kroky spustí objekt `ABI::Windows::System::Threading::IDeviceWatcher` a pomocí obslužných rutin událostí sleduje průběh. Rozhraní `IDeviceWatcher` umožňuje zobrazit výčet zařízení asynchronně nebo na pozadí a dostávat oznámení o přidání, odebrání nebo změně zařízení. Funkce [zpětného volání](callback-function-wrl.md) je důležitou součástí tohoto příkladu, protože umožňuje určit obslužné rutiny událostí, které zpracovávají výsledky operace na pozadí. Následující příklad následuje.

> [!WARNING]
> I když v aplikaci Univerzální platforma Windows obvykle C++ používáte knihovnu šablon prostředí Windows Runtime, tento příklad používá konzolovou aplikaci pro ilustraci. Funkce, jako například `wprintf_s`, nejsou z aplikace Univerzální platforma Windows k dispozici. Další informace o typech a funkcích, které můžete použít v aplikaci Univerzální platforma Windows, najdete v tématu [funkce CRT nepodporované v aplikacích Univerzální platforma Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) a [Win32 a com pro aplikace UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

1. Zahrnout (`#include`) všechny požadované prostředí Windows Runtime, prostředí Windows Runtime C++ knihovny šablon nebo C++ standardní hlavičky knihovny.

   [!code-cpp[wrl-consume-event#2](../codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]

   `Windows.Devices.Enumeration.h` deklaruje typy, které jsou nutné k zobrazení výčtu zařízení.

   Doporučujeme, abyste v souboru. cpp využili direktivu `using namespace`, abyste mohli kód čitelnější.

2. Deklarujte místní proměnné pro aplikaci. V tomto příkladu je uložený počet vyhodnocených zařízení a registračních tokenů, které jim umožní později zrušit odběr událostí.

   [!code-cpp[wrl-consume-event#7](../codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]

3. Inicializujte prostředí Windows Runtime.

   [!code-cpp[wrl-consume-event#3](../codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]

4. Vytvořte objekt [události](event-class-wrl.md) , který synchronizuje dokončení procesu výčtu s hlavní aplikací.

   [!code-cpp[wrl-consume-event#4](../codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]

   > [!NOTE]
   > Tato událost je určena pouze pro účely ukázky jako součást konzolové aplikace. V tomto příkladu se používá událost k zajištění, aby se asynchronní operace dokončila před ukončením aplikace. Ve většině aplikací obvykle nečekáte na dokončení asynchronních operací.

5. Vytvořte továrnu aktivace pro rozhraní `IDeviceWatcher`.

   [!code-cpp[wrl-consume-event#5](../codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]

   Prostředí Windows Runtime používá k identifikaci typů plně kvalifikované názvy. Parametr `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation` je řetězec, který je poskytován prostředí Windows Runtime a obsahuje požadovaný název běhové třídy.

6. Vytvořte objekt `IDeviceWatcher`.

   [!code-cpp[wrl-consume-event#6](../codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]

7. K přihlášení k odběru událostí `Added`, `EnumerationCompleted`a `Stopped` použijte funkci `Callback`.

   [!code-cpp[wrl-consume-event#8](../codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]

   Obslužná rutina události `Added` zvyšuje počet výčtu zařízení. Po nalezení deseti zařízení zastaví proces výčtu.

   Obslužná rutina události `Stopped` Odebere obslužné rutiny události a nastaví událost dokončení.

   Obslužná rutina události `EnumerationCompleted` zastaví proces výčtu. Tato událost se zpracovává v případě, že je méně než deset zařízení.

   > [!TIP]
   > Tento příklad používá výraz lambda pro definování zpětných volání. Můžete také použít objekty Functions (funktory), ukazatele na funkce nebo objekty [std:: Function](../../standard-library/function-class.md) . Další informace o výrazech lambda naleznete v tématu [lambda Expressions](../../cpp/lambda-expressions-in-cpp.md).

8. Spusťte proces výčtu.

   [!code-cpp[wrl-consume-event#9](../codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]

9. Počkejte, až se proces výčtu dokončí, a potom zprávu vytiskněte. Všechny objekty `ComPtr` a RAII připouštějí rozsah a automaticky se vydávají.

   [!code-cpp[wrl-consume-event#10](../codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]

Tady je kompletní příklad:

[!code-cpp[wrl-consume-event#1](../codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li zkompilovat kód, zkopírujte jej a vložte jej do projektu aplikace Visual Studio nebo jej vložte do souboru s názvem `wrl-consume-events.cpp` a poté spusťte následující příkaz v okně **příkazového řádku sady Visual Studio** .

`cl.exe wrl-consume-events.cpp runtimeobject.lib`

## <a name="see-also"></a>Viz také

[Knihovna šablon C++ prostředí Windows Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)
