---
title: Cgopherfilefind – třída
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
ms.openlocfilehash: bced5a95f65713915a1f06094bfe059db79aab2d
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503644"
---
# <a name="cgopherfilefind-class"></a>Cgopherfilefind – třída

Pomáhá při hledání internetových souborů na serverech gopher.

> [!NOTE]
>  Třídy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` a jejich členy jsou zastaralé, protože nebude fungovat na platformě Windows XP, ale budou i nadále fungovat na starší platformy.

## <a name="syntax"></a>Syntaxe

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|Vytvoří `CGopherFileFind` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CGopherFileFind::FindFile](#findfile)|Vyhledá soubor na gopher serveru.|
|[CGopherFileFind::FindNextFile](#findnextfile)|Pokračuje v hledání souborů z předchozího volání [FindFile](#findfile).|
|[CGopherFileFind::GetCreationTime](#getcreationtime)|Získá čas vytvoření zadaného souboru.|
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|Získá čas posledního přístupu k souboru.|
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|Získá dobu do posledního zápisu zadaného souboru.|
|[CGopherFileFind::GetLength](#getlength)|Získá délku nalezený soubor v bajtech.|
|[CGopherFileFind::GetLocator](#getlocator)|Získání `CGopherLocator` objektu.|
|[CGopherFileFind::GetScreenName](#getscreenname)|Získá název obrazovky gopher.|
|[CGopherFileFind::IsDots](#isdots)|Testy pro aktuální adresář a nadřazené značky adresáře při procházení souborů.|

## <a name="remarks"></a>Poznámky

`CGopherFileFind` zahrnuje členské funkce, které začínají vyhledávání, vyhledání souboru a vrátí adresu URL souboru.

Jiné třídy knihovny MFC navržené pro Internet a prohledávat místní soubor k zahrnutí [cftpfilefind –](../../mfc/reference/cftpfilefind-class.md) a [cfilefind –](../../mfc/reference/cfilefind-class.md). Spolu s `CGopherFileFind`, tyto třídy poskytnout bezproblémové mechanismus pro uživatele o nalezení konkrétní soubory, bez ohledu na to, protokol serveru, typ souboru nebo umístění (místní počítač nebo na vzdálený server.) Všimněte si, že neexistuje žádná třída knihovny MFC pro vyhledávání na serverech HTTP, protože HTTP nepodporuje manipulace s přímým přístupem soubor vyžadují vyhledávání.

> [!NOTE]
> `CGopherFileFind` nepodporuje následující funkce člena základní třídy [cfilefind –](../../mfc/reference/cfilefind-class.md):

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

Kromě toho při použití s `CGopherFileFind`, `CFileFind` členskou funkci [IsDots](../../mfc/reference/cfilefind-class.md#isdots) má vždy hodnotu FALSE.

Další informace o tom, jak používat `CGopherFileFind` a jiných tříd WinInet, najdete v článku [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

##  <a name="cgopherfilefind"></a>  CGopherFileFind::CGopherFileFind

Tato členská funkce je volána k sestavení kompletních `CGopherFileFind` objektu.

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pConnection*<br/>
Ukazatel [cgopherconnection –](../../mfc/reference/cgopherconnection-class.md) objektu.

*dwContext*<br/>
Identifikátor kontextu operace. Zobrazit **poznámky** Další informace o *dwContext*.

### <a name="remarks"></a>Poznámky

Výchozí hodnota pro *dwContext* odesílají knihovny MFC pro `CGopherFileFind` objektu z [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objekt vytvořený `CGopherFileFind` objektu. Při sestavování `CGopherFileFind` objektu, můžete přepsat výchozí identifikátor kontextu nastavena na hodnotu podle vašeho výběru. Identifikátor kontextu se vrátí do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav objektu, pomocí kterého je identifikován. Přečtěte si článek [Internet první kroky: WinInet](../../mfc/wininet-basics.md) Další informace o identifikátor kontextu.

##  <a name="findfile"></a>  CGopherFileFind::FindFile

Voláním této členské funkce gopher soubor se nenašel.

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
Odkaz na [cgopherlocator –](../../mfc/reference/cgopherlocator-class.md) objektu.

*pstrString*<br/>
Ukazatel na řetězec obsahující název souboru.

*dwFlags*<br/>
Příznaky popisující, jak zpracovat tuto relaci. Platný příznaky jsou:

- INTERNET_FLAG_RELOAD získat data ze vzdáleného serveru i v případě, že je v místní mezipaměti.

- INTERNET_FLAG_DONT_CACHE Neukládat do mezipaměti dat, místně nebo v žádné brány.

- Požádat o INTERNET_FLAG_SECURE zabezpečené transakce na lince Secure Sockets Layer nebo v PROC. Tento příznak se vztahuje pouze na požadavky HTTP.

- INTERNET_FLAG_USE_EXISTING Pokud je to možné, opakovaně používat existující připojení k serveru na nový `FindFile` požadavky, místo vytvoření nové relace pro každý požadavek.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Poznámky

Po volání `FindFile` načíst první objekt gopher, můžete volat [FindNextFile](#findnextfile) načíst soubory následné gopher.

##  <a name="findnextfile"></a>  CGopherFileFind::FindNextFile

Voláním této členské funkce pokračujte hledání souborů začal s voláním [CGopherFileFind::FindFile](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud existují další soubory. nula, pokud je nalezen soubor jako poslední v adresáři nebo pokud došlo k chybě. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror). Pokud je nalezen soubor poslední soubor v adresáři nebo neexistuje odpovídající soubory najdete, `GetLastError` funkce vrátí ERROR_NO_MORE_FILES.

##  <a name="getcreationtime"></a>  CGopherFileFind::GetCreationTime

Získá čas vytvoření pro aktuální soubor.

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

Nenulové, pokud je úspěšná. 0, pokud není úspěšné. `GetCreationTime` Vrátí hodnotu 0, pouze pokud [FindNextFile](#findnextfile) nikdy byla volána na tomto `CGopherFileFind` objektu.

### <a name="remarks"></a>Poznámky

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetCreationTime`.

