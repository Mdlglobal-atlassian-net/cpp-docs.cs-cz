---
title: 'Návod: Vytvoření aplikace pro UPW s použitím knihovny WRL a platformy Media Foundation'
ms.date: 04/23/2019
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: 272092982c5e9cc57f52043e08c8bd384c43ea96
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031508"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>Návod: Vytvoření aplikace pro UPW s použitím knihovny WRL a platformy Media Foundation

> [!NOTE]
> Pro nové aplikace a součásti UPW doporučujeme použít [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), novou standardní projekci jazyka C++17 pro rozhraní API prostředí Windows Runtime. C++/WinRT je k dispozici v systému Windows 10 SDK od verze 1803 dále. C++/WinRT je implementován výhradně v hlavičkových souborech a je navržen tak, aby vám poskytl prvotřídní přístup k modernímu rozhraní API systému Windows.

V tomto kurzu se dozvíte, jak pomocí knihovny šablon Prostředí Windows Runtime C++ (WRL) vytvořit aplikaci pro univerzální platformu Windows (UPW), která používá [microsoft media foundation](/windows/win32/medfound/microsoft-media-foundation-sdk).

Tento příklad vytvoří vlastní media foundation transformace, která platí efekt stupně šedi na obrazy, které jsou zachyceny z webové kamery. Aplikace používá C++ k definování vlastní transformace a C# pro použití komponenty k transformaci zachycených obrazů.

> [!NOTE]
> Místo C#, můžete také použít JavaScript, Visual Basic nebo C++ využívat vlastní součást transformace.

Ve většině případů můžete použít C++/CX k vytvoření prostředí Windows Runtime. Někdy však budete muset použít WRL. Například při vytváření rozšíření médií pro Microsoft Media Foundation, je nutné vytvořit součást, která implementuje rozhraní COM a Windows Runtime. Vzhledem k tomu, že c++/CX můžete vytvářet pouze objekty prostředí Windows Runtime, chcete-li vytvořit rozšíření média, musíte použít wrl, protože umožňuje implementaci rozhraní COM i Windows Runtime.

> [!NOTE]
> Přestože tento příklad kódu je dlouhý, ukazuje minimum, které je nutné k vytvoření užitečné media foundation transformace. Můžete jej použít jako výchozí bod pro vlastní transformaci. Tento příklad je upraven z [ukázky rozšíření media](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096), která používá rozšíření médií k použití efektů na video, dekódování videa a vytvoření obslužných rutin schémat, které vytvářejí datové proudy médií.

## <a name="prerequisites"></a>Požadované součásti

- V sadě Visual Studio 2017 a novější je podpora UPW volitelnou součástí. Chcete-li ji nainstalovat, otevřete instalační službu sady Visual Studio z nabídky Start systému Windows a vyhledejte svou verzi sady Visual Studio. Zvolte **Změnit** a ujistěte se, že je zaškrtnutá univerzální dlaždice **Vývoj platformy Windows.** V **části Volitelné součásti** zkontrolujte **nástroje C++ pro UPW (v141)** pro Visual Studio 2017 nebo **Nástroje C++ pro UPW (v142)** pro Visual Studio 2019. Potom zkontrolujte verzi sady Windows SDK, kterou chcete použít.

- Zkušenosti s [prostředím Windows Runtime](/uwp/api/).

- Zkušenosti s COM.

- Webová kamera.

## <a name="key-points"></a>Klíčové body

- Chcete-li vytvořit vlastní součást Media Foundation, použijte definiční soubor jazyka MIDL (Microsoft Interface Definition Language) k definování rozhraní, implementaci tohoto rozhraní a jeho aktivaci z jiných součástí.

- `namespace` Atributy `runtimeclass` a hodnota `NTDDI_WIN8`atributu [version](/windows/win32/Midl/version) jsou důležitými částmi definice MIDL pro komponentu Media Foundation, která používá wrl.

