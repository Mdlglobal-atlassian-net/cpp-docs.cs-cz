---
title: CWinApp a průvodce aplikací MFC
ms.date: 11/04/2016
f1_keywords:
- CWinApp
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: cb45c8ffae15628b0b99a1ebcd962d88d845f83b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266260"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp a průvodce aplikací MFC

Při vytváření kostry aplikace, Průvodce aplikací MFC deklaruje Aplikační třída odvozená z [CWinApp](../mfc/reference/cwinapp-class.md). Průvodce aplikací MFC také vygeneruje soubor implementace, která obsahuje následující položky:

- Mapy zpráv pro třídu aplikace.

- Prázdná třída konstruktor.

- Proměnná, která deklaruje pouze objekt třídy.

- Standardní implementace vaší `InitInstance` členskou funkci.

Třída aplikace je umístěn v záhlaví projektu a hlavní zdrojových souborů. Názvy třídy a soubory vytvořené jsou založeny na název projektu, který zadáte v průvodci MFC aplikace. Nejjednodušší způsob, jak zobrazit kód pro tyto třídy je prostřednictvím [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code).

Standardní implementace a mapování zpráv zadaný jsou dostatečné pro celou řadu účelů, ale můžete je upravit podle potřeby. Nejzajímavější z těchto implementací je `InitInstance` členskou funkci. Obvykle přidáte kód do základní implementace `InitInstance`.

## <a name="see-also"></a>Viz také:

[CWinApp Třída aplikace](../mfc/cwinapp-the-application-class.md)<br/>
[Přepisovatelné členské funkce CWinApp](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Speciální služby CWinApp](../mfc/special-cwinapp-services.md)
