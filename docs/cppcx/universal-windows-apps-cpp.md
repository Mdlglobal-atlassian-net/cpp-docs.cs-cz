---
title: Univerzální aplikace pro Windows (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.openlocfilehash: fbd5366ee52dfe32baef9458a82c16914666699e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392060"
---
# <a name="universal-windows-apps-c"></a>Univerzální aplikace pro Windows (C++)

Univerzální platforma Windows (UPW) je moderní programovací rozhraní pro Windows. S UWP zápisu aplikace nebo komponenty jednou a nasadit virtuální počítač na všechna zařízení s Windows 10. Můžete napsat komponenty v jazyce C++ a aplikace napsané v jiném jazyce kompatibilním UPW ji použít.

Většina dokumentace k UPW je ve stromu obsahu Windows na [dokumentace k univerzální platformě Windows](/windows/uwp/). Zde najdete kurzy od také jako referenční dokumentaci. 

Pro nové aplikace pro UPW a komponenty, doporučujeme použít [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), nový standard C ++ 17 jazyk projekci pro rozhraní API Windows Runtime. C++/ WinRT je k dispozici v sadě SDK Windows 10 verze 1803 dále. C++/ WinRT je implementovaný zcela v souborech hlaviček a je navržené pro poskytování je prvotřídní přístup k moderní rozhraní Windows API. Na rozdíl od C++/CX implementace. C++/ WinRT nepoužívá nestandardní syntaxe nebo jazyková rozšíření Microsoft a trvá naplno využít C++ kompilátoru k vytvoření vysoce optimalizovaný výstup. Další informace najdete v tématu [Úvod do C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

Převaděč aplikace přemostění na Desktop můžete balíček desktopové aplikace pro nasazení přes Microsoft Store. Další informace najdete v tématu [pomocí modulu Runtime Visual C++ v projektu Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) a [přemostění na Desktop](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-ccx"></a>Aplikace UWP, které používají C++/CX

|||
|-|-|
|[Vizuální C++ referenční informace k jazyku (C++/CX)](visual-c-language-reference-c-cx.md)|Popisuje sadu rozšíření, která jazyce C++ zjednodušují spotřebu rozhraní API Windows Runtime a povolit zpracování chyb, které je založené na výjimkách.|
|[Sestavení aplikací a knihoven (C++/CX)](building-apps-and-libraries-c-cx.md)|Popisuje postup vytvoření DLL a statických knihoven, které lze přistupovat z C++/CX aplikace nebo komponenty.|
|[Kurz: Vytvoření UPW aplikace "Hello, World" v C++/CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Návod, který představuje základní koncepty vývoje aplikací pro UWP v C++/CX. |
|[Vytváření komponent Windows Runtime v C++/CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Popisuje postup vytvoření DLL knihoven, které můžou využívat další aplikace UPW a součásti.|
|[Herní programování UPW](/windows/uwp/gaming/)|Popisuje, jak použít rozhraní DirectX a C++/CX vytváření her.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Aplikace UWP, které používají knihovna šablon C++ Windows Runtime (WRL)

Knihovna šablon C++ Windows Runtime nabízí nízkoúrovňová rozhraní modelu COM, podle kterých může kód ISO C++ přístup k prostředí Windows Runtime v prostředí bez výjimek. Ve většině případů doporučujeme použít C++/WinRT nebo C++/CX místo modulu Windows Runtime C++ šablony knihovny pro vývoj aplikací pro UPW. Informace o knihovna šablon C++ Runtime Windows najdete v tématu [Windows Runtime C++ šablony knihovny (WRL)](wrl/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Viz také:

[C++ v sadě Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Přehled programování v C++ v systému Windows](../windows/overview-of-windows-programming-in-cpp.md)<br/>