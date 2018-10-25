---
title: Crecentfilelist – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRecentFileList
- AFXADV/CRecentFileList
- AFXADV/CRecentFileList::CRecentFileList
- AFXADV/CRecentFileList::Add
- AFXADV/CRecentFileList::GetDisplayName
- AFXADV/CRecentFileList::GetSize
- AFXADV/CRecentFileList::ReadList
- AFXADV/CRecentFileList::Remove
- AFXADV/CRecentFileList::UpdateMenu
- AFXADV/CRecentFileList::WriteList
dev_langs:
- C++
helpviewer_keywords:
- CRecentFileList [MFC], CRecentFileList
- CRecentFileList [MFC], Add
- CRecentFileList [MFC], GetDisplayName
- CRecentFileList [MFC], GetSize
- CRecentFileList [MFC], ReadList
- CRecentFileList [MFC], Remove
- CRecentFileList [MFC], UpdateMenu
- CRecentFileList [MFC], WriteList
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f8f3d1b4be06caeacc86718eafed432979b0c59
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069422"
---
# <a name="crecentfilelist-class"></a>Crecentfilelist – třída

Podporuje ovládací prvek ze seznamu naposledy použitých souborů (MRU).

## <a name="syntax"></a>Syntaxe

```
class CRecentFileList
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CRecentFileList::CRecentFileList](#crecentfilelist)|Vytvoří `CRecentFileList` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRecentFileList::Add](#add)|Přidá soubor do seznamu naposledy použitých souborů.|
|[CRecentFileList::GetDisplayName](#getdisplayname)|Obsahuje zobrazovaný název nabídky zobrazení souboru seznamu naposledy použitých položek.|
|[CRecentFileList::GetSize](#getsize)|Získá počet souborů v seznamu naposledy použitých souborů.|
|[CRecentFileList::ReadList](#readlist)|Načte seznam naposledy použitých souborů z registru nebo. Soubor INI.|
|[CRecentFileList::Remove](#remove)|Odebere soubor ze seznamu naposledy použitých souborů.|
|[CRecentFileList::UpdateMenu](#updatemenu)|Aktualizace nabídky zobrazení seznamu naposledy použitých souborů.|
|[CRecentFileList::WriteList](#writelist)|Zapíše do seznamu naposledy použitých souborů z registru nebo. Soubor INI.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[[] Č. CRecentFileList::operator](#operator_at)|Vrátí `CString` objektu na dané pozici.|

## <a name="remarks"></a>Poznámky

Soubory můžete přidána nebo odstraněna ze seznamu naposledy použitých souborů, seznam souborů může číst nebo zapsat do registru nebo. Je možné aktualizovat soubor INI a nabídky zobrazení seznamu naposledy použitých souborů.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CRecentFileList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxadv.h

##  <a name="add"></a>  CRecentFileList::Add

Přidá soubor do seznamu naposledy použitých souborů (MRU).

```
virtual void Add(LPCTSTR lpszPathName);

virtual void Add(
    LPCTSTR lpszPathName,
    LPCTSTR lpszAppID);

void Add(
    IShellItem* pItem,
    LPCTSTR lpszAppID);

void Add(
    IShellLink* pLink,
    LPCTSTR lpszAppID);

void Add(
    PIDLIST_ABSOLUTE pidl,
    LPCTSTR lpszAppID);
```

### <a name="parameters"></a>Parametry

*lpszPathName*<br/>
Určuje název cesty, které mají být přidány do seznamu.

*lpszAppID*<br/>
Určuje ID modelu uživatele aplikace pro aplikaci.

*pItem*<br/>
Určuje ukazatel na prostředí položky, které chcete přidat do seznamu.

*pLink*<br/>
Určuje ukazatel na odkaz prostředí má být přidán do seznamu.

*PIDL*<br/>
Určuje IDLIST pro položku prostředí, který by měl být přidán do poslední složku s dokumentací.

### <a name="remarks"></a>Poznámky

Název souboru se přidají do horní části seznamu naposledy použitých. Pokud název souboru do seznamu naposledy použitých již existuje, bude přesunut do horní části.

##  <a name="crecentfilelist"></a>  CRecentFileList::CRecentFileList

Vytvoří `CRecentFileList` objektu.

```
CRecentFileList(
    UINT nStart,
    LPCTSTR lpszSection,
    LPCTSTR lpszEntryFormat,
    int nSize,
    int nMaxDispLen = AFX_ABBREV_FILENAME_LEN);
