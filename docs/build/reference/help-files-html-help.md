---
title: Soubory nápovědy (Nápověda jazyka HTML)
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], HTML Help files
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
ms.openlocfilehash: cde4809fa270e66081088d68d806e637f64e5344
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822965"
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

[Typy souborů vytvořených pro projekty Visual C++](file-types-created-for-visual-cpp-projects.md)
