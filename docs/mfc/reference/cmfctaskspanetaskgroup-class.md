---
title: Cmfctaskspanetaskgroup – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e2f53aa98d7743ccee804ed7a89df160368c8a23
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849158"
---
# <a name="cmfctaskspanetaskgroup-class"></a>Cmfctaskspanetaskgroup – třída
`CMFCTasksPaneTaskGroup` Třída je pomocná třída, používá [cmfctaskspane –](../../mfc/reference/cmfctaskspane-class.md) ovládacího prvku. Objekty typu `CMFCTasksPaneTaskGroup` představují *skupiny úloh*. Skupina úloh je seznam položek, které zobrazí rozhraní v rámci samostatného pole, které má tlačítko Sbalit. Pole může mít nepovinný titulek (název skupiny). Pokud je skupina sbalena, seznam úkolů není viditelný.  
  
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
|[CMFCTasksPaneTaskGroup::SetACCData](#setaccdata)|Určuje usnadnění dat pro danou skupinu úloh.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::m_bIsBottom](#m_bisbottom)|Určuje, zda skupina úloh je umístěno na dolní podokno úloh ovládacího prvku.|  
|[CMFCTasksPaneTaskGroup::m_bIsCollapsed](#m_biscollapsed)|Určuje, zda je sbalen skupiny úloh.|  
|[CMFCTasksPaneTaskGroup::m_bIsSpecial](#m_bisspecial)|Určuje, zda je skupina úloh *speciální.* Speciální popisky zobrazí rozhraní v různých barev.|  
|[CMFCTasksPaneTaskGroup::m_lstTasks](#m_lsttasks)|Obsahuje vnitřní seznam úkolů.|  
|[CMFCTasksPaneTaskGroup::m_rect](#m_rect)|Určuje titulek skupiny ohraničující obdélník.|  
|[CMFCTasksPaneTaskGroup::m_rectGroup](#m_rectgroup)|Určuje ohraničující obdélník skupiny.|  
|[CMFCTasksPaneTaskGroup::m_strName](#m_strname)|Určuje název skupiny.|  
  
## <a name="remarks"></a>Poznámky  
 Následující obrázek znázorňuje skupinu rozšířené úloh:  
  
 ![Skupiny úloh, rozbalení](../../mfc/reference/media/nexttaskgrpexpand.png "nexttaskgrpexpand")  
  
 Následující obrázek znázorňuje úkolu sbalené skupiny:  
  
 ![Skupina úloh sbalený](../../mfc/reference/media/nexttaskgrpcollapse.png "nexttaskgrpcollapse")  
  
 Následující obrázek znázorňuje skupinu úloh bez titulku:  
  
 ![Skupina úloh bez titulku](../../mfc/reference/media/nexttaskgrpnocapt.png "nexttaskgrpnocapt")  
  
 Následující obrázek znázorňuje dvě skupiny úloh. První skupiny úloh, která je označena jako speciální tak, že nastavíte `m_bIsSpecial` příznak na hodnotu TRUE, zatímco druhý úkol skupiny není speciální. Všimněte si, jak je o něco tmavší než druhé skupině úloh titulek pro první skupina úloh:  
  
 ![Skupina úloh speciální](../../mfc/reference/media/nexttaskgrpspecial.png "nexttaskgrpspecial")  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cmfctaskspanetaskgroup –](../../mfc/reference/cmfctaskspanetaskgroup-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxTasksPane.h  
  
##  <a name="cmfctaskspanetaskgroup"></a>  CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup  
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
 *lpszName*  
 Určuje název skupiny v popiscích skupiny.  
  
 *bIsBottom*  
 Určuje, zda skupina zarovnán do dolní podokno úloh ovládacího prvku.  
  
 *bIsSpecial*  
 Určuje, jestli skupiny je určený jako *speciální* a díky tomu se určuje, zda popisek skupiny je vyplněna jinou barvu.  
  
 *bIsCollapsed*  
 Určuje, zda je skupina sbalena.  
  
 *Fyzická_stránka*  
 Určuje stránku vlastností patřící do této skupiny úloh.  
  
 *hIcon*  
 Určuje ikonu, která se zobrazí v záhlaví skupiny.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_bisbottom"></a>  CMFCTasksPaneTaskGroup::m_bIsBottom  
 Určuje, zda skupina úloh je umístěno na dolní podokno úloh ovládacího prvku.  
  
```  
BOOL m_bIsBottom;  
```  
  
### <a name="remarks"></a>Poznámky  
 Jenom jedna skupina může být zarovnaný na dolní podokno úloh ovládacího prvku. Tato skupina úkolů musí být přidáni jako poslední. Další informace najdete v tématu [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).  
  
##  <a name="m_biscollapsed"></a>  CMFCTasksPaneTaskGroup::m_bIsCollapsed  
 Určuje, zda je sbalen skupiny úloh.  
  
```  
BOOL m_bIsCollapsed;  
```  
  
### <a name="remarks"></a>Poznámky  
 Můžete povolit nebo zakázat možnost sbalit skupiny v podokně úloh voláním [CMFCTasksPane::EnableGroupCollapse](../../mfc/reference/cmfctaskspane-class.md#enablegroupcollapse).  
  
##  <a name="m_bisspecial"></a>  CMFCTasksPaneTaskGroup::m_bIsSpecial  
 Určuje, zda je skupina úloh *speciální* a určuje, zda se mají titulek pro skupinu úloh speciální identifikovat pomocí různých barev.  
  
```  
BOOL m_bIsSpecial;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud vaše aplikace používá vizuální motiv Windows XP a `m_bIsSpecial` má hodnotu FALSE, volání rozhraní framework `DrawThemeBackground` s příznakem EBP_NORMALGROUPBACKGROUND. Pokud `m_bIsSpecial` má hodnotu TRUE, rámec volá `DrawThemeBackground` s příznakem EBP_SPECIALGROUPBACKGROUND.  
  
##  <a name="m_lsttasks"></a>  CMFCTasksPaneTaskGroup::m_lstTasks  
 Obsahuje vnitřní seznam úkolů.  
  
```  
CObList m_lstTasks;  
```  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li vyplnit tento seznam, zavolejte [CMFCTasksPane::AddTask](../../mfc/reference/cmfctaskspane-class.md#addtask).  
  
##  <a name="m_rect"></a>  CMFCTasksPaneTaskGroup::m_rect  
 Určuje titulek skupiny ohraničující obdélník.  
  
```  
CRect m_rect;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota se vypočítá automaticky podle rozhraní.  
  
##  <a name="m_rectgroup"></a>  CMFCTasksPaneTaskGroup::m_rectGroup  
 Určuje ohraničující obdélník skupiny.  
  
```  
CRect m_rectGroup;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota se vypočítá automaticky podle rozhraní.  
  
##  <a name="m_strname"></a>  CMFCTasksPaneTaskGroup::m_strName  
 Určuje název skupiny.  
  
```  
CString m_strName;  
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato hodnota je prázdný, není zobrazen titulek skupiny a skupiny nelze sbalené.  
  
##  <a name="setaccdata"></a>  CMFCTasksPaneTaskGroup::SetACCData  
 Určuje usnadnění dat pro danou skupinu úloh.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pParent*  
 Představuje nadřazené okno aktuální skupiny úlohy.  
  
 [out] *dat*  
 Objekt typu `CAccessibilityData` , který je naplněný daty usnadnění aktuální skupiny úlohy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud *data* parametr byl úspěšně naplněný daty usnadnění aktuální skupiny úlohy; v opačném případě hodnota FALSE.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Cmfctaskspane – třída](../../mfc/reference/cmfctaskspane-class.md)   
 [Cmfctaskspanetask – třída](../../mfc/reference/cmfctaskspanetask-class.md)   
 [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)
