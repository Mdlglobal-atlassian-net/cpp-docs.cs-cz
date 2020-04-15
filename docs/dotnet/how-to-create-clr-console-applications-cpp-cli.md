---
title: 'Postupy: Vytváření konzolových aplikací CLR (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- console applications, templates
- CLR console applications, project template
ms.assetid: e89bce3c-706f-4ae0-8a90-cb1a0f674e70
ms.openlocfilehash: 86e5abe330b0edc514fed74a12188ab73e8bfdd8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368540"
---
# <a name="how-to-create-clr-console-applications-ccli"></a>Postupy: Vytváření konzolových aplikací CLR (C++/CLI)

Pomocí šablony Konzolová aplikace lze vytvořit projekt konzolové aplikace, který již obsahuje základní odkazy a soubory projektu.

Konzolová aplikace je obvykle zkompilována do samostatného spustitelného souboru, ale neobsahuje grafické uživatelské rozhraní. Uživatel konzolovou aplikaci spustí z příkazového řádku a používá jej k zadávání pokynů spuštěné aplikaci. Aplikace do příkazového řádku také vypisuje výstupní informace. Díky své bezprostřednosti je konzolová aplikace skvělým výukovým způsobem programovacích technik bez zájmu o implementaci uživatelského rozhraní.

Projekt vytvořený pomocí šablony Konzolová aplikace automaticky přidá tyto odkazy a soubory:

- Odkazy na tyto obory názvů rozhraní .NET Framework:

  - <xref:System.AppDomainManager>– Obsahuje základní třídy a základní třídy, které definují běžně používané hodnoty a referenční datové typy, obslužné rutiny událostí a událostí, rozhraní, atributy a výjimky zpracování.

  - mscorlib – Sestavení knihovny DLL, která podporuje vývoj pomocí rozhraní .NET Framework.

- Zdrojové soubory:

  - Console (soubor .cpp) – Hlavní zdrojový soubor a vstupní bod do aplikace, kterou jste právě vytvořili. Identifikuje soubor .dll projektu a obor názvů projektu. Zadejte svůj vlastní kód v tomto souboru.

  - AssemblyInfo.cpp – Obsahuje atributy, soubory, prostředky, typy, informace o verzi, podpisové informace a další, které lze použít k úpravě metadat sestavení projektu. Další informace naleznete [v tématu Obsah sestavení](/dotnet/framework/app-domains/assembly-contents).

  - Stdafx.cpp – Používá se k sestavení předkompilovaného hlavičkového souboru s názvem Win32.pch a předkompilovaného souboru typů s názvem StdAfx.obj.

- Soubory hlaviček:

  - Stdafx.h – Používá se k sestavení předkompilovaného hlavičkového souboru s názvem Win32.pch a předkompilovaného souboru typů s názvem StdAfx.obj.

  - resource.h – Generovaný vložený soubor souboru app.rc.

- Soubory prostředků:

  - app.rc – Soubor skriptu prostředků programu.

  - app.ico – Ikona programu.

- ReadMe.txt – Popisuje soubory projektu.

## <a name="to-create-a-common-language-runtime-clr-console-app-project"></a>Vytvoření projektu konzolové aplikace modulu CLR

1. Na řádku nabídek zvolte **Soubor**, **Nový**, **Projekt**.

1. V dialogovém okně **Nový projekt** vyberte v části **Nainstalované šablony**uzel Visual **C++,** vyberte uzel **CLR** a pak vyberte šablonu konzolové aplikace.

1. Do pole **Název** zadejte jedinečný název aplikace.

   Lze zadat další nastavení projektu a řešení, ale nejsou vyžadovány.

1. Zvolte tlačítko **OK.**

## <a name="see-also"></a>Viz také

[Projekty CLR](../build/reference/files-created-for-clr-projects.md)
