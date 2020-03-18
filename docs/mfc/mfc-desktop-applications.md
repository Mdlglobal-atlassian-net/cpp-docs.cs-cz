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
ms.openlocfilehash: e9921d18e9ec060f61959278b68906338f02b5b7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447707"
---
# <a name="mfc-desktop-applications"></a>Běžné aplikace knihovny MFC

Knihovna Microsoft Foundation Class (MFC) poskytuje objektově orientovanou obálku nad mnoho rozhraní API Win32 a COM. I když lze použít k vytvoření velmi jednoduchých desktopových aplikací, je nejužitečnější, pokud potřebujete vyvíjet složitější uživatelská rozhraní s více ovládacími prvky. Knihovnu MFC lze použít k vytváření aplikací s uživatelskými rozhraními ve stylu systému Office. Dokumentaci k samotné platformě Windows najdete v [dokumentaci k Windows](/windows/index). Informace o vytváření aplikací pro Windows v C++ nástroji bez knihovny MFC naleznete v tématu [sestavování aplikací pro windows Desktop pomocí Win32 API](/windows/win32/index).

Odkaz na knihovnu MFC pokrývá třídy, globální funkce, globální proměnné a makra, které tvoří knihovna Microsoft Foundation Class.

Jednotlivé diagramy hierarchie, které jsou součástí každé třídy, jsou užitečné pro vyhledání základních tříd. Odkaz knihovny MFC obvykle nepopisuje zděděné členské funkce nebo zděděné operátory. Informace o těchto funkcích naleznete v základních třídách, které jsou znázorněny v diagramech hierarchie.

Dokumentace pro každou třídu obsahuje přehled třídy, souhrn členů podle kategorií a témata pro členské funkce, přetížené operátory a datové členy.

Členy veřejné a chráněné třídy jsou zdokumentovány pouze v případě, že jsou obvykle používány v aplikacích v aplikaci nebo v odvozených třídách. Úplný seznam členů třídy naleznete v hlavičkových souborech třídy.

> [!IMPORTANT]
>  Třídy MFC a jejich členové nelze použít v aplikacích, které jsou spouštěny v prostředí prostředí Windows Runtime.
>
>  Knihovny MFC (DLL) pro vícebajtové kódování znaků (MBCS) již nejsou součástí sady Visual Studio, ale jsou k dispozici jako doplněk sady Visual Studio. Další informace naleznete v tématu [doplněk MFC MBCS DLL](mfc-mbcs-dll-add-on.md).

## <a name="in-this-section"></a>V tomto oddílu

[Koncepty](mfc-concepts.md)<br/>
Koncepční články o tématech MFC.

[Graf hierarchie](hierarchy-chart.md)<br/>
Vizuálně podrobně popisuje vztahy tříd v knihovně tříd.

[Přehled třídy](class-library-overview.md)<br/>
Vypíše třídy v knihovně MFC podle kategorie.

[Návody](walkthroughs-mfc.md)<br/>
Obsahuje články, které vás provedou různými úkoly spojenými s funkcemi knihovny MFC.

[Technické poznámky](mfc-technical-notes.md)<br/>
Obsahuje odkazy na specializovaná témata vytvořená vývojovým týmem knihovny MFC v knihovně tříd.

[Přizpůsobení pro prostředí MFC](customization-for-mfc.md)<br/>
Poskytuje několik tipů pro přizpůsobení aplikace MFC.

[Třídy](reference/mfc-classes.md)<br/>
Poskytuje odkazy na informace a soubory hlaviček pro třídy MFC.

[Interní třídy](reference/internal-classes.md)<br/>
Používá se interně v MFC. V případě úplnosti Tato část popisuje tyto interní třídy, ale nejsou určeny pro použití přímo v kódu.

[Makra a globální prvky](reference/mfc-macros-and-globals.md)<br/>
Obsahuje odkazy na makra a globální funkce v knihovně MFC.

[Struktury, styly, zpětná volání a mapy zpráv](reference/structures-styles-callbacks-and-message-maps.md)<br/>
Obsahuje odkazy na struktury, styly, zpětná volání a mapy zpráv používané knihovnou MFC.

[Průvodci a dialogová okna knihovny MFC](reference/mfc-wizards-and-dialog-boxes.md)<br/>
Průvodce funkcemi v aplikaci Visual Studio pro vytváření aplikací knihovny MFC.

[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
Jak používat soubory prostředků ke správě dat statických uživatelských rozhraní, jako jsou řetězce uživatelského rozhraní a rozložení dialogového okna.

## <a name="related-sections"></a>Související oddíly

[Kategorie grafů hierarchie](hierarchy-chart-categories.md)<br/>
Popisuje graf hierarchie MFC podle kategorie.

[Sdílené třídy ATL/MFC](../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
Obsahuje odkazy na třídy, které jsou sdíleny mezi knihovnou MFC a knihovnou ATL.

[Ukázky knihovny MFC](../overview/visual-cpp-samples.md)<br/>
Obsahuje odkazy na ukázky, které ukazují, jak používat knihovnu MFC.

[Referenční C++ dokumentace knihoven vizuálů](../standard-library/cpp-standard-library-reference.md)<br/>
Obsahuje odkazy na různé knihovny poskytované pomocí vizuálu C++, včetně knihovny ATL, knihovny MFC, OLE DB šablon, knihovny run-time jazyka C a C++ standardní knihovny.

[Ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)<br/>
Obsahuje odkazy na používání ladicího programu sady Visual Studio k opravě logických chyb v aplikaci nebo uložených procedurách.

## <a name="see-also"></a>Viz také

[Rozhraní MFC a knihovna ATL](mfc-and-atl.md)
