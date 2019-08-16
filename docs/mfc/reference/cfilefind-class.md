---
title: CFileFind – třída
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
ms.openlocfilehash: 2ec8c50a317a09e97a212e8cd7b9be1b58272af9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506575"
---
# <a name="cfilefind-class"></a>CFileFind – třída

Provede vyhledávání místních souborů a je základní třídou pro [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) a [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md), které provádí hledání internetových souborů.

## <a name="syntax"></a>Syntaxe

```
class CFileFind : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CFileFind::CFileFind](#cfilefind)|`CFileFind` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CFileFind:: Close](#close)|Zavře požadavek hledání.|
|[CFileFind:: FindFile –](#findfile)|Vyhledá v adresáři zadaný název souboru.|
|[CFileFind::FindNextFile](#findnextfile)|Pokračuje v hledání souborů od předchozího volání [FindFile –](#findfile).|
|[CFileFind::GetCreationTime](#getcreationtime)|Získá čas vytvoření souboru.|
|[CFileFind:: getsoubor](#getfilename)|Získá název, včetně rozšíření nalezeného souboru.|
|[CFileFind:: GetFilePath](#getfilepath)|Načte celou cestu k nalezenému souboru.|
|[CFileFind::GetFileTitle](#getfiletitle)|Získá název nalezeného souboru. Název nezahrnuje příponu.|
|[CFileFind::GetFileURL](#getfileurl)|Získá adresu URL, včetně cesty k souboru nalezeného souboru.|
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|Získá čas posledního otevření souboru.|
|[CFileFind::GetLastWriteTime](#getlastwritetime)|Získá čas poslední změny a uložení souboru.|
|[CFileFind:: GetLength](#getlength)|Získá délku nalezeného souboru v bajtech.|
|[CFileFind:: GetRoot](#getroot)|Načte kořenový adresář nalezeného souboru.|
|[CFileFind:: archivu](#isarchived)|Určuje, zda byl nalezen soubor archivován.|
|[CFileFind:: dekomprimovaná](#iscompressed)|Určuje, zda je nalezen soubor komprimovaný.|
|[CFileFind::-adresář](#isdirectory)|Určuje, zda je nalezený soubor adresářem.|
|[CFileFind::-tečky](#isdots)|Určuje, zda název nalezeného souboru obsahuje název "." nebo "..", což značí, že je ve skutečnosti adresář.|
|[CFileFind:: Hidden](#ishidden)|Určuje, zda je nalezený soubor skrytý.|
|[CFileFind:: Normal – Normální](#isnormal)|Určuje, zda je nalezený soubor normální (jinými slovy, nemá žádné další atributy).|
|[CFileFind::IsReadOnly](#isreadonly)|Určuje, zda je nalezený soubor určen jen pro čtení.|
|[CFileFind:: FileSystem](#issystem)|Určuje, zda je nalezený soubor systémovým souborem.|
|[CFileFind::-dočasná](#istemporary)|Určuje, zda je nalezený soubor dočasný.|
|[CFileFind::MatchesMask](#matchesmask)|Určuje požadované atributy souboru souboru, který se má najít.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CFileFind::CloseContext](#closecontext)|Zavře soubor určený aktuálním popisovačem hledání.|

### <a name="protected-data-members"></a>Chránění členové dat

|Name|Popis|
|----------|-----------------|
|[CFileFind::m_pTM](#m_ptm)|Ukazatel na `CAtlTransactionManager` objekt.|

## <a name="remarks"></a>Poznámky

`CFileFind`zahrnuje členské funkce, které začínají hledání, vyhledají soubor a vrátí název, název nebo cestu k souboru. V případě hledání v Internetu vrátí [GetFileURL](#getfileurl) členské funkce adresu URL souboru.

`CFileFind`je základní třídou pro dvě další třídy knihovny MFC, které jsou navržené tak, `CGopherFileFind` aby prohledaly konkrétní typy serverů `CFtpFileFind` : pracují konkrétně se servery gopher a pracují výhradně se servery FTP. Tyto tři třídy společně poskytují bezproblémové mechanismy, jak klientovi najít soubory bez ohledu na serverový protokol, typ souboru nebo umístění na místním počítači nebo na vzdáleném serveru.

Následující kód vytvoří výčet všech souborů v aktuálním adresáři a vytiskne název každého souboru:

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

Aby byl příklad jednoduchý, používá tento kód C++ standardní knihovnu `cout` třídy. Řádek může být nahrazen `CListBox::AddString`voláním, například v programu s grafickým uživatelským rozhraním. `cout`

Další informace o tom, jak používat `CFileFind` a jiné třídy WinInet, najdete v článku [internetové programování s](../../mfc/win32-internet-extensions-wininet.md)rozhraním Wininet.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="cfilefind"></a>CFileFind::CFileFind

Tato členská funkce je volána, `CFileFind` když je objekt vytvořen.

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parametry

*pTM*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: getsouboru](#getfilename).

##  <a name="close"></a>CFileFind:: Close

Voláním této členské funkce ukončíte hledání, resetujete kontext a uvolníte všechny prostředky.

```
void Close();
```

### <a name="remarks"></a>Poznámky

Po volání `Close`není nutné před voláním metody [FindFile –](#findfile) vytvořit `CFileFind` novou instanci a zahájit nové hledání.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: getsouboru](#getfilename).

##  <a name="closecontext"></a>CFileFind::CloseContext

Zavře soubor určený aktuálním popisovačem hledání.

```
virtual void CloseContext();
```

### <a name="remarks"></a>Poznámky

Zavře soubor určený aktuální hodnotou popisovače hledání. Přepsáním této funkce změníte výchozí chování.

Chcete-li načíst platný popisovač hledání, je nutné volat funkce [FindFile –](#findfile) nebo [FindNextFile](#findnextfile) alespoň jednou. Funkce `FindFile` a`FindNextFile` používají popisovač hledání k vyhledání souborů s názvy, které odpovídají danému názvu.

##  <a name="findfile"></a>CFileFind:: FindFile –

Chcete-li otevřít hledání souborů, zavolejte tuto členskou funkci.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>Parametry

*pstrName*<br/>
Ukazatel na řetězec obsahující název souboru, který se má najít. Pokud předáte hodnotu nullpro pstrName `FindFile` , provede se zástupné\*vyhledávání (*.).

*dwUnused*<br/>
Vyhrazeno pro `FindFile` vytvoření polymorfního s odvozenými třídami. Musí mít hodnotu 0.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Poznámky

Po volání `FindFile` k zahájení hledání souborů zavolejte [FindNextFile](#findnextfile) pro načtení následných souborů. Před voláním `FindNextFile` kterékoli z následujících členských funkcí atributu je nutné zavolat alespoň jednou:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength –](#getlength)

- [GetRoot selhalo](#getroot)

- [Archivované](#isarchived)

- [IsCompressed](#iscompressed)

- [Adresář](#isdirectory)

- [V bodech](#isdots)

- [IsHidden](#ishidden)

- [Isnormal –](#isnormal)

- [IsReadOnly](#isreadonly)

- [Zadaným atributem IsSystem](#issystem)

- [Velmi dočasné](#istemporary)

- [MatchesMask](#matchesmask)

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::](#isdirectory).

##  <a name="findnextfile"></a>CFileFind::FindNextFile

Volejte tuto členskou funkci, aby pokračovala v hledání souboru z předchozího volání [FindFile –](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud existuje více souborů; nula, pokud se soubor našel jako poslední v adresáři, nebo pokud došlo k chybě Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Pokud je nalezen poslední soubor v adresáři, nebo pokud nelze nalézt žádné vyhovující soubory, `GetLastError` vrátí funkce ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Poznámky

Před voláním `FindNextFile` kterékoli z následujících členských funkcí atributu je nutné zavolat alespoň jednou:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength –](#getlength)

- [GetRoot selhalo](#getroot)

- [Archivované](#isarchived)

- [IsCompressed](#iscompressed)

- [Adresář](#isdirectory)

- [V bodech](#isdots)

- [IsHidden](#ishidden)

- [Isnormal –](#isnormal)

- [IsReadOnly](#isreadonly)

- [Zadaným atributem IsSystem](#issystem)

- [Velmi dočasné](#istemporary)

- [MatchesMask](#matchesmask)

`FindNextFile`zabalí funkci Win32 [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::](#isdirectory).

##  <a name="getcreationtime"></a>CFileFind::GetCreationTime

Chcete-li získat čas vytvoření zadaného souboru, zavolejte tuto členskou funkci.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parametry

*pTimeStamp*<br/>
Ukazatel na strukturu [času](/windows/win32/api/minwinbase/ns-minwinbase-filetime) souboru obsahující čas, kdy byl soubor vytvořen.

*refTime*<br/>
Odkaz na objekt [CTime –](../../atl-mfc-shared/reference/ctime-class.md) .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; 0, pokud neproběhla úspěšně. `GetCreationTime`Vrátí hodnotu 0 pouze v případě, že [FindNextFile](#findnextfile) nebyl nikdy `CFileFind` volán u tohoto objektu.

### <a name="remarks"></a>Poznámky

Před voláním [](#findnextfile) `GetCreationTime`je nutné volat FindNextFile alespoň jednou.

> [!NOTE]
>  Ne všechny systémy souborů používají stejnou sémantiku k implementaci časového razítka vráceného touto funkcí. Tato funkce může vracet stejnou hodnotu vrácenou jinými funkcemi časového razítka, Pokud podkladový systém souborů nebo server nepodporuje zachování atributu Time. Informace o formátech času najdete v [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktuře. V některých operačních systémech byl vrácený čas v časovém pásmu, které se nachází v místním počítači, ale soubor je umístěný. Další informace najdete v tématu rozhraní Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: GetLength](#getlength).

##  <a name="getfilename"></a>CFileFind:: getsoubor

Zavolejte tuto členskou funkci, aby získala název nalezeného souboru.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název souboru naposledy nalezeného souboru.

### <a name="remarks"></a>Poznámky

Před voláním metody getfiletable je nutné volat [FindNextFile](#findnextfile) alespoň jednou.

`GetFileName`je jedna ze tří `CFileFind` členských funkcí, které vracejí určitou formu názvu souboru. Následující seznam popisuje tři a jak se liší:

- `GetFileName`Vrátí název souboru, včetně přípony. Například volání `GetFileName` pro vygenerování zprávy uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *MyFile. txt*.

- [](#getfilepath) Funkce GetFilePath vrátí celou cestu k souboru. Například volání `GetFilePath` pro vygenerování zprávy uživatele o souboru *c:\myhtml\myfile.txt* vrátí cestu k souboru *c:\myhtml\myfile.txt*.

- [GetFileTitle](#getfiletitle) vrátí název souboru s výjimkou přípony souboru. Například volání `GetFileTitle` pro vygenerování zprávy uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *MyFile*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

##  <a name="getfilepath"></a>CFileFind:: GetFilePath

Chcete-li získat úplnou cestu k zadanému souboru, zavolejte tuto členskou funkci.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Návratová hodnota

Cesta k zadanému souboru.

### <a name="remarks"></a>Poznámky

Před voláním [](#findnextfile) `GetFilePath`je nutné volat FindNextFile alespoň jednou.

`GetFilePath`je jedna ze tří `CFileFind` členských funkcí, které vracejí určitou formu názvu souboru. Následující seznam popisuje tři a jak se liší:

- [Getfiletable](#getfilename) vrátí název souboru včetně přípony. Například volání `GetFileName` pro vygenerování zprávy uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *MyFile. txt*.

- `GetFilePath`Vrátí celou cestu k souboru. Například volání `GetFilePath` pro vygenerování zprávy uživatele o souboru `c:\myhtml\myfile.txt` vrátí cestu `c:\myhtml\myfile.txt`k souboru.

- [GetFileTitle](#getfiletitle) vrátí název souboru s výjimkou přípony souboru. Například volání `GetFileTitle` pro vygenerování zprávy uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *MyFile*.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: getsouboru](#getfilename).

##  <a name="getfiletitle"></a>CFileFind::GetFileTitle

Zavolejte tuto členskou funkci, aby se získal název nalezeného souboru.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Návratová hodnota

Název souboru

### <a name="remarks"></a>Poznámky

Před voláním [](#findnextfile) `GetFileTitle`je nutné volat FindNextFile alespoň jednou.

`GetFileTitle`je jedna ze tří `CFileFind` členských funkcí, které vracejí určitou formu názvu souboru. Následující seznam popisuje tři a jak se liší:

- [Getfiletable](#getfilename) vrátí název souboru včetně přípony. Například volání `GetFileName` pro vygenerování zprávy uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *MyFile. txt*.

- [](#getfilepath) Funkce GetFilePath vrátí celou cestu k souboru. Například volání `GetFilePath` pro vygenerování zprávy uživatele o souboru *c:\myhtml\myfile.txt* vrátí cestu k souboru *c:\myhtml\myfile.txt*.

- `GetFileTitle`Vrátí název souboru s výjimkou přípony souboru. Například volání `GetFileTitle` pro vygenerování zprávy uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *MyFile*.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: getsouboru](#getfilename).

##  <a name="getfileurl"></a>CFileFind::GetFileURL

Chcete-li načíst zadanou adresu URL, zavolejte tuto členskou funkci.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Návratová hodnota

Úplná adresa URL.

### <a name="remarks"></a>Poznámky

Před voláním [](#findnextfile) `GetFileURL`je nutné volat FindNextFile alespoň jednou.

`GetFileURL`se podobá funkci GetFilePath [](#getfilepath)členské funkce s tím rozdílem, že vrátí adresu URL ve `file://path`formuláři. Například volání `GetFileURL` pro získání úplné adresy URL pro *soubor MyFile. txt* vrátí adresu URL `file://c:\myhtml\myfile.txt`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: getsouboru](#getfilename).

