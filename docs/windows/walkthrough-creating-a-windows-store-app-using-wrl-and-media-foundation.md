---
title: "Návod: Vytvoření aplikace pro UPW pomocí knihovny WRL a platformy Media Foundation | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a104cab9ec15872fe9e1b1c7a1eaf7ccd705f7d2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>Návod: Vytvoření aplikace pro UPW pomocí knihovny WRL a platformy Media Foundation
Další informace o použití Windows Runtime C++ šablony knihovny (WRL) k vytvoření aplikace univerzální platformu Windows (UWP), která používá [Microsoft Media Foundation](http://msdn.microsoft.com/library/windows/apps/ms694197).  
  
 Tento příklad vytvoří vlastní transformace Media Foundation, která se použije ve stupních šedi vliv na obrázky, které jsou zachyceny z webová kamera. Aplikace C++ používá k definování vlastní transformace a C# k použití komponentu k transformaci zaznamenané bitové kopie.  
  
> [!NOTE]
>  Místo C# můžete také použít JavaScript, Visual Basic nebo C++ využívat komponentu vlastní transformace.  
  

 Ve většině případů můžete použít C + +/ CX k vytvoření prostředí Windows Runtime). Ale někdy je nutné použít WRL. Například při vytváření média rozšíření pro Microsoft Media Foundation, musíte vytvořit komponenty, která implementuje rozhraní COM a prostředí Windows Runtime. Protože C + +/ CX lze vytvořit pouze objekty prostředí Windows Runtime, chcete-li vytvořit médium rozšíření je nutné použít WRL protože umožní implementace rozhraní COM a prostředí Windows Runtime.  

  
> [!NOTE]
>  I když tento příklad kódu je dlouhý, představuje minimální, které je nutné vytvořit užitečné transformace Media Foundation. Můžete ho použít jako výchozí bod pro vlastní vlastní transformace. V tomto příkladu je přizpůsobené z [ukázky rozšíření média](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096), která používá rozšíření média použít dopad na video, dekódovat video a vytváření obslužných rutin schéma, které vytváří datové proudy médií.  
  
## <a name="prerequisites"></a>Požadavky  
  
