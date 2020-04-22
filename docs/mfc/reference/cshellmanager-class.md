---
title: Třída CShellManager
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
ms.openlocfilehash: 1c2f9ac1658f50f0ec5bd9e2f53d270c09bfcb6a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750319"
---
# <a name="cshellmanager-class"></a>Třída CShellManager

Implementuje několik metod, které umožňují pracovat s ukazateli na seznamy identifikátorů (PIDLs).

## <a name="syntax"></a>Syntaxe

```
class CShellManager : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CShellManager::CShellManager](#cshellmanager)|Vytvoří `CShellManager` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CShellManager::Procházetprosložku](#browseforfolder)|Zobrazí dialogové okno, které umožňuje uživateli vybrat složku prostředí.|
|[CShellManager::Zřetězitpoložku](#concatenateitem)|Zřetězí dva PIDL.|
|[CShellManager::CopyItem](#copyitem)|Vytvoří nový PIDL a zkopíruje dodaný PIDL.|
|[CShellManager::Vytvořitpoložku](#createitem)|Vytvoří nový PIDL zadané velikosti.|
|[CShellManager::FreeItem](#freeitem)|Odstraní dodaný PIDL.|
|[CShellManager::GetItemCount](#getitemcount)|Vrátí počet položek v zadaném pidl.|
|[CShellManager::GetItemSize](#getitemsize)|Vrátí velikost dodaného pidl.|
|[CShellManager::GetNextItem](#getnextitem)|Vrátí další položku z pidl.|
|[CShellManager::GetParentItem](#getparentitem)|Načte nadřazenou položku zadané položky.|
|[CShellManager::ItemFromPath](#itemfrompath)|Načte PIDL pro položku identifikovanou zadanou cestou.|

## <a name="remarks"></a>Poznámky

Metody třídy `CShellManager` se zabývají PIDL. PIDL je jedinečný identifikátor objektu prostředí.

Objekt byste neměli vytvářet `CShellManager` ručně. Bude vytvořen automaticky v rámci vaší aplikace. Měli byste však volat [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) během procesu inicializace vaší aplikace. Chcete-li získat ukazatel na správce prostředí pro vaši aplikaci, volejte [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Správce cshellů](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxshellmanager.h

## <a name="cshellmanagerbrowseforfolder"></a><a name="browseforfolder"></a>CShellManager::Procházetprosložku

Zobrazí dialogové okno, které umožňuje uživateli vybrat složku prostředí.

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
[out] Řetězec používaný metodou k uložení cesty k vybrané složce.

*pWndParent*<br/>
[v] Ukazatel na nadřazené okno.

*LplszInitialFolder*<br/>
[v] Řetězec obsahující složku, která je vybrána ve výchozím nastavení při zobrazení dialogového okna.

*lpszNázev*<br/>
[v] Název dialogového okna.

*ulPříznaky*<br/>
[v] Příznaky určující volby pro dialogové okno. Podrobný popis naleznete v [části BROWSEINFO.](/windows/win32/api/shlobj_core/ns-shlobj_core-browseinfow)

*piFolderImage*<br/>
[out] Ukazatel na hodnotu celéčíslo, kde metoda zapíše index obrazu vybrané složky.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud uživatel vybere složku z dialogového okna; jinak 0.

### <a name="remarks"></a>Poznámky

Při volání této metody aplikace vytvoří a zobrazí dialogové okno, které umožňuje uživateli vybrat složku. Metoda zapíše cestu složky do parametru *strOutFolder.*

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak načíst `CShellManager` odkaz na `CWinAppEx::GetShellManager` objekt pomocí metody `BrowseForFolder` a jak použít metodu. Tento fragment kódu je součástí [ukázky průzkumníka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

## <a name="cshellmanagerconcatenateitem"></a><a name="concatenateitem"></a>CShellManager::Zřetězitpoložku

Vytvoří nový seznam obsahující dva pidl.

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>Parametry

*pidl1*<br/>
[v] První položka.

*pidl2*<br/>
[v] Druhá položka.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nový seznam položek, pokud je funkce úspěšná, jinak NULL.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří nový [ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist) dostatečně velký, aby obsahoval *pidl1* a *pidl2*. Potom zkopíruje *pidl1* a *pidl2* do nového seznamu.

## <a name="cshellmanagercopyitem"></a><a name="copyitem"></a>CShellManager::CopyItem

Zkopíruje seznam položek.

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>Parametry

*pidlZdroj*<br/>
[v] Původní seznam položek.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově vytvořený seznam položek, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Nově vytvořený seznam položek má stejnou velikost jako seznam zdrojových položek.

## <a name="cshellmanagercreateitem"></a><a name="createitem"></a>CShellManager::Vytvořitpoložku

Vytvoří nový PIDL.

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>Parametry

*cbVelikost*<br/>
[v] Velikost seznamu položek.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na seznam vytvořených položek, pokud je úspěšný; jinak NULL.

## <a name="cshellmanagercshellmanager"></a><a name="cshellmanager"></a>CShellManager::CShellManager

Vytvoří `CShellManager` objekt.

```
CShellManager();
```

### <a name="remarks"></a>Poznámky

Ve většině případů není třeba vytvořit `CShellManager` přímo. Ve výchozím nastavení rozhraní vytvoří jeden pro vás. Chcete-li získat `CShellManager`ukazatel na , volejte [CWinAppEx::GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager). Pokud vytvoříte `CShellManager` ručně, musíte jej inicializovat metodou [CWinAppEx::InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager).

## <a name="cshellmanagerfreeitem"></a><a name="freeitem"></a>CShellManager::FreeItem

Odstraní seznam položek.

```cpp
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
[v] Seznam položek, který chcete odstranit.

