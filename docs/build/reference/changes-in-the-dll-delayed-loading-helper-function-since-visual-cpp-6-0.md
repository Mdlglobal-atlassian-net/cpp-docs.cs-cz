---
title: Změny v podpůrné funkci knihovny DLL s odloženým načtením od aplikace Visual C++ verze 6.0
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
ms.openlocfilehash: 536729e27c89d068957ea451355957e4a35348ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320611"
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Změny v podpůrné funkci knihovny DLL s odloženým načtením od aplikace Visual C++ verze 6.0

Pokud máte v počítači více verzí visual c++ nebo pokud jste definovali vlastní pomocnou funkci, mohou být ovlivněny změnami provedenými v pomocné funkci zpožděného načítání dll. Příklad:

- **__delayLoadHelper** je nyní **__delayLoadHelper2**

- **__pfnDliNotifyHook** je nyní **__pfnDliNotifyHook2**

- **__pfnDliFailureHook** je nyní **__pfnDliFailureHook2**

- **__FUnloadDelayLoadedDLL** je nyní **__FUnloadDelayLoadedDLL2**

> [!NOTE]
> Pokud používáte výchozí pomocnou funkci, tyto změny vás neovlivní. Neexistují žádné změny týkající se způsobu vyvolání propojovacího evidenátoru.

## <a name="multiple-versions-of-visual-c"></a>Více verzí visual c++

Pokud máte v počítači více verzí visual c++, ujistěte se, že propojovací program odpovídá delayimp.lib. Pokud dojde k neshodě, zobrazí se hlášení chyb `___delayLoadHelper2@8` `___delayLoadHelper@8` propojovacího objektu jako nevyřešeného externího symbolu. První znamená nový linker se starým delayimp.lib, a druhý znamená starý linker s novým delayimp.lib.

Pokud se zobrazí nevyřešená chyba propojovacího systému, spusťte [dumpbin /linkermember](linkermember.md):1 na souboru delayimp.lib, který očekáváte, že bude obsahovat pomocnou funkci, abyste zjistili, která pomocná funkce je definována místo toho. Pomocná funkce může být také definována v souboru objektu; spustit [dumpbin /symboly](symbols.md) a hledat `delayLoadHelper(2)`.

Pokud víte, že máte propojovací program Visual C++ 6.0, pak:

- Spusťte dumpbin v souboru lib nebo obj pomocníka pro zpoždění a zjistěte, zda definuje **__delayLoadHelper2**. Pokud ne, odkaz se nezdaří.

- Definujte **__delayLoadHelper** v souboru lib nebo obj pomocníka pro zpoždění.

## <a name="user-defined-helper-function"></a>Uživatelem definovaná pomocná funkce

Pokud jste definovali vlastní pomocnou funkci a používáte aktuální verzi visual c++, postupujte takto:

- Přejmenujte pomocnou funkci na **__delayLoadHelper2**.

- Vzhledem k tomu, že ukazatele v popisovači zpoždění (ImgDelayDescr v delayimp.h) byly změněny z absolutní adresy (VAs) na relativní adresy (RVAs) pracovat podle očekávání v 32- a 64bitových programech, je třeba převést tyto zpět na ukazatele. Byla zavedena nová funkce: PFromRva, nalezená v delayhlp.cpp. Tuto funkci můžete použít u každého z polí v popisovači a převést je zpět na 32bitové nebo 64bitové ukazatele. Výchozí funkce pomocníka pro načítání zpoždění je i nadále dobrou šablonou, kterou lze použít jako příklad.

## <a name="load-all-imports-for-a-delay-loaded-dll"></a>Načíst všechny importy pro zpožděnou dll

Propojovací aplikace může načíst všechny importy z dll, které jste zadali zpoždění načten. Další informace naleznete [v tématu Načítání všech importů pro zpoždění načtenou dll.](loading-all-imports-for-a-delay-loaded-dll.md)

## <a name="see-also"></a>Viz také

[Základní informace o podpůrné funkci](understanding-the-helper-function.md)
