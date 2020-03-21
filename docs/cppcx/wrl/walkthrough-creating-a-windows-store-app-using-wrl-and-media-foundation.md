---
title: 'Návod: Vytvoření aplikace pro UWP pomocí WRL a Media Foundation'
ms.date: 04/23/2019
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: 5c6fd2613c34fdecdf9128ed6a5d22d563961939
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079892"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>Návod: Vytvoření aplikace pro UWP pomocí WRL a Media Foundation

> [!NOTE]
> Pro nové aplikace a komponenty UWP doporučujeme používat [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), novou standardní projekci jazyka c++ 17 pro prostředí Windows Runtime API. C++/WinRT je k dispozici v sadě Windows 10 SDK od verze 1803 další. C++/WinRT je implementováno zcela v hlavičkových souborech a je navrženo tak, aby vám poskytovala prvotřídní přístup k modernímu rozhraní Windows API.

V tomto kurzu se naučíte, jak pomocí knihovny šablon prostředí Windows Runtime C++ (WRL) vytvořit aplikaci Univerzální platforma Windows (UWP), která používá [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk).

Tento příklad vytvoří vlastní transformaci Media Foundation, která aplikuje efekt ve stupních šedi na obrázky zachycené z webové kamery. Aplikace používá C++ k definování vlastní transformace a C# k použití komponenty k transformaci zachycených imagí.

> [!NOTE]
> Místo C#, můžete také použít JavaScript, Visual Basic nebo C++ pro využití vlastní transformační komponenty.

Ve většině případů můžete k vytváření prostředí Windows Runtime C++použít/CX. Někdy však musíte použít WRL. Pokud například vytvoříte rozšíření médií pro Microsoft Media Foundation, je nutné vytvořit komponentu, která implementuje rozhraní COM i prostředí Windows Runtime. Vzhledem C++k tomu, že objekt/CX může vytvořit pouze objekty prostředí Windows Runtime, aby bylo možné vytvořit rozšíření médií, je nutné použít WRL, protože umožňuje implementaci rozhraní COM i prostředí Windows Runtime.

> [!NOTE]
> I když je tento příklad kódu dlouhý, ukazuje minimum, které je nutné k vytvoření užitečné transformace Media Foundation. Můžete ho použít jako výchozí bod pro vlastní transformaci. Tento příklad je upravený z [ukázky rozšíření médií](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096), která používá rozšíření médií k aplikování efektů na video, dekódování videa a vytváření obslužných rutin, které vytvářejí datové proudy médií.

## <a name="prerequisites"></a>Předpoklady

- V aplikaci Visual Studio 2017 nebo novější je podpora UWP volitelnou komponentou. Chcete-li ji nainstalovat, otevřete Instalační program pro Visual Studio v nabídce Start systému Windows a vyhledejte svou verzi sady Visual Studio. Zvolte **Upravit** a ujistěte se, že je zaškrtnutá dlaždice **Univerzální platforma Windows vývojové** . V části **volitelné komponenty** kontrolujte  **C++ nástroje pro UWP (v141)** pro Visual Studio 2017 nebo  **C++ nástroje pro UWP (V142)** pro Visual Studio 2019. Pak zkontrolujte verzi Windows SDK, kterou chcete použít.

- Vyzkoušejte si [prostředí Windows Runtime](/uwp/api/).

- Prostředí COM.

- Webová kamera.

## <a name="key-points"></a>Klíčové body

- Chcete-li vytvořit vlastní komponentu Media Foundation, použijte definiční soubor rozhraní Microsoft Interface Definition Language (MIDL) k definování rozhraní, implementaci tohoto rozhraní a pak aktivovatelné z jiných komponent.

- Atributy `namespace` a `runtimeclass` a hodnota atributu `NTDDI_WIN8`[verze](/windows/win32/Midl/version) jsou důležité části definice MIDL pro komponentu Media Foundation, která používá WRL.

- [Microsoft:: WRL:: RuntimeClass](runtimeclass-class.md) je základní třída pro vlastní komponentu Media Foundation. Hodnota výčtu [Microsoft:: WRL:: RuntimeClassType –:: WinRtClassicComMix](runtimeclasstype-enumeration.md) , která je k dispozici jako argument šablony, označí třídu pro použití jako třídu prostředí Windows Runtime a jako klasickou třídu COM runtime.

