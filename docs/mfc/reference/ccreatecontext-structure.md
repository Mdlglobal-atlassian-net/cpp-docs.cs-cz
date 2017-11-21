---
title: Struktura CCreateContext | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CCreateContext
dev_langs: C++
helpviewer_keywords: CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 900664f43b132b118a8da0b855d5d5291fd79fee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccreatecontext-structure"></a>Struktura CCreateContext
Rozhraní používá `CCreateContext` struktury při vytváření okna s rámečkem a zobrazení, které jsou přidruženy dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CCreateContext  
```  
  
## <a name="remarks"></a>Poznámky  
 `CCreateContext`je struktura a nemá základní třídu.  
  
 Při vytváření okna hodnoty v této struktuře poskytují informace, které slouží pro připojení součástí dokument k zobrazení jeho data. Budete muset použít `CCreateContext` Pokud přepíšete součástí procesu vytváření.  
  
 A `CCreateContext` struktura obsahuje odkazy na dokument, okně s rámečkem, zobrazení a šablony dokumentu. Obsahuje taky odkazy `CRuntimeClass` identifikující na typu zobrazení pro vytvoření. Run-time třída informace a aktuální ukazatele dokumentu slouží k vytvoření nového zobrazení dynamicky. Následující tabulka doporučuje jak a kdy každý `CCreateContext` člen může být použit:  
  
|Člen|Typ|Co je pro|  
|------------|----------|--------------------|  
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass`k vytvoření nového zobrazení.|  
|`m_pCurrentDoc`|`CDocument*`|Stávající dokument, který se má přidružit nové zobrazení.|  
|`m_pNewDocTemplate`|`CDocTemplate*`|Šablony dokumentů přidružené k vytvoření nového okna MDI rámce.|  
|`m_pLastView`|`CView*`|Původní zobrazení, na kterém jsou modelovat další zobrazení, jako vytvoření rozdělovače okno zobrazení nebo vytvoření druhého zobrazení v dokumentu.|  
|`m_pCurrentFrame`|`CFrameWnd*`|Okno rámečku, na kterém jsou modelovat okna s rámečkem další jako vytvoření druhého okně s rámečkem v dokumentu.|  
  
 Pokud šablona dokumentu vytvoří dokument a jeho přidružených součásti, ověřuje informace uložené v `CCreateContext` struktura. Zobrazení například nesmí být vytvářeny pro neexistující dokument.  
  
> [!NOTE]
>  Všechny následující ukazatele v `CCreateContext` jsou volitelná a může být `NULL` Pokud určena nebo neznámé.  
  
 `CCreateContext`používá členské funkce uvedené v části "Viz také." Pokud budete chtít nepřepíšete najdete popis těchto funkcí konkrétní informace.  
  
 Tady je několik obecné pokyny:  
  
-   Když předat jako argument pro vytvoření oken, jako v `CWnd::Create`, `CFrameWnd::Create`, a `CFrameWnd::LoadFrame`, kontext vytvořit Určuje, co novém okně by měly být připojené k. Pro většinu windows celá struktura je volitelné a `NULL` lze předat ukazatel.  
  
-   Přepisovatelné členské funkce jako například `CFrameWnd::OnCreateClient`, `CCreateContext` argument je volitelný.  
  
-   Pro členské funkce související se situací v zobrazení vytváření, je nutné zadat dostatek informací pro vytvoření zobrazení. Pro první zobrazení v rozděleném okně, musíte třeba zadat informace o třídě zobrazení a aktuálním dokumentu.  
  
 Obecně platí, pokud chcete použít výchozí hodnoty framework, můžete ignorovat `CCreateContext`. Pokud se pokusíte pokročilejší úpravy, zdrojový kód Microsoft Foundation Class Library nebo ukázkové programy, jako je například VIEWEX, vám pomohou. Pokud zapomenete povinný parametr, framework assertion zjistit, co jste zapomněli.  
  
 Další informace o `CCreateContext`, naleznete v ukázce MFC [VIEWEX](../../visual-cpp-samples.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxext.h  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)   
 [CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)   
 [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)   
 [CSplitterWnd::Create](../../mfc/reference/csplitterwnd-class.md#create)   
 [CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)   
 [CWnd::Create](../../mfc/reference/cwnd-class.md#create)

