---
title: Cfilefind – třída
ms.date: 11/04/2016
f1_keywords:
- CFileFind
- AFX/CFileFind
- AFX/CFileFind::CFileFind
- AFX/CFileFind::Close
- AFX/CFileFind::FindFile
- AFX/CFileFind::FindNextFile
- AFX/CFileFind::GetCreationTime
- AFX/CFileFind::GetFileName
- AFX/CFileFind::GetFilePath
- AFX/CFileFind::GetFileTitle
- AFX/CFileFind::GetFileURL
- AFX/CFileFind::GetLastAccessTime
- AFX/CFileFind::GetLastWriteTime
- AFX/CFileFind::GetLength
- AFX/CFileFind::GetRoot
- AFX/CFileFind::IsArchived
- AFX/CFileFind::IsCompressed
- AFX/CFileFind::IsDirectory
- AFX/CFileFind::IsDots
- AFX/CFileFind::IsHidden
- AFX/CFileFind::IsNormal
- AFX/CFileFind::IsReadOnly
- AFX/CFileFind::IsSystem
- AFX/CFileFind::IsTemporary
- AFX/CFileFind::MatchesMask
- AFX/CFileFind::CloseContext
- AFX/CFileFind::m_pTM
helpviewer_keywords:
- CFileFind [MFC], CFileFind
- CFileFind [MFC], Close
- CFileFind [MFC], FindFile
- CFileFind [MFC], FindNextFile
- CFileFind [MFC], GetCreationTime
- CFileFind [MFC], GetFileName
- CFileFind [MFC], GetFilePath
- CFileFind [MFC], GetFileTitle
- CFileFind [MFC], GetFileURL
- CFileFind [MFC], GetLastAccessTime
- CFileFind [MFC], GetLastWriteTime
- CFileFind [MFC], GetLength
- CFileFind [MFC], GetRoot
- CFileFind [MFC], IsArchived
- CFileFind [MFC], IsCompressed
- CFileFind [MFC], IsDirectory
- CFileFind [MFC], IsDots
- CFileFind [MFC], IsHidden
- CFileFind [MFC], IsNormal
- CFileFind [MFC], IsReadOnly
- CFileFind [MFC], IsSystem
- CFileFind [MFC], IsTemporary
- CFileFind [MFC], MatchesMask
- CFileFind [MFC], CloseContext
- CFileFind [MFC], m_pTM
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
ms.openlocfilehash: da08b04b314df4916a290d4929a4cbaac87434d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296628"
---
# <a name="cfilefind-class"></a>Cfilefind – třída

Provede vyhledávání místních souborů a je základní třídou pro [cgopherfilefind –](../../mfc/reference/cgopherfilefind-class.md) a [cftpfilefind –](../../mfc/reference/cftpfilefind-class.md), které provádí hledání internetových souborů.

## <a name="syntax"></a>Syntaxe

