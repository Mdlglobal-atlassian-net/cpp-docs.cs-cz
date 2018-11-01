---
title: Specifikace nastavení projektu, Průvodce vytvořením nového projektu z existujících souborů kódu
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.importwiz.appsettings
helpviewer_keywords:
- Create New Project From Existing Code Files Wizard, project settings
ms.assetid: 9b8860c9-d35f-4f18-9565-2934d3d7f569
ms.openlocfilehash: f46436295e16d527718e59f1c4c199643f9e35ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522340"
---
# <a name="specify-project-settings-create-new-project-from-existing-code-files-wizard"></a>Specifikace nastavení projektu, Průvodce vytvořením nového projektu z existujících souborů kódu

Tato stránka Průvodce vytvoření nového projektu z existujících souborů kódu slouží k určení:

- Prostředí pro sestavení pro nový projekt

- Nastavení tak, aby odpovídaly konkrétní typ nové projekty ke generování sestavení

## <a name="task-list"></a>Seznam úloh

[Postupy: Vytvoření projektu jazyka C++ z existujícího kódu](../ide/how-to-create-a-cpp-project-from-existing-code.md)

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Pomocí sady Visual Studio**

   Určuje použití nástroje pro vytváření, které jsou zahrnuty v sadě Visual Studio pro vytváření nového projektu. Ve výchozím nastavení je vybraná tato možnost.

- **Typ projektu**

   Určuje typ projektu, který se bude generovat průvodce.

- **Projekt aplikace Windows**

   Označuje, že průvodce bude generovat projekt spustitelné aplikace Windows. Tato možnost je k dispozici **typu projektu** rozevíracího seznamu.

- **Projekt konzolové aplikace**

   Označuje, že průvodce bude generovat projekt konzolové aplikace. Tato možnost je k dispozici **typu projektu** rozevíracího seznamu.

- **Projekt dynamické knihovny (DLL)**

   Označuje, že průvodce bude generovat projektu pro aplikaci prázdný DLL knihovny. Tato možnost je k dispozici **typu projektu** rozevíracího seznamu.

- **Projekt statické knihovny (LIB)**

   Označuje, že průvodce bude generovat projekt statické knihovny. Tato možnost je k dispozici **typu projektu** rozevíracího seznamu.

- **Přidání podpory knihovny ATL**

   Přidá podporu ATL do nového projektu.

- **Přidat podporu knihovny MFC**

   Přidá podporu knihovny MFC do nového projektu.

- **Přidání podpory pro modul Common Language Runtime**

   Přidá podporu pro nový projekt CLR programování.

- **Modul Common Language Runtime**

   Určuje nový projekt, který má být zajištěn soulad funkce CLR.

- **Modul Common Language Runtime (stará syntaxe)**

   Určuje nový projekt, který má být zajištěn soulad spravovaného rozšíření pro C++ syntaxi, což je programovací syntaxe CLR před Visual C++ 2005.

- **Použití externího sestavovacího systému**

   Určuje použití nástroje sestavení, které nejsou zahrnuty v sadě Visual Studio pro vytváření nového projektu. Pokud je vybraná tato možnost, můžete určit příkazové řádky sestavení na **zadat konfigurační nastavení ladění** a **zadejte konfigurační nastavení vydání** stránky.

   > [!NOTE]
   > Když **použijte externí sestavovací systém** zaškrtnete políčko, rozhraní IDE nesestaví nový projekt, proto /D, / jsem, /FI, /AI nebo možnosti /FU je vyžadován pro kompilaci. Však musí tyto možnosti nastavit správně, aby IntelliSense fungovat správně.

## <a name="see-also"></a>Viz také

[Specifikace konfigurace nastavení pro ladění, Průvodce vytvořením nového projektu z existujících souborů kódu](../ide/specify-debug-configuration-settings.md)<br>
[Specifikace konfigurace nastavení pro vydání, Průvodce vytvoření nového projektu z existujících souborů kódu](../ide/specify-release-configuration.md)