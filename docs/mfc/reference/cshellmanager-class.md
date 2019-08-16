---
title: CShellManager – třída
ms.date: 11/04/2016
f1_keywords:
- CShellManager
- AFXSHELLMANAGER/CShellManager
- AFXSHELLMANAGER/CShellManager::CShellManager
- AFXSHELLMANAGER/CShellManager::BrowseForFolder
- AFXSHELLMANAGER/CShellManager::ConcatenateItem
- AFXSHELLMANAGER/CShellManager::CopyItem
- AFXSHELLMANAGER/CShellManager::CreateItem
- AFXSHELLMANAGER/CShellManager::FreeItem
- AFXSHELLMANAGER/CShellManager::GetItemCount
- AFXSHELLMANAGER/CShellManager::GetItemSize
- AFXSHELLMANAGER/CShellManager::GetNextItem
- AFXSHELLMANAGER/CShellManager::GetParentItem
- AFXSHELLMANAGER/CShellManager::ItemFromPath
helpviewer_keywords:
- CShellManager [MFC], CShellManager
- CShellManager [MFC], BrowseForFolder
- CShellManager [MFC], ConcatenateItem
- CShellManager [MFC], CopyItem
- CShellManager [MFC], CreateItem
- CShellManager [MFC], FreeItem
- CShellManager [MFC], GetItemCount
- CShellManager [MFC], GetItemSize
- CShellManager [MFC], GetNextItem
- CShellManager [MFC], GetParentItem
- CShellManager [MFC], ItemFromPath
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
ms.openlocfilehash: 8151550dafdd1bdf8593d555008af387cf548bc8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502625"
---
# <a name="cshellmanager-class"></a>CShellManager – třída

Implementuje několik metod, které umožňují pracovat s ukazateli na seznamy identifikátorů (PIDLs).

## <a name="syntax"></a>Syntaxe

```
class CShellManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CShellManager::CShellManager](#cshellmanager)|`CShellManager` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CShellManager::BrowseForFolder](#browseforfolder)|Zobrazí dialogové okno, které uživateli umožňuje vybrat složku prostředí.|
|[CShellManager::ConcatenateItem](#concatenateitem)|Zřetězí dva PIDLsy.|
|[CShellManager::CopyItem](#copyitem)|Vytvoří nový PIDL a zkopíruje dodaný PIDL.|
|[CShellManager::CreateItem](#createitem)|Vytvoří nový PIDL zadané velikosti.|
|[CShellManager::FreeItem](#freeitem)|Odstraní zadaný PIDL.|
|[CShellManager::GetItemCount](#getitemcount)|Vrátí počet položek v zadaném PIDL.|
|[CShellManager::GetItemSize](#getitemsize)|Vrátí velikost zadaného PIDL.|
|[CShellManager::GetNextItem](#getnextitem)|Vrátí další položku z PIDL.|
|[CShellManager::GetParentItem](#getparentitem)|Načte nadřazenou položku zadané položky.|
|[CShellManager::ItemFromPath](#itemfrompath)|Načte PIDL pro položku identifikovanou zadanou cestou.|

## <a name="remarks"></a>Poznámky

Metody `CShellManager` třídy se zaměří s PIDLs. PIDL je jedinečný identifikátor objektu Shell.

`CShellManager` Objekt byste neměli vytvářet ručně. Vytvoří se automaticky architekturou vaší aplikace. Během procesu inicializace vaší aplikace byste však měli zavolat metodu [CWinAppEx:: InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) . Chcete-li získat ukazatel na správce prostředí pro vaši aplikaci, zavolejte [CWinAppEx:: GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxshellmanager. h

##  <a name="browseforfolder"></a>CShellManager::BrowseForFolder

Zobrazí dialogové okno, které uživateli umožňuje vybrat složku prostředí.

```
BOOL BrowseForFolder(
    CString& strOutFolder,
    CWnd* pWndParent = NULL,
    LPCTSTR lplszInitialFolder = NULL,
    LPCTSTR lpszTitle = NULL,
    UINT ulFlags = BIF_RETURNONLYFSDIRS,
    LPINT piFolderImage = NULL);