```
class CFileFind : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CFileFind::CFileFind](#cfilefind)|Vytvoří `CFileFind` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFileFind::Close](#close)|Uzavře žádost o vyhledávání.|
|[CFileFind::FindFile](#findfile)|Vyhledá v adresáři pro zadaný název souboru.|
|[CFileFind::FindNextFile](#findnextfile)|Pokračuje v hledání souborů z předchozího volání [FindFile](#findfile).|
|[CFileFind::GetCreationTime](#getcreationtime)|Získá čas, kdy byl soubor vytvořen.|
|[CFileFind::GetFileName](#getfilename)|Získá název včetně přípony souboru nalezen|
|[CFileFind::GetFilePath](#getfilepath)|Získá celou cestu k souboru nalezen.|
|[CFileFind::GetFileTitle](#getfiletitle)|Získá název souboru nalezen. Název neobsahuje rozšíření.|
|[CFileFind::GetFileURL](#getfileurl)|Získá adresu URL, včetně cesta k souboru, souboru nalezen.|
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|Získá čas posledního přístupu k souboru.|
|[CFileFind::GetLastWriteTime](#getlastwritetime)|Získá dobu, byl soubor naposledy změnil a uložen.|
|[CFileFind::GetLength](#getlength)|Získá délku nalezený soubor v bajtech.|
|[CFileFind::GetRoot](#getroot)|Získá kořenový adresář souboru nalezen.|
|[CFileFind::IsArchived](#isarchived)|Určuje, pokud je nalezen soubor archivovat.|
|[CFileFind::IsCompressed](#iscompressed)|Určuje, pokud je komprimován nalezený soubor.|
|[CFileFind::IsDirectory](#isdirectory)|Určuje, zda nalezený soubor do adresáře.|
|[CFileFind::IsDots](#isdots)|Určuje, zda název nalezený soubor má název "."nebo"..", což indikuje, že je ve skutečnosti adresář.|
|[CFileFind::IsHidden](#ishidden)|Určuje, zda je skrytý nalezený soubor.|
|[CFileFind::IsNormal](#isnormal)|Určuje, zda je normální nalezený soubor (jinými slovy, nemá žádné atributy).|
|[CFileFind::IsReadOnly](#isreadonly)|Určuje, zda nalezený soubor je jen pro čtení.|
|[CFileFind::IsSystem](#issystem)|Určuje, zda je soubor nalezen systémový soubor.|
|[CFileFind::IsTemporary](#istemporary)|Určuje, zda je dočasný nalezený soubor.|
|[CFileFind::MatchesMask](#matchesmask)|Označuje atributy požadovaného souboru soubor, který má být nalezena.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CFileFind::CloseContext](#closecontext)|Zavře soubor určeného popisovačem aktuální hledání.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CFileFind::m_pTM](#m_ptm)|Ukazatel `CAtlTransactionManager` objektu.|

## <a name="remarks"></a>Poznámky

`CFileFind` zahrnuje členské funkce, které začínají vyhledávání, vyhledání souboru a vrátí název, název nebo cesta k souboru. Pro hledání na Internetu, členské funkce [GetFileURL](#getfileurl) vrátí adresu URL k souboru.

`CFileFind` Základní třída pro dvě další třídy knihovny MFC slouží k vyhledávání určitého serveru typy: `CGopherFileFind` konkrétně spolupracuje serverech gopher, a `CFtpFileFind` funguje konkrétně s FTP servery. Společně tyto tři třídy poskytují bezproblémovou mechanismus pro klienta k vyhledání souborů, bez ohledu na to, protokol serveru, typ souboru nebo umístění, na místním počítači nebo na vzdáleném serveru.

Následující kód projde všechny soubory v aktuálním adresáři, tisk název každého souboru:

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

Pro zjednodušení tento příklad, tento kód používá standardní knihovny C++ `cout` třídy. `cout` Řádku mohou nahradit volání `CListBox::AddString`, například v programu s grafickým uživatelským rozhraním.

Další informace o tom, jak používat `CFileFind` a jiných tříd WinInet, najdete v článku [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="cfilefind"></a>  CFileFind::CFileFind

Tato členská funkce je volána, když `CFileFind` objekt je vytvořen.

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parametry

*pTM*<br/>
Ukazatel na catltransactionmanager – objekt

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetFileName](#getfilename).

##  <a name="close"></a>  CFileFind::Close

Voláním této členské funkce ukončit vyhledávání, resetování kontextu a uvolnit všechny prostředky.

```
void Close();
```

### <a name="remarks"></a>Poznámky

Po volání `Close`, není nutné vytvořit novou `CFileFind` instance před voláním [FindFile](#findfile) zahájíte hledání.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetFileName](#getfilename).

##  <a name="closecontext"></a>  CFileFind::CloseContext

Zavře soubor určeného popisovačem aktuální hledání.

```
virtual void CloseContext();
```

### <a name="remarks"></a>Poznámky

Zavře soubor určený aktuální hodnotou popisovače vyhledávání. Tuto funkci chcete-li změnit výchozí chování přepište.

Je třeba zavolat [FindFile](#findfile) nebo [FindNextFile](#findnextfile) načíst popisovač platný vyhledávací funkce alespoň jednou. `FindFile` a `FindNextFile` funkce popisovač vyhledávání použijte k vyhledání souborů s názvy, které odpovídají zadaným názvem.

##  <a name="findfile"></a>  CFileFind::FindFile

Zavolejte tuto členskou funkci, otevřete hledání souborů.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>Parametry

*pstrName*<br/>
Ukazatel na řetězec obsahující název souboru, který má najít. Pokud předáte hodnotu NULL *pstrName*, `FindFile` nemá zástupný znak (*.\*) vyhledávání.

*dwUnused*<br/>
Vyhrazené aby `FindFile` polymorfní s odvozené třídy. Musí být 0.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="remarks"></a>Poznámky

Po volání `FindFile` zahájíte hledání souborů volání [FindNextFile](#findnextfile) načíst následující soubory. Je nutné volat `FindNextFile` alespoň jednou před voláním některé z následujících atributů členské funkce:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [Isnormal –](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::IsDirectory](#isdirectory).

##  <a name="findnextfile"></a>  CFileFind::FindNextFile

Voláním této členské funkce, chcete-li pokračovat v hledání souborů z předchozího volání [FindFile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud existují další soubory. nula, pokud je nalezen soubor jako poslední v adresáři nebo pokud došlo k chybě. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360). Pokud je nalezen soubor poslední soubor v adresáři nebo neexistuje odpovídající soubory najdete, `GetLastError` funkce vrátí ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Poznámky

Je nutné volat `FindNextFile` alespoň jednou před voláním některé z následujících atributů členské funkce:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [Isnormal –](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

`FindNextFile` zabalí funkci Win32 [FindNextFile](/windows/desktop/api/fileapi/nf-fileapi-findnextfilea).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::IsDirectory](#isdirectory).

##  <a name="getcreationtime"></a>  CFileFind::GetCreationTime

Voláním této členské funkce, chcete-li získat čas vytvoření zadaného souboru.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parametry

*pTimeStamp*<br/>
Ukazatel [hodnota FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) struktury obsahující čas vytvoření souboru.

*refTime*<br/>
Odkaz na [CTime](../../atl-mfc-shared/reference/ctime-class.md) objektu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. 0, pokud není úspěšné. `GetCreationTime` Vrátí hodnotu 0, pouze pokud [FindNextFile](#findnextfile) nikdy byla volána na tomto `CFileFind` objektu.

### <a name="remarks"></a>Poznámky

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetCreationTime`.

