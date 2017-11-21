---
title: Body vstupu procedury oken | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 99a4cf3fe356cf888101935aba5bec9a599135f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="window-procedure-entry-points"></a>Vstupní bod procedury okna
K ochraně procedury oken MFC, modul statické propojení s na speciální okno Postup implementace. Propojení se automaticky nastane, když modul je propojené s knihovnou MFC. Tento postup okno používá `AFX_MANAGE_STATE` makro správně nastavit stav efektivní modulu, pak zavolá **AfxWndProc**, která zase deleguje `WindowProc` členské funkce odpovídající `CWnd`-odvozené objekt.  
  
## <a name="see-also"></a>Viz také  
 [Správa údajů o stavu modulů knihovny MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

