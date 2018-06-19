---
title: Identifikátory standardních příkazů a oken | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- standard command and Window IDs
ms.assetid: 0424805c-fff8-4531-8f0c-15cfb13aa612
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 72b50108a9b880961f0dd8bcded1126a635fb9e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371647"
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