- [Microsoft::WRL::RuntimeClass](runtimeclass-class.md) je základní třída pro vlastní součást Media Foundation. Hodnota výčtu [Enum Microsoft::WRL::RuntimeClassType::WinRtClassicComMix,](runtimeclasstype-enumeration.md) která je k dispozici jako argument šablony, označí třídu pro použití jako třída Prostředí Windows Runtime i jako klasická třída runtime com.

- Makro [InspectableClass](inspectableclass-macro.md) implementuje základní funkce com, `QueryInterface` jako je například počítání odkazů a metoda, a nastaví název třídy runtime a úroveň důvěryhodnosti.

- Pomocí[třídy](module-class.md) Microsoft::WRL:: Module class implementujte funkce vstupního bodu knihovny DLL, jako jsou [DllGetActivationFactory](/windows/win32/winrt/functions), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)a [DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject).

- Propojte knihovnu DLL komponenty s souborem runtimeobject.lib. Také zadejte [/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md) na linkeru pro generování metadat systému Windows.

- Pomocí odkazů na projekt zpřístupníte komponenty WRL aplikacím UPW.

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>Použití příkazu WRL k vytvoření součásti transformace ve stupních šedi Media Foundation

1. V sadě Visual Studio vytvořte projekt **prázdného řešení.** Pojmenujte projekt, například *MediaCapture*.

1. Přidejte projekt **DLL (Universal Windows)** do řešení. Pojmenujte projekt, například *GrayscaleTransform*.

1. Přidejte do projektu soubor **midl souboru (.idl).** Pojmenujte soubor, například *GrayscaleTransform.idl*.

1. Přidejte tento kód do souboru GrayscaleTransform.idl:

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. K nahrazení obsahu `pch.h`:

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. Přidejte do projektu nový soubor `BufferLock.h`záhlaví, pojmenujte jej a nahraďte obsah tímto kódem:

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h`se v tomto příkladu nepoužívá. Pokud chcete, můžete jej z projektu odebrat.

1. K nahrazení obsahu `GrayscaleTransform.cpp`:

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. Přidejte do projektu nový soubor definice `GrayscaleTransform.def`modulu, pojmenujte jej a přidejte tento kód:

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. K nahrazení obsahu `dllmain.cpp`:

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. V dialogovém okně **Stránky vlastností** projektu nastavte následující vlastnosti **propojovacího zařízení.**

   1. V části **Vstup**zadejte v `GrayScaleTransform.def`poli **Soubor definice modulu**.

   1. Také **Input**v části `runtimeobject.lib` `mfuuid.lib`Input `mfplat.lib` přidejte , , a další **závislosti** vlastnost.

   1. V části **Metadata systému Windows**nastavte **možnost Generovat metadata systému Windows** na ano **(/WINMD).**

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>Použití vlastní součásti Media Foundation z aplikace C#

1. Přidejte do `MediaCapture` řešení nový projekt aplikace **C# Blank (Universal Windows).** Pojmenujte projekt, například *MediaCapture*.

1. V projektu **MediaCapture** přidejte odkaz `GrayscaleTransform` na projekt. Postup najdete v [tématu Jak: Přidání nebo odebrání odkazů pomocí Správce odkazů](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).

1. V `Package.appxmanifest`aplikaci vyberte na kartě **Možnosti** **možnost Mikrofon** a **webová kamera**. Obě funkce jsou nutné pro pořizování fotografií z webové kamery.

1. V `MainPage.xaml`oblasti přidejte tento kód do kořenového prvku [Grid:](/uwp/api/windows.ui.xaml.controls.grid)

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. K nahrazení obsahu `MainPage.xaml.cs`:

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

Následující obrázek `MediaCapture app`znázorňuje .

![Aplikace MediaCapture zachycující fotografii](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>Další kroky

Příklad ukazuje, jak pořit fotografie z výchozí webové kamery po jednom. [Ukázka rozšíření média](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) může být větší. Ukazuje, jak vytvořit výčet webových kamer ových zařízení a pracovat s místními manipulátory schématu a ukazuje další mediální efekty, které fungují na jednotlivých fotografiích i datových proudech videa.

## <a name="see-also"></a>Viz také

[Knihovna šablon C++ prostředí Windows Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)<br/>
[Ukázka rozšíření médií](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)
