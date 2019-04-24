---
title: CFtpConnection Class
ms.date: 11/04/2016
f1_keywords:
- CFtpConnection
- AFXINET/CFtpConnection
- AFXINET/CFtpConnection::CFtpConnection
- AFXINET/CFtpConnection::Command
- AFXINET/CFtpConnection::CreateDirectory
- AFXINET/CFtpConnection::GetCurrentDirectory
- AFXINET/CFtpConnection::GetCurrentDirectoryAsURL
- AFXINET/CFtpConnection::GetFile
- AFXINET/CFtpConnection::OpenFile
- AFXINET/CFtpConnection::PutFile
- AFXINET/CFtpConnection::Remove
- AFXINET/CFtpConnection::RemoveDirectory
- AFXINET/CFtpConnection::Rename
- AFXINET/CFtpConnection::SetCurrentDirectory
helpviewer_keywords:
- CFtpConnection [MFC], CFtpConnection
- CFtpConnection [MFC], Command
- CFtpConnection [MFC], CreateDirectory
- CFtpConnection [MFC], GetCurrentDirectory
- CFtpConnection [MFC], GetCurrentDirectoryAsURL
- CFtpConnection [MFC], GetFile
- CFtpConnection [MFC], OpenFile
- CFtpConnection [MFC], PutFile
- CFtpConnection [MFC], Remove
- CFtpConnection [MFC], RemoveDirectory
- CFtpConnection [MFC], Rename
- CFtpConnection [MFC], SetCurrentDirectory
ms.assetid: 5e3a0501-8893-49cf-a3d5-0628d8d6b936
ms.openlocfilehash: 12ef4de16279c5c2033a95df5928a6dfb7a2a652
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62181974"
---
# <a name="cftpconnection-class"></a>CFtpConnection Class

Spravuje FTP připojení k internetovému serveru a umožňuje přímou manipulaci s adresářů a souborů na tomto serveru.

