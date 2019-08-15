---
title: CGopherFileFind – třída
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
ms.openlocfilehash: 55c40fc04934f00ccb541a01cce611d9532bee1a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506176"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind – třída

Pomůcky při hledání internetových souborů na serverech Gopher.

> [!NOTE]
>  Třídy `CGopherConnection` `CGopherFile` ,`CGopherLocator` , a jejich členové jsou zastaralí, protože nefungují na platformě Windows XP, ale budou fungovat i na `CGopherFileFind`starších platformách.

## <a name="syntax"></a>Syntaxe

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|`CGopherFileFind` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CGopherFileFind:: FindFile –](#findfile)|Najde soubor na serveru Gopher.|
|[CGopherFileFind::FindNextFile](#findnextfile)|Pokračuje v hledání souborů od předchozího volání [FindFile –](#findfile).|
|[CGopherFileFind::GetCreationTime](#getcreationtime)|Získá čas vytvoření zadaného souboru.|
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|Získá čas posledního otevření zadaného souboru.|
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|Získá čas posledního zápisu zadaného souboru do.|
|[CGopherFileFind:: GetLength](#getlength)|Získá délku nalezeného souboru v bajtech.|
|[CGopherFileFind:: GetLocator](#getlocator)|`CGopherLocator` Získat objekt.|
|[CGopherFileFind:: getscreen](#getscreenname)|Získá název obrazovky protokolu Gopher.|
|[CGopherFileFind::-tečky](#isdots)|Testuje aktuální adresář a značky nadřazených adresářů během iterace souborů.|

## <a name="remarks"></a>Poznámky

`CGopherFileFind`zahrnuje členské funkce, které zahájí hledání, vyhledá soubor a vrátí adresu URL souboru.

Mezi další třídy knihovny MFC, které jsou určeny pro hledání na internetu a místní soubory, patří [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) a [CFileFind](../../mfc/reference/cfilefind-class.md). Spolu s `CGopherFileFind`nástrojem poskytují tyto třídy bezproblémové mechanizmus pro uživatele, aby našli konkrétní soubory bez ohledu na protokol serveru, typ souboru nebo umístění (buď místní počítač nebo vzdálený server). Všimněte si, že pro hledání na serverech HTTP není k dispozici žádná třída knihovny MFC, protože protokol HTTP nepodporuje přímou manipulaci se soubory požadovanou hledáním.

> [!NOTE]
> `CGopherFileFind`nepodporuje následující členské funkce své základní třídy [CFileFind](../../mfc/reference/cfilefind-class.md):

- [GetRoot selhalo](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

Kromě toho, když se používá `CGopherFileFind`s `CFileFind` , je členská funkce vždycky false. [](../../mfc/reference/cfilefind-class.md#isdots)

Další informace o tom, jak používat `CGopherFileFind` a jiné třídy WinInet, najdete v článku [internetové programování s](../../mfc/win32-internet-extensions-wininet.md)rozhraním Wininet.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet. h

##  <a name="cgopherfilefind"></a>CGopherFileFind::CGopherFileFind

Tato členská funkce je volána k vytvoření `CGopherFileFind` objektu.

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pConnection*<br/>
Ukazatel na objekt [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) .

*dwContext*<br/>
Identifikátor kontextu operace. Další informace o *dwContext*najdete v tématu **poznámky** .

### <a name="remarks"></a>Poznámky

Výchozí hodnota pro *dwContext* je odeslána knihovnou MFC do `CGopherFileFind` objektu z objektu [](../../mfc/reference/cinternetsession-class.md) `CGopherFileFind` CInternetSession, který objekt vytvořil. Při vytváření `CGopherFileFind` objektu můžete přepsat výchozí hodnotu pro nastavení identifikátoru kontextu na hodnotu, kterou zvolíte. Identifikátor kontextu je vrácen do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , aby poskytoval stav objektu, se kterým je identifikován. Přečtěte si [článek Internet First Step: Rozhraní](../../mfc/wininet-basics.md) WinInet pro další informace o identifikátoru kontextu.

##  <a name="findfile"></a>CGopherFileFind:: FindFile –

Chcete-li najít soubor protokolu Gopher, zavolejte tuto členskou funkci.

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
Odkaz na objekt [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

*pstrString*<br/>
Ukazatel na řetězec obsahující název souboru.

*dwFlags*<br/>
Příznaky popisující, jak tuto relaci zpracovat. Platné příznaky jsou:

- INTERNET_FLAG_RELOAD získá data ze vzdáleného serveru i v případě, že je místně uložené v mezipaměti.

- INTERNET_FLAG_DONT_CACHE data Neukládat do mezipaměti, a to buď místně, nebo v žádné bráně.

- INTERNET_FLAG_SECURE vyžadují zabezpečené transakce na lince s SSL (Secure Sockets Layer) nebo PCT. Tento příznak se vztahuje pouze na požadavky HTTP.

- INTERNET_FLAG_USE_EXISTING Pokud je to možné, znovu znovu použijte existující připojení na server `FindFile` pro nové požadavky, místo aby se vytvořila nová relace pro každý požadavek.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Poznámky

Po volání `FindFile` načtení prvního objektu gopher můžete volat [FindNextFile](#findnextfile) a načíst další soubory Gopher.

##  <a name="findnextfile"></a>CGopherFileFind::FindNextFile

Zavolejte tuto členskou funkci, aby bylo možné pokračovat v hledání souborů s voláním [CGopherFileFind:: FindFile –](#findfile).

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud existuje více souborů; nula, pokud se soubor našel jako poslední v adresáři, nebo pokud došlo k chybě Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Pokud je nalezen poslední soubor v adresáři, nebo pokud nelze nalézt žádné vyhovující soubory, `GetLastError` vrátí funkce ERROR_NO_MORE_FILES.

##  <a name="getcreationtime"></a>CGopherFileFind::GetCreationTime

Získá čas vytvoření aktuálního souboru.

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

Nenulové, pokud bylo úspěšné; 0, pokud neproběhla úspěšně. `GetCreationTime`Vrátí hodnotu 0 pouze v případě, že [FindNextFile](#findnextfile) nebyl nikdy `CGopherFileFind` volán u tohoto objektu.

### <a name="remarks"></a>Poznámky

Před voláním [](#findnextfile) `GetCreationTime`je nutné volat FindNextFile alespoň jednou.

> [!NOTE]
>  Ne všechny systémy souborů používají stejnou sémantiku k implementaci časového razítka vráceného touto funkcí. Tato funkce může vracet stejnou hodnotu vrácenou jinými funkcemi časového razítka, Pokud podkladový systém souborů nebo server nepodporuje zachování atributu Time. Informace o formátech času najdete v [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktuře. V některých operačních systémech byl vrácený čas v časovém pásmu, které se nachází v místním počítači, kde se nachází soubor. Další informace najdete v tématu rozhraní Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API.

##  <a name="getlastaccesstime"></a>CGopherFileFind::GetLastAccessTime

Získá čas posledního otevření zadaného souboru.

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

Nenulové, pokud bylo úspěšné; 0, pokud neproběhla úspěšně. `GetLastAccessTime`Vrátí hodnotu 0 pouze v případě, že [FindNextFile](#findnextfile) nebyl nikdy `CGopherFileFind` volán u tohoto objektu.

### <a name="remarks"></a>Poznámky

Před voláním [](#findnextfile) `GetLastAccessTime`je nutné volat FindNextFile alespoň jednou.

> [!NOTE]
>  Ne všechny systémy souborů používají stejnou sémantiku k implementaci časového razítka vráceného touto funkcí. Tato funkce může vracet stejnou hodnotu vrácenou jinými funkcemi časového razítka, Pokud podkladový systém souborů nebo server nepodporuje zachování atributu Time. Informace o formátech času najdete v [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktuře. V některých operačních systémech byl vrácený čas v časovém pásmu, které se nachází v místním počítači, kde se nachází soubor. Další informace najdete v tématu rozhraní Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API.

##  <a name="getlastwritetime"></a>CGopherFileFind::GetLastWriteTime

Získá čas poslední změny souboru.

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

Nenulové, pokud bylo úspěšné; 0, pokud neproběhla úspěšně. `GetLastWriteTime`Vrátí hodnotu 0 pouze v případě, že [FindNextFile](#findnextfile) nebyl nikdy `CGopherFileFind` volán u tohoto objektu.

### <a name="remarks"></a>Poznámky

Před voláním [](#findnextfile) `GetLastWriteTime`je nutné volat FindNextFile alespoň jednou.

> [!NOTE]
>  Ne všechny systémy souborů používají stejnou sémantiku k implementaci časového razítka vráceného touto funkcí. Tato funkce může vracet stejnou hodnotu vrácenou jinými funkcemi časového razítka, Pokud podkladový systém souborů nebo server nepodporuje zachování atributu Time. Informace o formátech času najdete v [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktuře. V některých operačních systémech byl vrácený čas v časovém pásmu, které se nachází v místním počítači, kde se nachází soubor. Další informace najdete v tématu rozhraní Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API.

##  <a name="getlength"></a>CGopherFileFind:: GetLength

Voláním této členské funkce získáte délku nalezeného souboru v bajtech.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka nalezeného souboru v bajtech

### <a name="remarks"></a>Poznámky

`GetLength`používá strukturu Win32 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) k získání hodnoty velikosti souboru v bajtech.

> [!NOTE]
>  V případě knihovny MFC 7,0 `GetLength` podporuje typy celočíselného celého čísla (64). Dříve existující kód sestavený pomocí této novější verze knihovny může způsobit upozornění na zkrácení.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CFile –:: GetLength](../../mfc/reference/cfile-class.md#getlength) (implementace základní třídy).

##  <a name="getlocator"></a>CGopherFileFind:: GetLocator

Voláním této členské funkce získáte objekt [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) , který [FindFile –](#findfile) používá k vyhledání souboru protokolu Gopher.

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>Návratová hodnota

A `CGopherLocator` objektu.

##  <a name="getscreenname"></a>CGopherFileFind:: getscreen

Chcete-li získat název obrazovky protokolu Gopher, zavolejte tuto členskou funkci.

```
CString GetScreenName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název obrazovky protokolu Gopher

##  <a name="isdots"></a>CGopherFileFind::-tečky

Testuje aktuální adresář a značky nadřazených adresářů během iterace souborů.

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud má nalezený soubor název "." nebo "..", který označuje, že nalezený soubor je ve skutečnosti adresář. V opačném případě 0.

### <a name="remarks"></a>Poznámky

Před voláním [](#findnextfile) `IsDots`je nutné volat FindNextFile alespoň jednou.

## <a name="see-also"></a>Viz také:

[CFileFind – třída](../../mfc/reference/cfilefind-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind – třída](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind – třída](../../mfc/reference/cfilefind-class.md)<br/>
[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile – třída](../../mfc/reference/chttpfile-class.md)
