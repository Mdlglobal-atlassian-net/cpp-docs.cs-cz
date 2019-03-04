---
title: Podpora linkeru pro knihovny DLL s odloženým načtením
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, linker support
ms.assetid: b2d7e449-2809-42b1-9c90-2c0ca5e31a14
ms.openlocfilehash: 2ff5143b8c3850386f73ff713e7986fdc3b59fd1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301386"
---
# <a name="linker-support-for-delay-loaded-dlls"></a>Podpora linkeru pro knihovny DLL s odloženým načtením

Linker Visual C++ teď podporuje opožděné načtení knihoven DLL. To která vás zbaví nutnosti použití funkce Windows SDK **LoadLibrary** a **GetProcAddress** implementace knihovny DLL s odloženým načtením.

Před Visual C++ 6.0, byl jediný způsob, jak načíst knihovny DLL v době běhu pomocí **LoadLibrary** a **GetProcAddress**; operační systém by načíst knihovnu DLL při spustitelný soubor nebo knihovny DLL pomocí byl načten.

Od verze Visual C++ 6.0, když implicitně propojení s knihovnou DLL, linker zajišťuje možnosti zpoždění načíst knihovnu DLL, dokud je program volá funkci v této knihovně DLL.

Aplikace může zpozdit načtení knihovny DLL pomocí [/delayload (Import načtení odloženého)](../../build/reference/delayload-delay-load-import.md) – možnost linkeru s funkcí pomocné rutiny (Visual C++ poskytuje výchozí implementaci). Pomocná funkce se načíst knihovnu DLL v době běhu voláním **LoadLibrary** a **GetProcAddress** za vás.

Zpoždění načítání knihovny DLL, pokud byste měli zvážit:

- Program nemůže volat funkci v knihovně DLL.

- Funkce v knihovně DLL nemusí zavolána až v pozdějších vykonávání vašeho programu.

Opožděné načtení knihovny DLL lze zadat během sestavování buď. Soubor EXE nebo. Projekt knihovny DLL. ODPOVĚĎ. Projekt knihovny DLL, která způsobuje zpoždění načítání knihovny DLL jeden nebo více neměli samotný volat odloženě zaváděné vstupní bod ve zpracování funkce Dllmain.

Následující témata popisují odloženého načítání knihoven DLL:

- [Určení knihoven DLL pro odložené načtení](../../build/reference/specifying-dlls-to-delay-load.md)

- [Explicitní uvolnění knihovny DLL načtené se zpožděním](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)

- [Načtení všech importů pro knihovnu DLL se zpožděným načtením](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md)

- [Import vazeb](../../build/reference/binding-imports.md)

- [Zpracování chyb a oznámení](../../build/reference/error-handling-and-notification.md)

- [Výpis importu se zpožděným načtením](../../build/reference/dumping-delay-loaded-imports.md)

- [Omezení odloženého načítání knihoven DLL](../../build/reference/constraints-of-delay-loading-dlls.md)

- [Základní informace o podpůrné funkci](understanding-the-helper-function.md)

- [Vývoj vlastní pomocné funkce](../../build/reference/developing-your-own-helper-function.md)

## <a name="see-also"></a>Viz také

[Knihovny DLL v jazyce Visual C++](../../build/dlls-in-visual-cpp.md)<br/>
[Propojování](../../build/reference/linking.md)
