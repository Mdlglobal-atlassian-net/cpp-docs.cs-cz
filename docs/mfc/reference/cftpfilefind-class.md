---
title: Třída CFtpFileFind
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
ms.openlocfilehash: cf4afb4a683c2d0cf5f2977107d02ee300a53cb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373744"
---
# <a name="cftpfilefind-class"></a>Třída CFtpFileFind

Pomáhá při vyhledávání souborů v Internetu na serverech FTP.

## <a name="syntax"></a>Syntaxe

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|Vytvoří `CFtpFileFind` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CFtpFileFind::FindFile](#findfile)|Vyhledá soubor na serveru FTP.|
|[CFtpFileFind::FindNextFile](#findnextfile)|Pokračuje v hledání souborů z předchozího volání [FindFile](#findfile).|
|[CFtpFileFind::GetFileURL](#getfileurl)|Získá adresu URL, včetně cesty, nalezeného souboru.|

## <a name="remarks"></a>Poznámky

`CFtpFileFind`Zahrnuje členské funkce, které zahajují hledání, vyhledání souboru a vrácení adresy URL nebo jiných popisných informací o souboru.

Mezi další třídy knihovny MFC určené pro vyhledávání v Internetu a místních souborech patří [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) a [CFileFind](../../mfc/reference/cfilefind-class.md). Společně `CFtpFileFind`s aplikacemi poskytují tyto třídy bezproblémový mechanismus pro klienta k vyhledání určitých souborů bez ohledu na serverový protokol nebo typ souboru (místní počítač nebo vzdálený server). Všimněte si, že neexistuje žádná třída knihovny MFC pro vyhledávání na serverech HTTP, protože protokol HTTP nepodporuje přímou manipulaci se soubory požadovanou pro vyhledávání.

Další informace o použití `CFtpFileFind` a další chod wininet naleznete v článku [Internetové programování s WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="example"></a>Příklad

Následující kód ukazuje, jak vytvořit výčet všech souborů v aktuálním adresáři serveru FTP.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="cftpfilefindcftpfilefind"></a><a name="cftpfilefind"></a>CFtpFileFind::CFtpFileFind

Tato členská funkce je `CFtpFileFind` volána k vytvoření objektu.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pPřipojení*<br/>
Ukazatel na `CFtpConnection` objekt. Připojení FTP můžete získat voláním [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).

*dwKontext*<br/>
Identifikátor kontextu pro `CFtpFileFind` objekt. Další informace o tomto parametru naleznete v **tématu Poznámky.**

### <a name="remarks"></a>Poznámky

Výchozí hodnota pro *dwContext* je odeslána `CFtpFileFind` knihovnou MFC do objektu z objektu [CInternetSession,](../../mfc/reference/cinternetsession-class.md) který `CFtpFileFind` objekt vytvořil. Můžete přepsat výchozí nastavení identifikátoru kontextu na hodnotu podle vašeho výběru. Identifikátor kontextu je [vrácena CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav na objekt, se kterým je identifikován. Další informace o identifikátoru kontextu naleznete v článku [První kroky Internetu: WinInet.](../../mfc/wininet-basics.md)

### <a name="example"></a>Příklad

  Podívejte se na příklad v přehledu třídy dříve v tomto tématu.

## <a name="cftpfilefindfindfile"></a><a name="findfile"></a>CFtpFileFind::FindFile

Voláním této členské funkce vyhledejte soubor FTP.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Parametry

*název pstr*<br/>
Ukazatel na řetězec obsahující název souboru, který chcete najít. Pokud null, volání provede hledání zástupnými symboly (*).

*dwFlags*<br/>
Příznaky popisující, jak zpracovat tuto relaci. Tyto příznaky lze kombinovat s bitovým operátorem OR (&#124;) a jsou následující:

- INTERNET_FLAG_RELOAD Získejte data z drátu, i když je místně uložena do mezipaměti. Toto je výchozí příznak.

- INTERNET_FLAG_DONT_CACHE Neukládat data do mezipaměti, místně ani v žádné braně.

- INTERNET_FLAG_RAW_DATA Přepsat výchozí vrátit nezpracovaná data [(WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw) struktury pro FTP).

- INTERNET_FLAG_SECURE Zabezpečuje transakce na lince pomocí sstojánky vrstvy nebo PCT. Tento příznak se vztahuje pouze na požadavky HTTP.

- INTERNET_FLAG_EXISTING_CONNECT Pokud je to možné, znovu použijte `FindFile` existující připojení k serveru pro nové požadavky namísto vytvoření nové relace pro každý požadavek.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="remarks"></a>Poznámky

Po `FindFile` volání k načtení prvního souboru FTP můžete volat [FindNextFile](#findnextfile) k načtení následných souborů FTP.

### <a name="example"></a>Příklad

  Podívejte se na předchozí příklad v tomto tématu.

## <a name="cftpfilefindfindnextfile"></a><a name="findnextfile"></a>CFtpFileFind::FindNextFile

Volání této členské funkce pokračovat hledání souborů začal o volání do funkce člena [FindFile.](#findfile)

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud existuje více souborů; nula, pokud je nalezený soubor poslední v adresáři nebo pokud došlo k chybě. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror). Pokud je nalezený soubor posledním souborem v adresáři nebo pokud `GetLastError` nelze nalézt žádné odpovídající soubory, vrátí funkce ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Poznámky

Tuto funkci je nutné volat alespoň jednou před voláním libovolné funkce atributu (viz [CFileFind::FindNextFile).](../../mfc/reference/cfilefind-class.md#findnextfile)

`FindNextFile`zabalí funkci Win32 [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew).

### <a name="example"></a>Příklad

  Viz příklad dříve v tomto tématu.

## <a name="cftpfilefindgetfileurl"></a><a name="getfileurl"></a>CFtpFileFind::GetFileURL

Volánítéto členské funkce získat adresu URL zadaného souboru.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Návratová hodnota

Soubor a cesta univerzálního lokátoru prostředků (URL).

### <a name="remarks"></a>Poznámky

`GetFileURL`je podobná členské funkci [CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)s tím rozdílem, `ftp://moose/dir/file.txt`že vrátí adresu URL ve formuláři .

## <a name="see-also"></a>Viz také

[CFileFind – třída](../../mfc/reference/cfilefind-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile – třída](../../mfc/reference/chttpfile-class.md)
