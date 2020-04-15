---
title: 'Postup: Vytvoření částečně důvěryhodné aplikace (C++/CLI)'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- partially trusted applications [C++]
- mixed assemblies [C++], partially trusted applications
- msvcm90[d].dll
- interoperability [C++], partially trusted applications
- interop [C++], partially trusted applications
- /clr compiler option [C++], partially trusted applications
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
ms.openlocfilehash: 9df3a751f4073472b9495425599aaf43878db99a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364405"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>Postupy: Vytvoření částečně důvěryhodné aplikace odebráním závislosti na modulu DLL knihovny CRT

Toto téma popisuje, jak vytvořit částečně důvěryhodnou aplikaci Common Language Runtime pomocí visual c++ odebráním závislosti na souboru msvcm90.dll.

Aplikace Visual C++ vytvořená pomocí **/clr** bude mít závislost na souboru msvcm90.dll, který je součástí knihovny C-Runtime. Pokud chcete, aby vaše aplikace byla použita v prostředí částečné důvěryhodnosti, CLR vynutí určitá pravidla zabezpečení přístupu kódu na vaší dll. Proto bude nutné tuto závislost odebrat, protože soubor msvcm90.dll obsahuje nativní kód a nelze v ní vynutit zásady zabezpečení přístupu kódu.

Pokud vaše aplikace nepoužívá žádné funkce knihovny C-Runtime a chcete odebrat závislost na této knihovně z vašeho kódu, budete muset použít **/NODEFAULTLIB:msvcmrt.lib** linker možnost a propojení s ptrustm.lib nebo ptrustmd.lib. Tyto knihovny obsahují soubory objektů pro inicializaci a zrušení inicializace aplikace, třídy výjimek používané inicializačním kódem a kód zpracování spravovaných výjimek. Propojení v jedné z těchto knihoven odebere všechny závislosti na souboru msvcm90.dll.

> [!NOTE]
> Pořadí neinicializace sestavení se může lišit pro aplikace, které používají knihovny ptrust. U běžných aplikací jsou sestavení obvykle uvolněna v opačném pořadí, ve které jsou načtena, ale to není zaručeno. U aplikací s částečnou důvěryhodností jsou sestavení obvykle uvolněna ve stejném pořadí, v jakém jsou načtena. To také není zaručeno.

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>Vytvoření částečně důvěryhodné smíšené (/clr) aplikace

1. Chcete-li odebrat závislost na souboru msvcm90.dll, je nutné zadat propojovacímu programu, aby tuto knihovnu nezahrnoval, pomocí možnosti propojovacího programu **/NODEFAULTLIB:msvcmrt.lib.** Informace o tom, jak to provést pomocí vývojového prostředí sady Visual Studio nebo programově, naleznete [v tématu /NODEFAULTLIB (Ignorovat knihovny).](../build/reference/nodefaultlib-ignore-libraries.md)

1. Přidejte jednu z knihoven ptrustm do závislostí vstupu linkeru. Pokud vytváříte aplikaci v režimu vydání, použijte soubor ptrustm.lib. Pro režim ladění použijte ptrustmd.lib. Informace o tom, jak to provést pomocí vývojového prostředí sady Visual Studio nebo programově, naleznete v tématu [. Lib soubory jako linker vstup](../build/reference/dot-lib-files-as-linker-input.md).

## <a name="see-also"></a>Viz také

[Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[Inicializace smíšených sestav](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[Podpora knihovny pro smíšená sestavení](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/link (předání možností linkeru)](../build/reference/link-pass-options-to-linker.md)
