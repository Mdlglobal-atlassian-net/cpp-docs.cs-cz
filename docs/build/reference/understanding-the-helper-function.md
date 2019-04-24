---
title: Základní informace o podpůrné funkci
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
ms.openlocfilehash: 3ad193d0101507f43145c6af9f8e6200ab6fcdb5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317663"
---
# <a name="understanding-the-helper-function"></a>Základní informace o podpůrné funkci

Pomocná funkce pro linker nepodporuje opožděné načtení je, co skutečně knihovnu DLL načte, v době běhu. Pomocná funkce pro přizpůsobení své chování psaní vlastní funkce a propojením k aplikaci místo pomocí zadané pomocné rutiny funkce v Delayimp.lib můžete upravit. Jeden pomocnou funkci slouží všechny zpožděné načtení knihovny DLL.

Pokud chcete provést konkrétní zpracování na základě názvů imports nebo knihovny DLL, můžete zadat vlastní verzi pomocnou funkci.

Pomocná funkce provede následující akce:

- Zkontroluje uložený popisovač do knihovny, které chcete zobrazit, pokud již byl načten

- Volání **LoadLibrary** pokusu o načtení knihovny DLL

- Volání **GetProcAddress** pokusu o získání adresy procedury

- Vrátí se import odloženého načtení převodní rutina volat teď načíst vstupní bod

Pomocná funkce můžete volat zpět hook oznámení ve svém programu po každé z následujících akcí:

- Při spuštění funkce pomocné rutiny

- Těsně před **LoadLibrary** je volána v pomocné funkce

- Těsně před **GetProcAddress** je volána v pomocné funkce

- Pokud volání **LoadLibrary** v pomocné funkce se nezdařilo

- Pokud volání **GetProcAddress** v pomocné funkce se nezdařilo

- Po pomocné funkce provádí zpracování

Každá z těchto bodů připojení může vrátit hodnotu, která bude úpravu normálního zpracování pomocné rutiny způsobem s výjimkou vrácené výsledky na převodní rutina zpoždění importu zatížení.

Kód pomocného objektu výchozí nacházely v Delayhlp.cpp a Delayimp.h (v vc\include) a je kompilován v Delayimp.lib (v vc\lib). Je potřeba zahrnout tuto knihovnu vaše kompilace Pokud napíšete vlastní pomocné funkce.

Následující témata popisují pomocnou funkci:

- [Změny v podpůrné funkci knihovny DLL s odloženým načtením od aplikace Visual C++ verze 6.0](changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)

- [Konvence volání, parametry a návratový typ](calling-conventions-parameters-and-return-type.md)

- [Struktura a definice konstant](structure-and-constant-definitions.md)

- [Výpočet nezbytných hodnot](calculating-necessary-values.md)

- [Uvolnění knihovny DLL s odloženým načtením](explicitly-unloading-a-delay-loaded-dll.md)

## <a name="see-also"></a>Viz také:

[Podpora linkeru pro knihovny DLL s odloženým načtením](linker-support-for-delay-loaded-dlls.md)
