---
title: CMFCShellListCtrl – Třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 02d4883c6b5445515d891c5e76ccf10b6bb35bba
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504925"
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl – Třída

`CMFCShellListCtrl` Třída poskytuje funkce ovládacího prvku seznam systému Windows a rozšiřuje je zahrnutím možnosti zobrazení seznamu položek prostředí.

## <a name="syntax"></a>Syntaxe

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|Zobrazí seznam položek, které jsou obsaženy v zadané složce.|
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|Zobrazí seznam položek, které jsou obsaženy ve složce, která je nadřazena aktuálně zobrazené složce.|
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Povoluje nebo zakazuje místní nabídku.|
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Načte cestu k aktuální složce.|
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Načte název aktuální složky.|
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Vrátí PIDL aktuální položky ovládacího prvku seznamu.|
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Vrátí ukazatel na aktuální složku prostředí.|
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Vrátí textovou cestu položky.|
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Vrátí typy položek prostředí, které jsou zobrazeny v ovládacím prvku seznam.|
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|Zkontroluje, jestli je aktuálně vybraná složka složkou plocha.|
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|Rozhraní volá tuto metodu, když porovná dvě položky. (Overrides [CMFCListCtrl:: OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|Volá se, když rozhraní načte datum souboru zobrazené ovládacím prvkem seznam.|
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|Volá se, když rozhraní převede velikost souboru ovládacího prvku seznam.|
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|Volá se, když rozhraní načte ikonu položky ovládacího prvku seznamu.|
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Volá se, když rozhraní převede text položky ovládacího prvku seznamu.|
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Volá se rozhraním, když nastavuje názvy sloupců.|
|[CMFCShellListCtrl:: Refresh](#refresh)|Aktualizuje a znovu vykreslí ovládací prvek seznam.|
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Nastaví typ položek zobrazených ovládacím prvkem seznam.|

## <a name="remarks"></a>Poznámky

Třída rozšiřuje funkčnost [třídy CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) tím, že umožňuje programu vypsat položky prostředí systému Windows. `CMFCShellListCtrl` Formát zobrazení, který se používá, je podobný jako v zobrazení seznamu okna Průzkumníka.

Objekt [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) může být přidružen `CMFCShellListCtrl` k objektu pro vytvoření úplného okna Průzkumníka. Poté, co vyberete položku v `CMFCShellTreeCtrl` objektu, způsobí, že `CMFCShellListCtrl` objekt vypíše obsah vybrané položky.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCShellListCtrl` třídy a jak zobrazit nadřazenou složku aktuálně zobrazené složky. Tento fragment kódu je součástí [ukázky Průzkumníka](../../overview/visual-cpp-samples.md).

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

**Header:** afxshelllistCtrl.h

##  <a name="displayfolder"></a>CMFCShellListCtrl::D isplayFolder

Zobrazí seznam položek, které jsou obsaženy v zadané složce.

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
pro Řetězec, který obsahuje cestu ke složce.

*lpItemInfo*<br/>
pro Ukazatel na `LPAFX_SHELLITEMINFO` strukturu, která popisuje složku, která se má zobrazit.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; E_FAIL jinak.

##  <a name="displayparentfolder"></a>  CMFCShellListCtrl::DisplayParentFolder

Aktualizuje objekt [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) tak, aby zobrazoval nadřazenou složku aktuálně zobrazené složky.

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; E_FAIL jinak.

##  <a name="enableshellcontextmenu"></a>CMFCShellListCtrl::EnableShellContextMenu

Povolí místní nabídku.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
pro Logická hodnota, která určuje, zda rozhraní povoluje místní nabídku.

##  <a name="getcurrentfolder"></a>  CMFCShellListCtrl::GetCurrentFolder

Načte cestu aktuálně vybrané složky v objektu [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>Parametry

*strPath*<br/>
mimo Odkaz na parametr řetězce, kde Metoda zapisuje cestu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; 0, jinak.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdařila, pokud v `CMFCShellListCtrl`nástroji není vybrána žádná složka.

##  <a name="getcurrentfoldername"></a>  CMFCShellListCtrl::GetCurrentFolderName

Načte název aktuálně vybrané složky v objektu [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>Parametry

*strName*<br/>
mimo Odkaz na řetězcový parametr, kde Metoda zapisuje název.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; 0, jinak.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdařila, pokud v `CMFCShellListCtrl`nástroji není vybrána žádná složka.

##  <a name="getcurrentitemidlist"></a>CMFCShellListCtrl::GetCurrentItemIdList

Vrátí PIDL aktuálně vybrané položky.

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>Návratová hodnota

PIDL aktuální položky

##  <a name="getcurrentshellfolder"></a>  CMFCShellListCtrl::GetCurrentShellFolder

Získá ukazatel na aktuálně vybranou položku v objektu [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [rozhraní IShellFolder](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder) pro vybraný objekt.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu NULL, pokud není aktuálně vybrán žádný objekt.

##  <a name="getitempath"></a>CMFCShellListCtrl::GetItemPath

Načte cestu pro položku.

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>Parametry

*strPath*<br/>
mimo Odkaz na řetězec, který obdrží cestu.

*iItem*<br/>
pro Index položky seznamu

### <a name="return-value"></a>Návratová hodnota

TRUE v případě úspěchu; V opačném případě NEPRAVDA.

### <a name="remarks"></a>Poznámky

Index dodaný pomocí *iItem* je založen na položkách aktuálně zobrazených objektem [třídy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

##  <a name="getitemtypes"></a>CMFCShellListCtrl:: getitemtypes

Vrátí typ položek zobrazených objektem [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf) , která obsahuje typ položek uvedených v `CMFCShellListCtrl`.

### <a name="remarks"></a>Poznámky

Chcete-li nastavit typ položek `CMFCShellListCtrl`, které jsou uvedeny v, zavolejte [CMFCShellListCtrl:: SetItemTypes](#setitemtypes).

##  <a name="isdesktop"></a>CMFCShellListCtrl:: plochý

Určuje, zda složka zobrazená v objektu [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) je složkou plocha.

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zobrazovaná složka složkou plocha; V opačném případě NEPRAVDA.

##  <a name="oncompareitems"></a>CMFCShellListCtrl::OnCompareItems

Další podrobnosti najdete ve zdrojovém kódu ve složce **VC\\atlmfc\\src\\MFC** v instalaci sady Visual Studio.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parametry

pro *lParam1*<br/>
pro *lParam2*<br/>
pro *iColumn*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="onformatfiledate"></a>  CMFCShellListCtrl::OnFormatFileDate

Rozhraní volá tuto metodu, když musí převést datum přidružené k objektu na řetězec.

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>Parametry

*tmFile*<br/>
pro Datum přidružené k souboru

*str*<br/>
mimo Řetězec, který obsahuje datum formátovaného souboru.

### <a name="remarks"></a>Poznámky

Když objekt [třídy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) zobrazí datum přidružené k souboru, musí toto datum převést na formát řetězce. `CMFCShellListCtrl` Používá tuto metodu k provedení tohoto převodu. Ve výchozím nastavení tato metoda používá aktuální národní prostředí k formátování data na řetězec.

##  <a name="onformatfilesize"></a>CMFCShellListCtrl::OnFormatFileSize

Rozhraní volá tuto metodu, když převede velikost objektu na řetězec.

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>Parametry

*lFileSize*<br/>
pro Velikost souboru, který se zobrazí v rozhraní

*str*<br/>
mimo Řetězec, který obsahuje velikost formátovaného souboru.

### <a name="remarks"></a>Poznámky

Pokud objekt [třídy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) potřebuje zobrazit velikost souboru, je nutné převést velikost souboru na formát řetězce. `CMFCShellListCtrl` Používá tuto metodu k provedení tohoto převodu. Ve výchozím nastavení tato metoda převede velikost souboru z bajtů na kilobajty a pak pomocí aktuálního národního prostředí naformátuje velikost na řetězec.

##  <a name="ongetitemicon"></a>CMFCShellListCtrl::OnGetItemIcon

Rozhraní volá tuto metodu, aby načetla ikonu přidruženou k položce seznamu prostředí.

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

*iItem*<br/>
pro Index položky

*pItem*<br/>
pro Parametr LPAFX_SHELLITEMINFO, který popisuje položku.

### <a name="return-value"></a>Návratová hodnota

Index obrázku ikony v případě úspěchu; -1, pokud se funkce nezdařila.

### <a name="remarks"></a>Poznámky

Index obrázku ikony je založen na seznamu systémových imagí.

Ve výchozím nastavení tato metoda spoléhá na parametr *pItem* . Hodnota *iItem* se ve výchozí implementaci nepoužívá. *IItem* můžete použít k implementaci vlastního chování.

##  <a name="ongetitemtext"></a>  CMFCShellListCtrl::OnGetItemText

Rozhraní volá tuto metodu, když musí načíst text položky prostředí.

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

*iItem*<br/>
pro Index položky

*iColumn*<br/>
pro Sloupec zájmu

*pItem*<br/>
pro Parametr LPAFX_SHELLITEMINFO, který popisuje položku.

### <a name="return-value"></a>Návratová hodnota

`CString` Obsahující text přidružený k položce.

### <a name="remarks"></a>Poznámky

Každá položka v `CMFCShellListCtrl` objektu může mít text v jednom nebo více sloupcích. Když rozhraní volá tuto metodu, určí sloupec, na který má zájem. Pokud tuto funkci zavoláte ručně, musíte zadat také sloupec, který vás zajímá.

Ve výchozím nastavení tato metoda spoléhá na parametr *pItem* , který určuje, která položka má být zpracována. Hodnota *iItem* se ve výchozí implementaci nepoužívá.

##  <a name="onsetcolumns"></a>CMFCShellListCtrl::OnSetColumns

Rozhraní volá tuto metodu, když nastaví názvy sloupců.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení rozhraní vytvoří čtyři sloupce v `CMFCShellListCtrl` objektu. Názvy těchto sloupců jsou **název**, **Velikost**, **typ**a upraveno. Tuto metodu můžete přepsat pro přizpůsobení počtu sloupců a jejich názvů.

##  <a name="refresh"></a>CMFCShellListCtrl:: Refresh

Aktualizuje a znovu vykreslí objekt [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>Návratová hodnota

`S_OK`v případě úspěchu; v opačném případě se jedná o chybovou hodnotu.

### <a name="remarks"></a>Poznámky

Voláním této metody aktualizujete seznam položek zobrazených `CMFCShellListCtrl` objektem.

##  <a name="setitemtypes"></a>CMFCShellListCtrl::SetItemTypes

Nastaví typ položek, které jsou uvedeny v objektu [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>Parametry

*nTypes*<br/>
pro Seznam typů položek, které `CMFCShellListCtrl` objekt podporuje.

### <a name="remarks"></a>Poznámky

Další informace o seznamu typů položek naleznete v tématu [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf).

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl – třída](../../mfc/reference/cmfclistctrl-class.md)<br/>
[CMFCShellTreeCtrl – třída](../../mfc/reference/cmfcshelltreectrl-class.md)
