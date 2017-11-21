---
title: "Třída CRecentFileList | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 449bdf4e56377cd4464f7759f59d0f0b5bf21be8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crecentfilelist-class"></a>CRecentFileList – třída
Podporuje ovládací prvek seznamu naposledy použitých souborů (naposledy použitých).  
  
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
|[CRecentFileList::GetDisplayName](#getdisplayname)|Poskytuje název zobrazení pro zobrazení nabídky naposledy použitých název souboru.|  
|[CRecentFileList::GetSize](#getsize)|Načte počet souborů v seznamu naposledy použitých souborů.|  
|[CRecentFileList::ReadList](#readlist)|Čte seznam naposledy použitých souborů z registru nebo. Soubor INI.|  
|[CRecentFileList::Remove](#remove)|Odebere soubor ze seznamu naposledy použitých souborů.|  
|[CRecentFileList::UpdateMenu](#updatemenu)|Aktualizuje zobrazení nabídky seznam naposledy použitých souborů.|  
|[CRecentFileList::WriteList](#writelist)|Zapíše seznam naposledy použitých souborů z registru nebo. Soubor INI.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[[CRecentFileList::operator]](#operator_at)|Vrátí `CString` objektu na dané pozici.|  
  
## <a name="remarks"></a>Poznámky  
 Soubory můžete přidat do nebo ze seznamu naposledy použitých souborů, seznam souborů může číst nebo zapisovat do registru nebo. Může aktualizovat soubor INI a v nabídce zobrazení seznamu naposledy použitých souborů.  
  
 Další informace o položky nabídky naposledy použitých najdete v tématu  
  
-   Článek znalostní báze Knowledge Base Q243751: postupy: přidání obslužné rutiny příkazů naposledy použitých položek nabídky v aplikace knihovny MFC  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CRecentFileList`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxadv.h  
  
##  <a name="add"></a>CRecentFileList::Add  
 Přidá soubor do seznamu naposledy použitých souborů (naposledy použitých).  
  
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
 `lpszPathName`  
 Určuje název cesty, který se má přidat do seznamu.  
  
 `lpszAppID`  
 Určuje Application User Model ID aplikace.  
  
 `pItem`  
 Určuje ukazatel na položku prostředí mají být přidány do seznamu.  
  
 `pLink`  
 Určuje ukazatel na odkaz prostředí má být přidán do seznamu.  
  
 `pidl`  
 Určuje IDLIST pro položku prostředí, které musí být přidaní do poslední složky Dokumenty.  
  
### <a name="remarks"></a>Poznámky  
 Název souboru se zařadí do horní části seznamu naposledy použitých. Pokud název souboru již existuje v tomto seznamu, bude přesunut do horní části.  
  
##  <a name="crecentfilelist"></a>CRecentFileList::CRecentFileList  
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
 `nStart`  
 Posunutí pro číslování v nabídce zobrazení seznamu (naposledy použité) naposledy použitých souborů.  
  
 `lpszSection`  
 Body k názvu oddílu registru nebo aplikace. Soubor INI, kde je seznam naposledy použitých souborů číst nebo zapisovat.  
  
 `lpszEntryFormat`  
 Odkazuje na řetězec formátu, který má být použit pro názvy položky uložené v registru nebo v aplikaci. Soubor INI.  
  
 `nSize`  
 Maximální počet souborů v seznamu naposledy použitých souborů.  
  
 `nMaxDispLen`  
 Maximální délka ve znacích, k dispozici pro zobrazení nabídky Název souboru v seznamu naposledy použitých souborů.  
  
### <a name="remarks"></a>Poznámky  
 Řetězec formátu na kterou odkazuje `lpszEntryFormat` by měl obsahovat "%d", který se použije pro nahrazení index každé naposledy použitých položky. Například, pokud je řetězec formátu `"file%d"` pak bude mít název položky `file0`, `file1`a tak dále.  
  
##  <a name="getdisplayname"></a>CRecentFileList::GetDisplayName  
 Získá zobrazovaný název souboru v seznamu naposledy použitých souborů pro použití v nabídce zobrazení seznamu naposledy použitých.  
  
```  
virtual BOOL GetDisplayName(
    CString& strName,  
    int nIndex,  
    LPCTSTR lpszCurDir,  
    int nCurDir,  
    BOOL bAtLeastName = TRUE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `strName`  
 Úplná cesta souboru, jehož název je má být zobrazen v nabídce seznam naposledy použitých souborů.  
  
 `nIndex`  
 Index nule souboru v seznamu naposledy použitých souborů.  
  
 *lpszCurDir*  
 Řetězec, který uchovává aktuální adresář.  
  
 *nCurDir*  
 Délka řetězce pro aktuální adresář.  
  
 `bAtLeastName`  
 Pokud nenulové hodnoty, určuje, zda má být vrácen základní název souboru, i v případě, že by byl překročen maximální zobrazení délka (předány jako `nMaxDispLen` parametru `CRecentFileList` konstruktor).  
  
### <a name="return-value"></a>Návratová hodnota  
 **FALSE** Pokud neexistuje žádný název souboru v zadaném indexu v seznamu naposledy použitých souborů (naposledy použitých).  
  
### <a name="remarks"></a>Poznámky  
 Pokud je soubor v aktuálním adresáři, ponechá funkce adresáři mimo zobrazení. Pokud název souboru je příliš dlouhý, se odstraní adresář a rozšíření. Pokud název souboru je stále příliš dlouhý, zobrazovaný název je nastavit na prázdný řetězec, pokud `bAtLeastName` nenulový.  
  
##  <a name="getsize"></a>CRecentFileList::GetSize  
 Načte počet souborů v seznamu naposledy použitých souborů.  
  
```  
int GetSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet souborů v aktuální naposledy použité seznamu souborů (naposledy použitých).  
  
##  <a name="operator_at"></a>[CRecentFileList::operator]  
 Přetížené dolní index ( `[]`) operátor vrátí jeden `CString` určeného index založený na nule v `nIndex`.  
  
```  
CString& operator[ ](int nindex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index počítaný od nuly `CString` v sadě `CString`s.  
  
##  <a name="readlist"></a>CRecentFileList::ReadList  
 Přečte naposledy použité seznam souborů (naposledy použitých) z registru nebo aplikace. Soubor INI.  
  
```  
virtual void ReadList();
```  
  
##  <a name="remove"></a>CRecentFileList::Remove  
 Odebere soubor ze seznamu naposledy použitých souborů.  
  
```  
virtual void Remove(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index nule souboru, který se odeberou ze seznamu naposledy použitých souborů (naposledy použitých).  
  
##  <a name="updatemenu"></a>CRecentFileList::UpdateMenu  
 Aktualizuje zobrazení nabídky seznam naposledy použitých souborů.  
  
```  
virtual void UpdateMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parametry  
 `pCmdUI`  
 Ukazatel [CCmdUI](../../mfc/reference/ccmdui-class.md) objekt pro nabídky seznam naposledy použitých souborů (naposledy použitých).  
  
##  <a name="writelist"></a>CRecentFileList::WriteList  
 Zapíše nejvíc nabízet (naposledy použitých) do registru nebo aplikace. Soubor INI.  
  
```  
virtual void WriteList();
```  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



