---
title: 'Postupy: Vytváření konzolových aplikací CLR (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- console applications, templates
- CLR console applications, project template
ms.assetid: e89bce3c-706f-4ae0-8a90-cb1a0f674e70
ms.openlocfilehash: 610efc8b0780422fc89e3bf9708ba488fe7d1f47
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080053"
---
# <a name="how-to-create-clr-console-applications-ccli"></a>Postupy: Vytváření konzolových aplikací CLR (C++/CLI)

Pomocí šablony Konzolová aplikace lze vytvořit projekt konzolové aplikace, který již obsahuje základní odkazy a soubory projektu.

Konzolová aplikace je obvykle zkompilována do samostatného spustitelného souboru, ale neobsahuje grafické uživatelské rozhraní. Uživatel konzolovou aplikaci spustí z příkazového řádku a používá jej k zadávání pokynů spuštěné aplikaci. Aplikace do příkazového řádku také vypisuje výstupní informace. Díky své bezprostřednosti je konzolová aplikace skvělým výukovým způsobem programovacích technik bez zájmu o implementaci uživatelského rozhraní.

Projekt vytvořený pomocí šablony Konzolová aplikace automaticky přidá tyto odkazy a soubory:

- Odkazy na tyto obory názvů .NET Framework:

   - <xref:System.AppDomainManager>– obsahuje základní třídy a základní třídy, které definují běžně používané hodnoty a referenční datové typy, události a obslužné rutiny událostí, rozhraní, atributy a zpracování výjimek.

   - mscorlib – Sestavení knihovny DLL, která podporuje vývoj pomocí rozhraní .NET Framework.

- Zdrojové soubory:

   - Console (soubor .cpp) – Hlavní zdrojový soubor a vstupní bod do aplikace, kterou jste právě vytvořili. Identifikuje soubor .dll projektu a obor názvů projektu. Zadejte vlastní kód do tohoto souboru.

   - AssemblyInfo.cpp – Obsahuje atributy, soubory, prostředky, typy, informace o verzi, podpisové informace a další, které lze použít k úpravě metadat sestavení projektu. Další informace najdete v tématu o [obsahu sestavení](/dotnet/framework/app-domains/assembly-contents).

   - Stdafx.cpp – Používá se k sestavení předkompilovaného hlavičkového souboru s názvem Win32.pch a předkompilovaného souboru typů s názvem StdAfx.obj.

- Hlavičkové soubory:

   - Stdafx.h – Používá se k sestavení předkompilovaného hlavičkového souboru s názvem Win32.pch a předkompilovaného souboru typů s názvem StdAfx.obj.

   - resource.h – Generovaný vložený soubor souboru app.rc.

- Soubory prostředků:

   - app.rc – Soubor skriptu prostředků programu.

   - app.ico – Ikona programu.

- ReadMe.txt – Popisuje soubory projektu.

## <a name="to-create-a-common-language-runtime-clr-console-app-project"></a>Vytvoření projektu konzolové aplikace modulu CLR

1. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.

1. V dialogovém okně **Nový projekt** v části **Nainstalované šablony**vyberte uzel  **C++ vizuálu** , vyberte uzel **CLR** a pak vyberte šablonu Konzolová aplikace.

1. Do pole **název** zadejte jedinečný název vaší aplikace.

   Lze zadat další nastavení projektu a řešení, ale nejsou vyžadovány.

1. Klikněte na tlačítko **OK** .

## <a name="see-also"></a>Viz také

[Projekty CLR](../build/reference/files-created-for-clr-projects.md)
