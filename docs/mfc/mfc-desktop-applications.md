---
title: Běžné aplikace knihovny MFC
ms.date: 07/28/2019
f1_keywords:
- MFC
helpviewer_keywords:
- libraries, MFC
- class libraries, MFC
- MFC, about MFC
ms.assetid: 7101cb18-a681-495c-8f2b-069ad20c72f7
ms.openlocfilehash: 3811fdcf278129ee72872ea489b42f8389957761
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359342"
---
# <a name="mfc-desktop-applications"></a>Běžné aplikace knihovny MFC

Knihovna třídy Microsoft Foundation (MFC) poskytuje objektově orientované obálky přes většinu rozhraní API Win32 a COM. Ačkoli to může být použit k vytvoření velmi jednoduché desktopové aplikace, to je nejužitečnější, když potřebujete vyvinout složitější uživatelská rozhraní s více ovládacími prvky. Knihovny MFC můžete použít k vytváření aplikací s uživatelskými rozhraními ve stylu Office. Dokumentaci na samotné platformě Windows naleznete v [dokumentaci k systému Windows](/windows/index). Informace o vytváření aplikací pro Windows v jazyce C++ bez knihovny MFC najdete [v tématu Vytváření aplikací pro stolní počítače pro Windows pomocí rozhraní API Win32](/windows/win32/index).

Odkaz knihovny MFC zahrnuje třídy, globální funkce, globální proměnné a makra, které tvoří knihovnu tříd Microsoft Foundation.

Jednotlivé hierarchické grafy zahrnuté v každé třídě jsou užitečné pro vyhledání základních tříd. Odkaz knihovny MFC obvykle nepopisuje zděděné členské funkce nebo zděděné operátory. Informace o těchto funkcích naleznete v základních třídách zobrazených v diagramech hierarchie.

Dokumentace pro každou třídu obsahuje přehled třídy, souhrn členů podle kategorie a témata pro členské funkce, přetížené operátory a datové členy.

Veřejné a chráněné členy třídy jsou dokumentovány pouze v případě, že jsou obvykle používány v aplikačních programech nebo odvozených třídách. Úplný seznam členů třídy najdete v souborech záhlaví třídy.

> [!IMPORTANT]
> Třídy knihovny MFC a jejich členy nelze použít v aplikacích, které se spouštějí v prostředí prostředí Prostředí Windows Runtime.
>
> Knihovny Knihovny MFC (DLL) pro vícebajtové kódování znaků (MBCS) již nejsou součástí sady Visual Studio, ale jsou k dispozici jako doplněk sady Visual Studio. Další informace naleznete v tématu [MFC MBCS DLL Add-on .](mfc-mbcs-dll-add-on.md)

## <a name="in-this-section"></a>V tomto oddílu

[Koncepty](mfc-concepts.md)<br/>
Koncepční články o tématech knihovny MFC.

[Graf hierarchie](hierarchy-chart.md)<br/>
Vizuálně podrobně popisuje vztahy tříd v knihovně tříd.

[Přehled třídy](class-library-overview.md)<br/>
Zobrazí seznam tříd v knihovně knihovny knihovny knihovny knihovny podle kategorie.

[Postupy](walkthroughs-mfc.md)<br/>
Obsahuje články, které vás provedou různými úkoly spojenými s funkcemi knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny.

[Technické poznámky](mfc-technical-notes.md)<br/>
Obsahuje odkazy na specializovaná témata napsaná vývojovým týmem knihovny MFC v knihovně tříd.

[Přizpůsobení pro prostředí MFC](customization-for-mfc.md)<br/>
Obsahuje několik tipů pro přizpůsobení aplikace knihovny MFC.

[Třídy](reference/mfc-classes.md)<br/>
Obsahuje odkazy na a informace o souboru záhlaví pro třídy knihovny MFC.

[Interní třídy](reference/internal-classes.md)<br/>
Používá se interně v knihovně MFC. Pro úplnost tato část popisuje tyto vnitřní třídy, ale nejsou určeny k použití přímo v kódu.

[Makra a globální](reference/mfc-macros-and-globals.md)<br/>
Obsahuje odkazy na makra a globální funkce v knihovně knihovny knihovny MFC.

[Struktury, styly, zpětná volání a mapy zpráv](reference/structures-styles-callbacks-and-message-maps.md)<br/>
Obsahuje odkazy na struktury, styly, zpětná volání a mapy zpráv používané knihovnou knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny.

[Průvodci a dialogová okna knihovny MFC](reference/mfc-wizards-and-dialog-boxes.md)<br/>
Průvodce funkcemi sady Visual Studio pro vytváření aplikací knihovny MFC.

[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
Jak používat soubory prostředků ke správě statických dat uživatelského rozhraní, jako jsou řetězce uživatelského rozhraní a rozložení dialogového okna.

## <a name="related-sections"></a>Související oddíly

[Kategorie grafů hierarchie](hierarchy-chart-categories.md)<br/>
Popisuje graf hierarchie knihovny MFC podle kategorií.

[Sdílené třídy KNIHOVNY ATL/Knihovny MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
Obsahuje odkazy na třídy, které jsou sdíleny mezi knihovnou MFC a knihovnou ATL.

[Ukázky knihovny MFC](../overview/visual-cpp-samples.md#mfc-samples)<br/>
Obsahuje odkazy na ukázky, které ukazují, jak používat knihovnu MFC.

[Referenční příručka knihoven visual c++](../standard-library/cpp-standard-library-reference.md)<br/>
Obsahuje odkazy na různé knihovny dodávané s visual c++, včetně knihovny ATL, Knihovny MFC, ŠABLONY OLE DB, knihovny run-time jazyka C a standardní knihovny jazyka C++.

[Ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)<br/>
Obsahuje odkazy na použití ladicího programu sady Visual Studio k opravě chyb logiky v aplikaci nebo uložených procedurách.

## <a name="see-also"></a>Viz také

[Rozhraní MFC a knihovna ATL](mfc-and-atl.md)
