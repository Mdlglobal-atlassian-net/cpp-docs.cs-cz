---
title: CWinApp a průvodce aplikací MFC
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: 1a46842d7b4d6a588da585d63e2ad56982bb0ff8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447039"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp a průvodce aplikací MFC

Když vytvoří kostru aplikace, Průvodce aplikací knihovny MFC deklaruje třídu aplikace odvozenou z [CWinApp](../mfc/reference/cwinapp-class.md). Průvodce aplikací knihovny MFC také generuje implementační soubor, který obsahuje následující položky:

- Mapa zpráv pro třídu aplikace

- Prázdný konstruktor třídy

- Proměnná, která deklaruje pouze jeden objekt třídy.

- Standardní implementace `InitInstance` členské funkce.

Třída aplikace je umístěna v záhlaví projektu a v hlavních zdrojových souborech. Názvy vytvořených tříd a souborů jsou založeny na názvu projektu, který zadáte v Průvodci aplikací knihovny MFC. Nejjednodušší způsob, jak zobrazit kód pro tyto třídy, je prostřednictvím [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code).

Standardní implementace a mapa zpráv jsou vhodné pro mnoho účelů, ale můžete je podle potřeby upravit. Nejzajímavější z těchto implementací je `InitInstance` členská funkce. Obvykle přidáte kód do implementace základní `InitInstance`.

## <a name="see-also"></a>Viz také

[CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)<br/>
[Přepisovatelné členské funkce CWinApp](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Speciální služby CWinApp](../mfc/special-cwinapp-services.md)
