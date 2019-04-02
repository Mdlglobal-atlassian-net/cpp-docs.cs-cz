---
title: Desktopový Průvodce pro Windows
ms.date: 03/29/2019
f1_keywords:
- vc.appwiz.win32.overview
- vc.appwiz.win32.appset
helpviewer_keywords:
- Windows Desktop Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
ms.openlocfilehash: 52ffd992480df517f8677e14161b697eb3ecc321
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786784"
---
# <a name="windows-desktop-wizard"></a>Desktopový Průvodce pro Windows

Desktopový Průvodce pro Windows nahrazuje Průvodce aplikací Win32 v sadě Visual Studio 2017 nebo novější. Průvodce umožňuje vytvořit čtyři typy projektů jazyka C++ (uvedeny v záhlaví v následující tabulce). V každém případě můžete zadat další možnosti, které jsou vhodné pro typ projektu, které můžete otevřít. 

   ![Desktopový Průvodce pro Windows](media/windows-desktop-wizard.png)

Následující tabulka uvádí, jaké možnosti jsou k dispozici pro všechny typy aplikací.

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

## <a name="application-type"></a>Typ aplikace

Vytvoří určený typ aplikace.

|Možnost|Popis|
|------------|-----------------|
|**Konzolová aplikace**|Vytvoří konzolovou aplikaci. Programy konzoly jsou vyvíjeny pomocí [funkce konzoly](https://msdn.microsoft.com/library/ms813137.aspx), které poskytují podporu znakového režimu v oknech konzoly. Visual C++ [běhové knihovny](../c-runtime-library/c-run-time-library-reference.md) také poskytují výstup a vstup z okna konzoly se standardních vstupních/výstupních funkcí, jako například `printf_s()` a `scanf_s()`. Konzolová aplikace nemá žádné grafické uživatelské rozhraní. Zkompiluje se do souboru .exe a lze ji spustit jako samostatnou aplikaci z příkazového řádku.<br /><br /> Do konzolové aplikace je možné přidat podporu knihovny MFC a knihovny ATL.|
|**Aplikace Windows**|Vytvoří program systému Win32. Program systému Win32 je spustitelná aplikace (EXE) napsaná v C nebo C++, využívající volání rozhraní API systému Win32 k vytvoření grafického uživatelského rozhraní.<br /><br /> Do aplikace pro systém Windows není možné přidat podporu knihovny MFC nebo knihovny ATL.|
|**Dynamické knihovny DLL**|Vytvoří dynamickou knihovnu (DLL) systému Win32. Knihovna DLL systému Win32 je binární soubor napsaný v C nebo C++, který používá volání rozhraní API systému Win32, nikoli tříd knihovny MFC, a funguje jako sdílená knihovna funkcí, které lze použít více aplikacemi současně.<br /><br /> Nelze přidat podporu knihovny MFC nebo ATL DLL aplikace vytvořené pomocí tohoto průvodce, ale můžete vytvořit knihovny MFC DLL vybrat **nový > Projekt > MFC DLL**.|
|**Statická knihovna**|Vytvoří statickou knihovnu. Statická knihovna je soubor obsahující objekty a jejich funkce a data, které jsou propojeny do programu při vytvoření spustitelného souboru. Toto téma vysvětluje, jak vytvořit počáteční soubory a [vlastnosti projektu](../build/reference/property-pages-visual-cpp.md) pro statické knihovny. Soubor statické knihovny poskytuje následující výhody:<br /><br />-Statická knihovna systému Win32 je užitečná, pokud aplikace, kterou právě pracujete provede volání rozhraní API systému Win32, nikoli tříd knihovny MFC.<br />-Proces propojení je stejný, ať zbytek aplikace Windows napsán v jazyce C nebo C++.<br />-Můžete propojit statickou knihovnu pro aplikace založené na knihovně MFC nebo do programu bez knihovny MFC.|

## <a name="additional-options"></a>Další možnosti

Definuje podporu a možnosti pro aplikaci v závislosti na jejím typu.

|Možnost|Popis|
|------------|-----------------|
|**Prázdný projekt**|Určuje, že soubory projektu jsou prázdné. Máte-li sadu zdrojových souborů (například soubory .cpp, soubory hlaviček, ikony, panely nástrojů, dialogová okna atd.) a chcete vytvořit projekt ve vývojovém prostředí Visual C++, je nutné nejprve vytvořit prázdný projekt a potom přidat soubory do projektu.<br /><br /> Tato možnost není k dispozici pro projekty statických knihoven.|
|**Symboly exportu**|Určuje, že projekt knihovny DLL exportuje symboly.|
|**Předkompilované hlavičky**|Určuje, že projekt statické knihovny používá předkompilovanou hlavičku.|
|**Zkontroluje Security Development Lifecycle (SDL)**|Další informace o SDL najdete v tématu [pokyny k procesu Microsoft Security Development Lifecycle (SDL)](../build/reference/sdl-enable-additional-security-checks.md)|

## <a name="add-common-headers-for"></a>Přidáte společné hlavičky pro:

Přidání podpory pro jednu z knihoven v aplikaci Visual C++.

|Možnost|Popis|
|------------|-----------------|
|**ATL**|Vytvoří do projektu podporu tříd v knihovně ATL (Active Template Library). Pouze pro konzolové aplikace systému Win32.<br /><br /> **Poznámka:** tato možnost neznamená podporu pro přidání objektů knihovny ATL knihovny ATL pomocí průvodců kódu. Je možné přidat objekty knihovny ATL pouze do podpory projektů knihovny ATL nebo projektů knihovny MFC.|
|**MFC**|Vytvoří do projektu podporu pro knihovnu MFC (Microsoft Foundation Class). Pouze pro konzolové aplikace systému Win32 a statické knihovny.|

## <a name="remarks"></a>Poznámky

Po vytvoření aplikace klasické pracovní plochy Windows, můžete přidat obecnou C++ třídu pomocí [obecný](../ide/generic-cpp-class-wizard.md) Průvodce kódem. Lze přidat další položky, jako jsou soubory HTML, soubory hlaviček, prostředky nebo textové soubory.

> [!NOTE]
> Nelze přidat třídy ATL a MFC – třídy můžete přidat pouze tyto typy aplikace klasické pracovní plochy Windows, které podporují knihovny MFC (viz předchozí tabulka).

Můžete zobrazit soubory Průvodce vytvoří pro váš projekt v **Průzkumníka řešení**. Další informace o souborech Průvodce vytvoří pro váš projekt, naleznete v generovaném souboru `ReadMe.txt`. Další informace o typech souborů [typy souborů vytvořené pro projekty Visual C++](../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Viz také

[Typy projektů Visual C++](../build/reference/visual-cpp-project-types.md)