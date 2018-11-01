---
title: Cftpfilefind – třída
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
ms.openlocfilehash: 72d1eb147f8d7387a04f25cc008cc4d4638ba691
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548223"
---
# <a name="cftpfilefind-class"></a>Cftpfilefind – třída

Pomáhá při hledání internetových souborů na serverech FTP.

## <a name="syntax"></a>Syntaxe

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|Vytvoří `CFtpFileFind` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFtpFileFind::FindFile](#findfile)|Vyhledá soubor na serveru FTP.|
|[CFtpFileFind::FindNextFile](#findnextfile)|Pokračuje v hledání souborů z předchozího volání [FindFile](#findfile).|
|[CFtpFileFind::GetFileURL](#getfileurl)|Získá adresu URL, včetně cesty souboru nalezen.|

## <a name="remarks"></a>Poznámky

`CFtpFileFind` zahrnuje členské funkce, které začínají vyhledávání, vyhledání souboru a vrátí adresu URL nebo jiné popisné informace o souboru.

Jiné třídy knihovny MFC navržené pro Internet a prohledávat místní soubor k zahrnutí [cgopherfilefind –](../../mfc/reference/cgopherfilefind-class.md) a [cfilefind –](../../mfc/reference/cfilefind-class.md). Spolu s `CFtpFileFind`, tyto třídy poskytnout bezproblémové mechanismus pro klienta vyhledat konkrétní soubory, bez ohledu na to, server protokolu nebo typ souboru (místní počítač nebo na vzdálený server). Všimněte si, že neexistuje žádná třída knihovny MFC pro vyhledávání na serverech HTTP, protože HTTP nepodporuje manipulace s přímým přístupem souboru vyžadované pro hledání.

Další informace o tom, jak používat `CFtpFileFind` a jiných tříd WinInet, najdete v článku [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="example"></a>Příklad

Následující kód ukazuje, jak vytvořit výčet všech souborů v aktuálním adresáři serveru FTP.

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cfilefind –](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

##  <a name="cftpfilefind"></a>  CFtpFileFind::CFtpFileFind

Tato členská funkce je volána k sestavení kompletních `CFtpFileFind` objektu.

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pConnection*<br/>
Ukazatel `CFtpConnection` objektu. Připojení k serveru FTP lze získat voláním [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).

*dwContext*<br/>
Identifikátor kontextu `CFtpFileFind` objektu. Zobrazit **poznámky** Další informace o tomto parametru.

### <a name="remarks"></a>Poznámky

Výchozí hodnota pro *dwContext* odesílají knihovny MFC pro `CFtpFileFind` objektu z [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objekt vytvořený `CFtpFileFind` objektu. Můžete přepsat výchozí identifikátor kontextu nastavena na hodnotu podle vašeho výběru. Identifikátor kontextu se vrátí do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav objektu, pomocí kterého je identifikován. Najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o identifikátor kontextu.

### <a name="example"></a>Příklad

  Podívejte se na příklad v přehledu třídy dříve v tomto tématu.

##  <a name="findfile"></a>  CFtpFileFind::FindFile

Voláním této členské funkce k vyhledání souboru protokolu FTP.

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>Parametry

*pstrName*<br/>
Ukazatel na řetězec obsahující název souboru, který má najít. Pokud má hodnotu NULL, provede volání hledání pomocí zástupných znaků (*).

*dwFlags*<br/>
Příznaky popisující, jak zpracovat tuto relaci. Tyto příznaky je možné kombinovat s bitový operátor OR (&#124;) a jsou následující:

- INTERNET_FLAG_RELOAD získat data z přenosu i v případě, že je v místní mezipaměti. Toto je výchozí příznak.

- INTERNET_FLAG_DONT_CACHE Neukládat do mezipaměti dat, místně nebo v žádné brány.

- INTERNET_FLAG_RAW_DATA přepsat výchozí nastavení pro vrácení nezpracovaných dat ( [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktury protokolu FTP).

- Zabezpečuje INTERNET_FLAG_SECURE transakce na lince (Secure Sockets Layer) nebo v PROC. Tento příznak se vztahuje pouze na požadavky HTTP.

- INTERNET_FLAG_EXISTING_CONNECT Pokud je to možné, opakovaně používat existující připojení k serveru na nový `FindFile` požadavky na místo vytvoření nové relace pro každý požadavek.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="remarks"></a>Poznámky

Po volání `FindFile` načíst první soubor protokolu FTP, můžete volat [FindNextFile](#findnextfile) načíst následující soubory protokolu FTP.

### <a name="example"></a>Příklad

  Podívejte se na předchozí příklad v tomto tématu.

##  <a name="findnextfile"></a>  CFtpFileFind::FindNextFile

Voláním této členské funkce pokračujte hledání souborů začal s voláním [FindFile](#findfile) členskou funkci.

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud existují další soubory. nula, pokud je nalezen soubor jako poslední v adresáři nebo pokud došlo k chybě. Chcete-li získat rozšířené informace o chybě, zavolejte funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360). Pokud je nalezen soubor poslední soubor v adresáři nebo neexistuje odpovídající soubory najdete, `GetLastError` funkce vrátí ERROR_NO_MORE_FILES.

### <a name="remarks"></a>Poznámky

Lze zavolat tuto funkci alespoň jednou před voláním jakékoli funkce atribut (viz [CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).

`FindNextFile` zabalí funkci Win32 [FindNextFile](/windows/desktop/api/fileapi/nf-fileapi-findnextfilea).

### <a name="example"></a>Příklad

  Podívejte se na příklad výše v tomto tématu.

##  <a name="getfileurl"></a>  CFtpFileFind::GetFileURL

Voláním této členské funkce získat adresu URL zadaného souboru.

```
CString GetFileURL() const;
```

### <a name="return-value"></a>Návratová hodnota

Souboru a cesty Universal Resource Locator (URL).

### <a name="remarks"></a>Poznámky

`GetFileURL` se podobá na členskou funkci [CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath), s tím rozdílem, že vrátí adresu URL ve formě `ftp://moose/dir/file.txt`.

## <a name="see-also"></a>Viz také

[CFileFind – třída](../../mfc/reference/cfilefind-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind – třída](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile – třída](../../mfc/reference/chttpfile-class.md)
