---
title: Win32 – průvodce aplikací
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.win32.overview
helpviewer_keywords:
- Win32 Application Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
ms.openlocfilehash: 1b89ae1c91536956924090f4a5eafa883053ed7e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526153"
---
# <a name="win32-application-wizard"></a>Win32 – průvodce aplikací

Průvodce aplikace Win32 Visual C++ umožňuje vytvořit čtyři typy projektů (uvedeny v záhlaví v následující tabulce). V každém případě můžete zadat další možnosti, které jsou vhodné pro typ projektu, které můžete otevřít. Následující tabulka uvádí, jaké možnosti jsou k dispozici pro všechny typy aplikací.

|Typ podpory|Konzolová aplikace|Aplikace spustitelný soubor (Windows)|Dynamická knihovna|Statická knihovna|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**Prázdný projekt**|Ano|Ano|Ano|Ne|
|**Symboly exportu**|Ne|Ne|Ano|Ne|
|**Předkompilované hlavičky**|Ne|Ne|Ne|Ano|
|**ATL – podpora**|Ano|Ne|Ne|Ne|
|**Podpora knihovny MFC**|Ano|Ne|Ne|Ano|

## <a name="overview"></a>Přehled

Tato stránka průvodce popisuje aktuální nastavení projektu pro vytvářenou aplikaci Win32. Ve výchozím nastavení jsou nastavené následující možnosti:

- Projekt je aplikace Windows.

- Projekt není prázdný.

- Projekt neobsahuje žádné symboly pro export.

- Projekt nepoužívá soubor předkompilované hlavičky (Tato možnost je k dispozici pro projekty statických knihoven pouze).

- Projekt nezahrnuje podporu pro knihovny MFC ani ATL.

Chcete-li změnit výchozí nastavení, klikněte na tlačítko [nastavení aplikace](../windows/application-settings-win-32-project-wizard.md) kartu v levém sloupci průvodce a proveďte požadované změny.

Po vytvoření aplikace klasické pracovní plochy Windows, můžete přidat obecnou C++ třídu pomocí [obecný](../ide/generic-cpp-class-wizard.md) Průvodce kódem. Lze přidat další položky, jako jsou soubory HTML, soubory hlaviček, prostředky nebo textové soubory.

> [!NOTE]
> Nelze přidat třídy ATL a MFC – třídy můžete přidat pouze tyto typy aplikace klasické pracovní plochy Windows, které podporují knihovny MFC (viz předchozí tabulka).

Můžete zobrazit soubory Průvodce vytvoří pro váš projekt v **Průzkumníka řešení**. Další informace o souborech Průvodce vytvoří pro váš projekt, naleznete v generovaném souboru `ReadMe.txt`. Další informace o typech souborů [typy souborů vytvořené pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Viz také

[Vytvoření prázdné desktopové aplikace Windows](../windows/creating-an-empty-windows-desktop-application.md)<br/>
[Typy projektů Visual C++](../ide/visual-cpp-project-types.md)