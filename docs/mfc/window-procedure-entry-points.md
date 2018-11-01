---
title: Vstupní bod procedury okna
ms.date: 11/04/2016
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
ms.openlocfilehash: 9e395ff96d27476bc2869e23139cb2d1233f02ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500916"
---
# <a name="window-procedure-entry-points"></a>Vstupní bod procedury okna

K ochraně procedury okna knihovny MFC, modul statické propojení s implementací okno zvláštní postup. Propojení se automaticky nastane, pokud modul je propojené s knihovnou MFC. Tento postup okno používá Makro AFX_MANAGE_STATE správně nastavit stav efektivní modulu, pak volá `AfxWndProc`, což zase delegoval vůči `WindowProc` členskou funkci odpovídající `CWnd`-odvozenému objektu.

## <a name="see-also"></a>Viz také

[Správa údajů o stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

