---
title: "Postupy: Vytvoření částečně důvěryhodné aplikace (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- partially trusted applications [C++]
- mixed assemblies [C++], partially trusted applications
- msvcm90[d].dll
- interoperability [C++], partially trusted applications
- interop [C++], partially trusted applications
- /clr compiler option [C++], partially trusted applications
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c91bcfeec3e6f9d7403b9797ccebe532f0751d70
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>Postupy: Vytvoření částečně důvěryhodné aplikace odebráním závislosti na modulu DLL knihovny CRT
Toto téma popisuje postup vytvoření částečně důvěryhodné aplikace modul Common Language Runtime Visual C++ pomocí odebráním závislosti na msvcm90.dll.  
  
 Visual C++ aplikace vytvořené s **/CLR** bude mít závislost na msvcm90.dll, která je součástí knihovny C Runtime. Když chcete, aby vaše aplikace, který se má použít v prostředí s částečnou důvěryhodností, modul CLR bude vynutit určitá pravidla zabezpečení přístupu kódu na vaše knihovna DLL. Proto bude potřeba tuto závislost odeberete, protože obsahuje msvcm90.dll nativního kódu a na něm nelze vynutit zásady zabezpečení přístupu kódu.  
  
 Pokud vaše aplikace nepoužívá žádné funkce knihoven C Runtime a chcete odebrat závislost na tuto knihovnu z vašeho kódu, budete muset použít **/NODEFAULTLIB:msvcmrt.lib** – možnost linkeru a odkaz s ptrustm.lib nebo ptrustmd.lib. Tyto knihovny obsahovat soubory objektů pro inicializaci a uninitialization aplikace, třídy výjimek používaný kód inicializace a spravovaný kód zpracování výjimek. Propojení v jednom z těchto knihoven odebere závislost na msvcm90.dll.  
  
> [!NOTE]
>  Pořadí sestavení uninitialization se mohou lišit pro aplikace, které používají ptrust knihovny. Pro běžné aplikace jsou obvykle odpojeno sestavení v obráceném pořadí, které budou načtena, ale to není zaručena. Pro aplikace s částečnou důvěryhodností jsou obvykle ve stejném pořadí, že jsou načtená odpojeno sestavení. To také není zaručena.  
  
### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>K vytvoření částečně důvěryhodné ve smíšeném (/ clr) aplikace  
  
1.  Chcete-li odebrat závislost na msvcm90.dll, musíte zadat linkeru není, aby používaly tuto knihovnu pomocí **/NODEFAULTLIB:msvcmrt.lib** – možnost linkeru. Informace o tom, jak to provést pomocí vývojovém prostředí sady Visual Studio nebo prostřednictvím kódu programu, najdete v části [/NODEFAULTLIB (Ignorovat knihovny)](../build/reference/nodefaultlib-ignore-libraries.md).  
  
2.  Přidejte jedno z knihovny ptrustm vstupní závislosti linkeru. Ptrustm.lib použijte, pokud vytváříte aplikace v režimu vydání. Režim ladění použijte ptrustmd.lib. Informace o tom, jak to provést pomocí vývojovém prostředí sady Visual Studio nebo prostřednictvím kódu programu, najdete v části [. Lib soubory jako vstup Linkeru](../build/reference/dot-lib-files-as-linker-input.md).  
  
## <a name="see-also"></a>Viz také  
 [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)   
 [Inicializace smíšených sestavení](../dotnet/initialization-of-mixed-assemblies.md)   
 [Podpora knihovny pro smíšená sestavení](../dotnet/library-support-for-mixed-assemblies.md)   
 [/ Link (předání možností Linkeru)](../build/reference/link-pass-options-to-linker.md)   
