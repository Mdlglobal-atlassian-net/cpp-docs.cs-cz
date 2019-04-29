---
title: 'Návod: Vytvoření aplikace UPW s použitím knihovny WRL a platformy Media Foundation'
ms.date: 09/17/2018
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: e0254be8c6fa185f75c46898d4da51742195550a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409207"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>Návod: Vytvoření aplikace UPW s použitím knihovny WRL a platformy Media Foundation

Další informace o použití Windows Runtime C++ šablony knihovny (WRL) k vytvoření aplikace pro univerzální platformu Windows (UPW), který používá [Microsoft Media Foundation](/windows/desktop/medfound/microsoft-media-foundation-sdk).

Tento příklad vytvoří vlastní transformace Media Foundation, která se použije ve stupních šedi mohou mít vliv na obrázky, které jsou zachyceny z webová kamera. Aplikace C++ používá k definování vlastní transformace a C# použít komponenty pro transformaci zaznamenané Image.

> [!NOTE]
> Místo C# také vám pomůže jazyka JavaScript, Visual Basic nebo C++ využívat komponentu vlastní transformace.

Ve většině případů můžete použít C++/CX k vytvoření prostředí Windows Runtime. Ale někdy je nutné použít WRL. Například při vytváření média rozšíření pro Microsoft Media Foundation, musíte vytvořit komponentu, která implementuje rozhraní COM a Windows Runtime. Protože C++/CX lze vytvořit pouze objekty modulu Windows Runtime, chcete-li vytvořit médium rozšíření je nutné použít WRL vzhledem k tomu, že umožňuje, aby implementace rozhraní COM a Windows Runtime.

> [!NOTE]
> Sice dlouhý tento příklad kódu ukazuje minimální potřebná k vytvoření užitečné transformace Media Foundation. Můžete ho použít jako výchozí bod pro vlastní vlastní transformace. V tomto příkladu jsou upraveny z [ukázkové rozšíření Media](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096), které používá media rozšíření použít dopad na video, dekódování video a vytváření obslužných rutin schéma, které vytvářejí datové proudy médií.

## <a name="prerequisites"></a>Požadavky

- Vyzkoušejte si [modulu Windows Runtime](https://msdn.microsoft.com/library/windows/apps/br211377.aspx).

- Zkušenosti s modelu COM.

- Webová kamera.

## <a name="key-points"></a>Klíčové body

- Pokud chcete vytvořit vlastní součást Media Foundation, pomocí souboru definice Microsoft Interface Definition Language (MIDL) definujte rozhraní implementují rozhraní a a pak si všechno aktivovatelné od jiných komponent.

- `namespace` a `runtimeclass` atributy a `NTDDI_WIN8` [verze](/windows/desktop/Midl/version) hodnota atributu jsou důležité části definice MIDL pro součást Media Foundation, který používá ke knihovně WRL.

- [Microsoft::WRL::RuntimeClass](runtimeclass-class.md) je základní třídou pro vlastní součást Media Foundation. [Microsoft::WRL::RuntimeClassType::WinRtClassicComMix](runtimeclasstype-enumeration.md) hodnotu výčtu, která se poskytuje jako argument šablony, označí třídy pro použití jako třída Windows Runtime i klasické třídy COM modulu runtime.

- [InspectableClass](inspectableclass-macro.md) – makro implementuje základní funkce modelu COM, jako je například počítání odkazů a `QueryInterface` metoda a nastaví název třídy modulu runtime a úroveň důvěryhodnosti.

- Použít Microsoft::WRL::[třídy modulu](module-class.md) provádět funkce vstupního bodu DLL [DllGetActivationFactory](https://msdn.microsoft.com/library/br205771.aspx), [DllCanUnloadNow](/windows/desktop/api/combaseapi/nf-combaseapi-dllcanunloadnow), a [ DllGetClassObject](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject).

- Propojte runtimeobject.lib vaše knihovna DLL komponenty. Také zadejte [winmd](../../cppcx/compiler-and-linker-options-c-cx.md) na řádku linkeru pro generování metadat Windows.

- Použití odkazů projektu zpřístupňovaly komponent knihovny WRL aplikací pro UWP.

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>Použití knihovny WRL vytvoření Media Foundation ve stupních šedi transformace komponenty

1. V sadě Visual Studio, vytvořit **prázdné řešení** projektu. Název projektu, například *MediaCapture*.

1. Přidat **knihovny DLL (Universal Windows)** projektu do řešení. Název projektu, například *GrayscaleTransform*.

1. Přidat **soubor Midl (.idl)** soubor do projektu. Název souboru, například *GrayscaleTransform.idl*.

1. Tento kód vložte do GrayscaleTransform.idl:

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. Pomocí následujícího kódu nahraďte obsah `pch.h`:

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. Přidejte do projektu nový soubor hlaviček, pojmenujte ho `BufferLock.h`a poté nahraďte obsah s tímto kódem:

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h` v tomto příkladu nepoužívá. Můžete ho odebrat z projektu Pokud budete chtít.

1. Pomocí následujícího kódu nahraďte obsah `GrayscaleTransform.cpp`:

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. Přidejte do projektu nový soubor definice modulu, pojmenujte ho `GrayscaleTransform.def`a následně přidejte následující kód:

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. Pomocí následujícího kódu nahraďte obsah `dllmain.cpp`:

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. V projektu **stránky vlastností** dialogovém okně nastavte následující **Linkeru** vlastnosti.

   1. V části **vstup**, pro **soubor definice modulu**, zadejte `GrayScaleTransform.def`.

   1. Také v části **vstup**, přidejte `runtimeobject.lib`, `mfuuid.lib`, a `mfplat.lib` k **Další závislosti** vlastnost.

   1. V části **metadat Windows**, nastavte **generování metadat Windows** k **Ano (/ WINMD)**.

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>Použití knihovny WRL vlastní součást Media Foundation z aplikace C#

1. Přidat nový **jazyka C# prázdná aplikace (Universal Windows)** projektu `MediaCapture` řešení. Název projektu, například *MediaCapture*.

1. V **MediaCapture** projektu, přidejte odkaz na `GrayscaleTransform` projektu. Další informace o postupu [jak: Přidání nebo odebrání odkazů pomocí Správce odkazů](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).

1. V `Package.appxmanifest`na **možnosti** kartu, vyberte možnost **mikrofon** a **webovou kameru**. Obě možnosti jsou nutné k zachycení fotky z webové kamery.

1. V `MainPage.xaml`, přidejte tento kód do kořenového adresáře [mřížky](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx) element:

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. Pomocí následujícího kódu nahraďte obsah `MainPage.xaml.cs`:

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

Je vidět na následujícím obrázku `MediaCapture app`.

![Aplikace MediaCapture zachytávání fotografii](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>Další kroky

Tento příklad ukazuje, jak zachytit fotky z výchozí webovou kameru, jeden po druhém. [Ukázkové rozšíření Media](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) více. Ukazuje, jak vytvořit výčet webová kamera zařízení a pracovat s obslužnými rutinami místní schéma a ukazuje účinky dalšího média, pracující na jednotlivé fotografie a datových proudů videa.

## <a name="see-also"></a>Viz také:

[Knihovna šablon C++ prostředí Windows Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft Media Foundation](/windows/desktop/medfound/microsoft-media-foundation-sdk)<br/>
[Ukázka rozšíření média](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)