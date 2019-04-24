---
title: 'Lokalizované prostředky v aplikacích MFC: Satelitní knihovny DLL'
ms.date: 11/04/2016
helpviewer_keywords:
- multiple language support [C++]
- localization [C++], MFC resources
- localized resources [C++]
- MFC DLLs [C++], localizing
- DLLs [C++], localizing MFC
- resources [MFC], localizing
- resource-only DLLs [C++]
- resource-only DLLs [C++], MFC applications
- satellite DLLs [C++]
ms.assetid: 3a1100ae-a9c8-47b5-adbd-cbedef5992ef
ms.openlocfilehash: c593d0bae6fc23cfd765116c44b07caa2a6d8ccf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188736"
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>Lokalizované prostředky v aplikacích MFC: Satelitní knihovny DLL

Knihovna MFC verze 7.0 nebo novější poskytuje rozšířenou podporu pro satelitní knihovny DLL, funkci, která pomáhá při vytváření aplikací lokalizovaných do více jazyků. Satelitní knihovna DLL je [knihovny DLL pouze prostředků](creating-a-resource-only-dll.md) , který obsahuje aplikace prostředky lokalizovanými pro konkrétní jazyk. Po zahájení provádění aplikace knihovny MFC automaticky načte lokalizované prostředky, které jsou nejvhodnější pro prostředí. Například můžete mít aplikace pomocí anglické jazykové prostředky se dvěma satelitní knihovny DLL, jedna obsahuje francouzské překlad svých prostředků a druhý obsahuje německý překlad. Při spuštění aplikace v anglickém jazyce systému používá anglické prostředky. Pokud je spuštěna ve francouzské systému, používá francouzské prostředků; Pokud je spuštěna v německé systému, používá německé prostředky.

K podpoře lokalizovaných prostředků v aplikaci knihovny MFC, knihovny MFC se pokusí načíst satelitní knihovny DLL obsahující prostředky lokalizována pro konkrétní jazyk. Satelitní knihovny DLL jsou pojmenovány *NázevAplikaceXXX*.dll, kde *ApplicationName* je název .exe nebo .dll pomocí knihovny MFC, a *XXX* je třípísmenný kód jazyka prostředky (například "CSY" nebo "DEU").

Knihovny MFC, pokusí se načíst DLL prostředku pro každý z těchto jazyků v pořadí, zastaví, když jej nalezne:

1. Aktuální uživatel výchozí jazyk uživatelského rozhraní, protože vrácená z rozhraní API systému Win32 GetUserDefaultUILanguage().

1. Aktuální uživatel výchozí jazyk uživatelského rozhraní, bez jakéhokoli konkrétního dílčího jazyka (to znamená, ENC [Kanadské anglické] stane CSY [USA V angličtině]).

1. V systému výchozí jazyk uživatelského rozhraní, protože vrácená GetSystemDefaultUILanguage() rozhraní API. Na jiných platformách Toto je jazyk operačního systému.

1. V systému výchozí jazyk uživatelského rozhraní, bez jakéhokoli konkrétního dílčího jazyka.

1. Falešné jazyce s využitím 3písmenný kód místní

Pokud MFC nebyly nalezeny všechny satelitní knihovny DLL, použije se libovolné prostředky jsou obsaženy v samotné aplikace.

Jako příklad předpokládejme, že LangExample.exe aplikace používá knihovnu MFC a běží na několika uživatelského rozhraní systému – jazyk uživatelského rozhraní je ENU [USA Angličtina] a jazyk uživatelského prostředí aktuálního uživatele je nastavená na FRC [francouzština (Kanada)]. Knihovna MFC hledá následující knihovny DLL v následujícím pořadí:

1. LangExampleFRC.dll (jazyk uživatelského rozhraní uživatele).

1. LangExampleFRA.dll (jazyk uživatelského rozhraní uživatele bez dílčího jazyka v tomto příkladu francouzština (Francie).

1. LangExampleENU.dll (jazyk uživatelského rozhraní systému).

1. LangExampleLOC.dll.

Pokud se nenajdou žádné z těchto knihoven DLL, knihovna MFC používá prostředky v LangExample.exe.

## <a name="see-also"></a>Viz také:

[Knihovny DLL v jazyce Visual C++](dlls-in-visual-cpp.md)<br/>
[TN057: Lokalizace komponent MFC](../mfc/tn057-localization-of-mfc-components.md)
