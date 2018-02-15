---
title: "Univerzální aplikace pro Windows (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a293f833de7bc575209089362bcaf146d074684b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="universal-windows-apps-c"></a>Univerzální aplikace pro Windows (C++)
Univerzální aplikace pro platformu Windows (UWP) obsahují sadu Principy návrhu, které zdůraznil jednoduchého uživatelského rozhraní, které zahrnují obsah, který automaticky přizpůsobí pro jiné velikosti obrazovky na různých zařízeních. Vytvoření uživatelského rozhraní v XAML značek a kódu v nativním kódu C++. Můžete také vytvořit komponent (DLL), které mohou být spotřebovávána aplikace UWP, které jsou zapsány v dalších jazycích. Plochy rozhraní API pro aplikace UWP je prostředí Windows Runtime, který je dobře započítané knihovny, která poskytuje širokou škálu služeb operačního systému.  

> [!TIP]  
> Pro Windows 10 můžete aplikaci převaděč plochy do balíčku plochy aplikace pro nasazení prostřednictvím Microsoft Store. Další informace najdete v tématu [pomocí modulu Runtime Visual C++ v projektu Centennial](https://blogs.msdn.microsoft.com/vcblog/2016/07/07/using-visual-c-runtime-in-centennial-project) a [přineste vaší aplikace na ploše do univerzální platformu Windows (UWP) s most plochy](https://msdn.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-root).
  
  
## <a name="uwp-apps-that-use-ccx"></a>Aplikace UWP, které používají C + +/ CX  
  
|||  
|-|-|  
|[Referenční příručka jazyka Visual C++ (C + +/ CX)](../cppcx/visual-c-language-reference-c-cx.md)|Popisuje sadu rozšíření, které zjednodušují C++ spotřeba rozhraní API systému Windows Runtime a povolit zpracování chyb, který je založen na výjimky.|  
|[Sestavení aplikací a knihoven (C++/CX)](../cppcx/building-apps-and-libraries-c-cx.md)|Popisuje postup vytvoření knihovny DLL a statických knihoven, které lze přistupovat z C + +/ CX aplikace nebo součást.|  
|[Kurz: Vytvoření první aplikace UWP s použitím jazyka C++](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Návod, který představuje základní koncepty vývoj aplikací UWP v jazyce C++. (Ještě nebyla aktualizována pro vývoj UWP ve Windows 10.)|  
|[Vytváření Windows Runtime komponent v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Popisuje postup vytvoření knihovny DLL, které můžou využívat jiné aplikace UWP a součásti.|  
|[Vývoj her](https://docs.microsoft.com/en-us/windows/uwp/gaming/)|Popisuje, jak používat rozhraní DirectX a C++ pro vytvoření hry.|  
  
## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Aplikace UWP, které používají Windows knihovna šablon C++ Runtime (WRL) 
 Knihovna šablon C++ Runtime Windows poskytuje nízké úrovně rozhraní modelu COM, po které ISO C++ – kód přístup k prostředí Windows Runtime v prostředí bez výjimky. Ve většině případů doporučujeme použít C + +/ CX místo Windows knihovna šablon C++ Runtime pro vývoj aplikací UWP. Informace o knihovna šablon C++ Runtime Windows najdete v tématu [Windows Runtime C++ šablony knihovny (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  
  
## <a name="see-also"></a>Viz také  
 [Visual C++](../visual-cpp-in-visual-studio.md)

