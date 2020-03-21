---
title: Typy projektů Visual C++
ms.date: 08/13/2019
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
ms.openlocfilehash: f322d16bbbe91d229fb8efdfb5f2d35cb0a686ae
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079223"
---
# <a name="c-project-templates"></a>Šablony projektů C++

Šablony projektů sady Visual Studio generují soubory zdrojového kódu, možnosti kompilátoru, nabídky, panely nástrojů, ikony, odkazy a `#include` příkazy, které jsou vhodné pro typ projektu, který chcete vytvořit. Visual Studio obsahuje několik druhů šablon C++ projektů a poskytuje průvodce pro mnohé z nich, aby bylo možné přizpůsobit projekty při jejich vytváření. Ihned po vytvoření projektu můžete sestavit a spustit aplikaci. Při vývoji aplikace se dobrým zvykem sestavovat.

> [!NOTE]
> Projekt jazyka C lze vytvořit pomocí C++ šablon projektů. Ve vygenerovaném projektu vyhledejte soubory, které mají příponu názvu souboru. cpp a změňte ji na. c. Pak na stránce **vlastností projektu** projektu (ne pro řešení) rozbalte položku **Vlastnosti konfigurace**, **C++ C/** a vyberte **Upřesnit**. Změňte nastavení **kompilovat jako** na **kompilovat jako kód jazyka C (/TC)** .

## <a name="project-templates"></a>Šablony projektů

Šablony projektů zahrnuté v aplikaci Visual Studio závisí na verzi produktu a na úlohách, které jste nainstalovali. Pokud jste nainstalovali desktopový vývoj s C++ úlohou, Visual Studio má tyto C++ šablony projektů.

### <a name="windows-desktop"></a>Windows Desktop

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|[Konzolová aplikace systému Windows](../../windows/creating-a-console-application.md)|Projekt pro vytvoření konzolové aplikace pro Windows|
|[Desktopová aplikace pro Windows](../../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|Projekt pro vytvoření desktopové aplikace pro Windows (Win32)|
|[Dynamická knihovna](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|Projekt pro vytvoření knihovny DLL (Dynamic-Link Library).|
|[Statická knihovna](../../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Projekt pro vytvoření statické knihovny (LIB).|
|[Desktopový průvodce pro Windows](../../windows/windows-desktop-wizard.md)|Průvodce vytvářením desktopových aplikací a knihoven systému Windows s dalšími možnostmi.|

### <a name="general"></a>Obecné

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|Prázdný projekt|Prázdný projekt pro vytvoření aplikace, knihovny nebo knihovny DLL. Je nutné přidat libovolný kód nebo požadované prostředky.|
|[Projekt makefile](creating-a-makefile-project.md)|Projekt, který zabalí soubor pravidel systému Windows v projektu sady Visual Studio. (Pokud chcete otevřít soubor pravidel tak, jak je v aplikaci Visual Studio, použijte [Otevřít složku](../open-folder-projects-cpp.md).|
|Projekt sdílených položek|Projekt, který se používá pro sdílení souborů kódu nebo souborů prostředků mezi několika projekty. Tento typ projektu nevytváří spustitelný soubor.|

### <a name="atl"></a>ATL

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|[ATL – projekt](../../atl/reference/creating-an-atl-project.md)|Projekt, který používá knihovnu Active Template Library.|

### <a name="test"></a>Test

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|[Nativní projekt testu jednotek](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|Projekt, který obsahuje nativní C++ testy jednotek.|

### <a name="mfc"></a>MFC

Pokud přidáte komponentu podpory knihovny MFC a ATL do instalace aplikace Visual Studio, tyto šablony projektu jsou přidány do sady Visual Studio.

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|[Aplikace MFC](../../mfc/reference/creating-an-mfc-application.md)|Projekt pro vytvoření aplikace, která používá knihovnu Microsoft Foundation Class (MFC).|
|[MFC – ovládací prvek ActiveX](../../mfc/reference/creating-an-mfc-activex-control.md)|Projekt pro vytvoření ovládacího prvku ActiveX, který používá knihovnu MFC.|
|[KNIHOVNA MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)|Projekt pro vytvoření knihovny DLL, která používá knihovnu MFC.|

### <a name="windows-universal-apps"></a>Univerzální aplikace pro Windows

Přidáte-li do C++ instalace aplikace Visual Studio součást nástrojů Univerzální platformy Windows, tyto šablony projektu budou přidány do sady Visual Studio.

Přehled univerzálních aplikací pro Windows v C++najdete v tématu [univerzální aplikace pro WindowsC++()](../../cppcx/universal-windows-apps-cpp.md).

|Šablona projektu|Popis|
|----------------------|-----------------------------|
|Prázdná aplikace|Projekt pro aplikaci s jednou stránkou Univerzální platforma Windows (UWP), která nemá předdefinované ovládací prvky ani rozložení.|
|Aplikace DirectX 11|Projekt pro aplikaci Univerzální platforma Windows používající rozhraní DirectX 11|
|Aplikace DirectX 12|Projekt aplikace pro Univerzální platforma Windows, který používá rozhraní DirectX 12|
|Aplikace DirectX 11 a XAML|Projekt aplikace pro Univerzální platforma Windows, který používá rozhraní DirectX 11 a XAML.|
|Aplikace pro testování částí|Projekt pro vytvoření aplikace testování částí pro aplikace Univerzální platforma Windows (UWP)|
|DLL|Projekt pro nativní dynamickou knihovnu (DLL), kterou může používat aplikace Univerzální platforma Windows nebo komponenta prostředí Runtime.|
|Statická knihovna|Projekt pro nativní knihovnu statických odkazů (LIB), kterou může používat aplikace Univerzální platforma Windows nebo komponenta prostředí Runtime.|
|Součást prostředí Windows Runtime|Projekt pro prostředí Windows Runtime komponentu, kterou může používat aplikace Univerzální platforma Windows, bez ohledu na programovací jazyk, ve kterém je aplikace napsaná.|
|Projekt pro balení aplikace pro systém Windows|Projekt, který vytváří balíček UWP, který umožňuje, aby se desktopová aplikace načetla nebo distribuována přes Microsoft Store.|

## <a name="todo-comments"></a>Komentáře TODO

Mnoho souborů generovaných šablonou projektu obsahuje komentáře TODO, které vám pomohou určit, kde můžete zadat vlastní zdrojový kód. Další informace o tom, jak přidat kód, naleznete v tématu [Přidání funkcionality pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md) a [práce se soubory prostředků](../../windows/working-with-resource-files.md).
