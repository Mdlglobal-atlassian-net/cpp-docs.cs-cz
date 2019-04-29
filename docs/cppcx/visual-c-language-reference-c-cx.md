---
title: Vizuální C++ referenční informace k jazyku (C++/CX)
ms.date: 09/15/2017
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
ms.openlocfilehash: ce0272499b653b9077a891e39e9b29797e7e051d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384943"
---
# <a name="visual-c-language-reference-ccx"></a>Vizuální C++ referenční informace k jazyku (C++/CX)

C++/CX je sada rozšíření C++ jazyk, který umožňují vytváření aplikací pro Windows a součásti prostředí Windows Runtime v idiom, který je co nejblíže k moderní C++. Použití C++/CX pro zápis aplikace Windows a komponenty v nativním kódu, který snadno pracovat s Vizuálem C#, Visual Basic a JavaScript a další jazyky, které podporují prostředí Windows Runtime. Ve vzácných případech, které vyžadují přímý přístup k nezpracované rozhraní modelu COM nebo nevýjimečným kódem, můžete použít [Windows Runtime C++ šablony knihovny (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

> [!NOTE]
> **[C++/ WinRT](/windows/uwp/cpp-and-winrt-apis/index) je doporučenou alternativou k C++/CX**. Je nový, standard C ++ 17 jazyk projekci pro API Windows Runtime, k dispozici v nejnovější sadu Windows 10 SDK verze 1803 dále. C++/ WinRT je implementována zcela v souborech hlaviček a navržená tak, aby poskytují přístup k prvotřídní moderní rozhraní Windows API.
>
> S C++/WinRT, můžete současně využívat a vytvářet rozhraní API Windows Runtime pomocí jakékoli standardům C ++ 17 kompilátoru. C++/ WinRT obvykle vrací lepší výsledky a vytváří menší binárních souborů než jakékoli jiné možnosti jazyka prostředí Windows Runtime. Budeme dál podporovat C++/CX a WRL, ale důrazně doporučujeme, aby nové aplikace pomocí C++/WinRT. Další informace najdete v tématu [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index).

S použitím C++/CX, můžete vytvořit:

- Aplikací C++ Universal Windows Platform (UWP), využívající XAML k definování uživatel rozhraní a používat nativní zásobníku. Další informace najdete v tématu [vytvořit aplikaci "hello world" v C++ (UPW)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

- Součásti modulu Windows Runtime C++, které mohou být spotřebovány aplikacemi Windows založené na jazyce JavaScript. Další informace najdete v tématu [vytváření komponent Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

- Hry rozhraní DirectX pro Windows a aplikace náročné na grafiku. Další informace najdete v tématu [vytvořit jednoduché hře pro UPW s rozhraním DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game).

## <a name="related-articles"></a>Související články

|||
|-|-|
|[Stručná referenční dokumentace](../cppcx/quick-reference-c-cx.md)|Tabulka klíčových slov a operátory pro C++/CX.|
|[Systém typů](../cppcx/type-system-c-cx.md)|Popisuje základní C++/CX typy a programovací konstrukce a jak využívat C++/CX využívat a vytvořit typy Windows Runtime.|
|[Sestavení aplikací a knihoven](../cppcx/building-apps-and-libraries-c-cx.md)|Popisuje, jak použít rozhraní IDE k sestavování aplikací a propojit statických knihoven a knihovny DLL.|
|[Spolupráce s jinými jazyky](../cppcx/interoperating-with-other-languages-c-cx.md)|Popisuje, jak komponenty, které jsou vytvořené pomocí C++/CX lze použít s komponentami, které jsou napsány v jazyce JavaScript, žádné spravované jazyk nebo modul Runtime Windows C++ knihovny šablon.|
|[Dělení do vláken a zařazování](../cppcx/threading-and-marshaling-c-cx.md)|Popisuje, jak můžete určit chování vláken a zařazování komponent, které vytvoříte.|
|[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)|Referenční dokumentace pro výchozí obor názvů, obor názvů Platform, Platform::Collections – a související obory názvů.|
|[Nepodporované funkce CRT v aplikacích pro Univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|Seznam funkcí CRT, které nejsou k dispozici pro použití v aplikacích pro Windows Runtime.|
|[Postupy pro aplikace pro Windows 10](https://msdn.microsoft.com/library/windows/apps/xaml/mt244352.aspx)|Obsahuje základní pokyny pro aplikace pro Windows 10 a odkazy na další informace.|
|[C++/CX součástí 0 \[n\]: Úvod](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction/)<br /><br />[C++/CX 1. části \[n\]: Jednoduchá třída](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class/)<br /><br />[C++/CX část 2 \[n\]: Typy, které Hats Wear](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C++/CX část 3 \[n\]: Ve výstavbě](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)<br /><br />[C++/CX část 4 \[n\]: Statické členské funkce](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions/)|Úvodní Visual C++ blogovou sérii na C++/CX.|
