---
title: Vstupní bod procedury okna
ms.date: 11/04/2016
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
ms.openlocfilehash: 6d91e2c432588afc5a84f7189fa87a7fc2531b1a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372009"
---
# <a name="window-procedure-entry-points"></a>Vstupní bod procedury okna

K ochraně procedury okna knihovny MFC, modul statické propojení s implementací okno zvláštní postup. Propojení se automaticky nastane, pokud modul je propojené s knihovnou MFC. Tento postup okno používá Makro AFX_MANAGE_STATE správně nastavit stav efektivní modulu, pak volá `AfxWndProc`, což zase delegoval vůči `WindowProc` členskou funkci odpovídající `CWnd`-odvozenému objektu.

## <a name="see-also"></a>Viz také:

[Správa údajů o stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)
