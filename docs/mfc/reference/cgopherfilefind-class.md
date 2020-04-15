---
title: Třída CGopherFileFind
ms.date: 11/04/2016
f1_keywords:
- CGopherFileFind
- AFXINET/CGopherFileFind
- AFXINET/CGopherFileFind::CGopherFileFind
- AFXINET/CGopherFileFind::FindFile
- AFXINET/CGopherFileFind::FindNextFile
- AFXINET/CGopherFileFind::GetCreationTime
- AFXINET/CGopherFileFind::GetLastAccessTime
- AFXINET/CGopherFileFind::GetLastWriteTime
- AFXINET/CGopherFileFind::GetLength
- AFXINET/CGopherFileFind::GetLocator
- AFXINET/CGopherFileFind::GetScreenName
- AFXINET/CGopherFileFind::IsDots
helpviewer_keywords:
- CGopherFileFind [MFC], CGopherFileFind
- CGopherFileFind [MFC], FindFile
- CGopherFileFind [MFC], FindNextFile
- CGopherFileFind [MFC], GetCreationTime
- CGopherFileFind [MFC], GetLastAccessTime
- CGopherFileFind [MFC], GetLastWriteTime
- CGopherFileFind [MFC], GetLength
- CGopherFileFind [MFC], GetLocator
- CGopherFileFind [MFC], GetScreenName
- CGopherFileFind [MFC], IsDots
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
ms.openlocfilehash: 7a42b99c919abd9098bff1897c4c5febf443314d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373684"
---
# <a name="cgopherfilefind-class"></a>Třída CGopherFileFind

Pomáhá při vyhledávání souborů na internetu gopher serverů.

> [!NOTE]
> Třídy `CGopherConnection` `CGopherFile`, `CGopherFileFind` `CGopherLocator` , a jejich členové byly zastaralé, protože nefungují na platformě systému Windows XP, ale budou pokračovat v práci na dřívějších platformách.

