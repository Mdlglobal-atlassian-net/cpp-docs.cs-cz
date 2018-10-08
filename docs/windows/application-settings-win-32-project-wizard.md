---
title: Nastavení aplikace, Průvodce projektem Win 32 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.appwiz.win32.appset
dev_langs:
- C++
helpviewer_keywords:
- application settings [C++]
- Win32 Project Wizard, application settings
ms.assetid: d6b818f0-9b23-4793-a6c5-df1c8c594bad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0c8e2294c7aee3634409a01c613d7e31729230a
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861821"
---
# <a name="application-settings-win-32-project-wizard"></a>Nastavení aplikace, Průvodce projektem Win 32

Tuto stránku průvodce použijte k nastavení voleb pro projekt Win32.

## <a name="application-type"></a>Typ aplikace

Vytvoří určený typ aplikace.

|Možnost|Popis|
|------------|-----------------|
|**Konzolová aplikace**|Vytvoří konzolovou aplikaci. Programy konzoly jsou vyvíjeny pomocí [funkce konzoly](https://msdn.microsoft.com/library/ms813137.aspx), které poskytují podporu znakového režimu v oknech konzoly. Visual C++ [běhové knihovny](../c-runtime-library/c-run-time-library-reference.md) také poskytují výstup a vstup z okna konzoly se standardních vstupních/výstupních funkcí, jako například `printf_s()` a `scanf_s()`. Konzolová aplikace nemá žádné grafické uživatelské rozhraní. Zkompiluje se do souboru .exe a lze ji spustit jako samostatnou aplikaci z příkazového řádku.<br /><br /> Do konzolové aplikace je možné přidat podporu knihovny MFC a knihovny ATL.|
|**Aplikace Windows**|Vytvoří program systému Win32. Program systému Win32 je spustitelná aplikace (EXE) napsaná v C nebo C++, využívající volání rozhraní API systému Win32 k vytvoření grafického uživatelského rozhraní.<br /><br /> Do aplikace pro systém Windows není možné přidat podporu knihovny MFC nebo knihovny ATL.|
|**KNIHOVNY DLL**|Vytvoří dynamickou knihovnu (DLL) systému Win32. Knihovna DLL systému Win32 je binární soubor napsaný v C nebo C++, který používá volání rozhraní API systému Win32, nikoli tříd knihovny MFC, a funguje jako sdílená knihovna funkcí, které lze použít více aplikacemi současně.<br /><br /> Do DLL aplikace nelze přidat podporu knihovny MFC nebo knihovny ATL. Je možné určit, že knihovna DLL exportuje symboly.|
|**Statická knihovna**|Vytvoří statickou knihovnu. Statická knihovna je soubor obsahující objekty a jejich funkce a data, které jsou propojeny do programu při vytvoření spustitelného souboru. Toto téma vysvětluje, jak vytvořit počáteční soubory a [vlastnosti projektu](../ide/property-pages-visual-cpp.md) pro statické knihovny. Soubor statické knihovny poskytuje následující výhody:<br /><br />-Statická knihovna systému Win32 je užitečná, pokud aplikace, kterou právě pracujete provede volání rozhraní API systému Win32, nikoli tříd knihovny MFC.<br />-Proces propojení je stejný, ať zbytek aplikace Windows napsán v jazyce C nebo C++.<br />-Můžete propojit statickou knihovnu pro aplikace založené na knihovně MFC nebo do programu bez knihovny MFC.|

## <a name="additional-options"></a>Další možnosti

Definuje podporu a možnosti pro aplikaci v závislosti na jejím typu.

|Možnost|Popis|
|------------|-----------------|
|**Prázdný projekt**|Určuje, že soubory projektu jsou prázdné. Máte-li sadu zdrojových souborů (například soubory .cpp, soubory hlaviček, ikony, panely nástrojů, dialogová okna atd.) a chcete vytvořit projekt ve vývojovém prostředí Visual C++, je nutné nejprve vytvořit prázdný projekt a potom přidat soubory do projektu.<br /><br /> Tato možnost není k dispozici pro projekty statických knihoven.|
|**Symboly exportu**|Určuje, že projekt knihovny DLL exportuje symboly.|
|**Předkompilované hlavičky**|Určuje, že projekt statické knihovny používá předkompilovanou hlavičku.|
|Kontroly životního cyklu bezpečnostního vývoje (SDL)|Další informace o SDL najdete v tématu [pokyny k procesu Microsoft Security Development Lifecycle (SDL)](../build/reference/sdl-enable-additional-security-checks.md)|

## <a name="add-support-for"></a>Přidat podporu pro

Přidání podpory pro jednu z knihoven v aplikaci Visual C++.

|Možnost|Popis|
|------------|-----------------|
|**ATL**|Vytvoří do projektu podporu tříd v knihovně ATL (Active Template Library). Pouze pro konzolové aplikace systému Win32.<br /><br /> **Poznámka:** tato možnost neznamená podporu pro přidání objektů knihovny ATL knihovny ATL pomocí průvodců kódu. Je možné přidat objekty knihovny ATL pouze do podpory projektů knihovny ATL nebo projektů knihovny MFC.|
|**KNIHOVNY MFC**|Vytvoří do projektu podporu pro knihovnu MFC (Microsoft Foundation Class). Pouze pro konzolové aplikace systému Win32 a statické knihovny.|

## <a name="see-also"></a>Viz také

[Win32 – průvodce aplikací](../windows/win32-application-wizard.md)  