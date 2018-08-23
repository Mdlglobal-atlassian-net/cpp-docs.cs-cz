---
title: Referenční dokumentace jazyka Visual C++ (C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/15/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 801a88573133a68beec4855dc499fcba27bb64e8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593866"
---
# <a name="visual-c-language-reference-ccx"></a>Referenční dokumentace jazyka Visual C++ (C + +/ CX)

C + +/ CX je sada rozšíření jazyka C++, které umožňují vytváření aplikací pro Windows a součásti prostředí Windows Runtime v idiom, který je co nejblíže k moderní C++. Pomocí C + +/ CX pro zápis aplikace Windows a komponenty v nativním kódu, který se snadno pracovat s Visual C#, Visual Basic a JavaScript a další jazyky, které podporují prostředí Windows Runtime. Ve vzácných případech, které vyžadují přímý přístup k nezpracované rozhraní modelu COM nebo nevýjimečným kódem, můžete použít [Windows Runtime C++ šablony knihovny (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

> [!NOTE]
> C + +/ WinRT je nový, standard C ++ 17 jazyk projekci pro rozhraní API Windows Runtime. Je k dispozici v nejnovější sadu Windows 10 SDK verze 1803 dále. C + +/ WinRT je implementované jenom v souborech hlaviček a navržená tak, aby poskytují přístup k prvotřídní moderní rozhraní Windows API.

> Pomocí C + +/ WinRT, můžete současně využívat a vytvářet rozhraní API Windows Runtime pomocí jakékoli standardům C ++ 17 kompilátoru. C + +/ WinRT obvykle vrací lepší výsledky a vytváří menší binárních souborů než jakékoli jiné možnosti jazyka prostředí Windows Runtime. Budeme dál podporovat C + +/ CX a WRL, ale důrazně doporučujeme, aby nové aplikace pomocí C + +/ WinRT. Další informace najdete v tématu [C + +/ WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/index).


S použitím C + +/ CX, můžete vytvořit:

- Aplikací C++ Universal Windows Platform (UWP), využívající XAML k definování uživatel rozhraní a používat nativní zásobníku. Další informace najdete v tématu [vytvořit aplikaci "hello world" v C++ (UPW)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

- Součásti modulu Windows Runtime C++, které mohou být spotřebovány aplikacemi Windows založené na jazyce JavaScript. Další informace najdete v tématu [vytváření komponent Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

- Hry rozhraní DirectX pro Windows a aplikace náročné na grafiku. Další informace najdete v tématu [vytvořit jednoduché hře pro UPW s rozhraním DirectX](/windows/uwp/gaming/tutorial--create-your-first-metro-style-directx-game).

## <a name="related-articles"></a>Související články

|||
|-|-|
|[Stručná referenční příručka](../cppcx/quick-reference-c-cx.md)|Tabulka klíčových slov a operátory pro C + +/ CX.|
|[Systém typů](../cppcx/type-system-c-cx.md)|Popisuje základní C + +/ CX typy a programovací konstrukce a jak využívat C + +/ CX využívat a vytvořit typy Windows Runtime.|
|[Vytváření aplikací a knihoven](../cppcx/building-apps-and-libraries-c-cx.md)|Popisuje, jak vytvářet aplikace a odkaz na aned statické knihovny DLL pomocí integrovaného vývojového prostředí.|
|[Spolupráce s jinými jazyky](../cppcx/interoperating-with-other-languages-c-cx.md)|Popisuje, jak komponenty, které jsou vytvořené pomocí jazyka C + +/ CX lze použít s komponentami, které jsou napsány v jazyce JavaScript, žádné spravované jazyka nebo knihovna šablon C++ Windows Runtime.|
|[Práce s vlákny a zařazování](../cppcx/threading-and-marshaling-c-cx.md)|Popisuje, jak můžete určit chování vláken a zařazování komponent, které vytvoříte.|
|[Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)|Referenční dokumentace pro výchozí obor názvů, obor názvů Platform, Platform::Collections – a související obory názvů.|
|[Nepodporované funkce CRT v aplikacích pro Univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|Seznam funkcí CRT, které nejsou k dispozici pro použití v aplikacích pro Windows Runtime.|
|[Postupy pro aplikace pro Windows 10](http://msdn.microsoft.com/library/windows/apps/xaml/mt244352.aspx)|Obsahuje základní pokyny pro aplikace pro Windows 10 a odkazy na další informace.|
|[C + +/ CX součástí 0 \[n\]: Úvod](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction/)<br /><br />[C + +/ CX, část 1 ze \[n\]: jednoduchou třídu](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class/)<br /><br />[C + +/ CX část 2 \[n\]: typy, které Wear Hats](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C + +/ CX část 3 \[n\]: vytvářený](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)<br /><br />[C + +/ CX část 4 \[n\]: statické členské funkce](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions/)|Úvodní sérii blogů Visual C++ v jazyce C + +/ CX.|