```

### <a name="parameters"></a>Parametry

*Nzačínat*<br/>
Posun číslování v nabídky zobrazení seznamu souborů (naposledy použité) seznamu naposledy použitých položek.

*lpszSection*<br/>
Odkazuje na název oddílu registru nebo aplikace. Soubor INI, kde je seznamu naposledy použitých souborů číst nebo zapisovat.

*lpszEntryFormat*<br/>
Odkazuje na řetězec formátu, který má být použit pro názvy položky uložené v registru nebo v aplikaci. Soubor INI.

*nSize*<br/>
Maximální počet souborů v seznamu naposledy použitých souborů.

*nMaxDispLen*<br/>
Maximální délka ve znacích, k dispozici pro zobrazení nabídky názvem souboru v seznamu naposledy použitých souborů.

### <a name="remarks"></a>Poznámky

Formátovací řetězec odkazované *lpszEntryFormat* by měl obsahovat "%d", který se použije pro nahraďte indexem položky seznamu naposledy použitých položek. Například, pokud je řetězec formátu `"file%d"` pak bude mít název položky `file0`, `file1`, a tak dále.

##  <a name="getdisplayname"></a>  CRecentFileList::GetDisplayName

Získá zobrazovaný název souboru v seznamu naposledy použitých souborů pro použití v nabídce zobrazení seznamu naposledy použitých položek.

```
virtual BOOL GetDisplayName(
    CString& strName,
    int nIndex,
    LPCTSTR lpszCurDir,
    int nCurDir,
    BOOL bAtLeastName = TRUE) const;
```

### <a name="parameters"></a>Parametry

*%{strName/*<br/>
Úplná cesta souboru, jehož název má být zobrazen v nabídce seznamu naposledy použitých souborů.

*nIndex*<br/>
Index založený na nule souboru v seznamu naposledy použitých souborů.

*lpszCurDir*<br/>
Řetězec uchovávající aktuální adresář.

*nCurDir*<br/>
Délka řetězce pro aktuální adresář.

*bAtLeastName*<br/>
Pokud nenulovou hodnotu, znamená, že má být vrácen základní název souboru, i když se překročí maximální zobrazení délky (předán jako *nMaxDispLen* parametr `CRecentFileList` konstruktoru).

### <a name="return-value"></a>Návratová hodnota

**FALSE** Pokud neexistuje žádný název souboru ve stanoveném indexu v seznamu naposledy použitých souborů (MRU).

### <a name="remarks"></a>Poznámky

Pokud je soubor v aktuálním adresáři, ponechá funkce adresáři mimo zobrazení. Pokud je příliš dlouhý název souboru, adresáře a rozšíření jsou odebrána. Pokud stále je příliš dlouhý název souboru, zobrazovaný název je nastavena na prázdný řetězec, není-li *bAtLeastName* nenulové.

##  <a name="getsize"></a>  CRecentFileList::GetSize

Získá počet souborů v seznamu naposledy použitých souborů.

```
int GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet souborů v aktuálním naposledy použité seznam souborů (MRU).

##  <a name="operator_at"></a>  [] Č. CRecentFileList::operator

Přetížená dolního indexu (`[]`) – operátor vrátí jednu `CString` určený index založený na nule v *nIndex*.

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index založený na nule `CString` sadu `CString`s.

##  <a name="readlist"></a>  CRecentFileList::ReadList

Načte naposledy použité seznam souborů (MRU) z registru nebo aplikace. Soubor INI.

```
virtual void ReadList();
```

##  <a name="remove"></a>  CRecentFileList::Remove

Odebere soubor ze seznamu naposledy použitých souborů.

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index založený na nule soubor, který má být odebrán ze seznamu naposledy použitých souborů (MRU).

##  <a name="updatemenu"></a>  CRecentFileList::UpdateMenu

Aktualizace nabídky zobrazení seznamu naposledy použitých souborů.

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel [ccmdui –](../../mfc/reference/ccmdui-class.md) objektu pro nabídku seznamu naposledy použitých souborů (MRU).

##  <a name="writelist"></a>  CRecentFileList::WriteList

Zapíše poslední použitou seznam souborů (MRU) do registru nebo aplikace. Soubor INI.

```
virtual void WriteList();
```

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)

