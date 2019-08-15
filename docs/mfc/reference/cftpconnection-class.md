---
title: CFtpConnection – třída
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
ms.openlocfilehash: 977a8c9fc6dd653a59434d29bb72b0fe28900001
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506376"
---
# <a name="cftpconnection-class"></a>CFtpConnection – třída

Spravuje připojení FTP k internetovému serveru a umožňuje přímou manipulaci s adresáři a soubory na tomto serveru.

## <a name="syntax"></a>Syntaxe

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CFtpConnection::CFtpConnection](#cftpconnection)|`CFtpConnection` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CFtpConnection::Command](#command)|Odešle příkaz přímo na server FTP.|
|[CFtpConnection:: CreateDirectory](#createdirectory)|Vytvoří adresář na serveru.|
|[CFtpConnection::GetCurrentDirectory](#getcurrentdirectory)|Načte aktuální adresář pro toto připojení.|
|[CFtpConnection::GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|Načte aktuální adresář pro toto připojení jako adresu URL.|
|[CFtpConnection:: GetFile](#getfile)|Načte soubor z připojeného serveru.|
|[CFtpConnection::OpenFile](#openfile)|Otevře soubor na připojeném serveru.|
|[CFtpConnection::P utFile](#putfile)|Umístí soubor na server.|
|[CFtpConnection:: Remove](#remove)|Odebere soubor ze serveru.|
|[CFtpConnection::RemoveDirectory](#removedirectory)|Odebere zadaný adresář ze serveru.|
|[CFtpConnection:: rename](#rename)|Přejmenuje soubor na serveru.|
|[CFtpConnection::SetCurrentDirectory](#setcurrentdirectory)|Nastaví aktuální adresář FTP.|

## <a name="remarks"></a>Poznámky

FTP je jedna ze tří služeb sítě Internet rozpoznávaných třídami WinInet knihovny MFC.

Abyste mohli komunikovat s internetovým serverem FTP, musíte nejdřív vytvořit instanci [CInternetSession](../../mfc/reference/cinternetsession-class.md)a pak vytvořit `CFtpConnection` objekt. Nikdy nevytvoříte `CFtpConnection` objekt přímo; místo toho zavolejte [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection) `CFtpConnection` , které vytvoří objekt a vrátí ukazatel na něj.

Další informace o tom, `CFtpConnection` jak pracovat s jinými internetovými třídami knihovny MFC, najdete v článku [internetové programování s](../../mfc/win32-internet-extensions-wininet.md)rozhraním Wininet. Další informace o komunikaci s dalšími dvěma podporovanými službami, HTTP a gopher najdete v tématu třídy [CHttpConnection](../../mfc/reference/chttpconnection-class.md) a [CGopherConnection](../../mfc/reference/cgopherconnection-class.md).

## <a name="example"></a>Příklad

  Podívejte se na příklad v přehledu třídy [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet. h

##  <a name="cftpconnection"></a>CFtpConnection::CFtpConnection

Tato členská funkce je volána k vytvoření `CFtpConnection` objektu.

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
Ukazatel na související objekt [CInternetSession](../../mfc/reference/cinternetsession-class.md) .

*hConnected*<br/>
Popisovač aktuální internetové relace v systému Windows.

*pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru FTP.

*dwContext*<br/>
Identifikátor kontextu operace. *dwContext* identifikuje informace o stavu operace vrácené funkcí [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). Výchozí nastavení je 1; Můžete ale explicitně přiřadit konkrétní ID kontextu pro danou operaci. K tomuto ID kontextu bude přidružen objekt a veškerá jeho práce.

*pstrUserName*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje jméno uživatele, který se má přihlásit. Pokud má hodnotu NULL, je výchozí hodnota anonymní.

*pstrPassword*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje heslo, které se má použít pro přihlášení. Pokud mají hodnoty *pstrPassword* i *pstrUserName* hodnotu null, výchozím anonymním heslem je e-mailová adresa uživatele. Pokud má *pstrPassword* hodnotu null (nebo prázdný řetězec), ale *pstrUserName* není null, použije se prázdné heslo. Následující tabulka popisuje chování pro čtyři možná nastavení *pstrUserName* a *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Uživatelské jméno odeslané na server FTP|Heslo odeslané na server FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL nebo ""|NULL nebo ""|Anonymous|E-mailová adresa uživatele|
|Řetězec, který není NULL|NULL nebo ""|*pstrUserName*|" "|
|Prázdný řetězec, který není NULL|CHYBA|CHYBA||
|Řetězec, který není NULL|Řetězec, který není NULL|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Číslo určující port TCP/IP, který má být použit na serveru.

*bPassive*<br/>
Určuje pasivní nebo aktivní režim pro tuto relaci FTP. Pokud je nastaveno na hodnotu TRUE, nastaví Win32 API *dwFlag* na INTERNET_FLAG_PASSIVE.

### <a name="remarks"></a>Poznámky

`CFtpConnection` Objekt nikdy nevytvoříte přímo. Místo toho zavolejte [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection), které vytvoří `CFptConnection` objekt.

##  <a name="command"></a>CFtpConnection:: – příkaz

Odešle příkaz přímo na server FTP.

```
CInternetFile* Command(
    LPCTSTR pszCommand,
    CmdResponseType eResponse = CmdRespNone,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pszCommand*<br/>
Ukazatel na řetězec obsahující příkaz, který má být odeslán.

*eResponse*<br/>
Určuje, zda je na serveru FTP očekávána odpověď. Může to být jedna z následujících hodnot:

- `CmdRespNone`Není očekávána žádná odpověď.

- `CmdRespRead`Očekává se odpověď.

*dwFlags*<br/>
Hodnota, která obsahuje příznaky, které ovládají tuto funkci. Úplný seznam najdete v tématu [FtpCommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw).

*dwContext*<br/>
Ukazatel na hodnotu obsahující hodnotu definovanou aplikací, která se používá k identifikaci kontextu aplikace ve zpětných voláních.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce funkce [FtpCommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw) , jak je popsáno v Windows SDK.

Pokud dojde k chybě, knihovna MFC vyvolá výjimku typu [CInternetException](../../mfc/reference/cinternetexception-class.md).

##  <a name="createdirectory"></a>CFtpConnection:: CreateDirectory

Zavolejte tuto členskou funkci pro vytvoření adresáře na připojeném serveru.

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName*<br/>
Ukazatel na řetězec obsahující název adresáře, který se má vytvořit.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Windows Function [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

### <a name="remarks"></a>Poznámky

Slouží `GetCurrentDirectory` k určení aktuálního pracovního adresáře pro toto připojení k serveru. Nepředpokládají, že se vzdálený systém připojil k kořenovému adresáři.

`pstrDirName` Parametr může být buď částečně, nebo plně kvalifikovaný název souboru relativní vzhledem k aktuálnímu adresáři. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro libovolný název. `CreateDirectory`přeloží oddělovače názvů adresářů na příslušné znaky před jejich použitím.

##  <a name="getcurrentdirectory"></a>CFtpConnection::GetCurrentDirectory

Chcete-li získat název aktuálního adresáře, zavolejte tuto členskou funkci.

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parametry

*strDirName*<br/>
Odkaz na řetězec, který získá název adresáře.

*pstrDirName*<br/>
Ukazatel na řetězec, který získá název adresáře.

*lpdwLen*<br/>
Ukazatel na DWORD, který obsahuje následující informace:

|||
|-|-|
|Při zadání|Velikost vyrovnávací paměti, na kterou odkazuje *pstrDirName*.|
|Při návratu|Počet znaků uložených do *pstrDirName*. Pokud dojde k chybě členské funkce a vrátí se ERROR_INSUFFICIENT_BUFFER, pak *lpdwLen* obsahuje počet bajtů, které musí aplikace přidělit, aby mohl získat řetězec.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

### <a name="remarks"></a>Poznámky

Chcete-li místo toho získat název adresáře, zavolejte [GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl).

Parametry *pstrDirName* a *strDirName* mohou být buď částečně kvalifikované názvy souborů vzhledem k aktuálnímu adresáři nebo plně kvalifikovanému. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro libovolný název. `GetCurrentDirectory`přeloží oddělovače názvů adresářů na příslušné znaky před jejich použitím.

##  <a name="getcurrentdirectoryasurl"></a>CFtpConnection::GetCurrentDirectoryAsURL

Zavolejte tuto členskou funkci, aby se název aktuálního adresáře získal jako adresa URL.

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parametry

*strDirName*<br/>
Odkaz na řetězec, který získá název adresáře.

*pstrDirName*<br/>
Ukazatel na řetězec, který získá název adresáře.

*lpdwLen*<br/>
Ukazatel na DWORD, který obsahuje následující informace:

|||
|-|-|
|Při zadání|Velikost vyrovnávací paměti, na kterou odkazuje *pstrDirName*.|
|Při návratu|Počet znaků uložených do *pstrDirName*. Pokud dojde k chybě členské funkce a vrátí se ERROR_INSUFFICIENT_BUFFER, pak *lpdwLen* obsahuje počet bajtů, které musí aplikace přidělit, aby mohl získat řetězec.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

### <a name="remarks"></a>Poznámky

`GetCurrentDirectoryAsURL`se chová stejně jako [GetCurrentDirectory](#getcurrentdirectory)

Parametr *strDirName* může být buď částečně kvalifikovaný název souborů relativní vzhledem k aktuálnímu adresáři, nebo plně kvalifikovaný. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro libovolný název. `GetCurrentDirectoryAsURL`přeloží oddělovače názvů adresářů na příslušné znaky před jejich použitím.

##  <a name="getfile"></a>CFtpConnection:: GetFile

Voláním této členské funkce získáte soubor ze serveru FTP a uložíte ho do místního počítače.

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
Ukazatel na řetězec zakončený hodnotou null obsahující název souboru, který se má načíst ze serveru FTP.

*pstrLocalFile*<br/>
Ukazatel na řetězec zakončený hodnotou null obsahující název souboru, který má být vytvořen v místním systému.

*bFailIfExists*<br/>
Určuje, zda již může být název souboru použit existujícím souborem. Pokud název místního souboru již existuje a tento parametr je true, `GetFile` dojde k chybě. `GetFile` V opačném případě Smaže existující kopii souboru.

*dwAttributes*<br/>
Určuje atributy souboru. Může to být libovolná kombinace následujících příznaků FILE_ATTRIBUTE_ *.

- FILE_ATTRIBUTE_ARCHIVE soubor je archivní soubor. Aplikace používají tento atribut k označení souborů pro zálohování nebo odebrání.

- FILE_ATTRIBUTE_COMPRESSED, že se soubor nebo adresář komprimuje. V případě souboru komprese znamená, že všechna data v souboru jsou komprimována. Pro adresář je komprese výchozím nastavením pro nově vytvořené soubory a podadresáře.

- FILE_ATTRIBUTE_DIRECTORY soubor je adresář.

- FILE_ATTRIBUTE_NORMAL soubor nemá nastavené žádné další atributy. Tento atribut je platný pouze v případě, že je použit samostatně. Všechny ostatní atributy souborů přepisují FILE_ATTRIBUTE_NORMAL:

- FILE_ATTRIBUTE_HIDDEN soubor je skrytý. Není zahrnutý do běžného výpisu adresáře.

- FILE_ATTRIBUTE_READONLY soubor je jen pro čtení. Aplikace můžou soubor číst, ale nemůžou do něj zapisovat ani ho odstraňovat.

- FILE_ATTRIBUTE_SYSTEM soubor je součástí nebo je používán výhradně operačním systémem.

- FILE_ATTRIBUTE_TEMPORARY soubor se používá pro dočasné úložiště. Aplikace by měly zapisovat do souboru pouze v případě, že je to nezbytně nutné. Většina dat souboru zůstává v paměti, aniž by byla vyprázdněna na médium, protože soubor bude brzy odstraněn.

*dwFlags*<br/>
Určuje podmínky, za kterých dojde k přenosu. Tento parametr může být libovolná z hodnot *dwFlags* popsaných v tématu [FtpGetFile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew) v Windows SDK.

*dwContext*<br/>
Identifikátor kontextu pro načtení souboru. Další informace o *dwContext*najdete v tématu **poznámky** .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

### <a name="remarks"></a>Poznámky

`GetFile`je rutina vysoké úrovně, která zpracovává veškerou režii spojenou s čtením souboru ze serveru FTP a jeho místní ukládání. Aplikace, které načítají jenom data souborů, nebo které vyžadují ukončení kontroly přenosu souborů, by měly `OpenFile` místo toho použít a [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read) .

Pokud je *DWFLAGS* FILE_TRANSFER_TYPE_ASCII, překlad dat souborů také převede ovládací prvky a formátovací znaky na ekvivalenty systému Windows. Výchozím přenosem je binární režim, ve kterém se soubor stáhne ve stejném formátu, ve kterém je uložený na serveru.

*PstrRemoteFile* i *pstrLocalFile* můžou být buď částečně kvalifikované názvy souborů vzhledem k aktuálnímu adresáři, nebo plně kvalifikované. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro libovolný název. `GetFile`přeloží oddělovače názvů adresářů na příslušné znaky před jejich použitím.

Přepsáním výchozí *dwContext* nastavte identifikátor kontextu na hodnotu, kterou zvolíte. Identifikátor kontextu je spojen s touto konkrétní operací `CFtpConnection` objektu vytvořeného jeho objektem [CInternetSession](../../mfc/reference/cinternetsession-class.md) . Hodnota se vrátí do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , která poskytne stav operace, se kterou se identifikuje. Přečtěte si [článek Internet First Step: Rozhraní](../../mfc/wininet-basics.md) WinInet pro další informace o identifikátoru kontextu.

##  <a name="openfile"></a>CFtpConnection:: OpenFile

Voláním této členské funkce otevřete soubor umístěný na serveru FTP pro čtení nebo zápis.

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
Určuje, jak bude k souboru přistup. Může být buď GENERIC_READ, nebo GENERIC_WRITE, ale ne obojí.

*dwFlags*<br/>
Určuje podmínky, za kterých dojde k dalším přenosům. Může to být kterákoli z následujících konstant FTP_TRANSFER_ *:

- FTP_TRANSFER_TYPE_ASCII přenos souborů pomocí metody přenosu FTP ASCII (Type A). Převede ovládací prvek a informace o formátování na lokální ekvivalenty.

- FTP_TRANSFER_TYPE_BINARY soubor přenáší data pomocí metody přenosu (Type I) FTP. Soubor přenáší data stejně, jako existuje, bez jakýchkoli změn. Toto je výchozí metoda přenosu.

*dwContext*<br/>
Identifikátor kontextu pro otevření souboru. Další informace o *dwContext*najdete v tématu **poznámky** .

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CInternetFile](../../mfc/reference/cinternetfile-class.md) .

### <a name="remarks"></a>Poznámky

`OpenFile`by měl být použit v následujících situacích:

- Aplikace obsahuje data, která je třeba odeslat a vytvořit jako soubor na serveru FTP, ale tato data nejsou v místním souboru. Po `OpenFile` otevření souboru aplikace použije [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write) k odeslání dat souboru FTP na server.

- Aplikace musí načíst soubor ze serveru a umístit ho do paměti řízené aplikací místo psaní na disk. Aplikace používá [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read) po použití `OpenFile` k otevření souboru.

- Aplikace potřebuje bezproblémovou úroveň kontroly nad přenosem souborů. Například aplikace může chtít zobrazit ovládací prvek průběh, který indikuje průběh stavu přenosu souboru při stahování souboru.

Po volání `OpenFile` a dokud volání `CInternetConnection::Close`může aplikace volat pouze [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read), [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write), `CInternetConnection::Close`nebo [CFtpFileFind:: FindFile –](../../mfc/reference/cftpfilefind-class.md#findfile). Volání dalších funkcí FTP pro stejnou relaci FTP selžou a kód chyby bude nastaven na FTP_ETRANSFER_IN_PROGRESS.

Parametr *pstrFileName* může být buď částečně kvalifikovaný název souboru relativní vzhledem k aktuálnímu adresáři, nebo plně kvalifikovaný název. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro libovolný název. `OpenFile`před použitím přeloží oddělovače názvů adresářů na příslušné znaky.

Přepsáním výchozí *dwContext* nastavte identifikátor kontextu na hodnotu, kterou zvolíte. Identifikátor kontextu je spojen s touto konkrétní operací `CFtpConnection` objektu vytvořeného jeho objektem [CInternetSession](../../mfc/reference/cinternetsession-class.md) . Hodnota se vrátí do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , která poskytne stav operace, se kterou se identifikuje. Přečtěte si [článek Internet First Step: Rozhraní](../../mfc/wininet-basics.md) WinInet pro další informace o identifikátoru kontextu.

##  <a name="putfile"></a>CFtpConnection::P utFile

Tuto členskou funkci volejte k uložení souboru na server FTP.

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pstrLocalFile*<br/>
Ukazatel na řetězec obsahující název souboru, který se má odeslat z místního systému.

*pstrRemoteFile*<br/>
Ukazatel na řetězec obsahující název souboru, který se má vytvořit na serveru FTP.

*dwFlags*<br/>
Určuje podmínky, za kterých dojde k přenosu souboru. Může to být kterákoli z konstant FTP_TRANSFER_ * popsaná ve [OpenFile](#openfile).

*dwContext*<br/>
Identifikátor kontextu pro umístění souboru. Další informace o *dwContext*najdete v tématu **poznámky** .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

### <a name="remarks"></a>Poznámky

`PutFile`je rutina vysoké úrovně, která zpracovává všechny operace spojené s ukládáním souboru na serveru FTP. Aplikace, které odesílají data pouze a které vyžadují lepší kontrolu nad přenosem souborů, by měly používat [OpenFile](#openfile) a [CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write).

Přepsáním `dwContext` výchozí hodnoty nastavte identifikátor kontextu na hodnotu, kterou zvolíte. Identifikátor kontextu je spojen s touto konkrétní operací `CFtpConnection` objektu vytvořeného jeho objektem [CInternetSession](../../mfc/reference/cinternetsession-class.md) . Hodnota se vrátí do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , která poskytne stav operace, se kterou se identifikuje. Přečtěte si [článek Internet First Step: Rozhraní](../../mfc/wininet-basics.md) WinInet pro další informace o identifikátoru kontextu.

##  <a name="remove"></a>CFtpConnection:: Remove

Voláním této členské funkce odstraníte zadaný soubor z připojeného serveru.

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>Parametry

*pstrFileName*<br/>
Ukazatel na řetězec obsahující název souboru, který se má odebrat.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

### <a name="remarks"></a>Poznámky

Parametr *pstrFileName* může být buď částečně kvalifikovaný název souboru relativní vzhledem k aktuálnímu adresáři, nebo plně kvalifikovaný název. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro libovolný název. `Remove` Funkce přeloží oddělovače názvů adresářů na příslušné znaky před jejich použitím.

##  <a name="removedirectory"></a>CFtpConnection::RemoveDirectory

Tuto členskou funkci volejte pro odebrání zadaného adresáře z připojeného serveru.

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName*<br/>
Ukazatel na řetězec obsahující adresář, který má být odebrán.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

### <a name="remarks"></a>Poznámky

K určení aktuálního pracovního adresáře serveru použijte [GetCurrentDirectory](#getcurrentdirectory) . Nepředpokládají, že se vzdálený systém připojil k kořenovému adresáři.

Parametr *pstrDirName* může být buď částečně, nebo plně kvalifikovaný název souboru relativní vzhledem k aktuálnímu adresáři. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro libovolný název. `RemoveDirectory`přeloží oddělovače názvů adresářů na příslušné znaky před jejich použitím.

##  <a name="rename"></a>CFtpConnection:: rename

Tuto členskou funkci zavolejte k přejmenování zadaného souboru na připojeném serveru.

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>Parametry

*pstrExisting*<br/>
Ukazatel na řetězec obsahující aktuální název souboru, který má být přejmenován.

*pstrNew*<br/>
Ukazatel na řetězec obsahující nový název souboru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

### <a name="remarks"></a>Poznámky

Parametry *pstrExisting* a *pstrNew* mohou být buď částečně kvalifikovaný název souboru relativní vzhledem k aktuálnímu adresáři nebo plně kvalifikovanému. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro libovolný název. `Rename`přeloží oddělovače názvů adresářů na příslušné znaky před jejich použitím.

##  <a name="setcurrentdirectory"></a>CFtpConnection::SetCurrentDirectory

Zavolejte tuto členskou funkci, aby se změnila na jiný adresář na serveru FTP.

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName*<br/>
Ukazatel na řetězec, který obsahuje název adresáře.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

### <a name="remarks"></a>Poznámky

Parametr *pstrDirName* může být buď částečně, nebo plně kvalifikovaný název souboru relativní vzhledem k aktuálnímu adresáři. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro libovolný název. `SetCurrentDirectory`přeloží oddělovače názvů adresářů na příslušné znaky před jejich použitím.

Pomocí [GetCurrentDirectory](#getcurrentdirectory) určete aktuální pracovní adresář serveru FTP. Nepředpokládají, že se vzdálený systém připojil k kořenovému adresáři.

## <a name="see-also"></a>Viz také:

[CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession – třída](../../mfc/reference/cinternetsession-class.md)
