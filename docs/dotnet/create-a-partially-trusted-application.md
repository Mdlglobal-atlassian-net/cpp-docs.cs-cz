---
title: 'Postupy: Vytvoření částečně důvěryhodné aplikace (C + +/ CLI)'
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
ms.openlocfilehash: fb65c8ff3dc4c3b03fa319fd1e7a6eb95f11bef2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445965"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>Postupy: Vytvoření částečně důvěryhodné aplikace odebráním závislosti na modulu DLL knihovny CRT

Toto téma popisuje, jak vytvořit pomocí jazyka Visual C++ odebráním závislosti na msvcm90.dll částečně důvěryhodné aplikace Common Language Runtime.

Sestavován aplikace Visual C++ **/CLR** bude mít závislost na msvcm90.dll, která je součástí knihovny C Runtime. Pokud chcete, aby vaše aplikace pro použití v prostředí s částečným vztahem důvěryhodnosti, modul CLR bude vynucovat určitá pravidla zabezpečení přístupu kódu na vaše knihovna DLL. Proto je potřeba tuto závislost odeberete, protože msvcm90.dll obsahující nativní kód a na něm nedají vynutit zásady zabezpečení přístupu kódu.

Pokud chcete odebrat závislost na tuto knihovnu v kódu aplikace nepoužívá žádné funkce knihovny C Runtime, budete muset použít **/NODEFAULTLIB:msvcmrt.lib** – možnost linkeru a propojení s knihovnou ptrustm.lib nebo ptrustmd.lib. Tyto knihovny obsahovat objektové soubory pro inicializaci a rušení inicializace aplikace, používá inicializační kód třídy výjimek a spravovaného kódu pro zpracování výjimek. Propojení v jednom z těchto knihoven odebere závislost na msvcm90.dll.

> [!NOTE]
>  Pořadí sestavení rušení inicializace se mohou lišit pro aplikace, které používají ptrust knihovny. Pro běžné aplikace sestavení jsou obvykle byla uvolněna v obráceném pořadí, která jsou načtena, ale to není zaručeno. Pro aplikace s částečnou důvěryhodností sestavení jsou obvykle byla uvolněna ve stejném pořadí, že jsou načteny. To také, není zaručeno.

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>K vytvoření částečně důvěryhodné smíšený (/ clr) aplikace

1. Odebrat závislost na msvcm90.dll, je nutné zadat linkeru, aby vložit tuto knihovnu pomocí **/NODEFAULTLIB:msvcmrt.lib** – možnost linkeru. Informace o tom, jak to udělat pomocí vývojového prostředí sady Visual Studio nebo prostřednictvím kódu programu, najdete v článku [: / NODEFAULTLIB (ignorování knihoven)](../build/reference/nodefaultlib-ignore-libraries.md).

1. Přidejte jeden z knihovny ptrustm vstupní závislostí linkeru. Pokud vytváříte aplikaci v režimu vydání, použijte ptrustm.lib. U režimu ladění použijte ptrustmd.lib. Informace o tom, jak to udělat pomocí vývojového prostředí sady Visual Studio nebo prostřednictvím kódu programu, najdete v článku [. Lib soubory jako vstup Linkeru](../build/reference/dot-lib-files-as-linker-input.md).

## <a name="see-also"></a>Viz také

[Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[Inicializace smíšených sestavení](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[Podpora knihovny pro smíšená sestavení](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/link (předání možností do linkeru)](../build/reference/link-pass-options-to-linker.md)
