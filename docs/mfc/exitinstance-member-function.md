---
title: ExitInstance – členská funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords: []
dev_langs:
- C++
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da411fbecdea0a1e7b8976ca119057204693a9bd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387858"
---
# <a name="exitinstance-member-function"></a>ExitInstance – členská funkce

[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) členské funkce třídy [CWinApp](../mfc/reference/cwinapp-class.md) je volána pokaždé, když kopii aplikace ukončí, obvykle v důsledku uživatele ukončování aplikace.

Přepsat `ExitInstance` potřebujete zpracování zvláštního vyčištění, jako jsou například uvolnění prostředků grafiky zařízení (GDI) rozhraní nebo rušení přidělení paměti používá při provádění programu. Vyčištění standardních položek, jako jsou dokumenty a zobrazeními, ale poskytuje rozhraní, pomocí jiných přepisovatelné funkce pro provádění zvláštního vyčištění, které jsou specifické pro tyto objekty.

## <a name="see-also"></a>Viz také

[CWinApp – třída aplikace](../mfc/cwinapp-the-application-class.md)
