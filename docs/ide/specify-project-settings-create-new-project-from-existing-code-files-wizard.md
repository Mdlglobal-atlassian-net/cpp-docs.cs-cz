---
title: Specifikace nastavení projektu z existujících souborů kódu pomocí Průvodce vytvořením nového projektu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.appsettings
dev_langs:
- C++
helpviewer_keywords:
- Create New Project From Existing Code Files Wizard, project settings
ms.assetid: 9b8860c9-d35f-4f18-9565-2934d3d7f569
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0f59b802b5a24c1b449f78cccee4744538a5a0e
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33338943"
---
# <a name="specify-project-settings-create-new-project-from-existing-code-files-wizard"></a>Specifikace nastavení projektu, Průvodce vytvořením nového projektu z existujících souborů kódu
Na této stránce Průvodce vytvoření nového projektu z existujících souborů kódu můžete zadat:  
  
-   Prostředí sestavení pro nový projekt  
  
-   Nastavení tak, aby odpovídaly určitý typ nového projektu pro generování sestavení  
  
## <a name="task-list"></a>Seznam úloh  
 [Postupy: Vytvoření projektu jazyka C++ z existujícího kódu](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Použijte sadu Visual Studio**  
 Určuje použití nástrojů sestavení, které jsou zahrnuté v sadě Visual Studio pro vytvoření nového projektu. Tato možnost je vybrána ve výchozím nastavení.  
  
 **Typ projektu**  
 Určuje typ projektu, průvodce bude generovat.  
  
 **Projekt aplikace Windows**  
 Označuje, že průvodce bude generovat projekt pro spustitelný soubor aplikace systému Windows. Tato možnost je dostupná z **typu projektu** rozevíracího seznamu.  
  
 **Projekt konzolové aplikace**  
 Označuje, že průvodce bude generovat projekt konzolové aplikace. Tato možnost je dostupná z **typu projektu** rozevíracího seznamu.  
  
 **Projekt dynamické knihovny (DLL)**  
 Označuje, že průvodce bude generovat projekt pro prázdný knihovny DLL. Tato možnost je dostupná z **typu projektu** rozevíracího seznamu.  
  
 **Statické knihovny LIB projektu**  
 Označuje, že průvodce bude generovat projekt pro statické knihovny. Tato možnost je dostupná z **typu projektu** rozevíracího seznamu.  
  
 **Přidat podporu pro knihovny ATL**  
 Přidá podporu knihovny ATL do nového projektu.  
  
 **Přidat podporu pro knihovny MFC**  
 Podpora MFC přidá do nového projektu.  
  
 **Přidání podpory pro modul Common Language Runtime**  
 Přidá podporu CLR programování do nového projektu.  
  
 **Modul Common Language Runtime**  
 Určuje nový projekt splňovat funkce modulu CLR.  
  
 **Modul Common Language Runtime (staré syntaxe)**  
 Určuje nový projekt tak, aby vyhovoval spravovaných rozšíření pro C++ syntaxi, což je programovací syntaxe CLR před Visual C++ 2005.  
  
 **Použít systém externí sestavení**  
 Určuje použití nástrojů sestavení, které nejsou zahrnuté v sadě Visual Studio pro vytvoření nového projektu. Pokud je vybraná tato možnost, můžete zadat sestavení příkazové řádky na **zadat nastavení konfigurace ladění** a **zadejte konfigurace nastavení pro vydání** stránky.  
  
> [!NOTE]
>  Když **použít externí sestavovací systém** zaškrtnutá možnost, rozhraní IDE nelze sestavit nový projekt, proto /D, / I, /FI, /AI nebo /FU možnosti jsou požadovány pro kompilaci. Však musí tyto možnosti nastavit správně v pořadí pro technologii IntelliSense, která fungovat správně.  
  
## <a name="see-also"></a>Viz také  
 [Zadejte nastavení pro konfiguraci ladění, vytvoření nového projektu z existujících souborů kódu pomocí Průvodce](../ide/specify-debug-configuration-settings.md)   
 [Specifikace konfigurace nastavení pro vydání, Průvodce vytvoření nového projektu z existujících souborů kódu](../ide/specify-release-configuration.md)