> [!NOTE]
>  Ne všechny systémy souborů implementace časové razítko vrácená touto funkcí pomocí stejné sémantiky. Tato funkce může vrátit stejnou hodnotu vrácenou příkazem jiné časové razítko funkce, pokud podkladový systém souborů nebo server nepodporuje atribut doby uchování. Zobrazit [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) strukturu pro informace o formáty času. V některých systémech operace vrácený čas je v čase místní zóny na počítači se, že se soubor nachází. Zobrazit Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) rozhraní API pro další informace.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).

##  <a name="getfilename"></a>  CFileFind::GetFileName

Voláním této členské funkce a získat tak název souboru nalezen.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název souboru nedávno zjištěno.

### <a name="remarks"></a>Poznámky

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním GetFileName.

`GetFileName` je jednou tři `CFileFind` členské funkce, které vracejí nějakou formu názvu souboru. Následující seznam popisuje tři a jak se liší:

- `GetFileName` Vrátí název souboru, včetně přípony. Například volání `GetFileName` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *myfile.txt*.

- [GetFilePath](#getfilepath) vrátí celou cestu k souboru. Například volání `GetFilePath` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí cestu k souboru *c:\myhtml\myfile.txt*.

- [GetFileTitle](#getfiletitle) vrátí název souboru bez přípony souboru. Například volání `GetFileTitle` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *myfile*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

##  <a name="getfilepath"></a>  CFileFind::GetFilePath

Voláním této členské funkce získat úplnou cestu zadaného souboru.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Návratová hodnota

Cesta zadaného souboru.

### <a name="remarks"></a>Poznámky

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetFilePath`.

`GetFilePath` je jednou tři `CFileFind` členské funkce, které vracejí nějakou formu názvu souboru. Následující seznam popisuje tři a jak se liší:

- [GetFileName](#getfilename) vrátí název souboru, včetně přípony. Například volání `GetFileName` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *myfile.txt*.

- `GetFilePath` Vrátí celou cestu k souboru. Například volání `GetFilePath` generovat zprávu uživatele o souboru `c:\myhtml\myfile.txt` vrátí cestu k souboru `c:\myhtml\myfile.txt`.

- [GetFileTitle](#getfiletitle) vrátí název souboru bez přípony souboru. Například volání `GetFileTitle` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *myfile*.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetFileName](#getfilename).

##  <a name="getfiletitle"></a>  CFileFind::GetFileTitle

Voláním této členské funkce se získat název souboru nalezen.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Návratová hodnota

Název souboru.

### <a name="remarks"></a>Poznámky

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetFileTitle`.

`GetFileTitle` je jednou tři `CFileFind` členské funkce, které vracejí nějakou formu názvu souboru. Následující seznam popisuje tři a jak se liší:

- [GetFileName](#getfilename) vrátí název souboru, včetně přípony. Například volání `GetFileName` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *myfile.txt*.

- [GetFilePath](#getfilepath) vrátí celou cestu k souboru. Například volání `GetFilePath` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí cestu k souboru *c:\myhtml\myfile.txt*.

- `GetFileTitle` Vrátí název souboru bez přípony souboru. Například volání `GetFileTitle` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *myfile*.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetFileName](#getfilename).

##  <a name="getfileurl"></a>  CFileFind::GetFileURL

Voláním této členské funkce načíst zadané adresy URL.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Návratová hodnota

Úplnou adresu URL.

### <a name="remarks"></a>Poznámky

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetFileURL`.

`GetFileURL` se podobá na členskou funkci [GetFilePath](#getfilepath), s tím rozdílem, že vrátí adresu URL ve formě `file://path`. Například volání `GetFileURL` získat úplnou adresu URL pro *myfile.txt* vrátí adresu URL `file://c:\myhtml\myfile.txt`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetFileName](#getfilename).

##  <a name="getlastaccesstime"></a>  CFileFind::GetLastAccessTime

Voláním této členské funkce, chcete-li získat čas posledního přístupu k souboru.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Parametry

*refTime*<br/>
Odkaz na [CTime](../../atl-mfc-shared/reference/ctime-class.md) objektu.

*pTimeStamp*<br/>
Ukazatel [hodnota FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) struktury obsahující čas posledního přístupu k souboru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. 0, pokud není úspěšné. `GetLastAccessTime` Vrátí hodnotu 0, pouze pokud [FindNextFile](#findnextfile) nikdy byla volána na tomto `CFileFind` objektu.

### <a name="remarks"></a>Poznámky

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetLastAccessTime`.

> [!NOTE]
>  Ne všechny systémy souborů implementace časové razítko vrácená touto funkcí pomocí stejné sémantiky. Tato funkce může vrátit stejnou hodnotu vrácenou příkazem jiné časové razítko funkce, pokud podkladový systém souborů nebo server nepodporuje atribut doby uchování. Zobrazit [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) strukturu pro informace o formáty času. V některých systémech operace vrácený čas je v čase místní zóny na počítači se, že se soubor nachází. Zobrazit Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) rozhraní API pro další informace.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).

##  <a name="getlastwritetime"></a>  CFileFind::GetLastWriteTime

Voláním této členské funkce zobrazíte čas poslední změny souboru.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parametry

*pTimeStamp*<br/>
Ukazatel [hodnota FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) struktury obsahující času posledního zápisu souboru na.

*refTime*<br/>
Odkaz na [CTime](../../atl-mfc-shared/reference/ctime-class.md) objektu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. 0, pokud není úspěšné. `GetLastWriteTime` Vrátí hodnotu 0, pouze pokud [FindNextFile](#findnextfile) nikdy byla volána na tomto `CFileFind` objektu.

### <a name="remarks"></a>Poznámky

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetLastWriteTime`.

> [!NOTE]
>  Ne všechny systémy souborů implementace časové razítko vrácená touto funkcí pomocí stejné sémantiky. Tato funkce může vrátit stejnou hodnotu vrácenou příkazem jiné časové razítko funkce, pokud podkladový systém souborů nebo server nepodporuje atribut doby uchování. Zobrazit [Win32_Find_Data](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) strukturu pro informace o formáty času. V některých systémech operace vrácený čas je v čase místní zóny na počítači se, že se soubor nachází. Zobrazit Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) rozhraní API pro další informace.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).

##  <a name="getlength"></a>  CFileFind::GetLength

Voláním této členské funkce získání délky nalezený soubor v bajtech.

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka souboru nalezený v bajtech.

### <a name="remarks"></a>Poznámky

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetLength`.

`GetLength` používá strukturu Win32 [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) k získání a návratová hodnota velikosti souboru v bajtech.

> [!NOTE]
>  Od verze MFC 7.0 `GetLength` podporuje 64bitové celočíselné typy. Dříve existující kód vytvořený s touto novější verzí knihovny může vést ke zkrácení upozornění.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

##  <a name="getroot"></a>  CFileFind::GetRoot

Voláním této členské funkce kořenu nalezený soubor.

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>Návratová hodnota

Kořen aktivní vyhledávání.

### <a name="remarks"></a>Poznámky

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetRoot`.

Tato členská funkce vrátí specifikátor jednotky a cestu používat k zahájení hledání. Například volání [FindFile](#findfile) s `*.dat` výsledkem `GetRoot` vrací prázdný řetězec. Předejte cestu, například `c:\windows\system\*.dll`do `FindFile` výsledky `GetRoot` vrácení `c:\windows\system\`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetFileName](#getfilename).

##  <a name="isarchived"></a>  CFileFind::IsArchived

Voláním této členské funkce k určení, pokud je nalezen soubor archivovat.

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Soubor archivu, které chcete zálohovat nebo odebrat pomocí FILE_ATTRIBUTE_ARCHIVE atribut souboru identifikované v označení aplikace [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury.

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsArchived`.

Naleznete v členské funkci [MatchesMask](#matchesmask) úplný seznam atributů souboru.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).

##  <a name="iscompressed"></a>  CFileFind::IsCompressed

Voláním této členské funkce k určení, pokud je komprimován nalezený soubor.

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Komprimovaný soubor je označené FILE_ATTRIBUTE_COMPRESSED, podle atributu souboru [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury. Pro soubor tento atribut označuje, že všechna data v souboru je komprimován. Pro adresář tento atribut označuje, že komprese je výchozí pro nově vytvořené soubory a podadresáře.

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsCompressed`.

Naleznete v členské funkci [MatchesMask](#matchesmask) úplný seznam atributů souboru.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).

##  <a name="isdirectory"></a>  CFileFind::IsDirectory

Voláním této členské funkce k určení, zda je nalezen soubor do adresáře.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Soubor, který je adresář je označené FILE_ATTRIBUTE_DIRECTORY podle atributu souboru [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury.

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsDirectory`.

Naleznete v členské funkci [MatchesMask](#matchesmask) úplný seznam atributů souboru.

### <a name="example"></a>Příklad

Tento program malý recurses každý adresář na jednotce C:\ a vytiskne název adresáře.

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

##  <a name="isdots"></a>  CFileFind::IsDots

Voláním této členské funkce pro testování pro aktuální adresář a nadřazené značky adresáře při procházení souborů.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je nalezen soubor má název "."nebo"..", což znamená, že nalezený soubor je ve skutečnosti adresář. Jinak 0.

### <a name="remarks"></a>Poznámky

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsDots`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::IsDirectory](#isdirectory).

##  <a name="ishidden"></a>  CFileFind::IsHidden

Voláním této členské funkce k určení, pokud je nalezen soubor skrytý.

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Skryté soubory, které jsou označené FILE_ATTRIBUTE_HIDDEN, podle atributu souboru [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury. Skrytý soubor není součástí běžných adresářů.

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsHidden`.

Naleznete v členské funkci [MatchesMask](#matchesmask) úplný seznam atributů souboru.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).

##  <a name="isnormal"></a>  CFileFind::IsNormal

Voláním této členské funkce k určení, zda nalezený soubor je soubor normální.

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Soubory označené FILE_ATTRIBUTE_NORMAL, podle atributu souboru [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury. Normální soubor nemá nastavené žádné jiné atributy. Všechny ostatní atributy souboru přepíše tento atribut.

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsNormal`.

Naleznete v členské funkci [MatchesMask](#matchesmask) úplný seznam atributů souboru.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).

##  <a name="isreadonly"></a>  CFileFind::IsReadOnly

Voláním této členské funkce k určení, zda nalezený soubor je jen pro čtení.

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Soubor určený jen pro čtení je označené FILE_ATTRIBUTE_READONLY, atribut souboru identifikované v [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury. Aplikace může číst takový soubor, ale nemůže zapisovat do něj nebo ho odstranit.

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsReadOnly`.

Naleznete v členské funkci [MatchesMask](#matchesmask) úplný seznam atributů souboru.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).

##  <a name="issystem"></a>  CFileFind::IsSystem

Voláním této členské funkce k určení, zda je soubor nalezen systémový soubor.

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Systém souborů je označené FILE_ATTRIBUTE_SYSTEM, atribut souboru identifikované v [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury. Systém souborů je součástí nebo používá výhradně, operační systém.

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsSystem`.

Naleznete v členské funkci [MatchesMask](#matchesmask) úplný seznam atributů souboru.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).

##  <a name="istemporary"></a>  CFileFind::IsTemporary

Voláním této členské funkce k určení, zda nalezený soubor je dočasný soubor.

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Dočasný soubor je označené FILE_ATTRIBUTE_TEMPORARY, podle atributu souboru [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury. Dočasný soubor se používá jako dočasné úložiště. Aplikace by měla zapisovat do souboru pouze v případě, že je nezbytně nutné. Většina dat souboru zůstane v paměti bez vyprazdňuje na médiu, protože ho budou brzy odstraněny.

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsTemporary`.

Naleznete v členské funkci [MatchesMask](#matchesmask) úplný seznam atributů souboru.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::GetLength](#getlength).

##  <a name="m_ptm"></a>  CFileFind::m_pTM

Ukazatel `CAtlTransactionManager` objektu.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Poznámky

##  <a name="matchesmask"></a>  CFileFind::MatchesMask

Voláním této členské funkce pro testování atributů souboru nalezený soubor.

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>Parametry

*dwMask*<br/>
Určuje jeden nebo více atributů souboru identifikované v [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) strukturu pro nalezený soubor. K vyhledání více atributů, použít bitový operátor OR (&#124;) – operátor. Je přijatelné jakoukoli kombinaci následujících atributů:

- FILE_ATTRIBUTE_ARCHIVE soubor je soubor archivu. K označení souborů pro zálohování nebo odebrání aplikací použijte tento atribut.

- Je komprimován FILE_ATTRIBUTE_COMPRESSED souboru nebo adresáře. Pro soubor to znamená, že všechna data v souboru je komprimován. Pro adresář to znamená, že komprese je výchozí pro nově vytvořené soubory a podadresáře.

- FILE_ATTRIBUTE_DIRECTORY souboru je adresář.

- FILE_ATTRIBUTE_NORMAL soubor nemá nastavené žádné jiné atributy. Tento atribut je platný jenom v případě, že používat samostatně. Všechny ostatní atributy souboru přepíše tento atribut.

- FILE_ATTRIBUTE_HIDDEN souboru je skrytý. Není součástí běžných adresářů.

- FILE_ATTRIBUTE_READONLY soubor je jen pro čtení. Aplikace může číst soubor, ale nelze do ní zapisovat nebo ho odstranit.

- FILE_ATTRIBUTE_SYSTEM soubor je součástí nebo používá výhradně operační systém.

- FILE_ATTRIBUTE_TEMPORARY soubor se používá jako dočasné úložiště. Aplikace by měla zapisovat do souboru pouze v případě, že je nezbytně nutné. Většina dat souboru zůstane v paměti bez vyprazdňuje na médiu, protože ho budou brzy odstraněny.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="remarks"></a>Poznámky

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `MatchesMask`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind – třída](../../mfc/reference/cftpfilefind-class.md)<br/>
[CGopherFileFind – třída](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile – třída](../../mfc/reference/chttpfile-class.md)
