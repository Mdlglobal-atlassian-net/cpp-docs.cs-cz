---
title: "Postupy: vytváření konzolových aplikací CLR (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- console applications, templates
- CLR console applications, project template
ms.assetid: e89bce3c-706f-4ae0-8a90-cb1a0f674e70
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4e5aa59f26a3feb485cf2e7aae0564aca8848acd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-create-clr-console-applications-ccli"></a>Postupy: Vytváření konzolových aplikací CLR (C++/CLI)
Pomocí šablony Konzolová aplikace lze vytvořit projekt konzolové aplikace, který již obsahuje základní odkazy a soubory projektu.  
  
 Konzolová aplikace je obvykle zkompilována do samostatného spustitelného souboru, ale neobsahuje grafické uživatelské rozhraní. Uživatel konzolovou aplikaci spustí z příkazového řádku a používá jej k zadávání pokynů spuštěné aplikaci. Aplikace do příkazového řádku také vypisuje výstupní informace. Díky své bezprostřednosti je konzolová aplikace skvělým výukovým způsobem programovacích technik bez zájmu o implementaci uživatelského rozhraní.  
  
 Projekt vytvořený pomocí šablony Konzolová aplikace automaticky přidá tyto odkazy a soubory:  
  
-   Odkazy na tyto obory názvů v rozhraní .NET Framework:  
  
    -   [Systém](https://msdn.microsoft.com/en-us/library/system.appdomainmanager.appdomainmanager.aspx)– obsahuje základní třídy a základní třídy, které definují běžně používá hodnoty a referenční datové typy, události a obslužné rutiny událostí, rozhraní, atributy a zpracování výjimek.  
  
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
  
1.  Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.  
  
2.  V **nový projekt** dialogovém **nainstalovaných šablonách**, vyberte **Visual C++** uzlu, vyberte **CLR** uzel a potom vyberte Šablona konzolové aplikace.  
  
3.  V **název** zadejte jedinečný název pro vaši aplikaci.  
  
     Lze zadat další nastavení projektu a řešení, ale nejsou vyžadovány.  
  
4.  Vyberte **OK** tlačítko.  
  
## <a name="see-also"></a>Viz také  
 [CLR – projekty](../ide/files-created-for-clr-projects.md)   


