---
title: CFtpFileFind – třída
ms.date: 11/04/2016
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
helpviewer_keywords:
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
ms.openlocfilehash: 2f4a394e29be135cac95edf6f504d8b066f53414
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866295"
---
# <a name="cftpfilefind-class"></a>CFtpFileFind – třída

Pomůcky při hledání internetových souborů na serverech FTP.

## <a name="syntax"></a>Syntaxe

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|Vytvoří objekt `CFtpFileFind`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFtpFileFind:: FindFile –](#findfile)|Najde soubor na serveru FTP.|
|[CFtpFileFind::FindNextFile](#findnextfile)|Pokračuje v hledání souborů od předchozího volání [FindFile –](#findfile).|
|[CFtpFileFind::GetFileURL](#getfileurl)|Získá adresu URL, včetně cesty, nalezeného souboru.|

## <a name="remarks"></a>Poznámky

`CFtpFileFind` zahrnují členské funkce, které zahájí hledání, vyhledají soubor a vrátí adresu URL nebo jiné popisné informace o souboru.

Mezi další třídy knihovny MFC, které jsou určeny pro hledání na internetu a místní soubory, patří [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) a [CFileFind](../../mfc/reference/cfilefind-class.md). Spolu s `CFtpFileFind`poskytují tyto třídy bezproblémové mechanismy, které klientovi umožní najít konkrétní soubory bez ohledu na protokol serveru nebo typ souboru (buď místní počítač nebo vzdálený server). Všimněte si, že pro hledání na serverech HTTP neexistuje žádná třída knihovny MFC, protože protokol HTTP nepodporuje přímou manipulaci se soubory nutnou k vyhledávání.

Další informace o tom, jak používat `CFtpFileFind` a jiné třídy WinInet, najdete v článku [internetové programování s](../../mfc/win32-internet-extensions-wininet.md)rozhraním Wininet.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak vytvořit výčet všech souborů v aktuálním adresáři serveru FTP.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet. h

##  <a name="cftpfilefind"></a>CFtpFileFind::CFtpFileFind

Tato členská funkce je volána k vytvoření objektu `CFtpFileFind`.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pConnection*<br/>
Ukazatel na objekt `CFtpConnection`. Připojení FTP můžete získat voláním [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).

*dwContext*<br/>
Identifikátor kontextu pro objekt `CFtpFileFind`. Další informace o tomto parametru najdete v části **poznámky** .

### <a name="remarks"></a>Poznámky

Výchozí hodnota pro *dwContext* je odeslána knihovnou MFC do objektu `CFtpFileFind` z objektu [CInternetSession](../../mfc/reference/cinternetsession-class.md) , který vytvořil objekt `CFtpFileFind`. Můžete přepsat výchozí nastavení a nastavit identifikátor kontextu na hodnotu, kterou zvolíte. Identifikátor kontextu je vrácen do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , aby poskytoval stav objektu, se kterým je identifikován. Další informace o identifikátoru kontextu najdete v článku [Internet First Steps: WinInet](../../mfc/wininet-basics.md) .

### <a name="example"></a>Příklad

  Podívejte se na příklad v přehledu třídy výše v tomto tématu.

##  <a name="findfile"></a>CFtpFileFind:: FindFile –

Chcete-li najít soubor FTP, zavolejte tuto členskou funkci.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Parametry

*pstrName*<br/>
Ukazatel na řetězec obsahující název souboru, který se má najít. Pokud je hodnota NULL, volání provede hledání pomocí zástupných znaků (*).

*dwFlags*<br/>
Příznaky popisující, jak tuto relaci zpracovat. Tyto příznaky lze kombinovat s bitovým operátorem OR (&#124;) a jsou následující:

- INTERNET_FLAG_RELOAD získat data z kabelu i v případě, že je místně Uloženo v mezipaměti. Toto je výchozí příznak.

- INTERNET_FLAG_DONT_CACHE data Neukládat do mezipaměti, a to buď místně, nebo v bráně.

- INTERNET_FLAG_RAW_DATA přepsat výchozí hodnotu, aby vracela nezpracovaná data ( [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktury pro FTP).

- INTERNET_FLAG_SECURE zabezpečuje transakce na lince pomocí SSL (Secure Sockets Layer) nebo PCT. Tento příznak se vztahuje pouze na požadavky HTTP.

- Pokud je to možné, INTERNET_FLAG_EXISTING_CONNECT znovu použít stávající připojení k serveru pro nové žádosti `FindFile` místo vytvoření nové relace pro každý požadavek.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Poznámky

Po volání `FindFile` k načtení prvního souboru FTP můžete volat [FindNextFile](#findnextfile) a načíst další soubory FTP.

### <a name="example"></a>Příklad

  Viz předchozí příklad v tomto tématu.

##  <a name="findnextfile"></a>CFtpFileFind::FindNextFile

Chcete-li pokračovat v hledání souborů pomocí volání členské funkce [FindFile –](#findfile) , zavolejte tuto členskou funkci.

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud existuje více souborů; nula, pokud se soubor našel jako poslední v adresáři, nebo pokud došlo k chybě Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Pokud je nalezen poslední soubor v adresáři, nebo pokud nelze nalézt žádné vyhovující soubory, funkce `GetLastError` vrátí ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Poznámky

Před voláním libovolné funkce atributu je nutné zavolat tuto funkci alespoň jednou (viz [CFileFind:: FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).

`FindNextFile` zabalí [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew)funkce Win32.

### <a name="example"></a>Příklad

  Podívejte se na příklad výše v tomto tématu.

##  <a name="getfileurl"></a>CFtpFileFind::GetFileURL

Zavolejte tuto členskou funkci, aby se získala adresa URL zadaného souboru.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Návratová hodnota

Soubor a cesta k adrese URL (Universal Resource Locator).

### <a name="remarks"></a>Poznámky

`GetFileURL` je podobná členské funkci [CFileFind:: GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)s tím rozdílem, že vrátí adresu URL ve formuláři `ftp://moose/dir/file.txt`.

## <a name="see-also"></a>Viz také

[CFileFind – třída](../../mfc/reference/cfilefind-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind – třída](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile – třída](../../mfc/reference/chttpfile-class.md)
