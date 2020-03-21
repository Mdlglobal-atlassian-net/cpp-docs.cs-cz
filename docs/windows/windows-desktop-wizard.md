---
title: Průvodce desktopem systému Windows
ms.date: 03/29/2019
f1_keywords:
- vc.appwiz.win32.overview
- vc.appwiz.win32.appset
helpviewer_keywords:
- Windows Desktop Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
ms.openlocfilehash: 3d8be0cc33e0435bc5a18191303dbbc91277de0b
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075455"
---
# <a name="windows-desktop-wizard"></a>Průvodce desktopem systému Windows

Průvodce prostředím Windows Desktop nahrazuje Průvodce aplikací Win32 v aplikaci Visual Studio 2017 a novějším. Průvodce umožňuje vytvořit libovolný ze čtyř typů C++ projektů (uvedených v záhlaví v tabulce níže). V každém případě můžete zadat další možnosti, které jsou vhodné pro typ projektu, který jste otevřeli.

   ![Průvodce desktopem systému Windows](media/windows-desktop-wizard.png)

Následující tabulka uvádí, které možnosti jsou k dispozici pro každý typ aplikace.

|Typ podpory|Konzolová aplikace|Spustitelná aplikace (Windows)|Dynamická knihovna|Statická knihovna|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**Prázdný projekt**|Ano|Ano|Ano|Ne|
|**Exportovat symboly**|Ne|Ne|Ano|Ne|
|**Předkompilovaná hlavička**|Ne|Ne|Ne|Ano|
|**Podpora ATL**|Ano|Ne|Ne|Ne|
|**Podpora MFC**|Ano|Ne|Ne|Ano|

## <a name="overview"></a>Přehled

Tato stránka průvodce popisuje aktuální nastavení projektu pro aplikaci Win32, kterou vytváříte. Ve výchozím nastavení jsou nastaveny následující možnosti:

- Projekt je aplikace systému Windows.

- Projekt není prázdný.

- Projekt neobsahuje žádné symboly pro export.

- Projekt nepoužívá soubor předkompilované hlavičky (Tato možnost je k dispozici pouze pro projekty statické knihovny).

- Projekt zahrnuje podporu ani knihovny MFC ani knihovny ATL.

## <a name="application-type"></a>Typ aplikace

Vytvoří určený typ aplikace.

|Možnost|Popis|
|------------|-----------------|
|**Konzolová aplikace**|Vytvoří konzolovou aplikaci. C++ [Běhové knihovny](../c-runtime-library/c-run-time-library-reference.md) Visual runtime také poskytují výstup a vstup z okna konzoly se standardními vstupně-výstupními funkcemi, jako jsou `printf_s()` a `scanf_s()`. Konzolová aplikace nemá žádné grafické uživatelské rozhraní. Zkompiluje se do souboru .exe a lze ji spustit jako samostatnou aplikaci z příkazového řádku.<br /><br /> Do konzolové aplikace je možné přidat podporu knihovny MFC a knihovny ATL.|
|**Aplikace systému Windows**|Vytvoří program systému Win32. Program systému Win32 je spustitelná aplikace (EXE) napsaná v C nebo C++, využívající volání rozhraní API systému Win32 k vytvoření grafického uživatelského rozhraní.<br /><br /> Do aplikace pro systém Windows není možné přidat podporu knihovny MFC nebo knihovny ATL.|
|**Knihovna dynamického propojení**|Vytvoří dynamickou knihovnu (DLL) systému Win32. Knihovna DLL systému Win32 je binární soubor napsaný v C nebo C++, který používá volání rozhraní API systému Win32, nikoli tříd knihovny MFC, a funguje jako sdílená knihovna funkcí, které lze použít více aplikacemi současně.<br /><br /> Podporu knihovny MFC nebo knihovny ATL nelze přidat do aplikace DLL vytvořené pomocí tohoto průvodce, ale můžete vytvořit knihovnu MFC DLL výběrem možnosti **nový > projekt > MFC DLL**.|
|**Statická knihovna**|Vytvoří statickou knihovnu. Statická knihovna je soubor obsahující objekty a jejich funkce a data, které jsou propojeny do programu při vytvoření spustitelného souboru. Toto téma vysvětluje, jak vytvořit počáteční soubory a [Vlastnosti projektu](../build/reference/property-pages-visual-cpp.md) pro statickou knihovnu. Soubor statické knihovny poskytuje následující výhody:<br /><br />– Statická knihovna Win32 je užitečná v případě, že aplikace, na které pracujete, provádí volání na Win32 API spíše než do tříd knihovny MFC.<br />– Proces propojení je stejný, bez ohledu na to, jestli je zbytek aplikace Windows napsaný v jazyce C++C nebo v.<br />-Můžete propojit statickou knihovnu k programu založenému na knihovně MFC nebo k programu, který není knihovnou MFC.|

