---
title: ExitInstance – členská funkce
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: c76f588b22ad8ffd1d3dae954c5113feffb62a3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405817"
---
# <a name="exitinstance-member-function"></a>ExitInstance – členská funkce

[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) členské funkce třídy [CWinApp](../mfc/reference/cwinapp-class.md) je volána pokaždé, když kopii aplikace ukončí, obvykle v důsledku uživatele ukončování aplikace.

Přepsat `ExitInstance` potřebujete zpracování zvláštního vyčištění, jako jsou například uvolnění prostředků grafiky zařízení (GDI) rozhraní nebo rušení přidělení paměti používá při provádění programu. Vyčištění standardních položek, jako jsou dokumenty a zobrazeními, ale poskytuje rozhraní, pomocí jiných přepisovatelné funkce pro provádění zvláštního vyčištění, které jsou specifické pro tyto objekty.

## <a name="see-also"></a>Viz také:

[CWinApp: Třída aplikace](../mfc/cwinapp-the-application-class.md)
