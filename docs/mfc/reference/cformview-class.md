---
title: "Třídy CFormView | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
dev_langs: C++
helpviewer_keywords:
- CFormView [MFC], CFormView
- CFormView [MFC], IsInitDlgCompleted
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f22256f7e471fd30753db36ba53059b2588e0da8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cformview-class"></a>Třídy CFormView – třída
Základní třída používaná pro zobrazení formuláře.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFormView : public CScrollView  
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFormView::CFormView](#cformview)|Vytvoří `CFormView` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|Používán k synchronizaci během inicializace.|  
  
## <a name="remarks"></a>Poznámky  
 Zobrazení formuláře je v podstatě zobrazení, které obsahuje ovládací prvky. Tyto ovládací prvky jsou podrobně popsány podle prostředků šablony dialogového okna. Použití `CFormView` Pokud chcete formuláře v aplikaci. Podporují se tyto zobrazení posouvání, podle potřeby, pomocí [CScrollView](../../mfc/reference/cscrollview-class.md) funkce.  
  
 Po [vytvoření aplikace založené na formulářích](../../mfc/reference/creating-a-forms-based-mfc-application.md), jeho třídy zobrazení můžete založit na `CFormView`, takže je k aplikaci založené na formulářích.  
  
 Můžete také vložit nový [formuláře témata](../../mfc/form-views-mfc.md) do aplikací na základě dokumentu zobrazení. I když se aplikace původně nepodporoval formulářů, Visual C++ přidá tato podpora při vložení nového formuláře.  
  
 Průvodce aplikací knihovny MFC a příkaz Přidat třídu jsou upřednostňované metody pro vytvoření aplikace založené na formulářích. Pokud potřebujete k vytvoření aplikace založené na formulářích bez použití těchto metod najdete v tématu [vytvoření aplikace založené na formulářích](../../mfc/reference/creating-a-forms-based-mfc-application.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 `CFormView`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxext.h  
  
##  <a name="cformview"></a>CFormView::CFormView  
 Vytvoří `CFormView` objektu.  
  
```  
CFormView(LPCTSTR lpszTemplateName);  
CFormView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszTemplateName`  
 Obsahuje řetězec ukončené hodnotou null, který je název prostředku šablony dialogového okna.  
  
 `nIDTemplate`  
 Obsahuje číslo ID prostředku šablony dialogového okna.  
  
### <a name="remarks"></a>Poznámky  
 Když vytvoříte objekt typ odvozený z `CFormView`, vyvolat jeden z konstruktorů vytvořit objekt zobrazení a identifikovat prostředku dialogového okna, na kterých je založena zobrazení. Prostředek můžete identifikovat pomocí názvu (pass řetězec jako argument konstruktoru) nebo pomocí jejího ID (pass celé číslo bez znaménka jako argument).  
  
 Ovládací prvky pro okno a podřízené zobrazení formuláře se vytvoří až v okamžiku `CWnd::Create` je volána. `CWnd::Create`je voláno rámcem jako součást dokumentů a zobrazení procesu vytváření, které vycházejí z šablony dokumentu.  
  
> [!NOTE]
>  Odvozené třídy *musí* zadat vlastní konstruktor. V konstruktoru, vyvolat konstruktor, `CFormView::CFormView`, s názvem prostředků nebo ID jako argument, jak je znázorněno v přehledu třídy předchozí.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]  
  
 [!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]  
  
##  <a name="isinitdlgcompleted"></a>CFormView::IsInitDlgCompleted  
 Využívané prostředím MFC zajistit, že inicializace je dokončit před prováděním dalších operací.  
  
```  
BOOL IsInitDlgCompleted() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud byla dokončena funkci inicializace pro toto dialogové okno.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC SNAPVW](../../visual-cpp-samples.md)   
 [Ukázka MFC VIEWEX](../../visual-cpp-samples.md)   
 [CScrollView – třída](../../mfc/reference/cscrollview-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDialog – třída](../../mfc/reference/cdialog-class.md)   
 [CScrollView – třída](../../mfc/reference/cscrollview-class.md)
