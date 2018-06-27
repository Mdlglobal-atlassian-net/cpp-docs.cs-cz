---
title: Body vstupu procedury oken | Microsoft Docs
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
ms.openlocfilehash: 315526a8f95a1d62ac89f3a76fab492c9b136715
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956379"
---
# <a name="window-procedure-entry-points"></a>Vstupní bod procedury okna
K ochraně procedury oken MFC, modul statické propojení s na speciální okno Postup implementace. Propojení se automaticky nastane, když modul je propojené s knihovnou MFC. Tento postup okno používá AFX_MANAGE_STATE – makro správně nastavit stav efektivní modul a potom zavolá `AfxWndProc`, která zase deleguje `WindowProc` členské funkce odpovídající `CWnd`-odvozené objektu.  
  
## <a name="see-also"></a>Viz také  
 [Správa údajů o stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