##  <a name="getlastaccesstime"></a>CFileFind::GetLastAccessTime

Zavolejte tuto členskou funkci, aby se získal čas posledního otevření zadaného souboru.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Parametry

*refTime*<br/>
Odkaz na objekt [CTime –](../../atl-mfc-shared/reference/ctime-class.md) .

*pTimeStamp*<br/>
Ukazatel na strukturu [času](/windows/win32/api/minwinbase/ns-minwinbase-filetime) souboru obsahující čas posledního otevření souboru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; 0, pokud neproběhla úspěšně. `GetLastAccessTime`Vrátí hodnotu 0 pouze v případě, že [FindNextFile](#findnextfile) nebyl nikdy `CFileFind` volán u tohoto objektu.

### <a name="remarks"></a>Poznámky

Před voláním [](#findnextfile) `GetLastAccessTime`je nutné volat FindNextFile alespoň jednou.

> [!NOTE]
>  Ne všechny systémy souborů používají stejnou sémantiku k implementaci časového razítka vráceného touto funkcí. Tato funkce může vracet stejnou hodnotu vrácenou jinými funkcemi časového razítka, Pokud podkladový systém souborů nebo server nepodporuje zachování atributu Time. Informace o formátech času najdete v [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktuře. V některých operačních systémech byl vrácený čas v časovém pásmu, které se nachází v místním počítači, ale soubor je umístěný. Další informace najdete v tématu rozhraní Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: GetLength](#getlength).

##  <a name="getlastwritetime"></a>CFileFind::GetLastWriteTime

Zavolejte tuto členskou funkci, aby se získal čas poslední změny souboru.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parametry

*pTimeStamp*<br/>
Ukazatel na strukturu [času](/windows/win32/api/minwinbase/ns-minwinbase-filetime) souboru obsahující čas, kdy byl soubor naposledy zapsán.

*refTime*<br/>
Odkaz na objekt [CTime –](../../atl-mfc-shared/reference/ctime-class.md) .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; 0, pokud neproběhla úspěšně. `GetLastWriteTime`Vrátí hodnotu 0 pouze v případě, že [FindNextFile](#findnextfile) nebyl nikdy `CFileFind` volán u tohoto objektu.

### <a name="remarks"></a>Poznámky

Před voláním [](#findnextfile) `GetLastWriteTime`je nutné volat FindNextFile alespoň jednou.

> [!NOTE]
>  Ne všechny systémy souborů používají stejnou sémantiku k implementaci časového razítka vráceného touto funkcí. Tato funkce může vracet stejnou hodnotu vrácenou jinými funkcemi časového razítka, Pokud podkladový systém souborů nebo server nepodporuje zachování atributu Time. Informace o formátech času najdete v [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktuře. V některých operačních systémech byl vrácený čas v časovém pásmu, které se nachází v místním počítači, ale soubor je umístěný. Další informace najdete v tématu rozhraní Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: GetLength](#getlength).

##  <a name="getlength"></a>CFileFind:: GetLength

Voláním této členské funkce získáte délku nalezeného souboru v bajtech.

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka nalezeného souboru v bajtech

### <a name="remarks"></a>Poznámky

Před voláním [](#findnextfile) `GetLength`je nutné volat FindNextFile alespoň jednou.

`GetLength`pomocí [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktury Win32 získá a vrátí hodnotu velikosti souboru (v bajtech).

> [!NOTE]
>  V případě knihovny MFC 7,0 `GetLength` podporuje typy celočíselného celého čísla (64). Dříve existující kód sestavený pomocí této novější verze knihovny může mít za následek upozornění na zkrácení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

##  <a name="getroot"></a>CFileFind:: GetRoot

Zavolejte tuto členskou funkci, aby se získal kořen nalezeného souboru.

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>Návratová hodnota

Kořen aktivního hledání

### <a name="remarks"></a>Poznámky

Před voláním [](#findnextfile) `GetRoot`je nutné volat FindNextFile alespoň jednou.

Tato členská funkce vrátí specifikátor jednotky a název cesty, který se používá ke spuštění hledání. Například volání [FindFile –](#findfile) s `*.dat` výsledkem `GetRoot` vrácení prázdného řetězce. Předání cesty, `c:\windows\system\*.dll`jako je například, do `FindFile` vrácených `c:\windows\system\`výsledků. `GetRoot`

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: getsouboru](#getfilename).

##  <a name="isarchived"></a>CFileFind:: archivu

Voláním této členské funkce určíte, zda byl nalezen soubor archivován.

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Aplikace označí archivní soubor, který se má zálohovat nebo odebrat, s FILE_ATTRIBUTE_ARCHIVE atributem souboru, který je identifikovaný ve struktuře [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) .

Před voláním [](#findnextfile) `IsArchived`je nutné volat FindNextFile alespoň jednou.

Úplný seznam atributů souborů najdete v tématu [MatchesMask](#matchesmask) členské funkce.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: GetLength](#getlength).

##  <a name="iscompressed"></a>CFileFind:: dekomprimovaná

Zavolejte tuto členskou funkci, abyste zjistili, jestli je nalezený soubor komprimovaný.

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Komprimovaný soubor je označený jako FILE_ATTRIBUTE_COMPRESSED, atribut souboru identifikovaný ve struktuře [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) . U souboru tento atribut označuje, že všechna data v souboru jsou komprimována. V případě adresáře tento atribut označuje, že komprese je výchozím nastavením pro nově vytvořené soubory a podadresáře.

Před voláním [](#findnextfile) `IsCompressed`je nutné volat FindNextFile alespoň jednou.

Úplný seznam atributů souborů najdete v tématu [MatchesMask](#matchesmask) členské funkce.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: GetLength](#getlength).

##  <a name="isdirectory"></a>CFileFind::-adresář

Zavolejte tuto členskou funkci, abyste zjistili, jestli je nalezený soubor adresářem.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Soubor, který je adresářem, je označený jako FILE_ATTRIBUTE_DIRECTORY atribut souboru identifikovaný ve struktuře [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) .

Před voláním [](#findnextfile) `IsDirectory`je nutné volat FindNextFile alespoň jednou.

Úplný seznam atributů souborů najdete v tématu [MatchesMask](#matchesmask) členské funkce.

### <a name="example"></a>Příklad

Tento malý program rozchází všechny adresáře na C:\. jednotka a vytiskne název adresáře.

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

##  <a name="isdots"></a>CFileFind::-tečky

Voláním této členské funkce otestujete aktuální adresář a značky nadřazených adresářů při iteracích souborů.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud má nalezený soubor název "." nebo "..", který označuje, že nalezený soubor je ve skutečnosti adresář. V opačném případě 0.

### <a name="remarks"></a>Poznámky

Před voláním [](#findnextfile) `IsDots`je nutné volat FindNextFile alespoň jednou.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind::](#isdirectory).

##  <a name="ishidden"></a>CFileFind:: Hidden

Zavolejte tuto členskou funkci, abyste zjistili, jestli je nalezený soubor skrytý.

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Skryté soubory, které jsou označeny FILE_ATTRIBUTE_HIDDEN, atribut souboru identifikovaný ve struktuře [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) . Skrytý soubor není zahrnutý v běžném výpisu adresáře.

Před voláním [](#findnextfile) `IsHidden`je nutné volat FindNextFile alespoň jednou.

Úplný seznam atributů souborů najdete v tématu [MatchesMask](#matchesmask) členské funkce.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: GetLength](#getlength).

##  <a name="isnormal"></a>CFileFind:: Normal – Normální

Zavolejte tuto členskou funkci, abyste zjistili, jestli je nalezený soubor normálním souborem.

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Soubory označené FILE_ATTRIBUTE_NORMAL, atribut souboru identifikovaný ve struktuře [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) . V normálním souboru nejsou nastaveny žádné další atributy. Všechny ostatní atributy souboru přepíšou tento atribut.

Před voláním [](#findnextfile) `IsNormal`je nutné volat FindNextFile alespoň jednou.

Úplný seznam atributů souborů najdete v tématu [MatchesMask](#matchesmask) členské funkce.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: GetLength](#getlength).

##  <a name="isreadonly"></a>CFileFind:: IsReadOnly

Zavolejte tuto členskou funkci, abyste zjistili, jestli je nalezený soubor jen pro čtení.

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Soubor, který je jen pro čtení, je označený jako FILE_ATTRIBUTE_READONLY, atribut souboru identifikovaný ve struktuře [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) . Aplikace můžou takový soubor číst, ale nemůžou do něj zapisovat ani ho odstraňovat.

Před voláním [](#findnextfile) `IsReadOnly`je nutné volat FindNextFile alespoň jednou.

Úplný seznam atributů souborů najdete v tématu [MatchesMask](#matchesmask) členské funkce.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: GetLength](#getlength).

##  <a name="issystem"></a>CFileFind:: FileSystem

Voláním této členské funkce určíte, zda je nalezený soubor systémový soubor.

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Systémový soubor je označený jako FILE_ATTRIBUTE_SYSTEM, atribut File identifikovaný ve struktuře [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) . Systémový soubor je součástí systému, nebo je používán výhradně operačním systémem.

Před voláním [](#findnextfile) `IsSystem`je nutné volat FindNextFile alespoň jednou.

Úplný seznam atributů souborů najdete v tématu [MatchesMask](#matchesmask) členské funkce.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: GetLength](#getlength).

##  <a name="istemporary"></a>CFileFind::-dočasná

Zavolejte tuto členskou funkci, abyste zjistili, jestli je nalezený soubor dočasným souborem.

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Dočasný soubor je označený jako FILE_ATTRIBUTE_TEMPORARY, atribut souboru identifikovaný ve struktuře [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) . Dočasný soubor se používá pro dočasné úložiště. Aplikace by měly zapisovat do souboru pouze v případě, že je to nezbytně nutné. Většina dat souboru zůstává v paměti, aniž by byla vyprázdněna na médium, protože soubor bude brzy odstraněn.

Před voláním [](#findnextfile) `IsTemporary`je nutné volat FindNextFile alespoň jednou.

Úplný seznam atributů souborů najdete v tématu [MatchesMask](#matchesmask) členské funkce.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFileFind:: GetLength](#getlength).

##  <a name="m_ptm"></a>CFileFind::m_pTM

Ukazatel na `CAtlTransactionManager` objekt.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Poznámky

##  <a name="matchesmask"></a>CFileFind::MatchesMask

Zavolejte tuto členskou funkci pro otestování atributů souboru v nalezeném souboru.

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>Parametry

*dwMask*<br/>
Určuje jeden nebo více atributů souboru identifikovaných ve struktuře [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) pro nalezený soubor. Chcete-li vyhledat více atributů, použijte operátor bitového&#124;operátoru OR (). Je přijatelné jakékoli kombinace následujících atributů:

- FILE_ATTRIBUTE_ARCHIVE soubor je archivní soubor. Aplikace používají tento atribut k označení souborů pro zálohování nebo odebrání.

- FILE_ATTRIBUTE_COMPRESSED, že se soubor nebo adresář komprimuje. V případě souboru to znamená, že všechna data v souboru jsou komprimována. V případě adresáře to znamená, že komprese je výchozím nastavením pro nově vytvořené soubory a podadresáře.

- FILE_ATTRIBUTE_DIRECTORY soubor je adresář.

- FILE_ATTRIBUTE_NORMAL soubor nemá nastavené žádné další atributy. Tento atribut je platný pouze v případě, že je použit samostatně. Všechny ostatní atributy souboru přepíšou tento atribut.

- FILE_ATTRIBUTE_HIDDEN soubor je skrytý. Není zahrnutý do běžného výpisu adresáře.

- FILE_ATTRIBUTE_READONLY soubor je jen pro čtení. Aplikace můžou soubor číst, ale nemůžou do něj zapisovat ani ho odstraňovat.

- FILE_ATTRIBUTE_SYSTEM soubor je součástí nebo je používán výhradně operačním systémem.

- FILE_ATTRIBUTE_TEMPORARY soubor se používá pro dočasné úložiště. Aplikace by měly zapisovat do souboru pouze v případě, že je to nezbytně nutné. Většina dat souboru zůstává v paměti, aniž by byla vyprázdněna na médium, protože soubor bude brzy odstraněn.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Poznámky

Před voláním [](#findnextfile) `MatchesMask`je nutné volat FindNextFile alespoň jednou.

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
