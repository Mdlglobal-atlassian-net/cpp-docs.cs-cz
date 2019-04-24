---
title: Typy projektů Visual C++
ms.date: 11/29/2018
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- Visual C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
ms.openlocfilehash: cac194ed2c830541711161dc139a42ed0529340f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316753"
---
# <a name="c-project-templates"></a>Šablony projektů C++

Šablony projektů sady Visual Studio generování souborů se zdrojovým kódem, možnosti kompilátoru, nabídky, panely nástrojů, ikony, odkazy, a `#include` příkazy, které jsou vhodné pro typ projektu chcete vytvořit. Visual Studio obsahuje několik druhů šablony projektů Visual C++ a poskytuje průvodce pro mnoho z nich tak, aby vaše projekty můžete přizpůsobit podle jejich vytvoření. Ihned po vytvoření projektu lze sestavit a spustit aplikaci. je dobrým zvykem přerušovaně sestavení při vývoji vaší aplikace.

> [!NOTE]
> Vytvořte projekt jazyka C pomocí šablon projektů jazyka C++. V generovaném projektu, vyhledejte soubory, které mají .cpp příponu názvu souboru a změňte ji na. c. Potom na **vlastnosti projektu** stránce projektu (ne pro řešení), rozbalte **vlastnosti konfigurace**, **C/C++** a vyberte **Upřesnit**. Změnit **zkompilovat jako** nastavení **kompilovat jako kód jazyka C (/ TC)**.

## <a name="project-templates"></a>Šablony projektů

Šablony projektů, které jsou součástí sady Visual Studio závisí na verzi produktu a úlohy, které jste nainstalovali. Pokud jste nainstalovali vývoj desktopových aplikací pomocí úlohy pro C++, Visual Studio obsahuje tyto šablony projektů Visual C++.

### <a name="windows-desktop"></a>Plocha Windows

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|[Konzolová aplikace Windows](../../windows/creating-a-console-application.md)|Projekt pro vytvoření konzolové aplikace pro Windows.|
|[Aplikace klasické pracovní plochy Windows](../../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|Projekt pro vytvoření aplikace pro Windows desktop (Win32).|
|[Dynamická knihovna](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|Projekt pro vytvoření dynamické knihovny (DLL).|
|[Statická knihovna](../../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Projekt pro vytvoření statické knihovny (LIB).|
|Desktopový Průvodce pro Windows|Průvodce pro vytváření aplikací klasické pracovní plochy Windows a knihovny s další možnosti.|

### <a name="general"></a>Obecné

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|Prázdný projekt|Prázdný projekt pro vytvoření aplikace, knihovny nebo knihovny DLL. Je nutné přidat kód ani prostředků, které vyžaduje.|
|[Projekt makefile](creating-a-makefile-project.md)|Projekt, který obtéká Windows souboru pravidel v projektu sady Visual Studio. (Chcete-li otevřít soubor pravidel jako-je v sadě Visual Studio, použijte [otevřít složku](../open-folder-projects-cpp.md).|
|Projekt sdílené položky|Projekt, který se používá ke sdílení kódu soubory nebo soubory prostředků mezi více projekty. Tento typ projektu nevytváří spustitelný soubor.|

### <a name="atl"></a>ATL

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|[ATL Project](../../atl/reference/creating-an-atl-project.md)|Projekt, který používá knihovnu Active Template Library.|

### <a name="test"></a>Test

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|[Nativní projekt testu jednotek](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|Projekt obsahující nativní testy jednotek C++.|

### <a name="mfc"></a>MFC

Pokud chcete přidat komponenty k instalaci sady Visual Studio podporu knihovny MFC a ATL, tyto šablony projektu jsou přidány k sadě Visual Studio.

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|[Aplikace MFC](../../mfc/reference/creating-an-mfc-application.md)|Projekt pro vytvoření aplikace, která používá knihovny Microsoft Foundation Class (MFC).|
|[MFC ActiveX Control](../../mfc/reference/creating-an-mfc-activex-control.md)|Projekt pro vytvoření ovládacího prvku ActiveX, který používá knihovnu MFC.|
|[MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)|Projekt pro vytvoření knihovny DLL, která používá knihovnu MFC.|

### <a name="windows-universal-apps"></a>Univerzální aplikace pro Windows

Pokud chcete přidat součást nástrojů pro univerzální platformu Windows C++ k instalaci sady Visual Studio, tyto šablony projektu jsou přidány k sadě Visual Studio.

Přehled Windows univerzální aplikace v jazyce C++, naleznete v tématu [univerzální aplikace pro Windows (C++)](../../windows/universal-windows-apps-cpp.md).

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|Prázdná aplikace|Projekt pro jednostránkovou aplikaci univerzální platformy Windows (UPW), který nemá žádné předdefinované ovládací prvky ani rozložení.|
|Aplikace DirectX 11|Projekt aplikace pro univerzální platformu Windows používající rozhraní DirectX 11.|
|Aplikace DirectX 12|Projekt aplikace pro univerzální platformu Windows využívající DirectX 12.|
|Rozhraní DirectX 11 a XAML aplikací|Projekt aplikace pro univerzální platformu Windows používající rozhraní DirectX 11 a XAML.|
|Aplikace testů jednotek|Projekt pro vytvoření aplikace testů jednotek pro aplikace univerzální platformy Windows (UPW).|
|DLL|Projekt pro nativní dynamickou knihovnu (DLL), použitý univerzální platformu Windows aplikace nebo komponenta prostředí runtime.|
|Statická knihovna|Projekt pro nativní knihovnu statických odkazů (LIB), který lze použít univerzální platformu Windows aplikace nebo komponenta prostředí runtime.|
|Součást prostředí Windows Runtime|Projekt pro součást prostředí Windows Runtime, která může používat aplikace pro univerzální platformu Windows, bez ohledu na programovací jazyk, ve kterém je aplikace vytvořená.|
|Projekt Windows Application Packaging|Projekt, který vytvoří balíček, UPW, která umožňuje desktopovou aplikaci zkušebně načtených nebo distribuované přes Microsoft Store.|

## <a name="todo-comments"></a>Komentáře TODO

Mnoho soubory generované záznamem šablony projektu obsahovat komentáře TODO, abyste mohli snadno identifikovat, ve kterém můžete zadat zdrojový kód. Další informace o tom, jak přidat kód, naleznete v tématu [přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md) a [práce se zdrojovými soubory](../../windows/working-with-resource-files.md).


