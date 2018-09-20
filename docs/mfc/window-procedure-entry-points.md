---
title: Body vstupu procedury oken | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3226df51d2a83484de78d0d76c9af67e150e8eb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403185"
---
# <a name="window-procedure-entry-points"></a>Vstupní bod procedury okna

K ochraně procedury okna knihovny MFC, modul statické propojení s implementací okno zvláštní postup. Propojení se automaticky nastane, pokud modul je propojené s knihovnou MFC. Tento postup okno používá Makro AFX_MANAGE_STATE správně nastavit stav efektivní modulu, pak volá `AfxWndProc`, což zase delegoval vůči `WindowProc` členskou funkci odpovídající `CWnd`-odvozenému objektu.

## <a name="see-also"></a>Viz také

[Správa údajů o stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

