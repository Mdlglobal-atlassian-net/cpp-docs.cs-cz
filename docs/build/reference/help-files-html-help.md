---
title: Soubory nápovědy (Nápověda jazyka HTML)
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], HTML Help files
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
ms.openlocfilehash: 2b856defdac51c978aa07cd13ef8df153c9c3f5f
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707025"
---
# <a name="help-files-html-help"></a>Soubory nápovědy (Nápověda jazyka HTML)

Následující soubory jsou vytvořeny při přidání typu nápovědy HTML nápovědy do vaší aplikace tak, že vyberete **kontextové nápovědy** zaškrtávací políčko a pak vyberete **formát nápovědy HTML** v [Rozšířené funkce](../../mfc/reference/advanced-features-mfc-application-wizard.md) stránky Průvodce aplikací knihovny MFC.

|Název souboru|Umístění adresáře|Umístění v Průzkumníku řešení|Popis|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*.hhp|*Název_projektu*\hlp|soubory nápovědy HTML|Soubor projektu nápovědy. Obsahuje data potřebná pro kompilaci soubory nápovědy do souboru .hxs nebo soubor CHM.|
|*Projname*.hhk|*Název_projektu*\hlp|soubory nápovědy HTML|Obsahuje index témat nápovědy.|
|*Název_projektu*.hhc|*Název_projektu*\hlp|soubory nápovědy HTML|Obsah nápovědy projektu.|
|Makehtmlhelp.bat|*Projname*|Zdrojové soubory|Používá systém sestavení projektu nápovědy při kompilaci projektu.|
|Afxcore.htm|*Název_projektu*\hlp|Témata nápovědy HTML|Obsahuje standardní témata nápovědy pro standardní příkazy knihovny MFC a objektů na obrazovce. Přidáte vlastní témata nápovědy k tomuto souboru.|
|Afxprint.htm|*Název_projektu*\hlp|Témata nápovědy HTML|Obsahuje témata nápovědy pro příkazy pro tisk.|
|*.jpg; \*.gif|*Název_projektu*\hlp\Images|Zdrojové soubory|Obsahují obrázky pro různé témata nápovědy.|

## <a name="see-also"></a>Viz také:

[Soubor typy vytvořené pro sadu Visual Studio C++ projekty](file-types-created-for-visual-cpp-projects.md)
