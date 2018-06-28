---
title: Třída CMFCTasksPaneTask | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::CMFCTasksPaneTask
- AFXTASKSPANE/CMFCTasksPaneTask::SetACCData
- AFXTASKSPANE/CMFCTasksPaneTask::m_bAutoDestroyWindow
- AFXTASKSPANE/CMFCTasksPaneTask::m_bIsBold
- AFXTASKSPANE/CMFCTasksPaneTask::m_dwUserData
- AFXTASKSPANE/CMFCTasksPaneTask::m_hwndTask
- AFXTASKSPANE/CMFCTasksPaneTask::m_nIcon
- AFXTASKSPANE/CMFCTasksPaneTask::m_nWindowHeight
- AFXTASKSPANE/CMFCTasksPaneTask::m_pGroup
- AFXTASKSPANE/CMFCTasksPaneTask::m_rect
- AFXTASKSPANE/CMFCTasksPaneTask::m_strName
- AFXTASKSPANE/CMFCTasksPaneTask::m_uiCommandID
dev_langs:
- C++
helpviewer_keywords:
- CMFCTasksPaneTask [MFC], CMFCTasksPaneTask
- CMFCTasksPaneTask [MFC], SetACCData
- CMFCTasksPaneTask [MFC], m_bAutoDestroyWindow
- CMFCTasksPaneTask [MFC], m_bIsBold
- CMFCTasksPaneTask [MFC], m_dwUserData
- CMFCTasksPaneTask [MFC], m_hwndTask
- CMFCTasksPaneTask [MFC], m_nIcon
- CMFCTasksPaneTask [MFC], m_nWindowHeight
- CMFCTasksPaneTask [MFC], m_pGroup
- CMFCTasksPaneTask [MFC], m_rect
- CMFCTasksPaneTask [MFC], m_strName
- CMFCTasksPaneTask [MFC], m_uiCommandID
ms.assetid: c5a7513b-cd8f-4e2e-b16f-650e1fe30954
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c16644a90bb349a78cac43867fdc648e9c01223d
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040698"
---
# <a name="cmfctaskspanetask-class"></a>CMFCTasksPaneTask – třída
`CMFCTasksPaneTask` Třída je pomocná třída, která představuje úlohy pro ovládací prvek podokna úloh ( [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)). Objekt úlohy představuje položku ve skupině úloh ( [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)). Každý úkol může mít příkaz, který rozhraní provede, když uživatel klikne na úlohy a ikonu, která se zobrazí vlevo od název úlohy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCTasksPaneTask : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCTasksPaneTask::CMFCTasksPaneTask](#cmfctaskspanetask)|Vytvoří a inicializuje `CMFCTasksPaneTask` objektu.|  
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCTasksPaneTask::SetACCData](#setaccdata)|Určuje nastavení dat pro usnadnění přístupu pro aktuální úlohu.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCTasksPaneTask::m_bAutoDestroyWindow](#m_bautodestroywindow)|Určuje, zda okno úloha automaticky zničena.|  
|[CMFCTasksPaneTask::m_bIsBold](#m_bisbold)|Určuje, zda rozhraní nevykresluje popisek úlohy tučným písmem.|  
|[CMFCTasksPaneTask::m_dwUserData](#m_dwuserdata)|Obsahuje uživatelská data, která přidruží rozhraní úlohy. Nastavte na nulu, pokud úloha nemá žádné přidružená data.|  
|[CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)|Obslužná rutina v okně úlohy.|  
|[CMFCTasksPaneTask::m_nIcon](#m_nicon)|Index v seznamu obrázků bitové kopie, rozhraní se zobrazí vedle úlohy.|  
|[CMFCTasksPaneTask::m_nWindowHeight](#m_nwindowheight)|Výška okna úloh. Pokud úloha nemá žádný časový interval pro úkol, je tato hodnota nula.|  
|[CMFCTasksPaneTask::m_pGroup](#m_pgroup)|Ukazatel `CMFCTasksPaneTaskGroup` náležející do této úlohy.|  
|[CMFCTasksPaneTask::m_rect](#m_rect)|Určuje ohraničující obdélník úlohu.|  
|[CMFCTasksPaneTask::m_strName](#m_strname)|Název úlohy|  
|[CMFCTasksPaneTask::m_uiCommandID](#m_uicommandid)|Určuje příkaz ID příkazu, který rozhraní provede, když uživatel klikne na úkol. Pokud tato hodnota není platný příkaz ID, úloha je považována za jednoduché štítek.|  
  
## <a name="remarks"></a>Poznámky  
 Následující obrázek znázorňuje skupinu úloh, která obsahuje tři úkoly:  
  
 ![Skupiny úloh, rozšířit](../../mfc/reference/media/nexttaskgrpexpand.png "nexttaskgrpexpand")  
  
> [!NOTE]
>  Pokud úloha nemá platný příkaz ID, se zpracovává jako jednoduchý štítek.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxTasksPane.h  
  
##  <a name="cmfctaskspanetask"></a>  CMFCTasksPaneTask::CMFCTasksPaneTask  
 Vytvoří a inicializuje `CMFCTasksPaneTask` objektu.  
  
```  
CMFCTasksPaneTask(
    CMFCTasksPaneTaskGroup* pGroup,  
    LPCTSTR lpszName,  
    int nIcon,  
    UINT uiCommandID,  
    DWORD dwUserData = 0,  
    HWND hwndTask = NULL,  
    BOOL bAutoDestroyWindow = FALSE,  
    int nWindowHeight = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *pGroup*  
 Určuje, [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) , ke které patří úkol.  
  
 *lpszName*  
 Určuje název úlohy.  
  
 *nIcon*  
 Určuje index image úkolu v seznamu obrázků.  
  
 *uiCommandID*  
 Určuje příkaz ID příkazu, který se spustí, až po kliknutí na úlohu.  
  
 *dwUserData*  
 Uživatelská data.  
  
 *hwndTask*  
 Určuje popisovač okna úloh.  
  
 *bAutoDestroyWindow*  
 Pokud `TRUE`, okno úlohy budou automaticky zničena.  
  
 *nWindowHeight*  
 Určuje výšku okna úloh.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_bautodestroywindow"></a>  CMFCTasksPaneTask::m_bAutoDestroyWindow  
 Určuje, zda okno úloha automaticky zničena.  
  
```  
BOOL m_bAutoDestroyWindow;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavte na `TRUE` určíte, že okna úloh ( [CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)) musí být zničený, automaticky; v opačném `FALSE`.  
  
##  <a name="m_bisbold"></a>  CMFCTasksPaneTask::m_bIsBold  
 Určuje, zda se popisek úlohy vykresluje v tučně.  
  
```  
BOOL m_bIsBold;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen nastavit na `TRUE` zobrazíte tučně pro popisek úlohy.  
  
##  <a name="m_dwuserdata"></a>  CMFCTasksPaneTask::m_dwUserData  
 Obsahuje uživatelská data, která souvisí s úlohu. Nastavte na nulu, pokud je přidružen úlohu žádná data.  
  
```  
DWORD m_dwUserData;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_hwndtask"></a>  CMFCTasksPaneTask::m_hwndTask  
 Obslužná rutina v okně úlohy.  
  
```  
HWND m_hwndTask;  
```  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li přidat úloha okno, volejte [CMFCTasksPane::AddWindow](../../mfc/reference/cmfctaskspane-class.md#addwindow).  
  
##  <a name="m_nicon"></a>  CMFCTasksPaneTask::m_nIcon  
 Index pozice v seznamu obrázků identifikující obrázek, který se zobrazí vedle zadané úloze.  
  
```  
int m_nIcon;  
```  
  
### <a name="remarks"></a>Poznámky  
 Seznam obrázků se nastavuje pomocí [CMFCTasksPane::SetIconsList](../../mfc/reference/cmfctaskspane-class.md#seticonslist).  
  
 Nastavit `m_nIcon` na -1, pokud chcete zobrazit úlohy bez bitovou kopii.  
  
##  <a name="m_nwindowheight"></a>  CMFCTasksPaneTask::m_nWindowHeight  
 Výška okna úloh. Pokud úloha nemá žádný časový interval pro úkol, je tato hodnota nula.  
  
```  
int m_nWindowHeight;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_pgroup"></a>  CMFCTasksPaneTask::m_pGroup  
 Ukazatel [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) , ke které patří tato úloha.  
  
```  
CMFCTasksPaneTaskGroup* m_pGroup;  
```  
  
### <a name="remarks"></a>Poznámky  
 Každý úkol, musí mít nadřazenou skupinu. Přidání skupiny do podokna úloh voláním [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).  
  
##  <a name="m_rect"></a>  CMFCTasksPaneTask::m_rect  
 Určuje ohraničující obdélník úlohu.  
  
```  
CRect m_rect;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota je vypočítána rozhraní při sestavování úlohu.  
  
##  <a name="m_strname"></a>  CMFCTasksPaneTask::m_strName  
 Název úlohy  
  
```  
CString m_strName;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_uicommandid"></a>  CMFCTasksPaneTask::m_uiCommandID  
 Určuje příkaz ID příkazu, který je spuštěn, když uživatel klikne na úkol. Pokud tato hodnota není platný příkaz ID, úloha je považována za jednoduché štítek.  
  
```  
UINT m_uiCommandID;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setaccdata"></a>  CMFCTasksPaneTask::SetACCData  
 Určuje nastavení dat pro usnadnění přístupu pro aktuální úlohu.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pParent*  
 Představuje nadřazeného okna aktuální úlohy.  
  
 [out] *dat*  
 Objekt typu `CAccessibilityData` který naplněný daty usnadnění aktuálního úkolu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud *data* parametr byl úspěšně vyplněná s daty usnadnění aktuálního úkolu, jinak hodnota `FALSE`.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)