- Makro [InspectableClass –](inspectableclass-macro.md) implementuje základní funkce modelu COM, jako je počítání odkazů a metoda `QueryInterface`, a nastaví název třídy modulu runtime a úroveň důvěryhodnosti.

- Použijte třídu Microsoft:: WRL::[Module](module-class.md) pro implementaci funkcí vstupního bodu knihovny DLL, jako je například [DllGetActivationFactory](/windows/win32/winrt/functions), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)a [DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject).

- Připojte knihovnu DLL komponenty k runtimeobject. lib. Pro generování metadat Windows zadejte také [/winmd](../../cppcx/compiler-and-linker-options-c-cx.md) na řádku linkeru.

- Pomocí odkazů na projekt zpřístupníte součásti WRL pro aplikace pro UWP.

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>Použití nástroje WRL k vytvoření Media Foundation transformační komponenty ve stupních šedi

1. V aplikaci Visual Studio vytvořte projekt **prázdného řešení** . Pojmenujte projekt, například *MediaCapture*.

1. Přidejte projekt **DLL (univerzální pro Windows)** do řešení. Pojmenujte projekt, například *GrayscaleTransform*.

1. Přidejte soubor **MIDL (. idl)** do projektu. Název souboru, například *GrayscaleTransform. idl*.

1. Přidejte tento kód do GrayscaleTransform. idl:

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. K nahrazení obsahu `pch.h`použijte následující kód:

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. Přidejte do projektu nový hlavičkový soubor, pojmenujte ho `BufferLock.h`a pak obsah nahraďte tímto kódem:

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. v tomto příkladu se nepoužívá `GrayscaleTransform.h`. Pokud chcete, můžete ho z projektu odebrat.

1. K nahrazení obsahu `GrayscaleTransform.cpp`použijte následující kód:

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. Přidejte do projektu nový soubor definice modulu, pojmenujte ho `GrayscaleTransform.def`a pak přidejte tento kód:

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. K nahrazení obsahu `dllmain.cpp`použijte následující kód:

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. V dialogovém okně **stránky vlastností** projektu nastavte následující vlastnosti **linkeru** .

   1. V části **vstup**zadejte pro **soubor definice modulu**`GrayScaleTransform.def`.

   1. Do vlastnosti **Další závislosti** také v části **vstup**přidejte `runtimeobject.lib`, `mfuuid.lib`a `mfplat.lib`.

   1. V části **metadata Windows**nastavte **generovat metadata Windows** na **Ano (/WinMD)** .

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>Použití WRL vlastní součásti Media Foundation z C# aplikace

1. Přidejte nový  **C# projekt aplikace (univerzální pro Windows)** do řešení `MediaCapture`. Pojmenujte projekt, například *MediaCapture*.

1. V projektu **MediaCapture** přidejte odkaz na projekt `GrayscaleTransform`. Informace o postupu najdete v tématu [Postup: Přidání nebo odebrání odkazů pomocí Správce odkazů](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).

1. V `Package.appxmanifest`na kartě **Možnosti** vyberte **mikrofon** a **Webová kamera**. Pro zachycení fotografií z webové kamery je potřeba obě možnosti.

1. V `MainPage.xaml`přidejte tento kód do kořenového elementu [mřížky](/uwp/api/Windows.UI.Xaml.Controls.Grid) :

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. K nahrazení obsahu `MainPage.xaml.cs`použijte následující kód:

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

`MediaCapture app`je znázorněno na následujícím obrázku.

![Aplikace MediaCapture, která zachytává fotografii](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>Další kroky

V tomto příkladu se dozvíte, jak zachytit fotky z výchozí webové kamery v jednom okamžiku. [Ukázka rozšíření médií](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) je další. Ukazuje, jak vytvořit výčet zařízení webové kamery a pracovat s obslužnými rutinami místních schémat a ukazuje další efekty multimédií, které fungují jak na jednotlivých fotografiích, tak v datových proudech videa.

## <a name="see-also"></a>Viz také

[Knihovna šablon C++ prostředí Windows Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)<br/>
[Ukázka rozšíření multimédií](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)