## <a name="syntax"></a>Syntaxe

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CFtpConnection::CFtpConnection](#cftpconnection)|Vytvoří `CFtpConnection` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFtpConnection::Command](#command)|Odešle příkaz přímo na FTP server.|
|[CFtpConnection::CreateDirectory](#createdirectory)|Vytvoří adresář na serveru.|
|[CFtpConnection::GetCurrentDirectory](#getcurrentdirectory)|Získá aktuální adresář pro toto připojení.|
|[CFtpConnection::GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|Získá aktuální adresář pro toto připojení jako adresu URL.|
|[CFtpConnection::GetFile](#getfile)|Načte soubor z připojeného serveru.|
|[CFtpConnection::OpenFile](#openfile)|Otevře soubor na připojeném serveru.|
|[CFtpConnection::PutFile](#putfile)|Umístí soubor na serveru.|
|[CFtpConnection::Remove](#remove)|Odebere soubor ze serveru.|
|[CFtpConnection::RemoveDirectory](#removedirectory)|Odebere zadaný adresář ze serveru.|
|[CFtpConnection::Rename](#rename)|Přejmenuje soubor na serveru.|
|[CFtpConnection::SetCurrentDirectory](#setcurrentdirectory)|Nastaví aktuální adresář serveru FTP.|

## <a name="remarks"></a>Poznámky

FTP je jednou tři služeb sítě Internet rozpoznat pomocí tříd WinInet knihovny MFC.

Ke komunikaci se serverem FTP Internet, musíte nejprve vytvořit instanci [cinternetsession –](../../mfc/reference/cinternetsession-class.md)a pak vytvořte `CFtpConnection` objektu. Nikdy nevytvářejte `CFtpConnection` objektu přímo; místo toho volat [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), která vytvoří `CFtpConnection` objekt a vrátí ukazatel na něj.

Další informace o tom, `CFtpConnection` funguje s jinými třídami MFC Internetu najdete v článku [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md). Další informace o komunikaci s další dvě jako podporované služby, HTTP a gopher, viz třídy [chttpconnection –](../../mfc/reference/chttpconnection-class.md) a [cgopherconnection –](../../mfc/reference/cgopherconnection-class.md).

## <a name="example"></a>Příklad

  Podívejte se na příklad v [cftpfilefind –](../../mfc/reference/cftpfilefind-class.md) přehledu třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

##  <a name="cftpconnection"></a>  CFtpConnection::CFtpConnection

Tato členská funkce je volána k sestavení kompletních `CFtpConnection` objektu.

```
CFtpConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CFtpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 0,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>Parametry

*pSession*<br/>
Ukazatel na související [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objektu.

*hConnected*<br/>
Popisovač Windows aktuální relace Internet.

*pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru FTP.

*dwContext*<br/>
Identifikátor kontextu operace. *dwContext* identifikuje informace o stavu operace vracené [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). Výchozí hodnota je nastavená na 1; Můžete však explicitně přiřadit konkrétní kontext ID operace. Objekt a veškerou práci, kterou provádí bude spojená s ID tohoto kontextu.

*pstrUserName*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje jméno uživatele k přihlášení. Pokud má hodnotu NULL, výchozí hodnota je anonymous.

*pstrPassword*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje heslo pro použití k protokolování. Pokud mají oba *pstrPassword* a *pstrUserName* hodnotu Null, je výchozí heslo anonymní uživatelské jméno e-mailu. Pokud *pstrPassword* má hodnotu NULL (nebo prázdný řetězec), ale *pstrUserName* nemá hodnotu NULL, prázdné heslo se používá. Následující tabulka popisuje chování pro čtyři možných nastavení *pstrUserName* a *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Uživatelské jméno odeslané na FTP server|Heslo odeslaných na FTP server|
|--------------------|--------------------|---------------------------------|---------------------------------|
|Hodnotu NULL nebo ""|Hodnotu NULL nebo ""|"anonymní"|Uživatelské jméno e-mailu|
|Řetězec NENULOVÉ|Hodnotu NULL nebo ""|*pstrUserName*|" "|
|Řetězec s NENULOVOU hodnotou NULL|CHYBA|CHYBA||
|Řetězec NENULOVÉ|Řetězec NENULOVÉ|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Číslo, které identifikuje port TCP/IP pro použití na serveru.

*bPassive*<br/>
Určuje režim pasivní nebo aktivní pro tuto relaci serveru FTP. Pokud je nastavena na hodnotu TRUE, nastaví rozhraní API systému Win32 *dwFlag* k INTERNET_FLAG_PASSIVE.

### <a name="remarks"></a>Poznámky

Nikdy nevytvářejte `CFtpConnection` objektu přímo. Namísto toho zavolejte metodu [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), která vytvoří `CFptConnection` objektu.

##  <a name="command"></a>  CFtpConnection::Command

Odešle příkaz přímo na FTP server.

```
CInternetFile* Command(
    LPCTSTR pszCommand,
    CmdResponseType eResponse = CmdRespNone,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pszCommand*<br/>
Ukazatel na řetězec obsahující příkaz k odeslání.

*eResponse*<br/>
Určuje, zda očekává se odpověď ze serveru FTP. Může být jedna z následujících hodnot:

- `CmdRespNone` Není očekávána žádná odpověď.

- `CmdRespRead` Očekává se odpověď.

*dwFlags*<br/>
Hodnota obsahující příznaky, které řídí této funkce. Úplný seznam najdete v tématu [FTPCommand](/windows/desktop/api/wininet/nf-wininet-ftpcommanda).

*dwContext*<br/>
Ukazatel na hodnotu obsahující hodnotu definovaného aplikací umožňují určit kontext aplikace v zpětná volání.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkčnost [FTPCommand](/windows/desktop/api/wininet/nf-wininet-ftpcommanda) fungovat, jak je popsáno v sadě Windows SDK.

Pokud dojde k chybě, MFC, vyvolá výjimku typu [cinternetexception –](../../mfc/reference/cinternetexception-class.md).

##  <a name="createdirectory"></a>  CFtpConnection::CreateDirectory

Voláním této členské funkce k vytvoření adresáře na připojeném serveru.

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName*<br/>
Ukazatel na řetězec obsahující název adresář, který chcete vytvořit.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud selže volání funkce Windows [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.

### <a name="remarks"></a>Poznámky

Použití `GetCurrentDirectory` určit aktuální pracovní adresář pro toto připojení k serveru. Nepředpokládejte, že vzdálený systém, můžete se připojil do kořenového adresáře.

`pstrDirName` Parametr může být buď částečně nebo plně kvalifikovaný název souboru relativní vzhledem k aktuálnímu adresáři. Zpětné lomítko (\\) nebo lomítkem (/) lze použít jako oddělovač adresářů pro buď název. `CreateDirectory` předtím, než se používají se přeloží název oddělovač do příslušných znaků.

##  <a name="getcurrentdirectory"></a>  CFtpConnection::GetCurrentDirectory

Voláním této členské funkce a získat tak název aktuálního adresáře.

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parametry

*strDirName*<br/>
Odkaz na řetězec, který se zobrazí název adresáře.

*pstrDirName*<br/>
Ukazatel na řetězec, který se zobrazí název adresáře.

*lpdwLen*<br/>
Ukazatel na DWORD, který obsahuje následující informace:

|||
|-|-|
|V položce|Velikost vyrovnávací paměti odkazuje *pstrDirName*.|
|Při návratu|Počet znaků, které jsou uloženy do *pstrDirName*. Pokud má členská funkce se nezdaří a ERROR_INSUFFICIENT_BUFFER nevrátí, znamená *lpdwLen* obsahuje počet bajtů, které aplikace musí přidělit za účelem přijímání řetězec.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.

### <a name="remarks"></a>Poznámky

Jako adresu URL získat místo toho název adresáře, volání [GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl).

Parametry *pstrDirName* nebo *strDirName* může být buď částečně kvalifikované názvy souborů, vzhledem k aktuálnímu adresáři nebo plně kvalifikovaný. Zpětné lomítko (\\) nebo lomítkem (/) lze použít jako oddělovač adresářů pro buď název. `GetCurrentDirectory` předtím, než se používají se přeloží název oddělovač do příslušných znaků.

##  <a name="getcurrentdirectoryasurl"></a>  CFtpConnection::GetCurrentDirectoryAsURL

Voláním této členské funkce se získat název aktuální adresář jako adresu URL.

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parametry

*strDirName*<br/>
Odkaz na řetězec, který se zobrazí název adresáře.

*pstrDirName*<br/>
Ukazatel na řetězec, který se zobrazí název adresáře.

*lpdwLen*<br/>
Ukazatel na DWORD, který obsahuje následující informace:

|||
|-|-|
|V položce|Velikost vyrovnávací paměti odkazuje *pstrDirName*.|
|Při návratu|Počet znaků, které jsou uloženy do *pstrDirName*. Pokud má členská funkce se nezdaří a ERROR_INSUFFICIENT_BUFFER nevrátí, znamená *lpdwLen* obsahuje počet bajtů, které aplikace musí přidělit za účelem přijímání řetězec.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.

### <a name="remarks"></a>Poznámky

`GetCurrentDirectoryAsURL` chová se stejně jako [GetCurrentDirectory](#getcurrentdirectory)

Parametr *strDirName* může být buď částečně kvalifikované názvy souborů, vzhledem k aktuálnímu adresáři nebo plně kvalifikovaný. Zpětné lomítko (\\) nebo lomítkem (/) lze použít jako oddělovač adresářů pro buď název. `GetCurrentDirectoryAsURL` předtím, než se používají se přeloží název oddělovač do příslušných znaků.

##  <a name="getfile"></a>  CFtpConnection::GetFile

Voláním této členské funkce získat soubor ze serveru FTP a uloží je na místním počítači.

```
BOOL GetFile(
    LPCTSTR pstrRemoteFile,
    LPCTSTR pstrLocalFile,
    BOOL bFailIfExists = TRUE,
    DWORD dwAttributes = FILE_ATTRIBUTE_NORMAL,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pstrRemoteFile*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název soubor, který chcete načíst ze serveru FTP.

*pstrLocalFile*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název souboru k vytvoření místního systému.

*bFailIfExists*<br/>
Určuje, zda název souboru může použít už existující soubor. Pokud název místního souboru již existuje, a tento parametr má hodnotu TRUE, `GetFile` selže. V opačném případě `GetFile` vymaže stávající kopie souboru.

*dwAttributes*<br/>
Označuje atributy souboru. To může být libovolná kombinace následující příznaky FILE_ATTRIBUTE_ *.

- FILE_ATTRIBUTE_ARCHIVE soubor je soubor archivu. K označení souborů pro zálohování nebo odebrání aplikací použijte tento atribut.

- Je komprimován FILE_ATTRIBUTE_COMPRESSED souboru nebo adresáře. Pro soubor komprese znamená, že všechna data v souboru je komprimován. Pro adresář komprese je výchozí pro nově vytvořené soubory a podadresáře.

- FILE_ATTRIBUTE_DIRECTORY souboru je adresář.

- FILE_ATTRIBUTE_NORMAL soubor nemá nastavené žádné jiné atributy. Tento atribut je platný jenom v případě, že používat samostatně. Všechny ostatní atributy souboru přepsat FILE_ATTRIBUTE_NORMAL:

- FILE_ATTRIBUTE_HIDDEN souboru je skrytý. Není součástí běžných adresářů.

- FILE_ATTRIBUTE_READONLY soubor je jen pro čtení. Aplikace může číst soubor, ale nelze do ní zapisovat nebo ho odstranit.

- FILE_ATTRIBUTE_SYSTEM soubor je součástí nebo používá výhradně operační systém.

- FILE_ATTRIBUTE_TEMPORARY soubor se používá jako dočasné úložiště. Aplikace by měla zapisovat do souboru pouze v případě, že je nezbytně nutné. Většina dat souboru zůstane v paměti bez vyprazdňuje na médiu, protože ho budou brzy odstraněny.

*dwFlags*<br/>
Určuje podmínky, za kterých dojde k přenosu. Tento parametr lze rozdělit *dwFlags* podle hodnoty [FtpGetFile](/windows/desktop/api/wininet/nf-wininet-ftpgetfilea) v sadě Windows SDK.

*dwContext*<br/>
Identifikátor kontextu načítání souborů. Zobrazit **poznámky** Další informace o *dwContext*.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.

### <a name="remarks"></a>Poznámky

`GetFile` je základní rutinu, která zpracovává všechny režie spojená se čtením souboru ze serveru FTP a ukládat místně. Aplikace, které jen načítají data souboru nebo Zavřít kontrolu nad přenosy souborů, které vyžadují by měly používat `OpenFile` a [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) místo.

Pokud *dwFlags* je FILE_TRANSFER_TYPE_ASCII překladu dat souboru platí také převede ovládacího prvku a formátování znaků, které mají Windows ekvivalenty. Výchozí přenos je binárním režimu, kde se soubor stáhne ve stejném formátu, jak je uložen na serveru.

Obě *pstrRemoteFile* a *pstrLocalFile* může být buď částečně kvalifikované názvy souborů, vzhledem k aktuálnímu adresáři nebo plně kvalifikovaný. Zpětné lomítko (\\) nebo lomítkem (/) lze použít jako oddělovač adresářů pro buď název. `GetFile` předtím, než se používají se přeloží název oddělovač do příslušných znaků.

Přepsat *dwContext* výchozí identifikátor kontextu nastavena na hodnotu podle vašeho výběru. Identifikátor kontextu souvisí s tuto konkrétní operaci `CFtpConnection` objekt vytvořený pomocí jeho [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objektu. Hodnota se vrátí do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) kvůli stavu na operaci, se kterým je identifikován. Přečtěte si článek [Internet první kroky: WinInet](../../mfc/wininet-basics.md) Další informace o identifikátor kontextu.

##  <a name="openfile"></a>  CFtpConnection::OpenFile

Voláním této členské funkce a otevřete soubor umístěný na serveru FTP pro čtení nebo zápis.

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pstrFileName*<br/>
Ukazatel na řetězec obsahující název souboru, který má být otevřen.

*dwAccess*<br/>
Určuje, jak budou mít přístup souboru. Může být všeobecné_čtení nebo GENERIC_WRITE, ale ne obojí.

*dwFlags*<br/>
Určuje podmínky, za kterých dojde k následující převody. Tou může být kterákoli z následujících konstant FTP_TRANSFER_ *:

- FTP_TRANSFER_TYPE_ASCII soubor přenese pomocí metody přenosu FTP ASCII (typu A). Převede ovládací prvek a informace o formátování na místní ekvivalenty.

- FTP_TRANSFER_TYPE_BINARY soubor přenosy dat prostřednictvím metody přenosu FTP's Image, (typ I). Soubor přenese data přesně tak, jak ho existuje beze změny. Toto je výchozí metodou přenosu.

*dwContext*<br/>
Identifikátor kontextu pro otevření souboru. Zobrazit **poznámky** Další informace o *dwContext*.

### <a name="return-value"></a>Návratová hodnota

Ukazatel [cinternetfile –](../../mfc/reference/cinternetfile-class.md) objektu.

### <a name="remarks"></a>Poznámky

`OpenFile` byste měli použít v následujících situacích:

- Aplikace obsahuje data, která se odesílají a vytvořen jako soubor na serveru FTP, ale, že data nejsou v místním souboru. Jednou `OpenFile` otevře soubor, tato aplikace používá [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write) k odesílání dat souboru protokolu FTP k serveru.

- Aplikace musí načíst soubor ze serveru a umístěte ji do aplikace řízené paměti namísto zápis na disk. Aplikace používá [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) po použití `OpenFile` k otevření souboru.

- Aplikace potřebuje jemné úroveň kontroly nad přenos souborů. Aplikace může třeba k zobrazení průběh řízení informace o průběhu stav přenosu souboru při stahování souboru.

Po volání `OpenFile` a až do volání `CInternetConnection::Close`, aplikace může volat pouze [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write), `CInternetConnection::Close`, nebo [ CFtpFileFind::FindFile](../../mfc/reference/cftpfilefind-class.md#findfile). Volání dalších funkcí FTP pro stejné relace FTP bude selže a nastaví kód chyby: FTP_ETRANSFER_IN_PROGRESS.

*PstrFileName* parametr může být buď částečně kvalifikované název souboru úplnou nebo relativní k aktuálnímu adresáři. Zpětné lomítko (\\) nebo lomítkem (/) lze použít jako oddělovač adresářů pro buď název. `OpenFile` Přeloží název oddělovač do příslušných znaků před jeho použitím.

Přepsat *dwContext* výchozí identifikátor kontextu nastavena na hodnotu podle vašeho výběru. Identifikátor kontextu souvisí s tuto konkrétní operaci `CFtpConnection` objekt vytvořený pomocí jeho [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objektu. Hodnota se vrátí do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) kvůli stavu na operaci, se kterým je identifikován. Přečtěte si článek [Internet první kroky: WinInet](../../mfc/wininet-basics.md) Další informace o identifikátor kontextu.

##  <a name="putfile"></a>  CFtpConnection::PutFile

Zavolejte tuto členskou funkci pro uložení souboru na FTP server.

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pstrLocalFile*<br/>
Ukazatel na řetězec obsahující název souboru má být odeslán z místního systému.

*pstrRemoteFile*<br/>
Ukazatel na řetězec obsahující název souboru k vytvoření serveru FTP.

*dwFlags*<br/>
Určuje podmínky, za kterých dojde k přenosu souboru. Může být konstanty FTP_TRANSFER_ * je popsáno v [OpenFile](#openfile).

*dwContext*<br/>
Identifikátor kontextu umístění souboru. Zobrazit **poznámky** Další informace o *dwContext*.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.

### <a name="remarks"></a>Poznámky

`PutFile` je základní rutinu, která zpracovává všechny operace spojené s ukládáním souboru na serveru FTP. Aplikace, která odesílala jen data, nebo, které vyžadují kontrolu nad přenosy souborů, by měly používat [OpenFile](#openfile) a [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write).

Přepsat `dwContext` výchozí identifikátor kontextu nastavena na hodnotu podle vašeho výběru. Identifikátor kontextu souvisí s tuto konkrétní operaci `CFtpConnection` objekt vytvořený pomocí jeho [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objektu. Hodnota se vrátí do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) kvůli stavu na operaci, se kterým je identifikován. Přečtěte si článek [Internet první kroky: WinInet](../../mfc/wininet-basics.md) Další informace o identifikátor kontextu.

##  <a name="remove"></a>  CFtpConnection::Remove

Voláním této členské funkce odstranit zadaný soubor z připojeného serveru.

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>Parametry

*pstrFileName*<br/>
Ukazatel na řetězec obsahující název souboru, který chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.

### <a name="remarks"></a>Poznámky

*PstrFileName* parametr může být buď částečně kvalifikované název souboru úplnou nebo relativní k aktuálnímu adresáři. Zpětné lomítko (\\) nebo lomítkem (/) lze použít jako oddělovač adresářů pro buď název. `Remove` Funkce překládá název oddělovač do příslušných znaků před jejich použití.

##  <a name="removedirectory"></a>  CFtpConnection::RemoveDirectory

Voláním této členské funkce k odebrání zadaného adresáře z připojeného serveru.

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName*<br/>
Ukazatel na řetězec obsahující adresář, který má být odebrán.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.

### <a name="remarks"></a>Poznámky

Použití [GetCurrentDirectory](#getcurrentdirectory) určit aktuální pracovní adresář serveru. Nepředpokládejte, že vzdálený systém, můžete se připojil do kořenového adresáře.

*PstrDirName* parametr může být buď částečně nebo plně kvalifikovaný název souboru relativní vzhledem k aktuálnímu adresáři. Zpětné lomítko (\\) nebo lomítkem (/) lze použít jako oddělovač adresářů pro buď název. `RemoveDirectory` předtím, než se používají se přeloží název oddělovač do příslušných znaků.

##  <a name="rename"></a>  CFtpConnection::Rename

Voláním této členské funkce přejmenovat zadaný soubor na připojeném serveru.

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>Parametry

*pstrExisting*<br/>
Ukazatel na řetězec obsahující aktuální název souboru, který má být přejmenován.

*pstrNew*<br/>
Ukazatel na řetězec obsahující název nového souboru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.

### <a name="remarks"></a>Poznámky

*PstrExisting* a *pstrNew* parametrů může být buď částečně kvalifikované název souboru úplnou nebo relativní k aktuálnímu adresáři. Zpětné lomítko (\\) nebo lomítkem (/) lze použít jako oddělovač adresářů pro buď název. `Rename` předtím, než se používají se přeloží název oddělovač do příslušných znaků.

##  <a name="setcurrentdirectory"></a>  CFtpConnection::SetCurrentDirectory

Voláním této členské funkce, chcete-li změnit na jiný adresář serveru FTP.

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName*<br/>
Ukazatel na řetězec obsahující název adresáře.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.

### <a name="remarks"></a>Poznámky

*PstrDirName* parametr může být buď částečně nebo plně kvalifikovaný název souboru relativní vzhledem k aktuálnímu adresáři. Zpětné lomítko (\\) nebo lomítkem (/) lze použít jako oddělovač adresářů pro buď název. `SetCurrentDirectory` předtím, než se používají se přeloží název oddělovač do příslušných znaků.

Použití [GetCurrentDirectory](#getcurrentdirectory) určit aktuální pracovní adresář serveru FTP. Nepředpokládejte, že vzdálený systém, můžete se připojil do kořenového adresáře.

## <a name="see-also"></a>Viz také:

[CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession – třída](../../mfc/reference/cinternetsession-class.md)