-   Prostředí s [prostředí Windows Runtime](http://msdn.microsoft.com/library/windows/apps/br211377.aspx).  
  
-   Zkušenosti s COM.  
  
-   Webová kamera.  
  
## <a name="key-points"></a>Klíčové body  
  
-   Pokud chcete vytvořit vlastní součást Media Foundation, pomocí souboru definice Microsoft rozhraní Definition Language (MIDL) definovat rozhraní, implementovat dané rozhraní a pak proveďte activatable z ostatních součástí.  
  
-   `namespace` a `runtimeclass` atributů a `NTDDI_WIN8` [verze](http://msdn.microsoft.com/en-us/66ac5cf3-2230-44fd-aaf6-8013e4a4ae81) hodnota atributu jsou důležitou součástí definici MIDL pro součást Media Foundation, která používá WRL.  
  
-   [Microsoft::WRL::RuntimeClass](../windows/runtimeclass-class.md) je základní třídou pro vlastní součást Media Foundation. [Microsoft::WRL::RuntimeClassType::WinRtClassicComMix](../windows/runtimeclasstype-enumeration.md) hodnotu výčtu, který je zadaný jako argument šablony, označí třída pro použití jako třída prostředí Windows Runtime a jako classic runtime třídy COM.  
  
-   [Inspectableclass –](../windows/inspectableclass-macro.md) makro implementuje základní funkce COM, jako je například počítání odkazů a `QueryInterface` metoda a nastaví název třídy modul runtime a úroveň důvěryhodnosti.  
  
-   Použít Microsoft::WRL::[Module – třídy](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/b4acf5de-2f4c-4c8b-b5ff-9140d023ecbe/locales/en-US) implementovat DLL vstupní bod funkce, jako [DllGetActivationFactory](http://msdn.microsoft.com/library/br205771.aspx), [DllCanUnloadNow](http://msdn.microsoft.com/library/windows/desktop/ms690368\(v=vs.85\).aspx), a [ DllGetClassObject](http://msdn.microsoft.com/library/windows/desktop/ms680760\(v=vs.85\).aspx).  
  
-   Propojte runtimeobject.lib příslušné součásti knihovny DLL. Zadat také [/WINMD](../cppcx/compiler-and-linker-options-c-cx.md) na řádek linkeru pro generování metadat Windows.  
  
-   Použijte odkazy na projekt zpřístupněte komponent knihovny WRL pro aplikace UWP.  
  
### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>Použití knihovny WRL vytvořit ve stupních šedi Media Foundation transformace součásti  
  
1.  V sadě Visual Studio, vytvoření **prázdného řešení** projektu. Název projektu, například `MediaCapture`.  
  
2.  Přidat **knihovny DLL (Universal Windows)** projektu k řešení. Název projektu, například `GrayscaleTransform`.  
  
3.  Přidat **soubor Midl (.)** souboru do projektu. Název souboru, například `GrayscaleTransform.idl`.  
  
4.  Tento kód vložte do GrayscaleTransform.idl.  
  
     [!code-cpp[wrl-media-capture#1](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]  
  
5.  Použijte následující kód k nahrazení obsah pch.h.  
  
     [!code-cpp[wrl-media-capture#2](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]  
  
6.  Přidejte do projektu nový soubor záhlaví, pojmenujte ji `BufferLock.h`a poté přidejte tento kód:  
  
     [!code-cpp[wrl-media-capture#3](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]  
  
7.  V tomto příkladu se nepoužije GrayscaleTransform.h. Můžete jej odebrat z projektu Pokud budete chtít.  
  
8.  Použijte následující kód k nahrazení obsah GrayscaleTransform.cpp.  
  
     [!code-cpp[wrl-media-capture#4](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]  
  
9. Přidejte do projektu nový soubor definice modulu, pojmenujte ji `GrayscaleTransform.def`a poté přidejte tento kód:  
  
   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```   
  
10. Použijte následující kód k nahrazení obsah dllmain.cpp.  
  
     [!code-cpp[wrl-media-capture#6](../windows/codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]  
  
11. V projektu **stránky vlastností** dialogové okno pole, nastavte následující **Linkeru** vlastnosti.  
  
    1.  V části **vstup**, pro **soubor definice modulu**, zadejte `GrayScaleTransform.def`.  
  
    2.  Také v části **vstup**, přidejte `runtimeobject.lib`, `mfuuid.lib`, a `mfplatf.lib` k **Další závislosti** vlastnost.  
  
    3.  V části **metadat Windows**, nastavte **generování metadat Windows** k **Ano (/ WINMD)**.  
  
### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>Použití knihovny WRL vlastní součást Media Foundation z aplikace C#  
  
1.  Přidejte nový **C# prázdná aplikace (XAML)** projektu do `MediaCapture` řešení. Název projektu, například `MediaCapture`.  
  
2.  V **MediaCapture** projekt, přidejte odkaz na `GrayscaleTransform` projektu. Další informace, jak zjistit, [postupy: Přidání nebo odebrání odkazů pomocí Správce odkazů](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).  
  
3.  V Package.appxmanifest na **možnosti** vyberte **mikrofon** a **webová kamera**. Obě možnosti jsou požadované pro zachycení fotografie z webové kamery.  
  
4.  V MainPage.xaml, přidejte tento kód do kořenového adresáře [mřížky](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx) element:  
  
     [!code-xml[wrl-media-capture#7](../windows/codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]  
  
5.  Použijte následující kód k nahrazení obsah MainPage.xaml.cs.  
  
     [!code-cs[wrl-media-capture#8](../windows/codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]  
  
 Následující obrázek znázorňuje MediaCapture aplikace.  
  
 ![Aplikace MediaCapture zaznamenávání fotografie](../windows/media/wrl_media_capture.png "WRL_Media_Capture")  
  
## <a name="next-steps"></a>Další kroky  
 Příklad ukazuje, jak zachytit fotografie z výchozí webová kamera, jeden v čase. [Ukázky rozšíření média](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) nemá informace. Ukazuje, jak výčet zařízení, webovou kameru a pracovat s místní schéma obslužné rutiny a předvádí důsledky dalšího média, které fungují na jednotlivé fotografie a datových proudů videa.  
  
## <a name="see-also"></a>Viz také  
 [Knihovna šablon C++ prostředí Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Microsoft Media Foundation](http://msdn.microsoft.com/library/windows/apps/ms694197)   
 [Ukázka rozšíření média](http://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)