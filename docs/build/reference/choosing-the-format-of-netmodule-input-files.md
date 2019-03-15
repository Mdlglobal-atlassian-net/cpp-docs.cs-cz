---
title: Výběr formátu vstupních souborů .netmodule
ms.date: 11/04/2016
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
ms.openlocfilehash: d48bfe84210143db333d1e6b081acf1aa66980cf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807322"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>Výběr formátu vstupních souborů .netmodule

Soubor .obj jazyka MSIL (zkompilovaná [/CLR](clr-common-language-runtime-compilation.md)) může také sloužit jako soubor .netmodule.  soubory .obj obsahovat metadata a nativních symbolů.  modulů .NET obsahují pouze metadata.

Můžete předat soubor .obj jazyka MSIL do jiných kompilátoru Visual Studio prostřednictvím možnost kompilátoru/addmodule (ale mějte na paměti, že soubor .obj stane součástí výsledného sestavení a musí být součástí sestavení).  Možnost kompilátoru/addmodule mít například Visual C# a Visual Basic.

> [!NOTE]
>  Ve většině případů je potřeba do propojovacího programu předat souboru .obj z kompilace, která vytvoří modul .net.  Předá linkeru soubor .dll nebo modul .NET MSIL modulu může mít za následek LNK1107.

soubory .obj, včetně jejich přidružených .h souborů, které odkazují prostřednictvím #include zdroje, umožňují aplikacím C++ využívat nativní typy v modulu, zatímco v soubor .netmodule můžete využívat pouze spravované typy aplikace v jazyce C++.  Pokud se pokusíte předat soubor .obj, který chcete #using, informace o nativních typů nebude k dispozici. #include souboru .h soubor .obj místo.

Jiné kompilátory sady Visual Studio může využívat pouze spravované typy z modulu.

Použijte následující postup k určení, jestli je potřeba použít .netmodule nebo soubor .obj jako vstup modulu MSVC linkeru:

- Pokud vytváříte s kompilátorem Visual Studio než Visual C++, .netmodule vytvářet a používat .netmodule jako vstup do linkeru.

- Pokud používáte a kompilátorem MSVC vytvářet moduly a moduly se použije k vytvoření něco jiného než knihovnu,-li používat soubory .obj jako vstup linkeru; modulu produkované kompilátorem Nepoužívejte soubor .netmodule jako vstup.

- Pokud moduly se použije k vytvoření knihovny nativní (není spravované), použijte soubory .obj jako vstup modulu do linkeru a vygenerovat soubor knihovny LIB.

- Pokud moduly se použije k vytvoření spravované knihovny a všech modulů vstup do linkeru bude ověřitelný (vytvořený pomocí/clr: safe), použijte soubory .obj jako vstup modulu do linkeru a generovat DLL (sestavení) nebo soubor knihovny .netmodule (modul).

- Pokud moduly se použije k vytvoření spravované knihovny a jeden nebo více modulů vstup do linkeru se nevytvoří se jen parametrem/CLR, použijte soubory .obj jako vstup modulu do linkeru a generovat DLL (sestavení).  Pokud chcete vystavit spravované typy z knihovny a pokud chcete využívat nativní typy v knihovně aplikace C++, knihovny bude obsahovat soubory .obj pro moduly komponentu knihovny (budete také chtít odeslání souborů .h jednotlivých modulů takže může být odkazováno pomocí #include ze zdrojového kódu).

## <a name="see-also"></a>Viz také:

[Soubory .netmodule jako vstup linkeru](netmodule-files-as-linker-input.md)