## <a name="cshellmanagergetitemcount"></a><a name="getitemcount"></a>CShellManager::GetItemCount

Vrátí počet položek v seznamu položek.

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
[v] Ukazatel na seznam položek.

### <a name="return-value"></a>Návratová hodnota

Počet položek v seznamu položek.

## <a name="cshellmanagergetitemsize"></a><a name="getitemsize"></a>CShellManager::GetItemSize

Vrátí velikost seznamu položek.

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
[v] Ukazatel na seznam položek.

### <a name="return-value"></a>Návratová hodnota

Velikost seznamu položek.

## <a name="cshellmanagergetnextitem"></a><a name="getnextitem"></a>CShellManager::GetNextItem

Načte další položku z ukazatele do seznamu identifikátorů položky (PIDL).

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parametry

*pidl*<br/>
[v] Seznam položek k iterovat.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další položku v seznamu.

### <a name="remarks"></a>Poznámky

Pokud nejsou žádné další položky v seznamu, tato metoda vrátí NULL.

## <a name="cshellmanagergetparentitem"></a><a name="getparentitem"></a>CShellManager::GetParentItem

Načte nadřazený ukazatel do seznamu identifikátorů položek (PIDL).

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>Parametry

*lpidl*<br/>
[v] PIDL, jehož nadřazený bude načten.

*lpidlParent*<br/>
[out] Odkaz na PIDL, kde metoda bude ukládat výsledek.

### <a name="return-value"></a>Návratová hodnota

Úroveň nadřazené pidl.

### <a name="remarks"></a>Poznámky

Úroveň PIDL je relativní vzhledem k ploše. Desktop PIDL je považován za úroveň 0.

## <a name="cshellmanageritemfrompath"></a><a name="itemfrompath"></a>CShellManager::ItemFromPath

Načte ukazatel do seznamu identifikátorů položky (PIDL) z položky identifikované řetězcovou cestou.

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
[v] Řetězec, který určuje cestu pro položku.

*pidl*<br/>
[out] Odkaz na PIDL. Metoda používá tento PIDL k uložení ukazatele na jeho vrácenou hodnotu.

### <a name="return-value"></a>Návratová hodnota

Vrátí funkce NOERROR, pokud je úspěšná. chybová hodnota definovaná ole.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
