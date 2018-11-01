---
title: ExitInstance – členská funkce
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: b1c5b3a20f25f909188023ab1650bc41316d7a9f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637733"
---
# <a name="exitinstance-member-function"></a>ExitInstance – členská funkce

[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) členské funkce třídy [CWinApp](../mfc/reference/cwinapp-class.md) je volána pokaždé, když kopii aplikace ukončí, obvykle v důsledku uživatele ukončování aplikace.

Přepsat `ExitInstance` potřebujete zpracování zvláštního vyčištění, jako jsou například uvolnění prostředků grafiky zařízení (GDI) rozhraní nebo rušení přidělení paměti používá při provádění programu. Vyčištění standardních položek, jako jsou dokumenty a zobrazeními, ale poskytuje rozhraní, pomocí jiných přepisovatelné funkce pro provádění zvláštního vyčištění, které jsou specifické pro tyto objekty.

## <a name="see-also"></a>Viz také

[CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
