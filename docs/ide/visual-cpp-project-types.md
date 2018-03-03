---
title: "Typy projektů Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 10/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- Visual C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a837aa04b0e0c2b8d3d9f5cfd48181a9ea23b346
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="visual-c-project-types"></a>Typy projektů Visual C++

Šablona projektu můžete použít k vytvoření struktura základní programu, nabídek, panely nástrojů, ikony, odkazy, a `#include` příkazy, které jsou vhodné pro typ projektu, kterou chcete vytvořit. Visual Studio obsahuje několik druhů šablony projektů Visual C++ a poskytuje průvodců pro mnoho z nich tak, aby si můžete přizpůsobit projekty, podle jejich vytvoření. Okamžitě po vytvoření projektu, můžete ji sestavíte a spustíte aplikaci; je dobrým zvykem sestavení občas, když budete vyvíjet aplikace.

Nemusíte používat šablonu pro vytvoření projektu, ale ve většině případů je efektivnější to provést, protože je jednodušší a upravit soubory zadaného projektu a struktura, než je při jejich vytváření od začátku.  
  
> [!NOTE]
> Projekt jazyka C můžete vytvořit pomocí šablony projektu jazyka C++. V projektu vygenerované najít soubory, které mají sada příponou názvu souboru a změňte ji na. c. Potom na **vlastnosti projektu** stránky pro projekt (není pro řešení), rozbalte položku **vlastnosti konfigurace**, **C/C++** a vyberte **Upřesnit**. Změna **zkompilovat jako** nastavení na **zkompilovat jako kódu jazyka C (/ TC)**.

## <a name="project-templates"></a>Šablony projektů

Šablony projektů, které jsou zahrnuté v sadě Visual Studio závisí na verzi produktu a úlohy, které jste nainstalovali. Pokud jste nainstalovali vývoj aplikací zatížením, C++, Visual Studio má tyto šablony projektů Visual C++.

### <a name="windows-desktop"></a>Windows Desktop

|Šablona projektu|Popis|  
|----------------------|-----------------------------| 
|[Konzolové aplikace pro Windows](../windows/creating-a-console-application.md)|Projekt pro vytvoření konzolové aplikace systému Windows.|
|[Aplikace pracovní plochy Windows](../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|Projekt pro vytvoření aplikace pro systém Windows desktop (Win32).|
|[Knihovna DLL](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|Projekt pro vytvoření dynamická knihovna (DLL).|
|[Statické knihovny](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Projekt pro vytvoření statické knihovny (LIB).|
|Průvodce na ploše systému Windows|Průvodce pro vytváření aplikací klasické pracovní plochy Windows a knihovny s další možnosti.|

### <a name="general"></a>Obecné

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|Prázdný projekt|Prázdný projekt pro vytvoření aplikace, knihovny nebo DLL. Je nutné přidat kód ani prostředků, které vyžaduje.|
|[Projektem souboru pravidel](../ide/creating-a-makefile-project.md)|Sestavení projektu pro použití externího systému.|
|Sdílené položky projektu|Projekt, který se používá pro sdílení souborů mezi více projektů.|

### <a name="atl"></a>ATL

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|[Projekt knihovny ATL](../atl/reference/creating-an-atl-project.md)|Projekt, který používá Active knihovna šablon.|

### <a name="test"></a>Test

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|[Nativní jednotky testovacího projektu](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|Projekt, který obsahuje nativní testování částí C++.|

### <a name="mfc"></a>MFC

Pokud přidáte MFC a knihovna ATL podporu součásti k instalaci sady Visual Studio, tyto šablony projektu se přidají do sady Visual Studio.

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|[Aplikace MFC](../mfc/reference/creating-an-mfc-application.md)|Projekt pro vytvoření aplikace, která používá knihovna Microsoft Foundation Class (MFC).|
|[Ovládací prvek ActiveX knihovny MFC](../mfc/reference/creating-an-mfc-activex-control.md)|Projekt pro vytvoření ovládacího prvku ActiveX, který používá knihovny MFC.|
|[MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md)|Projekt pro vytvoření dynamickou knihovnu, která používá knihovny MFC.|

### <a name="windows-universal-apps"></a>Univerzální aplikace pro Windows

Když přidáte komponentu nástroje pro univerzální platformu Windows C++ instalace Visual Studia, tyto šablony projektu se přidají k sadě Visual Studio.

Přehled univerzálních aplikací pro Windows v jazyce C++ najdete v tématu [univerzální aplikace pro Windows (C++)](../windows/universal-windows-apps-cpp.md).

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|Prázdná aplikace|Projekt pro jednostránkové aplikace univerzální platformu Windows (UWP), který nemá žádné předdefinované ovládací prvky nebo rozložení.|
|Aplikace rozhraní DirectX 11|Projekt pro univerzální platformu Windows aplikaci, která používá rozhraní DirectX 11.|
|Aplikace rozhraní DirectX 12|Projekt pro univerzální platformu Windows aplikaci, která používá rozhraní DirectX 12.|
|DirectX 11 a aplikace XAML|Projekt pro univerzální platformu Windows aplikaci, která používá rozhraní DirectX 11 a XAML.|
|Jednotka testování aplikace|Projekt k vytvoření aplikace testů jednotek pro aplikace pro univerzální platformu Windows (UWP).|
|DLL|Projekt pro nativní dynamická knihovna (DLL), které je možné součást aplikace nebo modul runtime univerzální platformu Windows.|
|Statické knihovny|Projekt pro nativní statická knihovna (LIB), které je možné součást aplikace nebo modul runtime univerzální platformu Windows.|
|Součást prostředí Windows Runtime|Projekt pro komponenty prostředí Windows Runtime, která mohou být využívána univerzální platformu Windows aplikace, bez ohledu na programovací jazyk, ve kterém je aplikace zapsána.|
|Balení projekt aplikace Windows|Projekt, který vytvoří UWP balíček, který umožňuje desktopová aplikace zkušebně načtených nebo distribuovaných přes Microsoft Store.|

## <a name="todo-comments"></a>Komentáře TODO

Řadu soubory generované šablona projektu obsahovat komentáře TODO, který vám pomůže identifikovat, kde můžete zadat vlastní zdrojového kódu. Další informace o tom, jak přidat kód najdete v tématu [přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md) a [práce se zdrojovými soubory](../windows/working-with-resource-files.md).

## <a name="see-also"></a>Viz také

[Tvorba desktopových projektů pomocí průvodců aplikací](../ide/creating-desktop-projects-by-using-application-wizards.md)   
