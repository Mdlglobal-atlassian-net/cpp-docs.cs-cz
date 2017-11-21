---
title: "Třída CMFCTasksPaneTaskGroup | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsBottom
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsCollapsed
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_bIsSpecial
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_lstTasks
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rect
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_rectGroup
- AFXTASKSPANE/CMFCTasksPaneTaskGroup::m_strName
dev_langs: C++
helpviewer_keywords:
- CMFCTasksPaneTaskGroup [MFC], CMFCTasksPaneTaskGroup
- CMFCTasksPaneTaskGroup [MFC], SetACCData
- CMFCTasksPaneTaskGroup [MFC], m_bIsBottom
- CMFCTasksPaneTaskGroup [MFC], m_bIsCollapsed
- CMFCTasksPaneTaskGroup [MFC], m_bIsSpecial
- CMFCTasksPaneTaskGroup [MFC], m_lstTasks
- CMFCTasksPaneTaskGroup [MFC], m_rect
- CMFCTasksPaneTaskGroup [MFC], m_rectGroup
- CMFCTasksPaneTaskGroup [MFC], m_strName
ms.assetid: 2111640b-a46e-4b27-b033-29e88632b86a
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1ccac37a7ffa7ab5967118ec2bcb4c2c4cf5501c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmfctaskspanetaskgroup-class"></a>CMFCTasksPaneTaskGroup – třída
`CMFCTasksPaneTaskGroup` Třída je pomocná třída používané [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) ovládacího prvku. Objekty typu `CMFCTasksPaneTaskGroup` představují *skupina úkolů*. Skupiny úloh je seznam položek, které zobrazuje rozhraní samostatné pole, která obsahuje tlačítko Sbalit. Pole může mít volitelné popisek (název skupiny). Pokud skupina sbalena, seznam úloh není viditelná.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCTasksPaneTaskGroup : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup](#cmfctaskspanetaskgroup)|Vytvoří `CMFCTasksPaneTaskGroup` objektu.|  
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::SetACCData](#setaccdata)|Určuje nastavení dat pro usnadnění přístupu pro aktuální skupině úloh.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|Určuje, zda je k dolnímu okraji ovládacího prvku podokno úloha zarovnán skupiny úloh.|  
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|Určuje, zda je sbalené skupiny úloh.|  
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|Určuje, zda je skupina úkolů *speciální.* Rozhraní zobrazuje speciální titulky jinou barvou.|  
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|Obsahuje vnitřní seznam úloh.|  
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|Určuje ohraničující obdélník titulek skupiny.|  
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|Určuje ohraničující obdélník skupiny.|  
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|Určuje název skupiny.|  
  
## <a name="remarks"></a>Poznámky  
 Následující obrázek znázorňuje skupinu rozšířené úloh:  
  
 ![Skupiny úloh, rozšířit](../../mfc/reference/media/nexttaskgrpexpand.png "nexttaskgrpexpand")  
  
 Následující obrázek znázorňuje skupinu sbalené úkolů:  
  
 ![Skupina sbalené úkolů](../../mfc/reference/media/nexttaskgrpcollapse.png "nexttaskgrpcollapse")  
  
 Následující obrázek znázorňuje skupinu úkolů bez popisek:  
  
 ![Skupiny úloh bez popisek](../../mfc/reference/media/nexttaskgrpnocapt.png "nexttaskgrpnocapt")  
  
 Následující obrázek znázorňuje dvě skupiny úloh. První skupinu úloh je označen jako speciální nastavením `m_bIsSpecial` příznak, který `TRUE`, zatímco druhý skupiny úloh není speciální. Všimněte si, jak je tmavší než druhý skupiny úloh titulek pro první skupinu úloh:  
  
 ![Skupina speciální úkolů](../../mfc/reference/media/nexttaskgrpspecial.png "nexttaskgrpspecial")  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxTasksPane.h  
  
##  <a name="cmfctaskspanetaskgroup"></a>CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup  
 Vytvoří `CMFCTasksPaneTaskGroup` objektu.  
  
```  
CMFCTasksPaneTaskGroup(
    LPCTSTR lpszName,  
    BOOL bIsBottom,  
    BOOL bIsSpecial=FALSE,  
    BOOL bIsCollapsed=FALSE,  
    CMFCTasksPanePropertyPage* pPage=NULL,  
    HICON hIcon=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszName`  
 Určuje název skupiny v záhlaví skupiny.  
  
 `bIsBottom`  
 Určuje, zda je skupině zarovnán k dolnímu okraji ovládacího prvku podokno úlohy.  
  
 `bIsSpecial`  
 Určuje, zda skupiny je určený jako *speciální* a tedy jestli titulek skupiny je plná barvu.  
  
 `bIsCollapsed`  
 Určuje, zda je skupina sbalena.  
  
 `pPage`  
 Určuje vlastnost stránku, který je součástí této skupiny úloh.  
  
 `hIcon`  
 Určuje ikona, která se zobrazí v záhlaví skupiny.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_bisbottom"></a>CMFCTasksPaneTaskGroup::m_bIsBottom  
 Určuje, zda je k dolnímu okraji ovládacího prvku podokno úloha zarovnán skupiny úloh.  
  
```  
BOOL m_bIsBottom;  
```  
  
### <a name="remarks"></a>Poznámky  
 V dolní části ovládacího prvku podokno úlohy lze zarovnávat jenom jedné skupiny. Poslední musí být přidaný této skupiny úloh. Další informace najdete v tématu [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).  
  
##  <a name="m_biscollapsed"></a>CMFCTasksPaneTaskGroup::m_bIsCollapsed  
 Určuje, zda je sbalené skupiny úloh.  
  
```  
BOOL m_bIsCollapsed;  
```  
  
### <a name="remarks"></a>Poznámky  
 Můžete povolit nebo zakázat možnost sbalit skupiny v podokně úloh voláním [CMFCTasksPane::EnableGroupCollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse).  
  
##  <a name="m_bisspecial"></a>CMFCTasksPaneTaskGroup::m_bIsSpecial  
 Určuje, zda je skupina úkolů *speciální* a jestli se mají titulek pro skupinu úloh speciální identifikovat pomocí různých barev.  
  
```  
BOOL m_bIsSpecial;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud vaše aplikace používá visual motiv systému Windows XP a `m_bIsSpecial` je `FALSE`, volání framework `DrawThemeBackground` s `EBP_NORMALGROUPBACKGROUND` příznak. Pokud `m_bIsSpecial` je `TRUE`, volání framework `DrawThemeBackground` s `EBP_SPECIALGROUPBACKGROUND` příznak.  
  
##  <a name="m_lsttasks"></a>CMFCTasksPaneTaskGroup::m_lstTasks  
 Obsahuje vnitřní seznam úloh.  
  
```  
CObList m_lstTasks;  
```  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li vyplnit tento seznam, volejte [CMFCTasksPane::AddTask](../../mfc/reference/cmfctaskspane-class.md#addtask).  
  
##  <a name="m_rect"></a>CMFCTasksPaneTaskGroup::m_rect  
 Určuje ohraničující obdélník titulek skupiny.  
  
```  
CRect m_rect;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota se vypočítá automaticky podle rozhraní.  
  
##  <a name="m_rectgroup"></a>CMFCTasksPaneTaskGroup::m_rectGroup  
 Určuje ohraničující obdélník skupiny.  
  
```  
CRect m_rectGroup;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota se vypočítá automaticky podle rozhraní.  
  
##  <a name="m_strname"></a>CMFCTasksPaneTaskGroup::m_strName  
 Určuje název skupiny.  
  
```  
CString m_strName;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato hodnota je prázdná, nezobrazí titulek skupiny a nemůže být sbalené skupiny.  
  
##  <a name="setaccdata"></a>CMFCTasksPaneTaskGroup::SetACCData  
 Určuje nastavení dat pro usnadnění přístupu pro aktuální skupině úloh.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pParent`  
 Představuje nadřazeného okna aktuální skupiny úlohy.  
  
 [out]`data`  
 Objekt typu `CAccessibilityData` který naplněný daty usnadnění aktuální skupiny úlohy.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud `data` parametr byl úspěšně vyplněná s daty usnadnění aktuální skupiny úlohy, jinak hodnota `FALSE`.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCTasksPane – třída](../../mfc/reference/cmfctaskspane-class.md)   
 [CMFCTasksPaneTask – třída](../../mfc/reference/cmfctaskspanetask-class.md)   
 [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)
