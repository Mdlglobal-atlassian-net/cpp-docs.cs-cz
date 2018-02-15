---
title: "Referenční dokumentace jazyka Visual C++ (C + +/ CX) | Microsoft Docs"
ms.custom: 
ms.date: 09/15/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0867cb30f1337ffaf1cb726a0c52977899f02d0a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="visual-c-language-reference-ccx"></a>Referenční dokumentace jazyka Visual C++ (C + +/ CX)

C + +/ CX je sada rozšíření pro jazyk C++, které umožňují vytvářet aplikace pro Windows a součásti prostředí Windows Runtime v stylu, které jsou dle zavřete jako moderní možné C++. Použijte C + +/ CX zápis aplikací pro Windows a součásti v nativním kódu, který se snadno pracovat s Visual C#, Visual Basic a JavaScript a další jazyky, které podporují prostředí Windows Runtime. Ve vzácných případech vyžadující přímý přístup k nezpracované rozhraní modelu COM nebo ostatním kódu, můžete použít [Windows Runtime C++ šablony knihovny (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

Nový model představuje novou generaci nativní C++ programování v systému Windows. Použití, můžete vytvořit:

- Aplikace C++ Universal Windows Platform (UWP), které používají XAML k definování uživatel rozhraní a používat nativní zásobníku. Další informace najdete v tématu [vytvořit aplikaci "hello, world" v C++ (UWP)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

- C++ prostředí Windows Runtime součásti, které mohou být spotřebovávána aplikací pro Windows na základě jazyka JavaScript. Další informace najdete v tématu [vytváření součásti systému Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

- Windows DirectX hry a aplikace náročné na grafiky. Další informace najdete v tématu [vytvořit jednoduchou UWP hru s DirectX](/windows/uwp/gaming/tutorial--create-your-first-metro-style-directx-game).

## <a name="related-articles"></a>Související články

|||
|-|-|
|[Stručná referenční příručka](../cppcx/quick-reference-c-cx.md)|Tabulku klíčová slova a operátory jazyka C + +/ CX.|
|[Systém typů](../cppcx/type-system-c-cx.md)|Popisuje základní C + +/ CX typy a programovací konstrukce a jak využívat C + +/ CX spotřebovat a vytvoří typy prostředí Windows Runtime.|
|[Vytváření aplikací a knihovny](../cppcx/building-apps-and-libraries-c-cx.md)|Popisuje, jak vytvářet aplikace a odkaz na aned statické knihovny DLL pomocí rozhraní IDE.|
|[Spolupráce s jinými jazyky](../cppcx/interoperating-with-other-languages-c-cx.md)|Popisuje, jak součásti, které jsou zapsány pomocí C + +/ CX lze použít s součástí, které jsou napsané v jazyce JavaScript, některé spravovány jazyka, nebo [!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)].|
|[Dělení na vlákna a zařazování](../cppcx/threading-and-marshaling-c-cx.md)|Popisuje, jak určit způsob chování vláken a zařazování komponent, které vytvoříte.|
|[Odkaz na obory názvů](../cppcx/namespaces-reference-c-cx.md)|Referenční dokumentace pro výchozí obor názvů, obor názvů Platform, Platform::Collections a související obory názvů.|
|[Nepodporované funkce CRT v aplikacích pro Univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|Obsahuje seznam funkcí CRT, které nejsou k dispozici pro použití v aplikacích pro prostředí Windows Runtime.|
|[Postup příručky pro aplikace pro Windows 10](http://msdn.microsoft.com/library/windows/apps/xaml/mt244352.aspx)|Obsahuje základní pokyny pro aplikace pro Windows 10 a odkazy na další informace.|
|[C + +/ CX část 0 \[ n \]: Úvod](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction/)<br /><br />[C + +/ CX část 1 / \[ n \]: jednoduchý – třída](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class/)<br /><br />[C + +/ CX část 2 / \[ n \]: typy, které nosit klobouky](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C + +/ CX části 3 \[ n \]: v části vytváření](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)<br /><br />[C + +/ CX část 4 \[ n \]: statické členské funkce](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions/)|Úvodní blog řady Visual C++ v jazyce C + +/ CX.|
