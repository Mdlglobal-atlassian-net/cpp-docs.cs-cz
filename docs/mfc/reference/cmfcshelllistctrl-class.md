---
title: CMFCShellListCtrl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c2fcd07f831133ff478dcccb4272ef24496e3cac
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066484"
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl – třída

`CMFCShellListCtrl` Třída poskytuje funkce pro řízení seznamu Windows a umožňuje jeho rozšíření tím včetně možnost zobrazit seznam položek prostředí.

## <a name="syntax"></a>Syntaxe

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|Zobrazí seznam položek, které jsou obsaženy v zadané složce.|
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|Zobrazí seznam položek, které jsou obsaženy ve složce, která je nadřazena složce aktuálně zobrazené.|
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|Povoluje nebo zakazuje místní nabídku.|
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|Načte cestu do aktuální složky.|
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|Načte název aktuální složky.|
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|Vrátí PIDL aktuální položku ovládacího prvku seznamu.|
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|Vrací ukazatel na aktuální složku prostředí.|
|[CMFCShellListCtrl::GetItemPath](#getitempath)|Vrátí textovou cesta položky.|
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|Vrátí typy položek prostředí, které jsou zobrazeny v ovládacím prvku seznamu.|
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|Zkontroluje, jestli aktuálně vybrané složky složky desktop.|
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|Rozhraní volá tuto metodu při porovná dvě položky. (Přepíše [CMFCListCtrl::OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|Volá se, když načte soubor datum zobrazeno pomocí ovládacího prvku seznam rozhraní framework.|
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|Volá se, když rozhraní převede velikost ovládacího prvku seznamu.|
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|Volá se, když rozhraní načte ikonu ovládacího prvku položky seznamu.|
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|Volá se, když rozhraní převede text ovládacího prvku položky seznamu.|
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|Volá se rozhraním, když se nastaví názvy sloupců.|
|[CMFCShellListCtrl::Refresh](#refresh)|Aktualizuje a překreslí ovládací prvek seznamu.|
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|Nastaví typ položek zobrazených na ovládací prvek seznamu.|

## <a name="remarks"></a>Poznámky

`CMFCShellListCtrl` Třída rozšiřuje funkce [cmfclistctrl – třída](../../mfc/reference/cmfclistctrl-class.md) tím, že váš program seznam položek prostředí Windows. Formát zobrazení, který se používá je například jako zobrazení seznamu pro okno Průzkumníka.

A [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) objektu lze přidružit `CMFCShellListCtrl` objekt k vytvoření kompletní okno Průzkumníka. Výběrem položky v `CMFCShellTreeCtrl` způsobí, že `CMFCShellListCtrl` objektu, který chcete zobrazovat obsah vybrané položky.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCShellListCtrl` třídy a jak zobrazit nadřazená složka aktuálně zobrazené složky. Tento fragment kódu je součástí [ukázka Průzkumníka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[Cmfclistctrl –](../../mfc/reference/cmfclistctrl-class.md)

`CMFCShellListCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxshelllistCtrl.h

##  <a name="displayfolder"></a>  CMFCShellListCtrl::DisplayFolder

Zobrazí seznam položek, které jsou obsaženy v zadané složce.

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
[in] Řetězec, který obsahuje cestu ke složce.

*lpItemInfo*<br/>
[in] Ukazatel `LPAFX_SHELLITEMINFO` struktura, která popisuje složku k zobrazení.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; Jinak E_FAIL.

##  <a name="displayparentfolder"></a>  CMFCShellListCtrl::DisplayParentFolder

Aktualizace [CMFCShellListCtrl –](../../mfc/reference/cmfcshelllistctrl-class.md) zobrazíte nadřazená složka aktuálně zobrazené složky.

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; Jinak E_FAIL.

##  <a name="enableshellcontextmenu"></a>  CMFCShellListCtrl::EnableShellContextMenu

Umožňuje v místní nabídce.

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[in] Logická hodnota, která určuje, zda rozhraní umožňuje místní nabídce.

##  <a name="getcurrentfolder"></a>  CMFCShellListCtrl::GetCurrentFolder

Načte cestu v aktuálně vybrané složky [CMFCShellListCtrl –](../../mfc/reference/cmfcshelllistctrl-class.md) objektu.

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>Parametry

*strPath*<br/>
[out] Odkaz na parametr řetězce, kde Metoda zapíše cestu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda selže, pokud neexistuje žádná složka ve vybrané `CMFCShellListCtrl`.

##  <a name="getcurrentfoldername"></a>  CMFCShellListCtrl::GetCurrentFolderName

Získá název aktuálně vybranou složku v [CMFCShellListCtrl –](../../mfc/reference/cmfcshelllistctrl-class.md) objektu.

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>Parametry

*%{strName/*<br/>
[out] Odkaz na parametr řetězce, kde Metoda zapíše název.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda selže, pokud neexistuje žádná složka ve vybrané `CMFCShellListCtrl`.

##  <a name="getcurrentitemidlist"></a>  CMFCShellListCtrl::GetCurrentItemIdList

Vrátí PIDL aktuálně vybrané položky.

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>Návratová hodnota

PIDL aktuální položky.

##  <a name="getcurrentshellfolder"></a>  CMFCShellListCtrl::GetCurrentShellFolder

Získá ukazatel na aktuálně vybrané položky v [CMFCShellListCtrl –](../../mfc/reference/cmfcshelllistctrl-class.md) objektu.

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [IShellFolder rozhraní](https://msdn.microsoft.com/library/windows/desktop/bb775075) pro vybraný objekt.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu NULL, pokud aktuálně není vybrán žádný objekt.

##  <a name="getitempath"></a>  CMFCShellListCtrl::GetItemPath

Načte cestu pro položku.

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>Parametry

*strPath*<br/>
[out] Odkaz na řetězec, který přijímá cesty.

*Položky*<br/>
[in] Index položky seznamu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě úspěchu; FALSE v opačném případě.

### <a name="remarks"></a>Poznámky

Index poskytnutých *položky* podle položek aktuálně zobrazený [CMFCShellListCtrl – třída](../../mfc/reference/cmfcshelllistctrl-class.md) objektu.

##  <a name="getitemtypes"></a>  CMFCShellListCtrl::GetItemTypes

Vrátí typ položek zobrazených [CMFCShellListCtrl –](../../mfc/reference/cmfcshelllistctrl-class.md) objektu.

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>Návratová hodnota

A [SHCONTF](/windows/desktop/api/shobjidl_core/ne-shobjidl_core-_shcontf) hodnotu, která obsahuje typ položky uvedené v `CMFCShellListCtrl`.

### <a name="remarks"></a>Poznámky

Chcete-li nastavit typ položky uvedené v `CMFCShellListCtrl`, volání [CMFCShellListCtrl::SetItemTypes](#setitemtypes).

##  <a name="isdesktop"></a>  CMFCShellListCtrl::IsDesktop

Určuje, zda složka, která je zobrazena v [CMFCShellListCtrl –](../../mfc/reference/cmfcshelllistctrl-class.md) objekt je složky desktop.

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je zobrazené složky složce klasické pracovní plochy. FALSE v opačném případě.

##  <a name="oncompareitems"></a>  CMFCShellListCtrl::OnCompareItems

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parametry

[in] *lParam1*<br/>
[in] *lParam2*<br/>
[in] *iColumn*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="onformatfiledate"></a>  CMFCShellListCtrl::OnFormatFileDate

Rozhraní volá tuto metodu, když je nutné převést data přidružená k objektu do řetězce.

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>Parametry

*tmFile*<br/>
[in] Data asociovaná se souborem.

*str*<br/>
[out] Řetězec, který obsahuje datum formátovaného souboru.

### <a name="remarks"></a>Poznámky

Když [CMFCShellListCtrl – třída](../../mfc/reference/cmfcshelllistctrl-class.md) objekt zobrazuje datum, které jsou přidružené k souboru, toto datum je nutné převést na řetězec formátu. `CMFCShellListCtrl` Tato metoda používá k vytvoření tohoto převodu. Ve výchozím nastavení tato metoda používá aktuální národní prostředí k formátování data do řetězce.

##  <a name="onformatfilesize"></a>  CMFCShellListCtrl::OnFormatFileSize

Rozhraní volá tuto metodu při převede velikost objektu na řetězec.

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>Parametry

*lFileSize*<br/>
[in] Velikost souboru, který se zobrazí rozhraní framework.

*str*<br/>
[out] Řetězec, který obsahuje velikost formátovaného souboru.

### <a name="remarks"></a>Poznámky

Když [CMFCShellListCtrl – třída](../../mfc/reference/cmfcshelllistctrl-class.md) objektu potřebuje rychle zobrazit velikost souboru, je potřeba převést velikost souboru do řetězce formátu. `CMFCShellListCtrl` Tato metoda používá k vytvoření tohoto převodu. Ve výchozím nastavení tato metoda převede velikost souboru z bajtů na kB a pak používá aktuální národní prostředí k formátování velikost do řetězce.

##  <a name="ongetitemicon"></a>  CMFCShellListCtrl::OnGetItemIcon

Rozhraní volá tuto metodu za účelem načtení ikony přidružené k položce seznamu prostředí.

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

*Položky*<br/>
[in] Index položky.

*pItem*<br/>
[in] LPAFX_SHELLITEMINFO parametr, který popisuje položku.

### <a name="return-value"></a>Návratová hodnota

Index obrázku ikony v případě úspěchu; -1, pokud funkce selže.

### <a name="remarks"></a>Poznámky

Index bitové kopie ikonu podle seznamu obrázků systému.

Ve výchozím nastavení, tato metoda se může spolehnout *pItem* parametru. Hodnota *položky* nepoužívá ve výchozí implementaci. Můžete použít *položky* implementovat vlastní chování.

##  <a name="ongetitemtext"></a>  CMFCShellListCtrl::OnGetItemText

Rozhraní volá tuto metodu, když ho musíte načíst text položky prostředí.

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Parametry

*Položky*<br/>
[in] Index položky.

*iColumn*<br/>
[in] Sloupec, které vás zajímají.

*pItem*<br/>
[in] LPAFX_SHELLITEMINFO parametr, který popisuje položku.

### <a name="return-value"></a>Návratová hodnota

A `CString` , který obsahuje text přidružený k položce.

### <a name="remarks"></a>Poznámky

Každá položka v `CMFCShellListCtrl` objekt může mít text v jedné nebo více sloupců. Když tato metoda volá framework, určuje sloupec, který ho zajímají. Pokud ručně voláním této funkce musíte zadat také sloupec, který vás zajímá.

Ve výchozím nastavení, tato metoda se může spolehnout *pItem* parametr k určení, která položku do procesu. Hodnota *položky* nepoužívá ve výchozí implementaci.

##  <a name="onsetcolumns"></a>  CMFCShellListCtrl::OnSetColumns

Rozhraní volá tuto metodu při nastaví názvy sloupců.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení, rozhraní vytvoří čtyři sloupce `CMFCShellListCtrl` objektu. Názvy těchto sloupců se **název**, **velikost**, **typ**, a **změněné**. Můžete přepsat tuto metodu za účelem přizpůsobení počet sloupců a jejich názvy.

##  <a name="refresh"></a>  CMFCShellListCtrl::Refresh

Aktualizuje a překreslí [CMFCShellListCtrl –](../../mfc/reference/cmfcshelllistctrl-class.md) objektu.

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>Návratová hodnota

`S_OK` v případě úspěchu; v opačném případě je hodnota chyba.

### <a name="remarks"></a>Poznámky

Voláním této metody můžete aktualizovat seznam položek zobrazených `CMFCShellListCtrl` objektu.

##  <a name="setitemtypes"></a>  CMFCShellListCtrl::SetItemTypes

Nastaví typ položky, které jsou uvedeny v [CMFCShellListCtrl –](../../mfc/reference/cmfcshelllistctrl-class.md) objektu.

```
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>Parametry

*nTypes*<br/>
[in] Seznam položek typy, které `CMFCShellListCtrl` podporuje.

### <a name="remarks"></a>Poznámky

Další informace o seznamu typů položek najdete v tématu [SHCONTF](/windows/desktop/api/shobjidl_core/ne-shobjidl_core-_shcontf).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl – třída](../../mfc/reference/cmfclistctrl-class.md)<br/>
[CMFCShellTreeCtrl – třída](../../mfc/reference/cmfcshelltreectrl-class.md)
