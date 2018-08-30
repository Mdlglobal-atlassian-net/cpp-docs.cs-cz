---
title: 'Postupy: vytváření konzolových aplikací CLR (C + +/ CLI) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- console applications, templates
- CLR console applications, project template
ms.assetid: e89bce3c-706f-4ae0-8a90-cb1a0f674e70
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 60804b3863a4b44bc963f289b1d6a8c2f2d5cbf7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211154"
---
# <a name="how-to-create-clr-console-applications-ccli"></a>Postupy: Vytváření konzolových aplikací CLR (C++/CLI)
Pomocí šablony Konzolová aplikace lze vytvořit projekt konzolové aplikace, který již obsahuje základní odkazy a soubory projektu.  
  
 Konzolová aplikace je obvykle zkompilována do samostatného spustitelného souboru, ale neobsahuje grafické uživatelské rozhraní. Uživatel konzolovou aplikaci spustí z příkazového řádku a používá jej k zadávání pokynů spuštěné aplikaci. Aplikace do příkazového řádku také vypisuje výstupní informace. Díky své bezprostřednosti je konzolová aplikace skvělým výukovým způsobem programovacích technik bez zájmu o implementaci uživatelského rozhraní.  
  
 Projekt vytvořený pomocí šablony Konzolová aplikace automaticky přidá tyto odkazy a soubory:  
  
-   Odkazy na tyto obory názvů rozhraní .NET Framework:  
  
    -   [Systém](https://msdn.microsoft.com/library/system.appdomainmanager.appdomainmanager.aspx)– obsahuje základní třídy a základních tříd, které definují běžně používá hodnoty a odkazové datové typy, události a obslužné rutiny událostí, rozhraní, atributy a zpracování výjimek.  
  
    -   mscorlib – Sestavení knihovny DLL, která podporuje vývoj pomocí rozhraní .NET Framework.  
  
-   Zdrojové soubory:  
  
    -   Console (soubor .cpp) – Hlavní zdrojový soubor a vstupní bod do aplikace, kterou jste právě vytvořili. Identifikuje soubor .dll projektu a obor názvů projektu. Zadejte vlastní kód v tomto souboru.  
  
    -   AssemblyInfo.cpp – Obsahuje atributy, soubory, prostředky, typy, informace o verzi, podpisové informace a další, které lze použít k úpravě metadat sestavení projektu. Další informace najdete v tématu [obsah sestavení](/dotnet/framework/app-domains/assembly-contents).  
  
    -   Stdafx.cpp – Používá se k sestavení předkompilovaného hlavičkového souboru s názvem Win32.pch a předkompilovaného souboru typů s názvem StdAfx.obj.  
  
-   Soubory hlaviček:  
  
    -   Stdafx.h – Používá se k sestavení předkompilovaného hlavičkového souboru s názvem Win32.pch a předkompilovaného souboru typů s názvem StdAfx.obj.  
  
    -   resource.h – Generovaný vložený soubor souboru app.rc.  
  
-   Soubory prostředků:  
  
    -   app.rc – Soubor skriptu prostředků programu.  
  
    -   app.ico – Ikona programu.  
  
-   ReadMe.txt – Popisuje soubory projektu.  
  
## <a name="to-create-a-common-language-runtime-clr-console-app-project"></a>Vytvoření projektu konzolové aplikace modulu CLR  
  
1.  V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
2.  V **nový projekt** dialogovém okně **nainstalované šablony**, vyberte **Visual C++** uzlu, vyberte **CLR** uzlu a pak vyberte Šablona konzolové aplikace.  
  
3.  V **název** zadejte jedinečný název pro vaši aplikaci.  
  
     Lze zadat další nastavení projektu a řešení, ale nejsou vyžadovány.  
  
4.  Zvolte **OK** tlačítko.  
  
## <a name="see-also"></a>Viz také  
 [Projekty CLR](../ide/files-created-for-clr-projects.md)   


