---
title: Univerzální aplikace pro Windows (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.topic: overview
ms.openlocfilehash: 11a32504dfdd380f621c380994f4f53073547a57
ms.sourcegitcommit: 7750e4c291d56221c8893120c56a1fe6c9af60d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274706"
---
# <a name="universal-windows-apps-c"></a>Univerzální aplikace pro Windows (C++)

Univerzální platforma Windows (UWP) je moderní programovací rozhraní pro Windows. Pomocí UWP sami napíšete aplikaci nebo komponentu a nasadíte ji na libovolné zařízení s Windows 10. Můžete napsat komponentu v C++ aplikaci a aplikace napsané v jakémkoli jiném jazyku, který je kompatibilní s UWP, může použít.

Většina dokumentace UWP je ve stromu obsahu Windows v [dokumentaci Univerzální platforma Windows](/windows/uwp/). Najdete tady úvodní kurzy a referenční dokumentaci. 

Pro nové aplikace a komponenty UWP doporučujeme používat [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), novou standardní projekci jazyka c++ 17 pro prostředí Windows Runtime API. C++/WinRT je k dispozici v sadě Windows 10 SDK od verze 1803 další. C++/WinRT je implementováno zcela v hlavičkových souborech a je navrženo tak, aby vám poskytovala prvotřídní přístup k modernímu rozhraní Windows API. Na C++rozdíl od implementace/CX. C++/WinRT nepoužívá nestandardní syntaxi nebo jazykové rozšíření od Microsoftu a plně využívá C++ kompilátor k vytváření vysoce optimalizovaného výstupu. Další informace najdete v tématu [Úvod do C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

Pomocí převaděče aplikace pro stolní počítače můžete zabalit stávající desktopovou aplikaci pro nasazení prostřednictvím Microsoft Store. Další informace najdete v tématu [použití modulu C++ Visual runtime v Centennialm projektu](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) a [desktopového mostu](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-ccx"></a>Aplikace UWP používající C++/CX

|||
|-|-|
|[C++/CX – Referenční dokumentace jazyka](visual-c-language-reference-c-cx.md)|V této části najdete popis sady rozšíření C++ , které zjednodušují spotřebu rozhraní prostředí Windows Runtime API a umožňují zpracování chyb založené na výjimkách.|
|[Sestavení aplikací a knihoven (C++/CX)](building-apps-and-libraries-c-cx.md)|Popisuje postup vytvoření knihoven DLL a statických knihoven, které jsou k dispozici z aplikace nebo komponenty C++/CX.|
|[Kurz: Vytvoření aplikace pro UWP "Hello, World" C++v/CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Návod, který zavádí základní koncepty vývoje aplikací pro UWP v C++/CX. |
|[Vytváření komponent prostředí Windows Runtime v C++/CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Popisuje postup vytvoření knihoven DLL, které mohou využívat jiné aplikace a komponenty UWP.|
|[Programování her pro UWP](/windows/uwp/gaming/)|Popisuje způsob použití rozhraní DirectX a C++/CX k vytváření her.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Aplikace UWP, které používají knihovnu C++ šablon prostředí Windows Runtime (WRL)

Knihovna šablon C++ prostředí Windows Runtime poskytuje rozhraní COM nízké úrovně, podle kterého může kód ISO C++ přistupovat k prostředí Windows Runtime v prostředí bez výjimky. Ve většině případů doporučujeme použít C++/WinRT nebo C++/cx namísto knihovny šablon prostředí Windows Runtime C++ pro vývoj aplikací pro UWP. Informace o prostředí Windows Runtime C++ knihovně šablon naleznete v tématu [Knihovna šablon C++ prostředí Windows Runtime (WRL)](wrl/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Viz také:

[C++ v sadě Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Přehled programování v C++ v systému Windows](../windows/overview-of-windows-programming-in-cpp.md)<br/>