## <a name="additional-options"></a>Další možnosti

Definuje podporu a možnosti pro aplikaci v závislosti na jejím typu.

|Možnost|Popis|
|------------|-----------------|
|**Prázdný projekt**|Určuje, že soubory projektu jsou prázdné. Máte-li sadu zdrojových souborů (například soubory .cpp, soubory hlaviček, ikony, panely nástrojů, dialogová okna atd.) a chcete vytvořit projekt ve vývojovém prostředí Visual C++, je nutné nejprve vytvořit prázdný projekt a potom přidat soubory do projektu.<br /><br /> Tato možnost není k dispozici pro projekty statických knihoven.|
|**Exportovat symboly**|Určuje, že projekt knihovny DLL exportuje symboly.|
|**Předkompilovaná hlavička**|Určuje, že projekt statické knihovny používá předkompilovanou hlavičku.|
|**Kontroly SDL (Security Development Lifecycle)**|Další informace o SDL najdete v tématu [Microsoft Security Development Lifecycle (SDL) doprovodné materiály procesu](../build/reference/sdl-enable-additional-security-checks.md) .|

## <a name="add-common-headers-for"></a>Přidat společné hlavičky pro:

Přidání podpory pro jednu z knihoven v aplikaci Visual C++.

|Možnost|Popis|
|------------|-----------------|
|**ATL**|Vytvoří do projektu podporu tříd v knihovně ATL (Active Template Library). Pouze pro konzolové aplikace systému Win32.<br /><br /> **Poznámka:** Tato možnost neuvádí podporu pro přidávání objektů ATL pomocí průvodců kódem ATL. Je možné přidat objekty knihovny ATL pouze do podpory projektů knihovny ATL nebo projektů knihovny MFC.|
|**KNIHOVNU**|Vytvoří do projektu podporu pro knihovnu MFC (Microsoft Foundation Class). Pouze pro konzolové aplikace systému Win32 a statické knihovny.|

## <a name="remarks"></a>Poznámky

Po vytvoření desktopové aplikace pro Windows můžete přidat obecné C++ třídy pomocí průvodce [obecným](../ide/generic-cpp-class-wizard.md) kódem. Můžete přidat další položky, například soubory HTML, hlavičkové soubory, zdroje nebo textové soubory.

> [!NOTE]
> Třídy ATL nelze přidat a třídy MFC lze přidat pouze k těmto typům aplikací pro stolní počítače systému Windows, které podporují knihovnu MFC (viz předchozí tabulka).

Můžete zobrazit soubory, které průvodce vytvoří pro projekt v **Průzkumník řešení**. Další informace o souborech, které průvodce vytvoří pro projekt, naleznete v souboru generovaném projektem `ReadMe.txt`. Další informace o typech souborů, [typech souborů vytvořených pro projekty sady Visual Studio C++ ](../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Viz také

[C++typy projektů v aplikaci Visual Studio](../build/reference/visual-cpp-project-types.md)