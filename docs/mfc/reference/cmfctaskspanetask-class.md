---
title: Cmfctaskspanetask – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: ee7c04ee4cd581395ff03763c2ebe50b421986d2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711136"
---
# <a name="cmfctaskspanetask-class"></a>Cmfctaskspanetask – třída
`CMFCTasksPaneTask` Třída je pomocná třída, která představuje úkoly pro podokno úloh ovládacího prvku ( [cmfctaskspane –](../../mfc/reference/cmfctaskspane-class.md)). Objekt úlohy představuje položku ve skupině úloh ( [cmfctaskspanetaskgroup –](../../mfc/reference/cmfctaskspanetaskgroup-class.md)). Každý úkol může mít příkaz, který rozhraní provede, když uživatel klepne na úlohu a ikonu, která se zobrazí vlevo od názvu úkolu.  
  
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
|[CMFCTasksPaneTask::SetACCData](#setaccdata)|Určuje usnadnění dat pro aktuální úlohu.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCTasksPaneTask::m_bAutoDestroyWindow](#m_bautodestroywindow)|Určuje, zda je okno úkolů automaticky odstraní.|  
|[CMFCTasksPaneTask::m_bIsBold](#m_bisbold)|Určuje, zda rozhraní nakreslí popisek úlohy tučným písmem.|  
|[CMFCTasksPaneTask::m_dwUserData](#m_dwuserdata)|Obsahuje data uživatelského rozhraní, přidruží k úkolu. Nastavte na hodnotu nula, pokud úloha nemá žádná přidružená data.|  
|[CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)|Popisovač okna úloh.|  
|[CMFCTasksPaneTask::m_nIcon](#m_nicon)|Index v seznamu obrázků obrázku, který se zobrazí vedle úloha rozhraní.|  
|[CMFCTasksPaneTask::m_nWindowHeight](#m_nwindowheight)|Výšku okna úloh. Pokud úloha nemá žádný časový interval pro úkol, tato hodnota je nula.|  
|[CMFCTasksPaneTask::m_pGroup](#m_pgroup)|Ukazatel `CMFCTasksPaneTaskGroup` patřící do této úlohy.|  
|[CMFCTasksPaneTask::m_rect](#m_rect)|Určuje ohraničující obdélník úkolu.|  
|[CMFCTasksPaneTask::m_strName](#m_strname)|Název úlohy|  
|[CMFCTasksPaneTask::m_uiCommandID](#m_uicommandid)|Určuje Identifikátor příkazu příkazu, který rozhraní spustí, když uživatel klikne úkol. Pokud tato hodnota není platný příkaz ID, je považován za jmenovku jednoduchý úkol.|  
  
## <a name="remarks"></a>Poznámky  
 Následující obrázek ukazuje skupiny úloh, která obsahuje tři úkoly:  
  
 ![Skupiny úloh, rozbalení](../../mfc/reference/media/nexttaskgrpexpand.png "nexttaskgrpexpand")  
  
> [!NOTE]
>  Pokud úloha nemá platný příkaz ID, je považován za jednoduché popisek.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cmfctaskspanetask –](../../mfc/reference/cmfctaskspanetask-class.md)  
  
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
 Určuje, [cmfctaskspanetaskgroup –](../../mfc/reference/cmfctaskspanetaskgroup-class.md) , ke které úkol patří.  
  
 *lpszName*  
 Určuje název úkolu.  
  
 *nIcon*  
 Určuje index bitové kopie úkol v seznamu obrázků.  
  
 *uiCommandID*  
 Určuje Identifikátor příkazu příkazu, který se spouští při kliknutí na úlohu.  
  
 *dwUserData*  
 Data definovaná uživatelem.  
  
 *hwndTask*  
 Určuje popisovač okna úloh.  
  
 *bAutoDestroyWindow*  
 Při hodnotě TRUE se okno úloha automaticky zničen.  
  
 *nWindowHeight*  
 Určuje výšku okna úloh.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_bautodestroywindow"></a>  CMFCTasksPaneTask::m_bAutoDestroyWindow  
 Určuje, zda je okno úkolů automaticky odstraní.  
  
```  
BOOL m_bAutoDestroyWindow;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavte na TRUE, pokud chcete určit, že okno úkolů ( [CMFCTasksPaneTask::m_hwndTask](#m_hwndtask)) by měl zničí automaticky; jinak hodnota FALSE.  
  
##  <a name="m_bisbold"></a>  CMFCTasksPaneTask::m_bIsBold  
 Určuje, jestli je popisek úlohy vykresleno tučným písmem.  
  
```  
BOOL m_bIsBold;  
```  
  
### <a name="remarks"></a>Poznámky  
 Nastavte tento člen pro hodnotu PRAVDA, zobrazení tučný text popisku úloh.  
  
##  <a name="m_dwuserdata"></a>  CMFCTasksPaneTask::m_dwUserData  
 Obsahuje uživatelem definované datové části, která je přidružená k úloze. Nastavte na hodnotu nula, pokud žádná data nejsou přidružená k úloze.  
  
```  
DWORD m_dwUserData;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_hwndtask"></a>  CMFCTasksPaneTask::m_hwndTask  
 Popisovač okna úloh.  
  
```  
HWND m_hwndTask;  
```  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li přidat časové období úkolu, zavolejte [CMFCTasksPane::AddWindow](../../mfc/reference/cmfctaskspane-class.md#addwindow).  
  
##  <a name="m_nicon"></a>  CMFCTasksPaneTask::m_nIcon  
 Index pozice v seznamu obrázků, který identifikuje bitovou kopii, která se zobrazí vedle zadanou úlohu.  
  
```  
int m_nIcon;  
```  
  
### <a name="remarks"></a>Poznámky  
 Seznam obrázků nastavuje [CMFCTasksPane::SetIconsList](../../mfc/reference/cmfctaskspane-class.md#seticonslist).  
  
 Nastavte `m_nIcon` na hodnotu -1, pokud chcete zobrazit úkol bez bitovou kopii.  
  
##  <a name="m_nwindowheight"></a>  CMFCTasksPaneTask::m_nWindowHeight  
 Výšku okna úloh. Pokud úloha nemá žádný časový interval pro úkol, tato hodnota je nula.  
  
```  
int m_nWindowHeight;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_pgroup"></a>  CMFCTasksPaneTask::m_pGroup  
 Ukazatel [cmfctaskspanetaskgroup –](../../mfc/reference/cmfctaskspanetaskgroup-class.md) , ke které úkol patří.  
  
```  
CMFCTasksPaneTaskGroup* m_pGroup;  
```  
  
### <a name="remarks"></a>Poznámky  
 Každá úloha musí mít nadřazenou skupinu. Přidejte skupiny do podokna úloh voláním [CMFCTasksPane::AddGroup](../../mfc/reference/cmfctaskspane-class.md#addgroup).  
  
##  <a name="m_rect"></a>  CMFCTasksPaneTask::m_rect  
 Určuje ohraničující obdélník úkolu.  
  
```  
CRect m_rect;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota je vypočítána rozhraní framework při vykreslení úlohy.  
  
##  <a name="m_strname"></a>  CMFCTasksPaneTask::m_strName  
 Název úlohy  
  
```  
CString m_strName;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="m_uicommandid"></a>  CMFCTasksPaneTask::m_uiCommandID  
 Určuje Identifikátor příkazu příkazu, který je spuštěn, když uživatel klikne úkol. Pokud tato hodnota není platný příkaz ID, je považován za jmenovku jednoduchý úkol.  
  
```  
UINT m_uiCommandID;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setaccdata"></a>  CMFCTasksPaneTask::SetACCData  
 Určuje usnadnění dat pro aktuální úlohu.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
*pParent*<br/>
[in] Představuje nadřazené okno aktuálního úkolu.  
  
*data*<br/>
[out] Objekt typu `CAccessibilityData` , který je naplněný daty usnadnění aktuálního úkolu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud *data* parametr byl úspěšně naplněný daty usnadnění aktuálního úkolu; v opačném případě hodnota FALSE.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)
