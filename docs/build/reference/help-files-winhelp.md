---
title: Soubory nápovědy (WinHelp)
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], WinHelp files
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
ms.openlocfilehash: 376d9faa87868cce842a1cb70273e220ff691fa4
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823170"
---
# <a name="help-files-winhelp"></a>Soubory nápovědy (WinHelp)

Následující soubory jsou vytvořeny při přidání typu WinHelp nápovědy do vaší aplikace tak, že vyberete **kontextové nápovědy** zaškrtávací políčko a pak vyberete **WinHelp formátu** v [Rozšířené funkce](../../mfc/reference/advanced-features-mfc-application-wizard.md) stránky Průvodce aplikací knihovny MFC.

|Název souboru|Umístění adresáře|Umístění v Průzkumníku řešení|Popis|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*.hpj|*Název_projektu*\hlp|Zdrojové soubory|Soubor nápovědy projekt používá kompilátor nápovědy k vytvoření aplikace nebo souboru nápovědy ovládacího prvku.|
|*Projname*.rtf|*Název_projektu*\hlp|Soubory nápovědy|Obsahuje informace o přizpůsobení souboru HPJ a šablony témata, které můžete upravovat.|
|*Název_projektu*.cnt|*Název_projektu*\hlp|Soubory nápovědy|Poskytuje strukturu pro **obsah** okno v nápovědě k Windows.|
|Makehelp.bat|*Projname*|Zdrojové soubory|Používá systém sestavení projektu nápovědy při kompilaci projektu.|
|Print.rtf|*Název_projektu*\hlp|Soubory nápovědy|Vytvoří, pokud váš projekt zahrnuje podporu tisku (výchozí). Popisuje příkazy pro tisk a dialogových oknech.|
|*.bmp|*Název_projektu*\hlp|Zdrojové soubory|Obsahují obrázky pro různé témata nápovědy.|

Podporu nápovědy do projektu knihovny ovládací prvek ActiveX knihovny MFC lze přidat výběrem **Generovat soubory nápovědy** v [nastavení aplikace](../../mfc/reference/application-settings-mfc-activex-control-wizard.md) kartu průvodce ovládací prvek ActiveX knihovny MFC. Následující soubory jsou přidány do projektu přidáte Nápověda a odborná pomoc pro ovládací prvek ActiveX knihovny MFC:

|Název souboru|Umístění adresáře|Umístění v Průzkumníku řešení|Popis|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*.hpj|*Název_projektu*\hlp|Zdrojové soubory|Soubor projektu používá kompilátor nápovědy k vytvoření aplikace nebo souboru nápovědy ovládacího prvku.|
|*Projname*.rtf|*Název_projektu*\hlp|Project|Obsahuje informace o přizpůsobení souboru HPJ a šablony témata, které můžete upravovat.|
|Makehelp.bat|*Projname*|Zdrojové soubory|Používá systém sestavení projektu nápovědy při kompilaci projektu.|
|Bullet.bmp|*Projname*|Zdrojové soubory|Používá standardní témata nápovědy k reprezentaci seznamy s odrážkami.|

## <a name="see-also"></a>Viz také:

[Typy souborů vytvořených pro projekty Visual C++](file-types-created-for-visual-cpp-projects.md)
