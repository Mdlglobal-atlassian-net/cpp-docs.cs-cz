---
title: Universal Windows Apps (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7ba556ee3803bb00f07032e0589209af2d32addf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591750"
---
# <a name="universal-windows-apps-c"></a>Univerzální aplikace pro Windows (C++)

Univerzální aplikace pro platformu Windows (UPW) začleněné sadu principů návrhu, které zdůrazňují jednoduché uživatelské rozhraní, které se zaměřením na obsah, který automaticky přizpůsobí velikosti různých obrazovek na různých zařízeních. Vytvoření uživatelského rozhraní ve značce XAML a kódu v nativním kódu C++. Můžete také vytvořit komponenty (knihovny DLL), které mohou být spotřebovány aplikací pro UWP, které jsou napsány v jiných jazycích. Plochy rozhraní API pro aplikace pro UPW je Windows Runtime, což je skvěle vytvořená knihovna, která poskytuje širokou škálu služeb operačního systému.

> [!TIP]
> Pro Windows 10 můžete použít převaděč aplikace přemostění na Desktop Pokud chcete zabalit desktopové aplikace pro nasazení přes Microsoft Store. Další informace najdete v tématu [pomocí modulu Runtime Visual C++ v projektu Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) a [přemostění na Desktop](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-cwinrt"></a>Aplikace UWP, které používají C + +/ WinRT

C + +/ WinRT je nový, pouze záhlaví založený na knihovně C++ language projekce prostředí Windows Runtime, který používá zcela standard C++, na rozdíl od s C + +/ CX implementace. C + +/ WinRT nepoužívá nestandardní syntaxe nebo Microsoft jazyková rozšíření, a plně využívá kompilátor C++ k vytvoření vysoce optimalizovaný výstup. Další informace najdete v tématu [C + +/ WinRT](/windows/uwp/cpp-and-winrt-apis). Úvod do jazyka C + +/ WinRT a kód rychlém startu najdete v části [Úvod do jazyka C + +/ WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

## <a name="uwp-apps-that-use-ccx"></a>Aplikace UWP, které používají C + +/ CX

|||
|-|-|
|[Referenční dokumentace jazyka Visual C++ (C + +/ CX)](../cppcx/visual-c-language-reference-c-cx.md)|Popisuje sadu rozšíření, která jazyce C++ zjednodušují spotřebu rozhraní API Windows Runtime a povolit zpracování chyb, které je založené na výjimkách.|
|[Sestavení aplikací a knihoven (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|Popisuje postup vytvoření DLL a statických knihoven, které mohou být přístupné z C + +/ CX aplikace nebo komponenty.|
|[Kurz: Vytvoření UPW aplikace "Hello, World" v jazyce C + +/ CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Návod, který představuje základní koncepty vývoje aplikací pro UPW v jazyce C + +/ CX. |
|[Vytváření komponent Windows Runtime v jazyce C + +/ CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Popisuje postup vytvoření DLL knihoven, které můžou využívat další aplikace UPW a součásti.|
|[Herní programování UPW](/windows/uwp/gaming/)|Popisuje, jak použít rozhraní DirectX a jazyka C + +/ CX vytváření her.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Aplikace UWP, které používají knihovna šablon C++ Windows Runtime (WRL)

Knihovna šablon C++ Windows Runtime nabízí nízkoúrovňová rozhraní modelu COM, podle kterých může kód ISO C++ přístup k prostředí Windows Runtime v prostředí bez výjimek. Ve většině případů doporučujeme použít C + +/ WinRT nebo C + +/ CX místo Windows Runtime knihovny šablon jazyka C++ pro vývoj aplikací pro UPW. Informace o knihovna šablon C++ Runtime Windows najdete v tématu [Windows Runtime C++ šablony knihovny (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Viz také:

[Visual C++](../visual-cpp-in-visual-studio.md)<br/>