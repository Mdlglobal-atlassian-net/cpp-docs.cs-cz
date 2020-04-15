---
title: CRecentFileList – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: a2102c6a39c14c548828e57ad1c49de6a5bc03dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370897"
---
# <a name="crecentfilelist-class"></a>CRecentFileList – třída

Podporuje řízení seznamu naposledy použitých souborů (MRU).

## <a name="syntax"></a>Syntaxe

```
class CRecentFileList
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CRecentFileList::CRecentFileList](#crecentfilelist)|Vytvoří `CRecentFileList` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CRecentFileList::Přidat](#add)|Přidá soubor do seznamu souborů MRU.|
|[CRecentFileList::GetDisplayName](#getdisplayname)|Poskytuje zobrazovaný název pro zobrazení nabídky názvu souboru MRU.|
|[CRecentFileList::GetSize](#getsize)|Načte počet souborů v seznamu souborů MRU.|
|[CRecentFileList::ReadList](#readlist)|Přečte seznam souborů MRU z registru nebo . INI.|
|[CRecentFileList::Odebrat](#remove)|Odebere soubor ze seznamu souborů MRU.|
|[CRecentFileList::UpdateMenu](#updatemenu)|Aktualizuje zobrazení nabídky seznamu souborů MRU.|
|[CRecentFileList::WriteList](#writelist)|Zapíše seznam souborů MRU z registru nebo . INI.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CRecentFileList::operátor \[\]](#operator_at)|Vrátí `CString` objekt na dané pozici.|

## <a name="remarks"></a>Poznámky

Soubory mohou být přidány nebo odstraněny ze seznamu souborů MRU, seznam souborů lze číst nebo zapisovat do registru nebo . ini a nabídku zobrazující seznam souborů MRU lze aktualizovat.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CRecentFileList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxadv.h

## <a name="crecentfilelistadd"></a><a name="add"></a>CRecentFileList::Přidat

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
Určuje název cesty, který má být přidán do seznamu.

*lpszAppID*<br/>
Určuje ID modelu uživatele aplikace pro aplikaci.

*pPoložka*<br/>
Určuje ukazatel na položku prostředí, která má být přidána do seznamu.

*pOdkaz*<br/>
Určuje ukazatel na shell odkaz, který má být přidán do seznamu.

*pidl*<br/>
Určuje idlista pro položku prostředí, která by měla být přidána do poslední složky docs.

### <a name="remarks"></a>Poznámky

Název souboru bude přidán do horní části seznamu mru. Pokud název souboru již v seznamu MRU existuje, bude přesunut na začátek.

## <a name="crecentfilelistcrecentfilelist"></a><a name="crecentfilelist"></a>CRecentFileList::CRecentFileList

Vytvoří `CRecentFileList` objekt.

```
CRecentFileList(
    UINT nStart,
    LPCTSTR lpszSection,
    LPCTSTR lpszEntryFormat,
    int nSize,
    int nMaxDispLen = AFX_ABBREV_FILENAME_LEN);
```

### <a name="parameters"></a>Parametry

*nStartovat*<br/>
Posun pro číslování v nabídce zobrazení seznamu souborů MRU (naposledy použité).

*lpszSekce*<br/>
Odkazuje na název části registru nebo aplikace . INI, kde je seznam souborů MRU číst a/nebo zapisovat.

*lpszEntryFormat*<br/>
Odkazuje na formátovací řetězec, který se použije pro názvy položek uložených v registru nebo v aplikaci . INI.

*nVelikost*<br/>
Maximální počet souborů v seznamu souborů MRU.

*nMaxDispLen*<br/>
Maximální délka ve znacích, která je k dispozici pro zobrazení názvu souboru v nabídce v seznamu souborů MRU.

### <a name="remarks"></a>Poznámky

Formátovací řetězec, na který poukazuje *lpszEntryFormat,* by měl obsahovat %d, který bude použit pro nahrazení indexu každé položky MRU. Pokud je `"file%d"` například formátovací řetězec, budou `file0` `file1`položky pojmenovány , a tak dále.

## <a name="crecentfilelistgetdisplayname"></a><a name="getdisplayname"></a>CRecentFileList::GetDisplayName

Získá zobrazovaný název souboru v seznamu souborů MRU pro použití v nabídce zobrazení seznamu MRU.

```
virtual BOOL GetDisplayName(
    CString& strName,
    int nIndex,
    LPCTSTR lpszCurDir,
    int nCurDir,
    BOOL bAtLeastName = TRUE) const;
```

### <a name="parameters"></a>Parametry

*strName*<br/>
Úplná cesta k souboru, jehož název má být zobrazen v seznamu nabídek souborů MRU.

*nIndex*<br/>
Nulový index souboru v seznamu souborů MRU.

*lpszCurDir*<br/>
Řetězec s aktuálním adresářem.

*nCurDir*<br/>
Délka aktuálního řetězce adresáře.

*bAtLeastName*<br/>
Pokud nenulová, označuje, že základní název souboru by měla být vrácena, i v případě, že `CRecentFileList` překročí maximální délku zobrazení (předánjako *nMaxDispLen* parametr konstruktoru).

### <a name="return-value"></a>Návratová hodnota

**FALSE,** pokud není název souboru v zadaném indexu v seznamu naposledy použitých souborů (MRU).

### <a name="remarks"></a>Poznámky

Pokud je soubor v aktuálním adresáři, funkce opustí adresář mimo zobrazení. Pokud je název souboru příliš dlouhý, adresář a přípona jsou odstraněny. Pokud je název souboru stále příliš dlouhý, zobrazovaný název je nastaven na prázdný řetězec, pokud *není název bAtLeastName* nenulový.

## <a name="crecentfilelistgetsize"></a><a name="getsize"></a>CRecentFileList::GetSize

Načte počet souborů v seznamu souborů MRU.

```
int GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet souborů v aktuálním seznamu naposledy použitých souborů (MRU).

## <a name="crecentfilelistoperator--"></a><a name="operator_at"></a>CRecentFileList::operátor [ ]

Operátor přetížený dolní`[]`index ( `CString` ) vrátí jeden zadaný indexem založeným na nule v *nIndex*.

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Nulový index a `CString` v sadě `CString`s.

## <a name="crecentfilelistreadlist"></a><a name="readlist"></a>CRecentFileList::ReadList

Přečte seznam naposledy použitých souborů (MRU) z registru nebo z aplikace . INI.

```
virtual void ReadList();
```

## <a name="crecentfilelistremove"></a><a name="remove"></a>CRecentFileList::Odebrat

Odebere soubor ze seznamu souborů MRU.

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Nulový index souboru, který má být odebrán ze seznamu naposledy použitých souborů (MRU).

## <a name="crecentfilelistupdatemenu"></a><a name="updatemenu"></a>CRecentFileList::UpdateMenu

Aktualizuje zobrazení nabídky seznamu souborů MRU.

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parametry

*pCmdUI*<br/>
Ukazatel na objekt [CCmdUI](../../mfc/reference/ccmdui-class.md) pro naposledy použitou nabídku seznamu souborů (MRU).

## <a name="crecentfilelistwritelist"></a><a name="writelist"></a>CRecentFileList::WriteList

Zapíše seznam naposledy použitých souborů (MRU) do registru nebo do seznamu aplikací . INI.

```
virtual void WriteList();
```

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)
