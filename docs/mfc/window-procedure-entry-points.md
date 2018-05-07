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
ms.openlocfilehash: 1095061cce8ff8f189984aca99a06eb741a46e83
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="window-procedure-entry-points"></a>Vstupní bod procedury okna
K ochraně procedury oken MFC, modul statické propojení s na speciální okno Postup implementace. Propojení se automaticky nastane, když modul je propojené s knihovnou MFC. Tento postup okno používá `AFX_MANAGE_STATE` makro správně nastavit stav efektivní modulu, pak zavolá **AfxWndProc**, která zase deleguje `WindowProc` členské funkce odpovídající `CWnd`-odvozené objekt.  
  
## <a name="see-also"></a>Viz také  
 [Správa údajů o stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