```

### <a name="parameters"></a>Parametry

*strOutFolder*<br/>
mimo Řetězec použitý metodou k uložení cesty vybrané složky.

*pWndParent*<br/>
pro Ukazatel na nadřazené okno.

*lplszInitialFolder*<br/>
pro Řetězec obsahující složku, která je ve výchozím nastavení vybrána při zobrazení dialogového okna.

*lpszTitle*<br/>
pro Název dialogového okna

*ulFlags*<br/>
pro Příznaky určující možnosti dialogového okna. Podrobný popis najdete v tématu [BROWSEINFO](/windows/win32/api/shlobj_core/ns-shlobj_core-browseinfow) .

*piFolderImage*<br/>
mimo Ukazatel na celočíselnou hodnotu, kde Metoda zapisuje index obrázku vybrané složky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud uživatel vybere složku z dialogového okna; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Když zavoláte tuto metodu, aplikace vytvoří a zobrazí dialogové okno, které uživateli umožňuje vybrat složku. Metoda zapíše cestu ke složce do parametru *strOutFolder* .

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak načíst odkaz na `CShellManager` objekt `CWinAppEx::GetShellManager` pomocí metody `BrowseForFolder` a způsobu použití metody. Tento fragment kódu je součástí [ukázky Průzkumníka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

##  <a name="concatenateitem"></a>CShellManager::ConcatenateItem

Vytvoří nový seznam, který obsahuje dvě PIDLs.

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>Parametry

*pidl1*<br/>
pro První položka.

*pidl2*<br/>
pro Druhá položka.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na seznam nové položky, pokud je funkce úspěšná, jinak NULL.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří nový [ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist) , který je dostatečně velký pro zahrnutí *pidl1* a *pidl2*. Pak zkopíruje *pidl1* a *pidl2* do nového seznamu.

##  <a name="copyitem"></a>CShellManager::CopyItem

Zkopíruje seznam položek.

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>Parametry

*pidlSource*<br/>
pro Původní seznam položek.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu ukazatel na nově vytvořený seznam položek; jinak NULL.

### <a name="remarks"></a>Poznámky

Nově vytvořený seznam položek má stejnou velikost jako seznam zdrojových položek.

##  <a name="createitem"></a>CShellManager:: CreateItem –

Vytvoří nový PIDL.

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>Parametry

*cbSize*<br/>
pro Velikost seznamu položek

### <a name="return-value"></a>Návratová hodnota

Ukazatel na seznam vytvořených položek, pokud je úspěšný; jinak NULL.

##  <a name="cshellmanager"></a>CShellManager::CShellManager

`CShellManager` Vytvoří objekt.

```
CShellManager();
```

### <a name="remarks"></a>Poznámky

Ve většině případů nemusíte vytvářet `CShellManager` přímo. Ve výchozím nastavení vytvoří rozhraní jednu za vás. Chcete-li získat ukazatel na `CShellManager`, zavolejte [CWinAppEx:: GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Pokud vytvoříte `CShellManager` ručně, je nutné ji inicializovat pomocí metody [CWinAppEx:: InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).

##  <a name="freeitem"></a>CShellManager::FreeItem

Odstraní seznam položek.

```
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
pro Seznam položek, které se mají odstranit

##  <a name="getitemcount"></a>CShellManager::GetItemCount

Vrátí počet položek v seznamu položek.

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
pro Ukazatel na seznam položek.

### <a name="return-value"></a>Návratová hodnota

Počet položek v seznamu položek.

##  <a name="getitemsize"></a>CShellManager::GetItemSize

Vrátí velikost seznamu položek.

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
pro Ukazatel na seznam položek.

### <a name="return-value"></a>Návratová hodnota

Velikost seznamu položek

##  <a name="getnextitem"></a>CShellManager::GetNextItem

Načte další položku z ukazatele na seznam identifikátorů položek (PIDL).

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
pro Seznam položek, které se mají iterovat

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další položku v seznamu.

### <a name="remarks"></a>Poznámky

Pokud v seznamu nejsou žádné další položky, vrátí tato metoda hodnotu NULL.

##  <a name="getparentitem"></a>CShellManager::GetParentItem

Načte nadřazený prvek ukazatele na seznam identifikátorů položek (PIDL).

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>Parametry

*lpidl*<br/>
pro PIDL, jehož nadřazená položka bude načtena.

*lpidlParent*<br/>
mimo Odkaz na PIDL, kde metoda uloží výsledek.

### <a name="return-value"></a>Návratová hodnota

Úroveň nadřazeného PIDLu

### <a name="remarks"></a>Poznámky

Úroveň PIDL je relativní vzhledem k ploše. Plocha PIDL se považuje za úroveň 0.

##  <a name="itemfrompath"></a>  CShellManager::ItemFromPath

Načte ukazatel na seznam identifikátorů položek (PIDL) z položky identifikované cestou k řetězci.

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
pro Řetězec, který určuje cestu pro položku.

*pidl*<br/>
mimo Odkaz na PIDL. Metoda používá tento PIDL k uložení ukazatele na jeho návratovou hodnotu.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí chybu. Hodnota chyby definovaná v technologii OLE.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
