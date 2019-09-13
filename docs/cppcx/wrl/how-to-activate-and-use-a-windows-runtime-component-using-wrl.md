---
title: 'Postupy: Aktivace a použití komponenty prostředí Windows Runtime pomocí WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
ms.openlocfilehash: 59a031968933ab151dc97a8089aff629026f5ea5
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926067"
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>Postupy: Aktivace a použití komponenty prostředí Windows Runtime pomocí WRL

Tento dokument ukazuje, jak pomocí knihovny šablon C++ prostředí Windows Runtime (WRL) inicializovat prostředí Windows Runtime a jak aktivovat a používat komponentu prostředí Windows Runtime.

Chcete-li použít komponentu, je nutné získat ukazatel rozhraní na typ, který je implementován komponentou. A vzhledem k tomu, že základní technologie prostředí Windows Runtime je model objektu komponenty (COM), je nutné dodržovat pravidla modelu COM pro zachování instance typu. Například je třeba zachovat *počet odkazů* , který určuje, kdy je typ odstraněn z paměti.

Aby bylo možné zjednodušit použití prostředí Windows Runtime, knihovna C++ šablon prostředí Windows Runtime poskytuje šablonu inteligentního ukazatele [\<ComPtr T >](comptr-class.md), která automaticky provádí počítání odkazů. Pokud deklarujete proměnnou `ComPtr<`, zadejte *identifikátor* *názvu* `>` rozhraní. Pro přístup k členu rozhraní použijte k identifikátoru operátor (`->`) šipky pro přístup členů.

> [!IMPORTANT]
> Při volání funkce rozhraní vždy testujte vrácenou hodnotu HRESULT.

## <a name="activating-and-using-a-windows-runtime-component"></a>Aktivace a použití komponenty prostředí Windows Runtime

Následující kroky používají `Windows::Foundation::IUriRuntimeClass` rozhraní k demonstraci toho, jak vytvořit objekt pro vytváření aktivace pro komponentu prostředí Windows Runtime, vytvořit instanci této komponenty a načíst hodnotu vlastnosti. Také ukazují, jak inicializovat prostředí Windows Runtime. Následující příklad následuje.

> [!IMPORTANT]
> I když obvykle používáte knihovnu šablon C++ prostředí Windows Runtime v aplikaci Univerzální platforma Windows (UWP), v tomto příkladu se pro ilustraci používá aplikace konzoly. Funkce, jako `wprintf_s` například, nejsou k dispozici z aplikace pro UWP. Další informace o typech a funkcích, které můžete použít v aplikaci pro UWP, najdete v tématu [funkce CRT nepodporované v aplikacích Univerzální platforma Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) a [Win32 a com pro aplikace UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

#### <a name="to-activate-and-use-a-windows-runtime-component"></a>Aktivace a používání součásti prostředí Windows Runtime

1. Include (`#include`) všechny požadované prostředí Windows Runtime, knihovny C++ šablon prostředí Windows Runtime nebo C++ hlavičky standardních knihoven.

   [!code-cpp[wrl-consume-component#2](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]

   Doporučujeme použít `using namespace` direktivu v souboru. cpp, aby byl kód čitelnější.

2. Inicializujte vlákno, ve kterém se aplikace spouští. Každá aplikace musí inicializovat svůj podproces a model vláken. Tento příklad používá třídu [Microsoft:: WRL:: Wrappers:: RoInitializeWrapper](roinitializewrapper-class.md) pro inicializaci prostředí Windows Runtime a určuje [RO_INIT_MULTITHREADED](/windows/win32/api/roapi/ne-roapi-ro_init_type) jako model vláken. Třída volá `Windows::Foundation::Initialize` konstrukci a`Windows::Foundation::Uninitialize` při jejím zničení. `RoInitializeWrapper`

   [!code-cpp[wrl-consume-component#3](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]

   Ve druhém příkazu vrátí `HRESULT` operátor [RoInitializeWrapper:: HRESULT](roinitializewrapper-class.md#hresult) `Windows::Foundation::Initialize`z volání metody.

3. Vytvořte *továrnu aktivace* pro `ABI::Windows::Foundation::IUriRuntimeClassFactory` rozhraní.

   [!code-cpp[wrl-consume-component#4](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]

   Prostředí Windows Runtime používá k identifikaci typů plně kvalifikované názvy. `RuntimeClass_Windows_Foundation_Uri` Parametr je řetězec, který je poskytován prostředí Windows Runtime a obsahuje požadovaný název běhové třídy.

4. Inicializujte proměnnou [Microsoft:: WRL:: Wrappers:: HSTRING](hstring-class.md) , která představuje identifikátor `"https://www.microsoft.com"`URI.

   [!code-cpp[wrl-consume-component#6](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]

   V prostředí Windows Runtime nepřiřazujte paměť pro řetězec, který bude používat prostředí Windows Runtime. Místo toho prostředí Windows Runtime vytvoří kopii řetězce ve vyrovnávací paměti, kterou udržuje a používá pro operace, a poté vrátí popisovač do vyrovnávací paměti, kterou vytvořil.

5. K vytvoření objektu použijte metodu `IUriRuntimeClassFactory::CreateUri`Factory `ABI::Windows::Foundation::IUriRuntimeClass` .

   [!code-cpp[wrl-consume-component#7](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]

6. Zavolejte metodu pro načtení hodnoty `Domain` vlastnosti. `IUriRuntimeClass::get_Domain`

   [!code-cpp[wrl-consume-component#8](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]

7. Vytiskněte název domény do konzoly a vraťte se. Všechny `ComPtr` objekty a RAII připouštějí rozsah a automaticky se vydávají.

   [!code-cpp[wrl-consume-component#9](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]

   Funkce [WindowsGetStringRawBuffer](/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer) načte základní formát Unicode řetězce identifikátoru URI.

Tady je kompletní příklad:

[!code-cpp[wrl-consume-component#1](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Pro zkompilování kódu ho zkopírujte a vložte do projektu sady Visual Studio, nebo jej vložte do souboru s názvem `wrl-consume-component.cpp` a pak spusťte následující příkaz v okně příkazového řádku sady Visual Studio.

`cl.exe wrl-consume-component.cpp runtimeobject.lib`

## <a name="see-also"></a>Viz také:

[Knihovna šablon C++ prostředí Windows Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)