---
title: Referenční C++ dokumentace jazyka VisualC++(/CX)
ms.date: 09/15/2017
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
ms.openlocfilehash: 0b2d344f9889d5669164cd917ba569b5f35d83a5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498427"
---
# <a name="visual-c-language-reference-ccx"></a>Referenční C++ dokumentace jazyka VisualC++(/CX)

C++/CX je sada rozšíření C++ , která umožňují vytváření aplikací pro Windows a prostředí Windows Runtime komponent v idiom, která je co nejblíže k modernímu. C++ Pomocí C++technologie/CX můžete psát aplikace a komponenty pro Windows v nativním kódu, který C#umožňuje snadnou interakci s visualmi, Visual Basicmi a JavaScriptu a dalšími jazyky, které podporují prostředí Windows Runtime. V těchto vzácných případech, které vyžadují přímý přístup k nezpracovaným rozhraním COM nebo nevýjimečný kód, můžete [použít C++ knihovnu šablon prostředí Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

> [!NOTE]
> **/WinRT je Doporučená alternativa pro C++/CX. [ C++](/windows/uwp/cpp-and-winrt-apis/index) Je to nová standardní jazyková projekce C++ 17 pro rozhraní prostředí Windows Runtime API, která je k dispozici v nejnovější sadě Windows 10 SDK verze 1803. C++/WinRT je implementována zcela v hlavičkových souborech a je navržena tak, aby vám poskytovala prvotřídní přístup k modernímu rozhraní Windows API.
>
> Pomocí C++/WinRT můžete využívat i vytvářet prostředí Windows Runtime rozhraní API pomocí všech kompilátorů c++ 17 odpovídajících standardům. C++/WinRT obvykle provádí lepší a vytváří menší binární soubory než jakákoli jiná možnost jazyka pro prostředí Windows Runtime. Budeme dál podporovat C++/CX a WRL, ale důrazně doporučujeme, aby nové aplikace používaly C++/WinRT. Další informace najdete v tématu [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index).

Pomocí nástroje C++/CX můžete vytvořit:

- C++Aplikace Univerzální platforma Windows (UWP), které používají jazyk XAML k definování uživatelského rozhraní a používání nativního zásobníku. Další informace najdete v tématu [Vytvoření aplikace Hello World v C++ (UWP)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

- C++Prostředí Windows Runtime komponenty, které mohou být spotřebovány aplikacemi pro Windows založenými na jazyce JavaScript. Další informace naleznete v tématu [Creating prostředí Windows Runtime Components C++in ](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

- Hry rozhraní Windows DirectX a aplikace náročné na grafiku. Další informace najdete v tématu [Vytvoření jednoduché hry UWP s rozhraním DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game).

## <a name="related-articles"></a>Související články

|||
|-|-|
|[Stručná referenční dokumentace](../cppcx/quick-reference-c-cx.md)|Tabulka klíčových slov a operátorů C++pro/CX.|
|[Systém typů](../cppcx/type-system-c-cx.md)|Popisuje základní C++typy/CX a programovací konstrukce a způsob využití C++nástrojů/CX ke využívání a vytváření prostředí Windows runtimech typů.|
|[Sestavení aplikací a knihoven](../cppcx/building-apps-and-libraries-c-cx.md)|Popisuje, jak používat integrované vývojové prostředí k vytváření aplikací a propojení se statickými knihovnami a knihovnami DLL.|
|[Spolupráce s jinými jazyky](../cppcx/interoperating-with-other-languages-c-cx.md)|Popisuje, jak lze součásti, které jsou C++zapsány pomocí rozhraní/CX, použít s komponentami, které jsou napsány v jazyce C++ JavaScript, jakémkoli spravovaném jazyce nebo knihovně šablon prostředí Windows Runtime.|
|[Dělení do vláken a zařazování](../cppcx/threading-and-marshaling-c-cx.md)|Popisuje, jak zadat chování vláken a zařazování pro komponenty, které vytvoříte.|
|[Referenční informace o oborech názvů](../cppcx/namespaces-reference-c-cx.md)|Referenční dokumentace pro výchozí obor názvů, obor názvů platformy, Platform:: Collections a související obory názvů.|
|[Nepodporované funkce CRT v aplikacích pro Univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|Obsahuje seznam funkcí CRT, které nejsou k dispozici pro použití v aplikacích prostředí Windows Runtime.|
|[Začínáme s aplikacemi pro Windows 10](/windows/uwp/get-started/)|Poskytuje základní informace o aplikacích pro Windows 10 a odkazy na Další informace.|
|[C++/CX – část 0 \[z\]n: Úvod](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction/)<br /><br />[C++/CX – část 1 \[z\]n: Jednoduchá třída](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class/)<br /><br />[C++/CX – část 2 \[z\]n: Typy, které nosit Hats](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C++/CX – část 3 \[z\]n: Pod konstrukcí](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)<br /><br />[C++/CX – část 4 \[z\]n: Statické členské funkce](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions/)|Úvodní vizuál C++ série blogů na C++/CX.|
