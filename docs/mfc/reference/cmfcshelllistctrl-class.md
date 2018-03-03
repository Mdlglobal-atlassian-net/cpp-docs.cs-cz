---
title: "Třída CMFCShellListCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayParentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::EnableShellContextMenu
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolderName
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentItemIdList
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentShellFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemPath
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemTypes
- AFXSHELLLISTCTRL/CMFCShellListCtrl::IsDesktop
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnCompareItems
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileDate
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileSize
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemIcon
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemText
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnSetColumns
- AFXSHELLLISTCTRL/CMFCShellListCtrl::Refresh
- AFXSHELLLISTCTRL/CMFCShellListCtrl::SetItemTypes
dev_langs:
- C++
helpviewer_keywords:
- CMFCShellListCtrl [MFC], DisplayFolder
- CMFCShellListCtrl [MFC], DisplayParentFolder
- CMFCShellListCtrl [MFC], EnableShellContextMenu
- CMFCShellListCtrl [MFC], GetCurrentFolder
- CMFCShellListCtrl [MFC], GetCurrentFolderName
- CMFCShellListCtrl [MFC], GetCurrentItemIdList
- CMFCShellListCtrl [MFC], GetCurrentShellFolder
- CMFCShellListCtrl [MFC], GetItemPath
- CMFCShellListCtrl [MFC], GetItemTypes
- CMFCShellListCtrl [MFC], IsDesktop
- CMFCShellListCtrl [MFC], OnCompareItems
- CMFCShellListCtrl [MFC], OnFormatFileDate
- CMFCShellListCtrl [MFC], OnFormatFileSize
- CMFCShellListCtrl [MFC], OnGetItemIcon
- CMFCShellListCtrl [MFC], OnGetItemText
- CMFCShellListCtrl [MFC], OnSetColumns
- CMFCShellListCtrl [MFC], Refresh
- CMFCShellListCtrl [MFC], SetItemTypes
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d4b5204fe92685431ccdd2c6735553c9b7ce85bd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl – třída
`CMFCShellListCtrl` Třída poskytuje funkce ovládací prvek seznamu Windows a rozbalí zahrnutím možnost zobrazit seznam položek prostředí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCShellListCtrl : public CMFCListCtrl  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|Zobrazí seznam položek, které jsou obsaženy v zadané složce.|  
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|Zobrazí seznam položek, které jsou obsaženy ve složce, která je nadřazeným prvkem aktuálně zobrazené složky.|  
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Povolí nebo zakáže místní nabídky.|  
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Načte cestu aktuální složky.|  
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Načte název aktuální složky.|  
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Vrátí PIDL aktuální položky ovládací prvek seznamu.|  
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Vrací ukazatel na aktuální složku prostředí.|  
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Vrátí textovou cesta položky.|  
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Vrátí typy položek prostředí, které se zobrazují pomocí ovládacího prvku seznam.|  
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|Zkontroluje, jestli aktuálně vybrané složce složce plochy.|  
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|Tato metoda volá framework při porovná dvě položky. (Přepisuje [CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|  
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|Voláno, pokud rozhraní načte datum souboru zobrazí ovládací prvek seznamu.|  
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|Voláno, když velikost souboru ovládacího prvku seznam převede rozhraní.|  
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|Voláno, pokud rozhraní načte ikonu položky ovládací prvek seznamu.|  
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Voláno, pokud rozhraní převede text položky ovládací prvek seznamu.|  
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Voláno rámcem, pokud se nastaví názvy sloupců.|  
|[CMFCShellListCtrl::Refresh](#refresh)|Aktualizuje a překreslí ovládacího prvku seznam.|  
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Nastaví typ zobrazených pomocí ovládacího prvku seznam položek.|  
  
## <a name="remarks"></a>Poznámky  
 `CMFCShellListCtrl` Třídy rozšiřuje funkce [CMFCListCtrl třída](../../mfc/reference/cmfclistctrl-class.md) povolením vašeho programu Windows prostředí položky seznamu. Formát zobrazení, který se používá se jako u zobrazení seznamu pro okno Průzkumníka.  
  
 A [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objekt může být přidružený `CMFCShellListCtrl` objekt k vytvoření dokončení okno Průzkumníka. Potom vyberte položku v `CMFCShellTreeCtrl` způsobí, že `CMFCShellListCtrl` objekt, který chcete zobrazit obsah vybrané položky.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCShellListCtrl` třídy a způsob zobrazení nadřazené složky aktuálně zobrazené složky. Tento fragment kódu je součástí [ukázka Průzkumníka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]  
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListCtrl](../../mfc/reference/clistctrl-class.md)  
  
 [CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)  
  
 `CMFCShellListCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxshelllistCtrl.h  
  
##  <a name="displayfolder"></a>CMFCShellListCtrl::DisplayFolder  
 Zobrazí seznam položek, které jsou obsaženy v zadané složce.  
  
```  
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszPath`  
 Řetězec, který obsahuje cestu ke složce.  
  
 [v]`lpItemInfo`  
 Ukazatel na `LPAFX_SHELLITEMINFO` struktura, která popisuje složku pro zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK`v případě úspěšného; `E_FAIL` jinak.  
  
##  <a name="displayparentfolder"></a>CMFCShellListCtrl::DisplayParentFolder  
 Aktualizace [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objekt, který chcete zobrazit nadřazené složky aktuálně zobrazené složky.  
  
```  
virtual HRESULT DisplayParentFolder();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK`v případě úspěšného; `E_FAIL` jinak.  
  
##  <a name="enableshellcontextmenu"></a>CMFCShellListCtrl::EnableShellContextMenu  
 Umožňuje místní nabídky.  
  
```  
void EnableShellContextMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 Logická hodnota, která určuje, zda rozhraní umožňuje místní nabídky.  
  
##  <a name="getcurrentfolder"></a>CMFCShellListCtrl::GetCurrentFolder  
 Načte cestu v aktuálně vybrané složky [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objektu.  
  
```  
BOOL GetCurrentFolder(CString& strPath) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`strPath`  
 Odkaz na řetězcový parametr, kam metodu zapisuje cestu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda selže, pokud je vybrané v žádné složky `CMFCShellListCtrl`.  
  
##  <a name="getcurrentfoldername"></a>CMFCShellListCtrl::GetCurrentFolderName  
 Načte název složky v aktuálně vybraných [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objektu.  
  
```  
BOOL GetCurrentFolderName(CString& strName) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`strName`  
 Odkaz na metodu, kam zapisuje název parametr řetězce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda selže, pokud je vybrané v žádné složky `CMFCShellListCtrl`.  
  
##  <a name="getcurrentitemidlist"></a>CMFCShellListCtrl::GetCurrentItemIdList  
 Vrátí PIDL aktuálně vybrané položky.  
  
```  
LPITEMIDLIST GetCurrentItemIdList() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 PIDL s aktuální položkou.  
  
##  <a name="getcurrentshellfolder"></a>CMFCShellListCtrl::GetCurrentShellFolder  
 Získá ukazatel na aktuálně vybrané položky [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objektu.  
  
```  
const IShellFolder* GetCurrentShellFolder() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [IShellFolder rozhraní](http://msdn.microsoft.com/library/windows/desktop/bb775075) pro vybraný objekt.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu `NULL` Pokud aktuálně není vybrán žádný objekt.  
  
##  <a name="getitempath"></a>CMFCShellListCtrl::GetItemPath  
 Načte cestu pro položku.  
  
```  
BOOL GetItemPath(
    CString& strPath,  
    int iItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`strPath`  
 Odkaz na řetězec, který obdrží cestu.  
  
 [v]`iItem`  
 Index položky seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`v případě úspěšného; `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Index poskytl `iItem` je založena na položky zobrazené ve [CMFCShellListCtrl třída](../../mfc/reference/cmfcshelllistctrl-class.md) objektu.  
  
##  <a name="getitemtypes"></a>CMFCShellListCtrl::GetItemTypes  
 Vrátí typ položky zobrazené ve [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objektu.  
  
```  
SHCONTF GetItemTypes() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [SHCONTF](http://msdn.microsoft.com/library/windows/desktop/bb762539) hodnotu, která obsahuje typ položky ve `CMFCShellListCtrl`.  
  
### <a name="remarks"></a>Poznámky  
 Nastavte typ položky ve `CMFCShellListCtrl`, volání [CMFCShellListCtrl::SetItemTypes](#setitemtypes).  
  
##  <a name="isdesktop"></a>CMFCShellListCtrl::IsDesktop  
 Určuje, zda složky, která je zobrazena v [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objekt je složce plochy.  
  
```  
BOOL IsDesktop() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud zobrazené složky složce plochy; `FALSE` jinak.  
  
##  <a name="oncompareitems"></a>CMFCShellListCtrl::OnCompareItems  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int OnCompareItems(
    LPARAM lParam1,  
    LPARAM lParam2,  
    int iColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lParam1`  
 [v]`lParam2`  
 [v]`iColumn`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onformatfiledate"></a>CMFCShellListCtrl::OnFormatFileDate  
 Rozhraní framework volá tuto metodu, když je nutné převést data přidružená k objektu na řetězec.  
  
```  
virtual void OnFormatFileDate(
    const CTime& tmFile,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`tmFile`  
 Datum přidružené k souboru.  
  
 [out]`str`  
 Řetězec, který obsahuje datum formátovaného souboru.  
  
### <a name="remarks"></a>Poznámky  
 Když [CMFCShellListCtrl třída](../../mfc/reference/cmfcshelllistctrl-class.md) objekt zobrazí datum přidružené k souboru, datum je nutné převést do řetězce formátu. `CMFCShellListCtrl` Používá tato metoda tento převod. Ve výchozím nastavení tato metoda používá aktuální národní prostředí k formátování data na řetězec.  
  
##  <a name="onformatfilesize"></a>CMFCShellListCtrl::OnFormatFileSize  
 Tato metoda volá framework při převede ji velikost objektu na řetězec.  
  
```  
virtual void OnFormatFileSize(
    long lFileSize,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lFileSize`  
 Velikost souboru, který se zobrazí rozhraní.  
  
 [out]`str`  
 Řetězec, který obsahuje velikost formátovaného souboru.  
  
### <a name="remarks"></a>Poznámky  
 Když [CMFCShellListCtrl třída](../../mfc/reference/cmfcshelllistctrl-class.md) objekt musí zobrazit velikost souboru, je nutné převést do řetězce formátu velikost souboru. `CMFCShellListCtrl` Používá tato metoda tento převod. Ve výchozím nastavení tato metoda převede velikost souboru z bajtů na kilobajtů a pak používá aktuální národní prostředí k formátování velikost do řetězce.  
  
##  <a name="ongetitemicon"></a>CMFCShellListCtrl::OnGetItemIcon  
 Rozhraní framework volá tuto metodu za účelem načtení ikony přidružené k položce seznamu prostředí.  
  
```  
virtual int OnGetItemIcon(
    int iItem,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iItem`  
 Index položky.  
  
 [v]`pItem`  
 A `LPAFX_SHELLITEMINFO` parametr, který popisuje položku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index obrázku ikony v případě úspěšného; -1, pokud funkce se nezdaří.  
  
### <a name="remarks"></a>Poznámky  
 Index bitové kopie ikonu je založen na seznamu obrázků systému.  
  
 Ve výchozím nastavení, tato metoda je založena na `pItem` parametr. Hodnota `iItem` ještě není používáno ve výchozí implementace. Můžete použít `iItem` implementovat vlastní chování.  
  
##  <a name="ongetitemtext"></a>CMFCShellListCtrl::OnGetItemText  
 Tato metoda volá framework při musí získat text položky prostředí.  
  
```  
virtual CString OnGetItemText(
    int iItem,  
    int iColumn,  
    LPAFX_SHELLITEMINFO pItem);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iItem`  
 Index položky.  
  
 [v]`iColumn`  
 Sloupec, které vás zajímají.  
  
 [v]`pItem`  
 A `LPAFX_SHELLITEMINFO` parametr, který popisuje položku.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` obsahující text související s položkou.  
  
### <a name="remarks"></a>Poznámky  
 Jednotlivé položky `CMFCShellListCtrl` objekt může mít text v jedné nebo více sloupců. Když tato metoda volá framework, určuje sloupec, který je zajímá. Pokud volání této funkce ručně, musíte zadat také sloupec, který vás zajímá.  
  
 Ve výchozím nastavení, tato metoda je založena na `pItem` parametr k určení, které položky procesu. Hodnota `iItem` ještě není používáno ve výchozí implementace.  
  
##  <a name="onsetcolumns"></a>CMFCShellListCtrl::OnSetColumns  
 Tato metoda volá framework při nastaví názvy sloupců.  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, rozhraní framework vytvoří čtyři sloupce v `CMFCShellListCtrl` objektu. Názvy těchto sloupců jsou `Name`, `Size`, `Type`, a `Modified`. Můžete přepsat tuto metodu za účelem přizpůsobení počet sloupců a jejich názvy.  
  
##  <a name="refresh"></a>CMFCShellListCtrl::Refresh  
 Aktualizuje a překreslí [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objektu.  
  
```  
virtual HRESULT Refresh();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK`v případě úspěšného; v opačném případě chybovou hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu provést aktualizaci seznamu položek zobrazuje `CMFCShellListCtrl` objektu.  
  
##  <a name="setitemtypes"></a>CMFCShellListCtrl::SetItemTypes  
 Nastaví typ položky, které jsou uvedeny v [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) objektu.  
  
```  
void SetItemTypes(SHCONTF nTypes);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nTypes`  
 Typy seznam položek, které `CMFCShellListCtrl` objektu podporuje.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o seznamu typů položek, které najdete v tématu [SHCONTF](http://msdn.microsoft.com/library/windows/desktop/bb762539).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl – třída](../../mfc/reference/cmfclistctrl-class.md)   
 [CMFCShellTreeCtrl – třída](../../mfc/reference/cmfcshelltreectrl-class.md)
