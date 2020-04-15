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
ms.openlocfilehash: f01aa84593afed5a4f2f102da7d161ad42917080
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373879"
---
# <a name="cfilefind-class"></a>CFileFind – třída

Provádí místní vyhledávání souborů a je základní třídou [pro CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) a [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md), které provádějí vyhledávání souborů v Internetu.

## <a name="syntax"></a>Syntaxe

```
class CFileFind : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CFileFind::CFileFind](#cfilefind)|Vytvoří `CFileFind` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CFileFind::Zavřít](#close)|Zavře požadavek na hledání.|
|[CFileFind::FindFile](#findfile)|Vyhledá v adresáři zadaný název souboru.|
|[CFileFind::FindNextFile](#findnextfile)|Pokračuje v hledání souborů z předchozího volání [FindFile](#findfile).|
|[CFileFind::GetCreationTime](#getcreationtime)|Získá čas, kdy byl soubor vytvořen.|
|[CFileFind::GetFileName](#getfilename)|Získá název, včetně přípony nalezeného souboru|
|[CFileFind::GetFilePath](#getfilepath)|Získá celou cestu nalezeného souboru.|
|[CFileFind::GetFileTitle](#getfiletitle)|Získá název nalezeného souboru. Název neobsahuje rozšíření.|
|[CFileFind::GetFileURL](#getfileurl)|Získá adresu URL, včetně cesty k souboru nalezeného souboru.|
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|Získá čas, kdy byl soubor naposledy přístupná.|
|[CFileFind::GetLastWriteTime](#getlastwritetime)|Získá čas, kdy byl soubor naposledy změněn a uložen.|
|[CFileFind::GetLength](#getlength)|Získá délku nalezeného souboru v bajtů.|
|[CFileFind::GetRoot](#getroot)|Získá kořenový adresář nalezeného souboru.|
|[CFileFind::Archivováno](#isarchived)|Určuje, zda je nalezený soubor archivován.|
|[CFileFind::Jekomprimovaný](#iscompressed)|Určuje, zda je nalezený soubor komprimován.|
|[cfilefind::isdirectory](#isdirectory)|Určuje, zda je nalezený soubor adresář.|
|[CFileFind::IsDots](#isdots)|Určuje, zda má název nalezeného souboru název "." nebo "..", což znamená, že se ve skutečnosti jedná o adresář.|
|[cfilefind::ishidden](#ishidden)|Určuje, zda je nalezený soubor skrytý.|
|[cfilefind::isnormální](#isnormal)|Určuje, zda je nalezený soubor normální (jinými slovy nemá žádné další atributy).|
|[cfilefind::Pouze isreadonly](#isreadonly)|Určuje, zda je nalezený soubor jen pro čtení.|
|[cfilefind::IsSystem](#issystem)|Určuje, zda je nalezený soubor systémový soubor.|
|[cfilefind::IsTemporary](#istemporary)|Určuje, zda je nalezený soubor dočasný.|
|[CFileFind::Maska shody](#matchesmask)|Označuje požadované atributy souboru, který má být nalezen.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CFileFind::CloseContext](#closecontext)|Zavře soubor určený aktuálním popisovačem hledání.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CFileFind::m_pTM](#m_ptm)|Ukazatel na `CAtlTransactionManager` objekt.|

## <a name="remarks"></a>Poznámky

`CFileFind`zahrnuje členské funkce, které zahájí hledání, vyhledají soubor a vrátí název, název nebo cestu k souboru. Pro vyhledávání v Internetu vrátí členská funkce [GetFileURL](#getfileurl) adresu URL souboru.

`CFileFind`je základní třída pro další dvě třídy knihovny `CGopherFileFind` MFC určené k `CFtpFileFind` vyhledávání konkrétních typů serverů: pracuje konkrétně se servery gopher a pracuje konkrétně se servery FTP. Tyto tři třídy společně poskytují klientům bezproblémový mechanismus hledání souborů bez ohledu na serverový protokol, typ souboru nebo umístění na místním počítači nebo na vzdáleném serveru.

Následující kód vytvoří výčet všech souborů v aktuálním adresáři a vytiskne název každého souboru:

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

Chcete-li zachovat v jednoduchém příkladu, `cout` tento kód používá třídu C++ Standard Library. Řádek `cout` může být nahrazen voláním `CListBox::AddString`na , například v programu s grafickým uživatelským rozhraním.

Další informace o použití `CFileFind` a další chod wininet naleznete v článku [Internetové programování s WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="cfilefindcfilefind"></a><a name="cfilefind"></a>CFileFind::CFileFind

Tato členská funkce `CFileFind` je volána při vytvoření objektu.

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parametry

*Ptm*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetFileName](#getfilename).

## <a name="cfilefindclose"></a><a name="close"></a>CFileFind::Zavřít

Volání této členské funkce ukončit hledání, obnovit kontext a uvolnit všechny prostředky.

```
void Close();
```

### <a name="remarks"></a>Poznámky

Po `Close`volání není před voláním `CFileFind` [souboru FindFile](#findfile) třeba vytvořit novou instanci, chcete-li zahájit nové hledání.

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetFileName](#getfilename).

## <a name="cfilefindclosecontext"></a><a name="closecontext"></a>CFileFind::CloseContext

Zavře soubor určený aktuálním popisovačem hledání.

```
virtual void CloseContext();
```

### <a name="remarks"></a>Poznámky

Zavře soubor určený aktuální hodnotou popisovače hledání. Přepsáním této funkce změňte výchozí chování.

Chcete-li načíst platný popisovač hledání, musíte alespoň jednou volat funkce [FindFile](#findfile) nebo [FindNextFile.](#findnextfile) Funkce `FindFile` `FindNextFile` a používají popisovač hledání k vyhledání souborů s názvy, které odpovídají danému názvu.

## <a name="cfilefindfindfile"></a><a name="findfile"></a>CFileFind::FindFile

Volánítéto členské funkce otevřete hledání souborů.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>Parametry

*název pstr*<br/>
Ukazatel na řetězec obsahující název souboru, který chcete najít. Pokud předáte hodnotu NULL `FindFile` pro *název pstrName*, prohledá zástupný znak (*.\*).

*dwNevyužito*<br/>
Vyhrazeno `FindFile` pro polymorfní s odvozenými třídami. Musí být 0.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Poznámky

Po `FindFile` volání zahájit hledání souboru, volání [FindNextFile](#findnextfile) načíst následné soubory. Před voláním některé z následujících členských funkcí atributů je nutné volat `FindNextFile` alespoň jednou:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [Soubor GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [Jekomprimovaný](#iscompressed)

- [Adresář IsDirectory](#isdirectory)

- [IsTečky](#isdots)

- [IsSkryté](#ishidden)

- [Jenormální](#isnormal)

- [IsReadOnly](#isreadonly)

- [Systém IS](#issystem)

- [Jedočasné](#istemporary)

- [Maska shozů](#matchesmask)

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::IsDirectory](#isdirectory).

## <a name="cfilefindfindnextfile"></a><a name="findnextfile"></a>CFileFind::FindNextFile

Volání této členské funkce pokračovat hledání souborů z předchozího volání [FindFile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud existuje více souborů; nula, pokud je nalezený soubor poslední v adresáři nebo pokud došlo k chybě. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Pokud je nalezený soubor posledním souborem v adresáři nebo pokud `GetLastError` nelze nalézt žádné odpovídající soubory, vrátí funkce ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Poznámky

Před voláním některé z následujících členských funkcí atributů je nutné volat `FindNextFile` alespoň jednou:

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [Soubor GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [Jekomprimovaný](#iscompressed)

- [Adresář IsDirectory](#isdirectory)

- [IsTečky](#isdots)

- [IsSkryté](#ishidden)

- [Jenormální](#isnormal)

- [IsReadOnly](#isreadonly)

- [Systém IS](#issystem)

- [Jedočasné](#istemporary)

- [Maska shozů](#matchesmask)

`FindNextFile`zabalí funkci Win32 [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew).

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::IsDirectory](#isdirectory).

## <a name="cfilefindgetcreationtime"></a><a name="getcreationtime"></a>CFileFind::GetCreationTime

Volání této členské funkce získat čas, kdy byl vytvořen zadaný soubor.

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parametry

*pTimeStamp*<br/>
Ukazatel na strukturu [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) obsahující čas vytvoření souboru.

*refTime*<br/>
Odkaz na [ctime](../../atl-mfc-shared/reference/ctime-class.md) objekt.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; 0 v případě neúspěchu. `GetCreationTime`vrátí hodnotu 0 pouze v případě, `CFileFind` že [findnextfile](#findnextfile) nebyl nikdy volán na tento objekt.

### <a name="remarks"></a>Poznámky

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `GetCreationTime`před voláním .

> [!NOTE]
> Ne všechny systémy souborů používají stejnou sémantiku k implementaci časového razítka vráceného touto funkcí. Tato funkce může vrátit stejnou hodnotu vrácenou jinými funkcemi časového razítka, pokud základní systém souborů nebo server nepodporuje zachování atributu time. Informace o formátech času naleznete ve struktuře [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) V některých operačních systémech je vrácený čas v místním časovém pásmu počítače, pokud je soubor umístěn. Další informace naleznete v rozhraní API rozhraní Api pro soubor Win32 [FileTimeToLocalFileTime.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetLength](#getlength).

## <a name="cfilefindgetfilename"></a><a name="getfilename"></a>CFileFind::GetFileName

Volání této členské funkce získat název nalezeného souboru.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název naposledy nalezeného souboru.

### <a name="remarks"></a>Poznámky

Musíte volat [FindNextFile](#findnextfile) alespoň jednou před voláním GetFileName.

`GetFileName`je jednou `CFileFind` ze tří členských funkcí, které vracejí nějakou formu názvu souboru. Následující seznam popisuje tři a jak se liší:

- `GetFileName`vrátí název souboru včetně přípony. Například volání `GetFileName` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *myfile.txt*.

- [GetFilePath](#getfilepath) vrátí celou cestu pro soubor. Například volání `GetFilePath` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí cestu k souboru *c:\myhtml\myfile.txt*.

- [Funkce GetFileTitle](#getfiletitle) vrátí název souboru s výjimkou přípony souboru. Například volání `GetFileTitle` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *myfile*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

## <a name="cfilefindgetfilepath"></a><a name="getfilepath"></a>CFileFind::GetFilePath

Volání této členské funkce získat úplnou cestu k zadanému souboru.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Návratová hodnota

Cesta k zadanému souboru.

### <a name="remarks"></a>Poznámky

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `GetFilePath`před voláním .

`GetFilePath`je jednou `CFileFind` ze tří členských funkcí, které vracejí nějakou formu názvu souboru. Následující seznam popisuje tři a jak se liší:

- [Funkce GetFileName](#getfilename) vrátí název souboru včetně přípony. Například volání `GetFileName` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *myfile.txt*.

- `GetFilePath`vrátí celou cestu k souboru. Například volání `GetFilePath` generovat zprávu uživatele o `c:\myhtml\myfile.txt` souboru `c:\myhtml\myfile.txt`vrátí cestu k souboru .

- [Funkce GetFileTitle](#getfiletitle) vrátí název souboru s výjimkou přípony souboru. Například volání `GetFileTitle` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *myfile*.

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetFileName](#getfilename).

## <a name="cfilefindgetfiletitle"></a><a name="getfiletitle"></a>CFileFind::GetFileTitle

Volánítéto členské funkce získat název nalezeného souboru.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Návratová hodnota

Název souboru.

### <a name="remarks"></a>Poznámky

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `GetFileTitle`před voláním .

`GetFileTitle`je jednou `CFileFind` ze tří členských funkcí, které vracejí nějakou formu názvu souboru. Následující seznam popisuje tři a jak se liší:

- [Funkce GetFileName](#getfilename) vrátí název souboru včetně přípony. Například volání `GetFileName` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *myfile.txt*.

- [GetFilePath](#getfilepath) vrátí celou cestu pro soubor. Například volání `GetFilePath` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí cestu k souboru *c:\myhtml\myfile.txt*.

- `GetFileTitle`vrátí název souboru s výjimkou přípony souboru. Například volání `GetFileTitle` generovat zprávu uživatele o souboru *c:\myhtml\myfile.txt* vrátí název souboru *myfile*.

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetFileName](#getfilename).

## <a name="cfilefindgetfileurl"></a><a name="getfileurl"></a>CFileFind::GetFileURL

Volání této členské funkce načíst zadanou adresu URL.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Návratová hodnota

Úplná adresa URL.

### <a name="remarks"></a>Poznámky

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `GetFileURL`před voláním .

`GetFileURL`je podobná členské funkci [GetFilePath](#getfilepath)s tím rozdílem, `file://path`že vrátí adresu URL ve formuláři . Například volání `GetFileURL` získat úplnou adresu URL pro *myfile.txt* vrátí adresu URL `file://c:\myhtml\myfile.txt`.

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetFileName](#getfilename).

## <a name="cfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a>CFileFind::GetLastAccessTime

Volání této členské funkce získat čas, který byl naposledy přístup k zadanému souboru.

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>Parametry

*refTime*<br/>
Odkaz na [ctime](../../atl-mfc-shared/reference/ctime-class.md) objekt.

*pTimeStamp*<br/>
Ukazatel na strukturu [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) obsahující čas posledního přístupu k souboru.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; 0 v případě neúspěchu. `GetLastAccessTime`vrátí hodnotu 0 pouze v případě, `CFileFind` že [findnextfile](#findnextfile) nebyl nikdy volán na tento objekt.

### <a name="remarks"></a>Poznámky

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `GetLastAccessTime`před voláním .

> [!NOTE]
> Ne všechny systémy souborů používají stejnou sémantiku k implementaci časového razítka vráceného touto funkcí. Tato funkce může vrátit stejnou hodnotu vrácenou jinými funkcemi časového razítka, pokud základní systém souborů nebo server nepodporuje zachování atributu time. Informace o formátech času naleznete ve struktuře [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) V některých operačních systémech je vrácený čas v místním časovém pásmu počítače, pokud je soubor umístěn. Další informace naleznete v rozhraní API rozhraní Api pro soubor Win32 [FileTimeToLocalFileTime.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetLength](#getlength).

## <a name="cfilefindgetlastwritetime"></a><a name="getlastwritetime"></a>CFileFind::GetLastWriteTime

Volání této členské funkce získat poslední čas byl změněn soubor.

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>Parametry

*pTimeStamp*<br/>
Ukazatel na strukturu [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) obsahující čas, do kterého byl soubor naposledy zapsán.

*refTime*<br/>
Odkaz na [ctime](../../atl-mfc-shared/reference/ctime-class.md) objekt.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; 0 v případě neúspěchu. `GetLastWriteTime`vrátí hodnotu 0 pouze v případě, `CFileFind` že [findnextfile](#findnextfile) nebyl nikdy volán na tento objekt.

### <a name="remarks"></a>Poznámky

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `GetLastWriteTime`před voláním .

> [!NOTE]
> Ne všechny systémy souborů používají stejnou sémantiku k implementaci časového razítka vráceného touto funkcí. Tato funkce může vrátit stejnou hodnotu vrácenou jinými funkcemi časového razítka, pokud základní systém souborů nebo server nepodporuje zachování atributu time. Informace o formátech času naleznete ve struktuře [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) V některých operačních systémech je vrácený čas v místním časovém pásmu počítače, pokud je soubor umístěn. Další informace naleznete v rozhraní API rozhraní Api pro soubor Win32 [FileTimeToLocalFileTime.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetLength](#getlength).

## <a name="cfilefindgetlength"></a><a name="getlength"></a>CFileFind::GetLength

Volání této členské funkce získat délku nalezeného souboru, v bajtů.

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka nalezeného souboru v bajtů.

### <a name="remarks"></a>Poznámky

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `GetLength`před voláním .

`GetLength`Používá win32 struktura [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) získat a vrátit hodnotu velikosti souboru, v bajtů.

> [!NOTE]
> Od knihovny MFC `GetLength` 7.0 podporuje 64bitové celočíselné typy. Dříve existující kód vytvořený s touto novější verzí knihovny může mít za následek upozornění na zkrácení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

## <a name="cfilefindgetroot"></a><a name="getroot"></a>CFileFind::GetRoot

Volání této členské funkce získat kořen nalezeného souboru.

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>Návratová hodnota

Kořen aktivního hledání.

### <a name="remarks"></a>Poznámky

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `GetRoot`před voláním .

Tato členská funkce vrátí specifikátor jednotky a název cesty použitý ke spuštění hledání. Například volání [FindFile](#findfile) `*.dat` s `GetRoot` výsledky při vrácení prázdný řetězec. Předání cesty, `c:\windows\system\*.dll`například `FindFile` , `GetRoot` k `c:\windows\system\`návratu výsledků .

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetFileName](#getfilename).

## <a name="cfilefindisarchived"></a><a name="isarchived"></a>CFileFind::Archivováno

Volání této členské funkce k určení, zda je nalezený soubor archivován.

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Aplikace označují archivní soubor, který má být zálohován nebo odebrán, s FILE_ATTRIBUTE_ARCHIVE atributem souboru identifikovaným ve [struktuře WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `IsArchived`před voláním .

Úplný seznam atributů souboru naleznete v členské funkci [MatchesMask.](#matchesmask)

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetLength](#getlength).

## <a name="cfilefindiscompressed"></a><a name="iscompressed"></a>CFileFind::Jekomprimovaný

Volání této členské funkce k určení, zda je nalezený soubor komprimován.

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Komprimovaný soubor je označen FILE_ATTRIBUTE_COMPRESSED, atributem souboru identifikovaným ve struktuře [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) U souboru tento atribut označuje, že všechna data v souboru jsou komprimována. Pro adresář tento atribut označuje, že komprese je výchozí pro nově vytvořené soubory a podadresáře.

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `IsCompressed`před voláním .

Úplný seznam atributů souboru naleznete v členské funkci [MatchesMask.](#matchesmask)

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetLength](#getlength).

## <a name="cfilefindisdirectory"></a><a name="isdirectory"></a>cfilefind::isdirectory

Volání této členské funkce k určení, zda nalezený soubor je adresář.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Soubor, který je adresářje označen FILE_ATTRIBUTE_DIRECTORY atribut souboru identifikován ve struktuře [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `IsDirectory`před voláním .

Úplný seznam atributů souboru naleznete v členské funkci [MatchesMask.](#matchesmask)

### <a name="example"></a>Příklad

Tento malý program recurses každý adresář na C:\ a vytiskne název adresáře.

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

## <a name="cfilefindisdots"></a><a name="isdots"></a>CFileFind::IsDots

Volání této členské funkce otestovat aktuální adresář a nadřazené značky adresáře při iterace prostřednictvím souborů.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud má nalezený soubor název "." nebo "..", což znamená, že nalezený soubor je ve skutečnosti adresář. Jinak 0.

### <a name="remarks"></a>Poznámky

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `IsDots`před voláním .

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::IsDirectory](#isdirectory).

## <a name="cfilefindishidden"></a><a name="ishidden"></a>cfilefind::ishidden

Volání této členské funkce k určení, zda je nalezený soubor skrytý.

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Skryté soubory, které jsou označeny FILE_ATTRIBUTE_HIDDEN, atribut souboru identifikovaný ve [struktuře WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Skrytý soubor není součástí běžného výpisu adresáře.

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `IsHidden`před voláním .

Úplný seznam atributů souboru naleznete v členské funkci [MatchesMask.](#matchesmask)

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetLength](#getlength).

## <a name="cfilefindisnormal"></a><a name="isnormal"></a>cfilefind::isnormální

Volání této členské funkce k určení, zda nalezený soubor je normální soubor.

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Soubory označené FILE_ATTRIBUTE_NORMAL, atribut souboru identifikovaný ve struktuře [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Normální soubor nemá nastaveny žádné další atributy. Všechny ostatní atributy souboru tento atribut přepíší.

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `IsNormal`před voláním .

Úplný seznam atributů souboru naleznete v členské funkci [MatchesMask.](#matchesmask)

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetLength](#getlength).

## <a name="cfilefindisreadonly"></a><a name="isreadonly"></a>cfilefind::Pouze isreadonly

Volání této členské funkce k určení, zda nalezený soubor je jen pro čtení.

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Soubor jen pro čtení je označen FILE_ATTRIBUTE_READONLY, atributem souboru identifikovaným ve struktuře [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Aplikace mohou takový soubor číst, ale nemohou do něj zapisovat ani odstraňovat.

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `IsReadOnly`před voláním .

Úplný seznam atributů souboru naleznete v členské funkci [MatchesMask.](#matchesmask)

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetLength](#getlength).

## <a name="cfilefindissystem"></a><a name="issystem"></a>cfilefind::IsSystem

Volání této členské funkce k určení, zda nalezený soubor je systémový soubor.

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Systémový soubor je označen FILE_ATTRIBUTE_SYSTEM , atributem souboru identifikovaným ve struktuře [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Systémový soubor je součástí operačního systému nebo je používán výhradně operačním systémem.

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `IsSystem`před voláním .

Úplný seznam atributů souboru naleznete v členské funkci [MatchesMask.](#matchesmask)

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetLength](#getlength).

## <a name="cfilefindistemporary"></a><a name="istemporary"></a>cfilefind::IsTemporary

Volání této členské funkce k určení, zda nalezený soubor je dočasný soubor.

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Dočasný soubor je označen FILE_ATTRIBUTE_TEMPORARY, atributem souboru identifikovaným ve [struktuře WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) Dočasný soubor se používá pro dočasné úložiště. Aplikace by měly zapisovat do souboru pouze v případě, že je to nezbytně nutné. Většina dat souboru zůstává v paměti, aniž by byla vyprázdněna na médium, protože soubor bude brzy odstraněn.

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `IsTemporary`před voláním .

Úplný seznam atributů souboru naleznete v členské funkci [MatchesMask.](#matchesmask)

### <a name="example"></a>Příklad

  Viz příklad [cfilefind::GetLength](#getlength).

## <a name="cfilefindm_ptm"></a><a name="m_ptm"></a>CFileFind::m_pTM

Ukazatel na `CAtlTransactionManager` objekt.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Poznámky

## <a name="cfilefindmatchesmask"></a><a name="matchesmask"></a>CFileFind::Maska shody

Volání této členské funkce otestovat atributy souboru na nalezený soubor.

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>Parametry

*dwMask*<br/>
Určuje jeden nebo více atributů souboru identifikovaných ve struktuře [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) nalezeného souboru. Chcete-li vyhledat více atributů, použijte bitový operátor OR (&#124;). Jakákoli kombinace následujících atributů je přijatelná:

- FILE_ATTRIBUTE_ARCHIVE Soubor je archivní soubor. Aplikace používají tento atribut k označení souborů pro zálohování nebo odebrání.

- FILE_ATTRIBUTE_COMPRESSED Soubor nebo adresář je komprimován. U souboru to znamená, že všechna data v souboru jsou komprimována. Pro adresář to znamená, že komprese je výchozí pro nově vytvořené soubory a podadresáře.

- FILE_ATTRIBUTE_DIRECTORY Soubor je adresář.

- FILE_ATTRIBUTE_NORMAL Soubor nemá nastaveny žádné další atributy. Tento atribut je platný pouze při použití samostatně. Všechny ostatní atributy souboru tento atribut přepíší.

- FILE_ATTRIBUTE_HIDDEN Soubor je skrytý. Nesmí být zahrnuta do běžného seznamu adresářů.

- FILE_ATTRIBUTE_READONLY Soubor je jen pro čtení. Aplikace mohou soubor číst, ale nemohou do něj zapisovat ani odstraňovat.

- FILE_ATTRIBUTE_SYSTEM Soubor je součástí operačního systému nebo je používán výhradně operačním systémem.

- FILE_ATTRIBUTE_TEMPORARY Soubor se používá pro dočasné uložení. Aplikace by měly zapisovat do souboru pouze v případě, že je to nezbytně nutné. Většina dat souboru zůstává v paměti, aniž by byla vyprázdněna na médium, protože soubor bude brzy odstraněn.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Poznámky

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `MatchesMask`před voláním .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)<br/>
[Třída CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile – třída](../../mfc/reference/chttpfile-class.md)
