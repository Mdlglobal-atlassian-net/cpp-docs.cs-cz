---
title: 'Místní zdroje v aplikacích MFC: Satelitní knihovny DLL'
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
ms.openlocfilehash: 1f512cc17832564b5eb530b97f8bfb2642c43d43
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220738"
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>Místní zdroje v aplikacích MFC: Satelitní knihovny DLL

MFC verze 7,0 a novější poskytuje rozšířenou podporu pro satelitní knihovny DLL, funkci, která pomáhá při vytváření aplikací lokalizovaných pro více jazyků. Satelitní knihovna DLL je [Knihovna DLL pouze pro prostředky](creating-a-resource-only-dll.md) , která obsahuje prostředky aplikace lokalizované pro určitý jazyk. Po zahájení provádění aplikace MFC automaticky načte lokalizovaný prostředek, který je pro prostředí nejvhodnější. Můžete mít například aplikaci s anglickou jazykovou knihovnou se dvěma satelitními knihovnami DLL, jednu obsahující francouzskou překlady vašich prostředků a druhý obsahující německý překlad. Když je aplikace spuštěna v anglickém jazyce, používá anglické prostředky. Pokud běží na francouzském systému, používá francouzské prostředky; Při spuštění v německém systému používá německé prostředky.

Pro podporu lokalizovaných prostředků v aplikaci knihovny MFC se pokusí načíst satelitní knihovnu DLL obsahující prostředky lokalizované do konkrétního jazyka. Satelitní knihovny DLL jsou pojmenovány *ApplicationNameXXX*. dll, kde *ApplicationName* je název souboru. exe nebo. dll pomocí knihovny MFC, a *xxx* je kód tří písmen pro jazyk prostředků (například "CSY" nebo "DEU").

Knihovna MFC se pokusí načíst prostředek knihovny DLL pro každý z následujících jazyků v pořadí, zastavení při jeho nalezení:

1. Výchozí jazyk uživatelského rozhraní aktuálního uživatele vrácený Win32 API GetUserDefaultUILanguage ().

1. Výchozí jazyk uživatelského rozhraní aktuálního uživatele bez konkrétního podjazyku (tj. ENC [Kanadská angličtina] se bude CSY [americká angličtina]).

1. Výchozí jazyk uživatelského rozhraní systému, jak se vrátilo z rozhraní API GetSystemDefaultUILanguage (). Na jiných platformách se jedná o jazyk samotného operačního systému.

1. Výchozí jazyk uživatelského rozhraní systému, bez jakéhokoli konkrétního podjazyku.

1. Falešného jazyka s 3 písmeny kódu LOC

Pokud knihovna MFC nenajde žádné satelitní knihovny DLL, používá všechny prostředky obsažené v samotné aplikaci.

Předpokládejme například, že aplikace LangExample. exe používá knihovnu MFC a je spuštěna v rámci více systémů uživatelského rozhraní; jazyk uživatelského rozhraní systému je CSY [americká angličtina] a jazyk uživatelského rozhraní aktuálního uživatele je nastavený na FRC [kanadská francouzština]. Knihovna MFC vyhledá následující knihovny DLL v následujícím pořadí:

1. LangExampleFRC. dll (jazyk uživatelského rozhraní uživatele).

1. LangExampleFRA. dll (jazyk uživatelského rozhraní bez podjazyku, v tomto příkladu francouzština (Francie).

1. LangExampleENU. dll (jazyk uživatelského rozhraní systému).

1. LangExampleLOC. dll.

Pokud není nalezena žádná z těchto knihoven DLL, knihovna MFC použije prostředky v souboru LangExample. exe.

## <a name="see-also"></a>Viz také

[Vytváření knihoven DLL jazyka C/C++ v aplikaci Visual Studio](dlls-in-visual-cpp.md)<br/>
[TN057: Lokalizace komponent MFC](../mfc/tn057-localization-of-mfc-components.md)
