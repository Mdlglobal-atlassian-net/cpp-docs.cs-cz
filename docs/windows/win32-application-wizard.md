---
title: "Win32 – Průvodce aplikací | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.win32.overview
dev_langs: C++
helpviewer_keywords:
- Win32 Application Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c97caee74e1ae918924632802c155b23fffe0527
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="win32-application-wizard"></a>Win32 – průvodce aplikací
Průvodce aplikace Win32 Visual C++ umožňuje vytvořit čtyři typy projektů (uvedené v záhlaví v následující tabulce). V každém případě můžete zadat další možnosti, které jsou vhodné pro typ projektu, který můžete otevřít. Následující tabulka uvádí, které možnosti jsou dostupné pro jednotlivé typy aplikací.  
  
|Typ podpory|Konzolová aplikace|Aplikace spustitelný soubor (Windows)|Knihovna DLL|Statická knihovna|  
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|  
|**Prázdný projekt**|Ano|Ano|Ano|Ne|  
|**Export symbolů**|Ne|Ne|Ano|Ne|  
|**Předkompilovaných hlaviček**|Ne|Ne|Ne|Ano|  
|**Podpora ATL**|Ano|Ne|Ne|Ne|  
|**Podpora MFC**|Ano|Ne|Ne|Ano|  
  
## <a name="overview"></a>Přehled  
 Tato stránka průvodce popisuje aktuální nastavení projektu pro aplikace Win32, kterou vytváříte. Ve výchozím nastavení jsou nastavené následující možnosti:  
  
-   Projekt je aplikace systému Windows.  
  
-   Projekt není prázdný.  
  
-   Projekt obsahuje žádné symboly export.  
  
-   Projekt nepoužívá předkompilovaný hlavičkový soubor (Tato možnost je dostupná pro projekty statických knihoven pouze).  
  
-   Tento projekt zahrnuje podporu pro knihovny MFC ani ATL.  
  
 Chcete-li změnit toto výchozí nastavení, klikněte na tlačítko [nastavení aplikace](../windows/application-settings-win-32-project-wizard.md) v levém sloupci průvodce a proveďte požadované změny.  
  
 Po vytvoření aplikace systému Windows, můžete přidat obecné třídy C++ pomocí [Obecné](../ide/generic-cpp-class-wizard.md) kód průvodce. Můžete přidat další položky, jako jsou soubory, soubory hlaviček, zdroje nebo textové soubory HTML.  
  
> [!NOTE]
>  Nelze přidat třídy ATL a MFC – třídy můžete přidat pouze ty typy aplikace pracovní plochy Windows, které podporují MFC (viz předchozí tabulka).  
  
 Průvodce vytvoří soubory můžete zobrazit pro svůj projekt v **Průzkumníku řešení**. Další informace o souborech Průvodce vytvoří pro váš projekt, naleznete v souboru projektu vygenerované souboru ReadMe.txt. Další informace o typech souborů [typy souborů vytvořené pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytváření aplikací prázdný Windows Desktop](../windows/creating-an-empty-windows-desktop-application.md)   
 [Typy projektů Visual C++](../ide/visual-cpp-project-types.md)