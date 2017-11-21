---
title: "Identifikátory standardních příkazů a oken | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros
dev_langs: C++
helpviewer_keywords: standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a7209e3c6e85e5d5855ddac513f95115b02cd1aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="standard-command-and-window-ids"></a>Standardní identifikátory příkazů a oken
Knihovny Microsoft Foundation Class definuje počet standardních příkazů a oken ID Afxres.h. Tyto identifikátory se nejčastěji používají v rámci editory prostředků a v okně Vlastnosti pro mapování zpráv na funkce obslužné rutiny. Všechny standardní příkazy **ID_** předponu. Například pokud použijete editor nabídek, obvykle vytvoření vazby soubor otevřete položku nabídky u standardního `ID_FILE_OPEN` příkaz ID.  
  
 Pro většinu standardních příkazů, kódu aplikace není nutné k odkazování na ID příkazu, protože rozhraní samotného zpracovává příkazy prostřednictvím mapy zpráv v jeho primární framework tříd ( `CWinThread`, `CWinApp`, < c4 > `CView` , **CDocument**a tak dále).  
  
 Kromě identifikátory standardních příkazů, jsou definovány počet dalších standardní ID, které mají následující předpony z **AFX_ID**. Tyto identifikátory zahrnují ID standardní okno (předponu **AFX_IDW_**), řetězec ID (předponu **AFX_IDS_**) a několik dalších typů.  
  
 ID, které začínají **AFX_ID** předponu zřídka používají programátoři, ale možná budete muset při přepisování framework funkcí, které se také podívat na odkazovat tyto identifikátory **AFX_ID**s.  
  
 ID nejsou jednotlivě popsané v této referenci. Další informace o nich najdete v technické poznámky [20](../../mfc/tn020-id-naming-and-numbering-conventions.md), [21](../../mfc/tn021-command-and-message-routing.md), a [22](../../mfc/tn022-standard-commands-implementation.md).  
  
> [!NOTE]
>  Soubor hlaviček Afxres.h je nepřímo součástí Afxwin.h. Následující příkaz musí explicitně zahrnout do souboru skriptu (.rc) prostředků vaší aplikace:  
  
 [!code-cpp[NVC_MFC_Utilities#47](../../mfc/codesnippet/cpp/standard-command-and-window-ids_1.h)]  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