> [!NOTE]
>  Ne všechny systémy souborů implementace časové razítko vrácená touto funkcí pomocí stejné sémantiky. Tato funkce může vrátit stejnou hodnotu vrácenou příkazem jiné časové razítko funkce, pokud podkladový systém souborů nebo server nepodporuje atribut doby uchování. Zobrazit [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) strukturu pro informace o formáty času. U některých operačních systémů vrácený čas je v čase místní zóny na počítači se, že se soubor nachází. Zobrazit Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) rozhraní API pro další informace.

##  <a name="getlastaccesstime"></a>  CGopherFileFind::GetLastAccessTime

Získá čas posledního přístupu k souboru.

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

Nenulové, pokud je úspěšná. 0, pokud není úspěšné. `GetLastAccessTime` Vrátí hodnotu 0, pouze pokud [FindNextFile](#findnextfile) nikdy byla volána na tomto `CGopherFileFind` objektu.

### <a name="remarks"></a>Poznámky

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetLastAccessTime`.

> [!NOTE]
>  Ne všechny systémy souborů implementace časové razítko vrácená touto funkcí pomocí stejné sémantiky. Tato funkce může vrátit stejnou hodnotu vrácenou příkazem jiné časové razítko funkce, pokud podkladový systém souborů nebo server nepodporuje atribut doby uchování. Zobrazit [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) strukturu pro informace o formáty času. U některých operačních systémů vrácený čas je v čase místní zóny na počítači se, že se soubor nachází. Zobrazit Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) rozhraní API pro další informace.

##  <a name="getlastwritetime"></a>  CGopherFileFind::GetLastWriteTime

Získá čas poslední změny souboru.

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

Nenulové, pokud je úspěšná. 0, pokud není úspěšné. `GetLastWriteTime` Vrátí hodnotu 0, pouze pokud [FindNextFile](#findnextfile) nikdy byla volána na tomto `CGopherFileFind` objektu.

### <a name="remarks"></a>Poznámky

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `GetLastWriteTime`.

> [!NOTE]
>  Ne všechny systémy souborů implementace časové razítko vrácená touto funkcí pomocí stejné sémantiky. Tato funkce může vrátit stejnou hodnotu vrácenou příkazem jiné časové razítko funkce, pokud podkladový systém souborů nebo server nepodporuje atribut doby uchování. Zobrazit [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) strukturu pro informace o formáty času. U některých operačních systémů vrácený čas je v čase místní zóny na počítači se, že se soubor nachází. Zobrazit Win32 [FileTimeToLocalFileTime](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime) rozhraní API pro další informace.

##  <a name="getlength"></a>  CGopherFileFind::GetLength

Voláním této členské funkce, chcete-li získat délku v bajtech nalezený soubor.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka v bajtech, souboru nalezen.

### <a name="remarks"></a>Poznámky

`GetLength` používá strukturu Win32 [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) má být získána hodnota velikosti souboru v bajtech.

> [!NOTE]
>  Od verze MFC 7.0 `GetLength` podporuje 64bitové celočíselné typy. Dříve existující kód vytvořený s touto novější verzí knihovny může vést ke zkrácení upozornění.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) (implementaci základní třídy).

##  <a name="getlocator"></a>  CGopherFileFind::GetLocator

Zavolat tuto členskou funkci zobrazíte [cgopherlocator –](../../mfc/reference/cgopherlocator-class.md) objekt, který [FindFile](#findfile) používá k vyhledání souboru gopher.

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>Návratová hodnota

A `CGopherLocator` objektu.

##  <a name="getscreenname"></a>  CGopherFileFind::GetScreenName

Voláním této členské funkce a získat tak název obrazovky gopher.

```
CString GetScreenName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název obrazovky gopher.

##  <a name="isdots"></a>  CGopherFileFind::IsDots

Testy pro aktuální adresář a nadřazené značky adresáře při procházení souborů.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je nalezen soubor má název "."nebo"..", což znamená, že nalezený soubor je ve skutečnosti adresář. Jinak 0.

### <a name="remarks"></a>Poznámky

Je nutné volat [FindNextFile](#findnextfile) alespoň jednou před voláním `IsDots`.

## <a name="see-also"></a>Viz také:

[CFileFind – třída](../../mfc/reference/cfilefind-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind – třída](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind – třída](../../mfc/reference/cfilefind-class.md)<br/>
[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile – třída](../../mfc/reference/chttpfile-class.md)
