---
title: CMFCShellListCtrl – třída
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
ms.openlocfilehash: d5c987e1d7dbe053a0cff093d1a9113f762cee26
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368783"
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl – třída

Třída `CMFCShellListCtrl` poskytuje funkce řízení seznamu systému Windows a rozšiřuje ji zahrnutím možnost i zobrazit seznam položek prostředí.

## <a name="syntax"></a>Syntaxe

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|Zobrazí seznam položek, které jsou obsaženy v zadaný spár.|
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|Zobrazí seznam položek, které jsou obsaženy ve složce, která je nadřazenou aktuálně zobrazenou složkou.|
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Povolí nebo zakáže místní nabídku.|
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Načte cestu k aktuální složce.|
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Načte název aktuální složky.|
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Vrátí hodnotu PIDL aktuální položky ovládacího prvku seznamu.|
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Vrátí ukazatel na aktuální složku prostředí.|
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Vrátí textovou cestu položky.|
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Vrátí typy položek prostředí, které jsou zobrazeny ovládacím prvkem seznamu.|
|[CMFCShellListCtrl::isdesktop](#isdesktop)|Zkontroluje, zda je aktuálně vybranou složkou složka plochy.|
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|Rozhraní Framework volá tuto metodu při porovnávání dvě položky. (Přepíše [CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|
|[CMFCShellListCtrl::onformatfiledate](#onformatfiledate)|Volána při načtení matného souboru data zobrazeného ovládacím prvkem seznamu.|
|[CMFCShellListCtrl::onformatfilesize](#onformatfilesize)|Nazývá se, když rozhraní převede velikost souboru ovládacího prvku seznamu.|
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|Volána při načtení matné ikony položky ovládacího prvku seznamu.|
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Nazývá se, když rozhraní převede text položky ovládacího prvku seznamu.|
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Volat rámci při nastaví názvy sloupců.|
|[CMFCShellListCtrl::Aktualizovat](#refresh)|Aktualizuje a překreslí ovládací prvek seznamu.|
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Nastaví typ položek zobrazených ovládacím prvkem seznamu.|

## <a name="remarks"></a>Poznámky

Třída `CMFCShellListCtrl` rozšiřuje funkce [třídy CMFCListCtrl tím,](../../mfc/reference/cmfclistctrl-class.md) že umožňuje programu uvádět položky prostředí systému Windows. Formát zobrazení, který se používá, je podobný zobrazení seznamu pro okno Průzkumníka.

Objekt [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) může být `CMFCShellListCtrl` přidružen k objektu a vytvořit tak úplné okno Průzkumníka. Potom výběrem položky `CMFCShellTreeCtrl` v objektu způsobí, že `CMFCShellListCtrl` objekt zobrazí obsah vybrané položky.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCShellListCtrl` třídy a jak zobrazit nadřazenou složku aktuálně zobrazené složky. Tento fragment kódu je součástí [ukázky průzkumníka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

`CMFCShellListCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxshelllistCtrl.h

## <a name="cmfcshelllistctrldisplayfolder"></a><a name="displayfolder"></a>CMFCShellListCtrl::DisplayFolder

Zobrazí seznam položek, které jsou obsaženy v zaané složce.

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
[v] Řetězec, který obsahuje cestu ke složce.

*lpItemInfo*<br/>
[v] Ukazatel na `LPAFX_SHELLITEMINFO` strukturu, která popisuje složku, která se má zobrazit.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; E_FAIL jinak.

## <a name="cmfcshelllistctrldisplayparentfolder"></a><a name="displayparentfolder"></a>CMFCShellListCtrl::DisplayParentFolder

Aktualizuje objekt [CMFCShellListCtrl,](../../mfc/reference/cmfcshelllistctrl-class.md) aby zobrazil nadřazenou složku aktuálně zobrazené složky.

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; E_FAIL jinak.

## <a name="cmfcshelllistctrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellListCtrl::EnableShellContextMenu

Povolí místní nabídku.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] Logická hodnota, která určuje, zda rozhraní umožňuje místní nabídku.

## <a name="cmfcshelllistctrlgetcurrentfolder"></a><a name="getcurrentfolder"></a>CMFCShellListCtrl::GetCurrentFolder

Načte cestu k aktuálně vybrané složce v objektu [CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>Parametry

*strPath*<br/>
[out] Odkaz na parametr řetězce, kde metoda zapíše cestu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; 0 jinak.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdaří, pokud `CMFCShellListCtrl`není v souboru nebyla vybrána žádná složka.

## <a name="cmfcshelllistctrlgetcurrentfoldername"></a><a name="getcurrentfoldername"></a>CMFCShellListCtrl::GetCurrentFolderName

Načte název aktuálně vybrané složky v objektu [CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>Parametry

*strName*<br/>
[out] Odkaz na parametr řetězce, kde metoda zapíše název.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; 0 jinak.

### <a name="remarks"></a>Poznámky

Tato metoda se nezdaří, pokud `CMFCShellListCtrl`není v souboru nebyla vybrána žádná složka.

## <a name="cmfcshelllistctrlgetcurrentitemidlist"></a><a name="getcurrentitemidlist"></a>CMFCShellListCtrl::GetCurrentItemIdList

Vrátí hodnotu PIDL aktuálně vybrané položky.

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>Návratová hodnota

PIDL aktuální položky.

## <a name="cmfcshelllistctrlgetcurrentshellfolder"></a><a name="getcurrentshellfolder"></a>CMFCShellListCtrl::GetCurrentShellFolder

Získá ukazatel na aktuálně vybranou položku v objektu [CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [rozhraní IShellFolder](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder) pro vybraný objekt.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu NULL, pokud není aktuálně vybrán žádný objekt.

## <a name="cmfcshelllistctrlgetitempath"></a><a name="getitempath"></a>CMFCShellListCtrl::GetItemPath

Načte cestu pro položku.

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>Parametry

*strPath*<br/>
[out] Odkaz na řetězec, který přijímá cestu.

*iPoložka*<br/>
[v] Index položky seznamu.

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; FALSE jinak.

### <a name="remarks"></a>Poznámky

Index poskytnutý *iItem* je založen na položkách aktuálně zobrazených objektem [třídy CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

## <a name="cmfcshelllistctrlgetitemtypes"></a><a name="getitemtypes"></a>CMFCShellListCtrl::GetItemTypes

Vrátí typ položek zobrazených objektem [CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota [SHCONTF,](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf) která obsahuje typ položek `CMFCShellListCtrl`uvedených v .

### <a name="remarks"></a>Poznámky

Chcete-li nastavit typ položek `CMFCShellListCtrl`uvedených v a , zavolejte [CMFCShellListCtrl::SetItemTypes](#setitemtypes).

## <a name="cmfcshelllistctrlisdesktop"></a><a name="isdesktop"></a>CMFCShellListCtrl::isdesktop

Určuje, zda je složka zobrazená v objektu [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) složka plochy.

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zobrazená složka složka plochy; FALSE jinak.

## <a name="cmfcshelllistctrloncompareitems"></a><a name="oncompareitems"></a>CMFCShellListCtrl::OnCompareItems

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parametry

[v] *lParam1*<br/>
[v] *lParam2*<br/>
[v] *iColumn*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcshelllistctrlonformatfiledate"></a><a name="onformatfiledate"></a>CMFCShellListCtrl::onformatfiledate

Rozhraní Framework volá tuto metodu, když musí převést datum přidružené k objektu do řetězce.

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>Parametry

*soubor tm*<br/>
[v] Datum přidružené k souboru.

*Str*<br/>
[out] Řetězec, který obsahuje datum formátovaného souboru.

### <a name="remarks"></a>Poznámky

Když objekt [třídy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) zobrazí datum přidružené k souboru, musí toto datum převést na formát řetězce. Používá `CMFCShellListCtrl` tuto metodu k tomu, aby tento převod. Ve výchozím nastavení tato metoda používá aktuální národní prostředí k formátování data do řetězce.

## <a name="cmfcshelllistctrlonformatfilesize"></a><a name="onformatfilesize"></a>CMFCShellListCtrl::onformatfilesize

Framework volá tuto metodu při převedení velikosti objektu na řetězec.

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>Parametry

*lVelikost souboru*<br/>
[v] Velikost souboru, který se zobrazí v rámci.

*Str*<br/>
[out] Řetězec, který obsahuje formátovaný soubor velikost.

### <a name="remarks"></a>Poznámky

Když objekt [třídy CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md) potřebuje zobrazit velikost souboru, musí převést velikost souboru do formátu řetězce. Používá `CMFCShellListCtrl` tuto metodu k tomu, aby tento převod. Ve výchozím nastavení tato metoda převede velikost souboru z bajtů na kilobajty a potom použije aktuální národní prostředí pro formátování velikosti do řetězce.

## <a name="cmfcshelllistctrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShellListCtrl::OnGetItemIcon

Rozhraní Framework volá tuto metodu k načtení ikony přidružené k položce seznamu prostředí.

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

*iPoložka*<br/>
[v] Index položky.

*pPoložka*<br/>
[v] Parametr LPAFX_SHELLITEMINFO, který popisuje položku.

### <a name="return-value"></a>Návratová hodnota

Index obrázku ikony v případě úspěchu; -1, pokud funkce selže.

### <a name="remarks"></a>Poznámky

Index obrázku ikony je založen na seznamu bitových obrázků systému.

Ve výchozím nastavení tato metoda závisí na parametru *pItem.* Hodnota *iItem* se nepoužívá ve výchozí implementaci. Můžete použít *iItem* k implementaci vlastní chování.

## <a name="cmfcshelllistctrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShellListCtrl::OnGetItemText

Rozhraní Framework volá tuto metodu, když musí načíst text položky prostředí.

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

*iPoložka*<br/>
[v] Index položky.

*iColumn*<br/>
[v] Sloupec zájmu.

*pPoložka*<br/>
[v] Parametr LPAFX_SHELLITEMINFO, který popisuje položku.

### <a name="return-value"></a>Návratová hodnota

A, `CString` který obsahuje text přidružený k položce.

### <a name="remarks"></a>Poznámky

Každá položka `CMFCShellListCtrl` v objektu může mít text v jednom nebo více sloupcích. Když framework volá tuto metodu, určuje sloupec, který má zájem. Pokud tuto funkci zavoláte ručně, musíte také zadat sloupec, který vás zajímá.

Ve výchozím nastavení tato metoda závisí na *parametru pItem* k určení, která položka má být zpracována. Hodnota *iItem* se nepoužívá ve výchozí implementaci.

## <a name="cmfcshelllistctrlonsetcolumns"></a><a name="onsetcolumns"></a>CMFCShellListCtrl::OnSetColumns

Rozhraní Framework volá tuto metodu při nastaví názvy sloupců.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení rozhraní vytvoří `CMFCShellListCtrl` čtyři sloupce v objektu. Názvy těchto sloupců jsou **Název**, **Velikost**, **Typ**a **Změněno**. Tuto metodu můžete přepsat a přizpůsobit počet sloupců a jejich názvy.

## <a name="cmfcshelllistctrlrefresh"></a><a name="refresh"></a>CMFCShellListCtrl::Aktualizovat

Aktualizuje a překreslí objekt [CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>Návratová hodnota

`S_OK`v případě úspěchu; jinak chybová hodnota.

### <a name="remarks"></a>Poznámky

Volánítéto metody aktualizovat seznam položek zobrazených `CMFCShellListCtrl` objektem.

## <a name="cmfcshelllistctrlsetitemtypes"></a><a name="setitemtypes"></a>CMFCShellListCtrl::SetItemTypes

Nastaví typ položek, které jsou uvedeny v objektu [CMFCShellListCtrl.](../../mfc/reference/cmfcshelllistctrl-class.md)

```
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>Parametry

*nTypy*<br/>
[v] Seznam typů položek, `CMFCShellListCtrl` které objekt podporuje.

### <a name="remarks"></a>Poznámky

Další informace o seznamu typů položek naleznete v tématu [SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl – třída](../../mfc/reference/cmfclistctrl-class.md)<br/>
[CMFCShellTreeCtrl – třída](../../mfc/reference/cmfcshelltreectrl-class.md)
