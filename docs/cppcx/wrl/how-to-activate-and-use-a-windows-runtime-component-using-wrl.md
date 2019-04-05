---
title: 'Postupy: Aktivace a používání komponent Windows Runtime s použitím knihovny WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
ms.openlocfilehash: 8c0bed825f76fdf0f2c5cc1fa095e54f08bb8a67
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037208"
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>Postupy: Aktivace a používání komponent Windows Runtime s použitím knihovny WRL

Tento dokument ukazuje, jak použít Windows Runtime C++ šablony knihovny (WRL) se inicializovat modul Windows Runtime a aktivaci a používání komponent prostředí Windows Runtime.

Chcete-li použít komponentu, musíte získat ukazatele rozhraní na typ, který je implementováno komponentou. A protože základní technologie Windows Runtime je modelu COM (Component Object), je třeba dodržovat pravidla COM Udržovat instance typu. Například musíte mít *referenční počet* , který určuje, kdy je typ odstraněn z paměti.

Pro zjednodušení použití prostředí Windows Runtime, knihovny šablon jazyka C++ Windows Runtime poskytuje šablony inteligentního ukazatele [ComPtr\<T >](comptr-class.md), která automaticky provádí počítání odkazů. Pokud deklarujete proměnnou, zadejte `ComPtr<` *název rozhraní* `>` *identifikátor*. Chcete-li získat přístup k člen rozhraní, použijte šipku operátora přístupu členů (`->`) k identifikátoru.

> [!IMPORTANT]
> Při volání funkce protokolem rozhraní vždy testujte návratovou hodnotu HRESULT.

## <a name="activating-and-using-a-windows-runtime-component"></a>Aktivace a pomocí komponenty Windows Runtime

Následující kroky použijte `Windows::Foundation::IUriRuntimeClass` rozhraní ukazují, jak vytvořit objekt factory pro aktivaci pro součást prostředí Windows Runtime, vytvořit instanci této součásti a hodnot vlastností. Jsou také ukazují, jak inicializovat Windows Runtime. Následuje Úplný příklad.

> [!IMPORTANT]
> I když používáte obvykle knihovna šablon C++ Windows Runtime v aplikaci pro univerzální platformu Windows (UPW), v tomto příkladu používá konzolovou aplikaci pro ilustraci. Funkce, jako například `wprintf_s` nejsou k dispozici prostřednictvím aplikace pro UPW. Další informace o typech a funkce, které můžete použít v aplikaci UWP, naleznete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) a [Win32 a COM pro aplikace pro UPW](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

#### <a name="to-activate-and-use-a-windows-runtime-component"></a>K aktivaci a používání komponent prostředí Windows Runtime

1. Zahrnout (`#include`) veškeré požadované prostředí Windows Runtime, knihovny šablon jazyka C++ Windows Runtime nebo hlavičky standardní knihovny C++.

   [!code-cpp[wrl-consume-component#2](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]

   Doporučujeme využívat `using namespace` direktivy v souboru .cpp, aby byl kód čitelnější.

2. Inicializujte vláken, ve kterém se spustí aplikace. Každá aplikace musí inicializovat jeho vlákna a dělení na vlákna modelu. V tomto příkladu [Microsoft::WRL::Wrappers::RoInitializeWrapper](roinitializewrapper-class.md) třídy se inicializovat modul Windows Runtime a určuje [RO_INIT_MULTITHREADED](/windows/desktop/api/roapi/ne-roapi-ro_init_type) jako model vláken. `RoInitializeWrapper` Třídy volání `Windows::Foundation::Initialize` při konstrukci, a `Windows::Foundation::Uninitialize` při jeho zničení.

   [!code-cpp[wrl-consume-component#3](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]

   V druhém příkazu [RoInitializeWrapper::HRESULT](roinitializewrapper-class.md#hresult) operátor vrátí `HRESULT` z volání `Windows::Foundation::Initialize`.

3. Vytvoření *objektu factory pro aktivaci* pro `ABI::Windows::Foundation::IUriRuntimeClassFactory` rozhraní.

   [!code-cpp[wrl-consume-component#4](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]

   Modul Windows Runtime používá k identifikaci typy plně kvalifikovaných názvů. `RuntimeClass_Windows_Foundation_Uri` Parametr je řetězec, který je poskytován modulu Windows Runtime a obsahuje název třídy runtime vyžaduje.

4. Inicializace [Microsoft::WRL::Wrappers::HString](hstring-class.md) proměnné, která představuje identifikátor URI `"http://www.microsoft.com"`.

   [!code-cpp[wrl-consume-component#6](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]

   V modulu Windows Runtime není přidělit paměť pro řetězec, který bude používat modul Windows Runtime. Místo toho modul Windows Runtime vytvoří kopii vašeho řetězce do vyrovnávací paměti, že udržuje a používá pro operace a potom vrátí popisovač do vyrovnávací paměti, které vytvořili.

5. Použití `IUriRuntimeClassFactory::CreateUri` metoda factory `ABI::Windows::Foundation::IUriRuntimeClass` objektu.

   [!code-cpp[wrl-consume-component#7](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]

6. Volání `IUriRuntimeClass::get_Domain` metodu pro načtení hodnoty `Domain` vlastnost.

   [!code-cpp[wrl-consume-component#8](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]

7. Vypsat názvy domény do konzoly a vrátit. Všechny `ComPtr` a objekty RAII ponechte oboru a automaticky se vydávají.

   [!code-cpp[wrl-consume-component#9](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]

   [WindowsGetStringRawBuffer](/windows/desktop/api/winstring/nf-winstring-windowsgetstringrawbuffer) funkce načte základní Unicode formu řetězec identifikátoru URI.

Tady je úplný příklad:

[!code-cpp[wrl-consume-component#1](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Chcete-li kód zkompilovat, ho zkopírujte a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `wrl-consume-component.cpp` a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.

`cl.exe wrl-consume-component.cpp runtimeobject.lib`

## <a name="see-also"></a>Viz také:

[Knihovna šablon C++ prostředí Windows Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)