## <a name="syntax"></a>Syntaxe

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|Vytvoří `CGopherFileFind` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CGopherFileFind::FindFile](#findfile)|Najde soubor na serveru gopher.|
|[CGopherFileFind::FindNextFile](#findnextfile)|Pokračuje v hledání souborů z předchozího volání [FindFile](#findfile).|
|[CGopherFileFind::GetCreationTime](#getcreationtime)|Získá čas, kdy byl vytvořen zadaný soubor.|
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|Získá čas, kdy byl naposledy přístupný soubor.|
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|Získá čas zadaný soubor byl naposledy zapsán do.|
|[CGopherFileFind::GetLength](#getlength)|Získá délku nalezeného souboru v bajtů.|
|[CGopherFileFind::GetLocator](#getlocator)|Získejte `CGopherLocator` objekt.|
|[CGopherFileFind::GetScreenName](#getscreenname)|Získá název gopher obrazovky.|
|[CGopherFileFind::IsDots](#isdots)|Testuje aktuální značky adresáře a nadřazené adresáře při iterace prostřednictvím souborů.|

## <a name="remarks"></a>Poznámky

`CGopherFileFind`zahrnuje členské funkce, které zahajují hledání, vyhledání souboru a vrácení adresy URL souboru.

Mezi další třídy knihovny MFC určené pro vyhledávání v Internetu a místních souborech patří [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) a [CFileFind](../../mfc/reference/cfilefind-class.md). Společně `CGopherFileFind`s aplikacemi poskytují tyto třídy uživatelům bezproblémový mechanismus k vyhledání určitých souborů bez ohledu na serverový protokol, typ souboru nebo umístění (místní počítač nebo vzdálený server).) Všimněte si, že neexistuje žádná třída knihovny MFC pro vyhledávání na serverech HTTP, protože protokol HTTP nepodporuje přímou manipulaci se soubory vyžadou vyhledávání.

> [!NOTE]
> `CGopherFileFind`nepodporuje následující členské funkce základní třídy [CFileFind](../../mfc/reference/cfilefind-class.md):

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [Soubor GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

Kromě toho při `CGopherFileFind`použití `CFileFind` s , členská funkce [IsDots](../../mfc/reference/cfilefind-class.md#isdots) je vždy FALSE.

Další informace o použití `CGopherFileFind` a další chod wininet naleznete v článku [Internetové programování s WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="cgopherfilefindcgopherfilefind"></a><a name="cgopherfilefind"></a>CGopherFileFind::CGopherFileFind

Tato členská funkce je `CGopherFileFind` volána k vytvoření objektu.

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pPřipojení*<br/>
Ukazatel na objekt [CGopherConnection.](../../mfc/reference/cgopherconnection-class.md)

*dwKontext*<br/>
Identifikátor kontextu pro operaci. Další informace o *dwContext*naleznete v **tématu Poznámky** .

### <a name="remarks"></a>Poznámky

Výchozí hodnota pro *dwContext* je odeslána `CGopherFileFind` knihovnou MFC do objektu z objektu [CInternetSession,](../../mfc/reference/cinternetsession-class.md) který `CGopherFileFind` objekt vytvořil. Při vytváření `CGopherFileFind` objektu můžete přepsat výchozí nastavení identifikátoru kontextu na hodnotu podle vašeho výběru. Identifikátor kontextu je [vrácena CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav na objekt, se kterým je identifikován. Další informace o identifikátoru kontextu naleznete v článku [První kroky Internetu: WinInet.](../../mfc/wininet-basics.md)

## <a name="cgopherfilefindfindfile"></a><a name="findfile"></a>CGopherFileFind::FindFile

Volání této členské funkce najít soubor gopher.

```
virtual BOOL FindFile(
    CGopherLocator& refLocator,
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);

virtual BOOL FindFile(
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Parametry

*refLocator*<br/>
Odkaz na objekt [CGopherLocator.](../../mfc/reference/cgopherlocator-class.md)

*pstrString*<br/>
Ukazatel na řetězec obsahující název souboru.

*dwFlags*<br/>
Příznaky popisující, jak zpracovat tuto relaci. Platné příznaky jsou:

- INTERNET_FLAG_RELOAD Získejte data ze vzdáleného serveru, i když je místně uložena do mezipaměti.

- INTERNET_FLAG_DONT_CACHE Neukládat data do mezipaměti, místně ani v žádné braně.

- INTERNET_FLAG_SECURE Požadovat zabezpečené transakce na lince pomocí sschlovací vrstvy nebo PCT. Tento příznak se vztahuje pouze na požadavky HTTP.

- INTERNET_FLAG_USE_EXISTING Pokud je to možné, znovu použijte `FindFile` existující připojení k serveru pro nové požadavky namísto vytvoření nové relace pro každý požadavek.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Poznámky

Po `FindFile` volání načíst první gopher objekt, můžete volat [FindNextFile](#findnextfile) načíst následné gopher soubory.

## <a name="cgopherfilefindfindnextfile"></a><a name="findnextfile"></a>CGopherFileFind::FindNextFile

Volání této členské funkce pokračovat hledání souborů začal o volání [CGopherFileFind::FindFile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud existuje více souborů; nula, pokud je nalezený soubor poslední v adresáři nebo pokud došlo k chybě. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Pokud je nalezený soubor posledním souborem v adresáři nebo pokud `GetLastError` nelze nalézt žádné odpovídající soubory, vrátí funkce ERROR_NO_MORE_FILES.

## <a name="cgopherfilefindgetcreationtime"></a><a name="getcreationtime"></a>CGopherFileFind::GetCreationTime

Získá čas vytvoření pro aktuální soubor.

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

Nenulová, pokud je úspěšná; 0 v případě neúspěchu. `GetCreationTime`vrátí hodnotu 0 pouze v případě, `CGopherFileFind` že [findnextfile](#findnextfile) nebyl nikdy volán na tento objekt.

### <a name="remarks"></a>Poznámky

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `GetCreationTime`před voláním .

> [!NOTE]
> Ne všechny systémy souborů používají stejnou sémantiku k implementaci časového razítka vráceného touto funkcí. Tato funkce může vrátit stejnou hodnotu vrácenou jinými funkcemi časového razítka, pokud základní systém souborů nebo server nepodporuje zachování atributu time. Informace o formátech času naleznete ve struktuře [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) V některých operačních systémech je vrácený čas v místním časovém pásmu počítače, pokud je soubor umístěn. Další informace naleznete v rozhraní API rozhraní Api pro soubor Win32 [FileTimeToLocalFileTime.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

## <a name="cgopherfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a>CGopherFileFind::GetLastAccessTime

Získá čas, kdy byl naposledy přístupný soubor.

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

Nenulová, pokud je úspěšná; 0 v případě neúspěchu. `GetLastAccessTime`vrátí hodnotu 0 pouze v případě, `CGopherFileFind` že [findnextfile](#findnextfile) nebyl nikdy volán na tento objekt.

### <a name="remarks"></a>Poznámky

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `GetLastAccessTime`před voláním .

> [!NOTE]
> Ne všechny systémy souborů používají stejnou sémantiku k implementaci časového razítka vráceného touto funkcí. Tato funkce může vrátit stejnou hodnotu vrácenou jinými funkcemi časového razítka, pokud základní systém souborů nebo server nepodporuje zachování atributu time. Informace o formátech času naleznete ve struktuře [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) V některých operačních systémech je vrácený čas v místním časovém pásmu počítače, pokud je soubor umístěn. Další informace naleznete v rozhraní API rozhraní Api pro soubor Win32 [FileTimeToLocalFileTime.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

## <a name="cgopherfilefindgetlastwritetime"></a><a name="getlastwritetime"></a>CGopherFileFind::GetLastWriteTime

Získá při poslední změně souboru.

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

Nenulová, pokud je úspěšná; 0 v případě neúspěchu. `GetLastWriteTime`vrátí hodnotu 0 pouze v případě, `CGopherFileFind` že [findnextfile](#findnextfile) nebyl nikdy volán na tento objekt.

### <a name="remarks"></a>Poznámky

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `GetLastWriteTime`před voláním .

> [!NOTE]
> Ne všechny systémy souborů používají stejnou sémantiku k implementaci časového razítka vráceného touto funkcí. Tato funkce může vrátit stejnou hodnotu vrácenou jinými funkcemi časového razítka, pokud základní systém souborů nebo server nepodporuje zachování atributu time. Informace o formátech času naleznete ve struktuře [WIN32_FIND_DATA.](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) V některých operačních systémech je vrácený čas v místním časovém pásmu počítače, pokud je soubor umístěn. Další informace naleznete v rozhraní API rozhraní Api pro soubor Win32 [FileTimeToLocalFileTime.](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime)

## <a name="cgopherfilefindgetlength"></a><a name="getlength"></a>CGopherFileFind::GetLength

Volání této členské funkce získat délku, v bajtů, nalezeného souboru.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka nalezeného souboru v bajtech.

### <a name="remarks"></a>Poznámky

`GetLength`používá win32 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) WIN32_FIND_DATA struktury získat hodnotu velikosti souboru v bajtů.

> [!NOTE]
> Od knihovny MFC `GetLength` 7.0 podporuje 64bitové celočíselné typy. Dříve existující kód vytvořený s touto novější verzí knihovny může mít za následek upozornění na zkrácení.

### <a name="example"></a>Příklad

  Viz příklad pro [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) (implementace základní třídy).

## <a name="cgopherfilefindgetlocator"></a><a name="getlocator"></a>CGopherFileFind::GetLocator

Volání této členské funkce získat [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objekt, který [FindFile](#findfile) používá k nalezení souboru gopher.

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt. `CGopherLocator`

## <a name="cgopherfilefindgetscreenname"></a><a name="getscreenname"></a>CGopherFileFind::GetScreenName

Volání této členské funkce získat název gopher obrazovky.

```
CString GetScreenName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název obrazovky gopher.

## <a name="cgopherfilefindisdots"></a><a name="isdots"></a>CGopherFileFind::IsDots

Testuje aktuální značky adresáře a nadřazené adresáře při iterace prostřednictvím souborů.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud má nalezený soubor název "." nebo "..", což znamená, že nalezený soubor je ve skutečnosti adresář. Jinak 0.

### <a name="remarks"></a>Poznámky

Musíte volat [FindNextFile](#findnextfile) alespoň jednou `IsDots`před voláním .

## <a name="see-also"></a>Viz také

[CFileFind – třída](../../mfc/reference/cfilefind-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind – třída](../../mfc/reference/cfilefind-class.md)<br/>
[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile – třída](../../mfc/reference/chttpfile-class.md)
