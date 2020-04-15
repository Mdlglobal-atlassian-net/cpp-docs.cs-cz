---
title: CFtpConnection – třída
ms.date: 08/29/2019
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
ms.openlocfilehash: a1fe516869aa98cc291597211eee175ef591e45d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373780"
---
# <a name="cftpconnection-class"></a>CFtpConnection – třída

Spravuje připojení FTP k internetovému serveru a umožňuje přímou manipulaci s adresáři a soubory na tomto serveru.

## <a name="syntax"></a>Syntaxe

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CFtpConnection::CFtpConnection](#cftpconnection)|Vytvoří `CFtpConnection` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CFtpConnection::Příkaz](#command)|Odešle příkaz přímo na server FTP.|
|[CFtpConnection::CreateDirectory](#createdirectory)|Vytvoří adresář na serveru.|
|[CFtpConnection::GetCurrentDirectory](#getcurrentdirectory)|Získá aktuální adresář pro toto připojení.|
|[CFtpConnection::GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|Získá aktuální adresář pro toto připojení jako adresu URL.|
|[CFtpConnection::GetFile](#getfile)|Získá soubor z připojeného serveru.|
|[CFtpConnection::OpenFile](#openfile)|Otevře soubor na připojeném serveru.|
|[CFtpConnection::PutFile](#putfile)|Umístí soubor na server.|
|[CFtpConnection::Odebrat](#remove)|Odebere soubor ze serveru.|
|[CFtpConnection::RemoveDirectory](#removedirectory)|Odebere zadaný adresář ze serveru.|
|[CFtpConnection::Přejmenovat](#rename)|Přejmenuje soubor na serveru.|
|[CFtpConnection::SetCurrentDirectory](#setcurrentdirectory)|Nastaví aktuální adresář FTP.|

## <a name="remarks"></a>Poznámky

FTP je jednou ze tří internetových služeb uznávaných třídami MFC WinInet.

Chcete-li komunikovat s internetovým serverem FTP, musíte nejprve vytvořit `CFtpConnection` instanci [CInternetSession](../../mfc/reference/cinternetsession-class.md)a potom vytvořit objekt. Nikdy nevytváříte `CFtpConnection` objekt přímo; místo toho volání [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection) `CFtpConnection` , který vytvoří objekt a vrátí ukazatel na něj.

Další informace o `CFtpConnection` práci s ostatními třídami MFC Internet naleznete v článku [Internetové programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md). Další informace o komunikaci s dalšími dvěma podporovanými službami, HTTP a gopher, naleznete v třídách [CHttpConnection](../../mfc/reference/chttpconnection-class.md) a [CGopherConnection](../../mfc/reference/cgopherconnection-class.md).

## <a name="example"></a>Příklad

  Podívejte se na příklad v přehledu třídy [CFtpFileFind.](../../mfc/reference/cftpfilefind-class.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="cftpconnectioncftpconnection"></a><a name="cftpconnection"></a>CFtpConnection::CFtpConnection

Tato členská funkce je `CFtpConnection` volána k vytvoření objektu.

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

*pRelace*<br/>
Ukazatel na související objekt [CInternetSession.](../../mfc/reference/cinternetsession-class.md)

*hPřipojeno*<br/>
Popisovač systému Windows aktuální relace Internetu.

*server pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru FTP.

*dwKontext*<br/>
Identifikátor kontextu pro operaci. *dwContext* identifikuje informace o stavu operace vrácené [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). Výchozí hodnota je nastavena na hodnotu 1. můžete však explicitně přiřadit konkrétní ID kontextu pro operaci. Objekt a všechny práce, které provede, budou přidruženy k tomuto ID kontextu.

*pstrUserName*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který určuje jméno uživatele, který se má přihlásit. Pokud null, výchozí hodnota je anonymní.

*pstrPassword*<br/>
Ukazatel na řetězec s nulovým ukončením, který určuje heslo, které se má použít k přihlášení. Pokud jsou *hodnota pstrPassword* i *pstrUserName* null, je výchozím anonymním heslem e-mailové jméno uživatele. Pokud *pstrPassword* je NULL (nebo prázdný řetězec), ale *pstrUserName* není NULL, je použito prázdné heslo. Následující tabulka popisuje chování pro čtyři možná nastavení *pstrUserName* a *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Uživatelské jméno odeslané serveru FTP|Heslo odeslané na server FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|Null nebo " "|Null nebo " "|"anonymní"|E-mailová značka uživatele|
|Ne- nulový řetězec|Null nebo " "|*pstrUserName*|" "|
|Null non- NULL řetězec|ERROR|ERROR||
|Ne- nulový řetězec|Ne- nulový řetězec|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Číslo, které identifikuje port TCP/IP, který má být na serveru používán.

*bPasivní*<br/>
Určuje pasivní nebo aktivní režim pro tuto relaci FTP. Pokud je nastavena na hodnotu TRUE, nastaví win32 API *dwFlag* na INTERNET_FLAG_PASSIVE.

### <a name="remarks"></a>Poznámky

Nikdy nevytváříte `CFtpConnection` objekt přímo. Místo toho volejte [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection) `CFptConnection` , který vytvoří objekt.

## <a name="cftpconnectioncommand"></a><a name="command"></a>CFtpConnection::Příkaz

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

*eOdezva*<br/>
Určuje, zda je od serveru FTP očekávána odpověď. Může se na nich vyvěšovat jedna z následujících hodnot:

- `CmdRespNone`Neočekává se žádná odpověď.
- `CmdRespRead`Očekává se odpověď.
- `CmdRespWrite`Nepoužívá se.

CmdResponseType je členem CFtpConnection, definované v *afxinet.h*.

*dwFlags*<br/>
Hodnota obsahující příznaky, které řídí tuto funkci. Úplný seznam naleznete v tématu [FTPCommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw).

*dwKontext*<br/>
Ukazatel na hodnotu obsahující hodnotu definovanou aplikací, která slouží k identifikaci kontextu aplikace v zpětných voláních.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce [FTPCommand,](/windows/win32/api/wininet/nf-wininet-ftpcommandw) jak je popsáno v sadě Windows SDK.

Pokud dojde k chybě, knihovna MFC vyvolá výjimku typu [CInternetException](../../mfc/reference/cinternetexception-class.md).

## <a name="cftpconnectioncreatedirectory"></a><a name="createdirectory"></a>CFtpConnection::CreateDirectory

Voláním této členské funkce vytvořte adresář na připojeném serveru.

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName*<br/>
Ukazatel na řetězec obsahující název adresáře, který chcete vytvořit.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, může být volána funkce systému Windows [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) k určení příčiny chyby.

### <a name="remarks"></a>Poznámky

Slouží `GetCurrentDirectory` k určení aktuálního pracovního adresáře pro toto připojení k serveru. Nepředpokládejte, že vás vzdálený systém připojil ke kořenovému adresáři.

Parametr `pstrDirName` může být částečně nebo plně kvalifikovaný název souboru vzhledem k aktuálnímu adresáři. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro oba názvy. `CreateDirectory`převede oddělovače názvů adresářů na příslušné znaky před jejich použitím.

## <a name="cftpconnectiongetcurrentdirectory"></a><a name="getcurrentdirectory"></a>CFtpConnection::GetCurrentDirectory

Volání této členské funkce získat název aktuálního adresáře.

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parametry

*strDirName*<br/>
Odkaz na řetězec, který obdrží název adresáře.

*pstrDirName*<br/>
Ukazatel na řetězec, který obdrží název adresáře.

*lpdwLen*<br/>
Ukazatel na dword, který obsahuje následující informace:

|||
|-|-|
|Při vstupu|Velikost vyrovnávací paměti odkazuje *pstrDirName*.|
|Při návratu|Počet znaků uložených do *pstrDirName*. Pokud členská funkce selže a ERROR_INSUFFICIENT_BUFFER je vrácena, pak *lpdwLen* obsahuje počet bajtů, které musí aplikace přidělit, aby přijala řetězec.|

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

### <a name="remarks"></a>Poznámky

Chcete-li místo toho získat název adresáře jako adresu URL, zavolejte [adresu GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl).

Parametry *pstrDirName* nebo *strDirName* mohou být částečně kvalifikované názvy souborů vzhledem k aktuálnímu adresáři nebo plně kvalifikované. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro oba názvy. `GetCurrentDirectory`převede oddělovače názvů adresářů na příslušné znaky před jejich použitím.

## <a name="cftpconnectiongetcurrentdirectoryasurl"></a><a name="getcurrentdirectoryasurl"></a>CFtpConnection::GetCurrentDirectoryAsURL

Volánítéto členské funkce získat název aktuálního adresáře jako URL.

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>Parametry

*strDirName*<br/>
Odkaz na řetězec, který obdrží název adresáře.

*pstrDirName*<br/>
Ukazatel na řetězec, který obdrží název adresáře.

*lpdwLen*<br/>
Ukazatel na dword, který obsahuje následující informace:

|||
|-|-|
|Při vstupu|Velikost vyrovnávací paměti odkazuje *pstrDirName*.|
|Při návratu|Počet znaků uložených do *pstrDirName*. Pokud členská funkce selže a ERROR_INSUFFICIENT_BUFFER je vrácena, pak *lpdwLen* obsahuje počet bajtů, které musí aplikace přidělit, aby přijala řetězec.|

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

### <a name="remarks"></a>Poznámky

`GetCurrentDirectoryAsURL`chová se stejně jako [GetCurrentDirectory](#getcurrentdirectory)

Parametr *strDirName* může být částečně kvalifikované názvy souborů vzhledem k aktuálnímu adresáři nebo plně kvalifikovaný. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro oba názvy. `GetCurrentDirectoryAsURL`převede oddělovače názvů adresářů na příslušné znaky před jejich použitím.

## <a name="cftpconnectiongetfile"></a><a name="getfile"></a>CFtpConnection::GetFile

Volání této členské funkce získat soubor ze serveru FTP a uložit jej v místním počítači.

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

*soubor pstrRemoteFile*<br/>
Ukazatel na řetězec s ukončeným hodnotou null obsahující název souboru, který má být načten ze serveru FTP.

*pstrLocalFile*<br/>
Ukazatel na řetězec s nulovým ukončením obsahující název souboru, který má být v místním systému vytvořit.

*bFailIfExists*<br/>
Označuje, zda již může být název souboru používán existujícím souborem. Pokud místní název souboru již existuje a `GetFile` tento parametr je TRUE, selže. V `GetFile` opačném případě vymaže existující kopii souboru.

*dwAtributy*<br/>
Označuje atributy souboru. Může se jednalo o libovolnou kombinaci následujících příznaků FILE_ATTRIBUTE_*.

- FILE_ATTRIBUTE_ARCHIVE Soubor je archivní soubor. Aplikace používají tento atribut k označení souborů pro zálohování nebo odebrání.

- FILE_ATTRIBUTE_COMPRESSED Soubor nebo adresář je komprimován. Pro soubor komprese znamená, že všechna data v souboru jsou komprimována. Pro adresář je komprese výchozí pro nově vytvořené soubory a podadresáře.

- FILE_ATTRIBUTE_DIRECTORY Soubor je adresář.

- FILE_ATTRIBUTE_NORMAL Soubor nemá nastaveny žádné další atributy. Tento atribut je platný pouze při použití samostatně. Všechny ostatní atributy souboru přepíší FILE_ATTRIBUTE_NORMAL:

- FILE_ATTRIBUTE_HIDDEN Soubor je skrytý. Nesmí být zahrnuta do běžného seznamu adresářů.

- FILE_ATTRIBUTE_READONLY Soubor je jen pro čtení. Aplikace mohou soubor číst, ale nemohou do něj zapisovat ani odstraňovat.

- FILE_ATTRIBUTE_SYSTEM Soubor je součástí operačního systému nebo je používán výhradně operačním systémem.

- FILE_ATTRIBUTE_TEMPORARY Soubor se používá pro dočasné uložení. Aplikace by měly zapisovat do souboru pouze v případě, že je to nezbytně nutné. Většina dat souboru zůstává v paměti, aniž by byla vyprázdněna na médium, protože soubor bude brzy odstraněn.

*dwFlags*<br/>
Určuje podmínky, za kterých k přenosu dochází. Tento parametr může být libovolná z hodnot *dwFlags* popsaných v [souboru FtpGetFile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew) v sadě Windows SDK.

*dwKontext*<br/>
Identifikátor kontextu pro načítání souboru. Další informace o *dwContext*naleznete v **tématu Poznámky** .

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

### <a name="remarks"></a>Poznámky

`GetFile`je rutina vysoké úrovně, která zpracovává všechny režijní náklady spojené se čtením souboru ze serveru FTP a jeho ukládáním místně. Aplikace, které pouze načítají data souborů nebo které vyžadují `OpenFile` pečlivou kontrolu nad přenosem souborů, by měly používat a [CInternetFile::Read.](../../mfc/reference/cinternetfile-class.md#read)

Pokud *je FILE_TRANSFER_TYPE_ASCII dwFlags,* překlad dat souboru také převádí znaky ovládacího prvku a formátování na ekvivalenty systému Windows. Výchozí přenos je binární režim, kde je soubor stažen ve stejném formátu, který je uložen na serveru.

*Oba pstrRemoteFile* a *pstrLocalFile* může být buď částečně kvalifikované názvy souborů vzhledem k aktuálnímu adresáři nebo plně kvalifikované. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro oba názvy. `GetFile`převede oddělovače názvů adresářů na příslušné znaky před jejich použitím.

Přepište *výchozí hodnotu dwContext* a nastavte identifikátor kontextu na hodnotu podle vašeho výběru. Identifikátor kontextu je spojen s touto `CFtpConnection` konkrétní operací objektu vytvořeného jeho objektem [CInternetSession.](../../mfc/reference/cinternetsession-class.md) Hodnota je vrácena [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav operace, s níž je identifikován. Další informace o identifikátoru kontextu naleznete v článku [První kroky Internetu: WinInet.](../../mfc/wininet-basics.md)

## <a name="cftpconnectionopenfile"></a><a name="openfile"></a>CFtpConnection::OpenFile

Volánítéto členské funkce otevřete soubor umístěný na serveru FTP pro čtení nebo zápis.

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*název souboru pstrFile*<br/>
Ukazatel na řetězec obsahující název souboru, který má být otevřen.

*dwAccess*<br/>
Určuje, jak bude k souboru přistupováno. Může být buď GENERIC_READ nebo GENERIC_WRITE, ale ne obojí.

*dwFlags*<br/>
Určuje podmínky, za kterých dojde k následným přenosům. Může se jedná o některou z následujících FTP_TRANSFER_* konstanty:

- FTP_TRANSFER_TYPE_ASCII Přenos souborů pomocí metody přenosu FTP ASCII (typ A). Převede informace o ovládacím prvku a formátování na místní ekvivalenty.

- FTP_TRANSFER_TYPE_BINARY Soubor přenáší data pomocí metody přenosu obrazu FTP (typ I). Soubor přenáší data přesně tak, jak existuje, bez evidencí. Toto je výchozí metoda přenosu.

*dwKontext*<br/>
Identifikátor kontextu pro otevření souboru. Další informace o *dwContext*naleznete v **tématu Poznámky** .

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CInternetFile.](../../mfc/reference/cinternetfile-class.md)

### <a name="remarks"></a>Poznámky

`OpenFile`by měly být použity v následujících situacích:

- Aplikace obsahuje data, která je třeba odeslat a vytvořit jako soubor na serveru FTP, ale tato data nejsou v místním souboru. Jakmile `OpenFile` aplikace otevře soubor, použije [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write) k odeslání dat souboru FTP na server.

- Aplikace musí načíst soubor ze serveru a umístit jej do paměti řízené aplikací, namísto zápisu na disk. Aplikace používá [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) `OpenFile` po použití k otevření souboru.

- Aplikace potřebuje jemnou úroveň kontroly nad přenosem souborů. Aplikace může například chtít zobrazit ovládací prvek průběhu, který označuje průběh stavu přenosu souboru při stahování souboru.

Po `OpenFile` volání a `CInternetConnection::Close`do volání může aplikace volat pouze [CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read) `CInternetConnection::Close`, [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write), , nebo [CFtpFileFind::FindFile](../../mfc/reference/cftpfilefind-class.md#findfile). Volání jiných funkcí FTP pro stejnou relaci FTP se nezdaří a nastaví kód chyby na FTP_ETRANSFER_IN_PROGRESS.

Parametr *pstrFileName* může být částečně kvalifikovaný název souboru vzhledem k aktuálnímu adresáři nebo plně kvalifikovaný. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro oba názvy. `OpenFile`převede oddělovače názvů adresářů na příslušné znaky před jeho použitím.

Přepište *výchozí hodnotu dwContext* a nastavte identifikátor kontextu na hodnotu podle vašeho výběru. Identifikátor kontextu je spojen s touto `CFtpConnection` konkrétní operací objektu vytvořeného jeho objektem [CInternetSession.](../../mfc/reference/cinternetsession-class.md) Hodnota je vrácena [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav operace, s níž je identifikován. Další informace o identifikátoru kontextu naleznete v článku [První kroky Internetu: WinInet.](../../mfc/wininet-basics.md)

## <a name="cftpconnectionputfile"></a><a name="putfile"></a>CFtpConnection::PutFile

Volání této členské funkce pro uložení souboru na serveru FTP.

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pstrLocalFile*<br/>
Ukazatel na řetězec obsahující název souboru odeslaného z místního systému.

*soubor pstrRemoteFile*<br/>
Ukazatel na řetězec obsahující název souboru, který má být na serveru FTP vytvořit.

*dwFlags*<br/>
Určuje podmínky, za kterých dojde k přenosu souboru. Může to být libovolná FTP_TRANSFER_* konstantami popsanými v [OpenFile](#openfile).

*dwKontext*<br/>
Identifikátor kontextu pro umístění souboru. Další informace o *dwContext*naleznete v **tématu Poznámky** .

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

### <a name="remarks"></a>Poznámky

`PutFile`je rutina vysoké úrovně, která zpracovává všechny operace spojené s ukládáním souboru na server FTP. Aplikace, které odesílají pouze data nebo vyžadují bližší kontrolu nad přenosem souborů, by měly používat [OpenFile](#openfile) a [CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write).

Přepište `dwContext` výchozí nastavení identifikátoru kontextu na hodnotu podle vašeho výběru. Identifikátor kontextu je spojen s touto `CFtpConnection` konkrétní operací objektu vytvořeného jeho objektem [CInternetSession.](../../mfc/reference/cinternetsession-class.md) Hodnota je vrácena [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav operace, s níž je identifikován. Další informace o identifikátoru kontextu naleznete v článku [První kroky Internetu: WinInet.](../../mfc/wininet-basics.md)

## <a name="cftpconnectionremove"></a><a name="remove"></a>CFtpConnection::Odebrat

Voláním této členské funkce odstraňte zadaný soubor z připojeného serveru.

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>Parametry

*název souboru pstrFile*<br/>
Ukazatel na řetězec obsahující název souboru, který chcete odebrat.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

### <a name="remarks"></a>Poznámky

Parametr *pstrFileName* může být částečně kvalifikovaný název souboru vzhledem k aktuálnímu adresáři nebo plně kvalifikovaný. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro oba názvy. Funkce `Remove` převede oddělovače názvů adresářů na příslušné znaky před jejich použitím.

## <a name="cftpconnectionremovedirectory"></a><a name="removedirectory"></a>CFtpConnection::RemoveDirectory

Voláním této členské funkce odeberte zadaný adresář z připojeného serveru.

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName*<br/>
Ukazatel na řetězec obsahující adresář, který má být odebrán.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

### <a name="remarks"></a>Poznámky

Pomocí [funkce GetCurrentDirectory](#getcurrentdirectory) určete aktuální pracovní adresář serveru. Nepředpokládejte, že vás vzdálený systém připojil ke kořenovému adresáři.

Parametr *pstrDirName* může být částečně nebo plně kvalifikovaný název souboru vzhledem k aktuálnímu adresáři. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro oba názvy. `RemoveDirectory`převede oddělovače názvů adresářů na příslušné znaky před jejich použitím.

## <a name="cftpconnectionrename"></a><a name="rename"></a>CFtpConnection::Přejmenovat

Voláním této členské funkce přejmenujte zadaný soubor na připojeném serveru.

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>Parametry

*pstrExistující*<br/>
Ukazatel na řetězec obsahující aktuální název souboru, který má být přejmenován.

*pstrNovinka*<br/>
Ukazatel na řetězec obsahující nový název souboru.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

### <a name="remarks"></a>Poznámky

Parametry *pstrExisting* a *pstrNew* mohou být částečně kvalifikovanýnázev souboru vzhledem k aktuálnímu adresáři nebo plně kvalifikované. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro oba názvy. `Rename`převede oddělovače názvů adresářů na příslušné znaky před jejich použitím.

## <a name="cftpconnectionsetcurrentdirectory"></a><a name="setcurrentdirectory"></a>CFtpConnection::SetCurrentDirectory

Voláním této členské funkce převolejte na jiný adresář na serveru FTP.

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>Parametry

*pstrDirName*<br/>
Ukazatel na řetězec obsahující název adresáře.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

### <a name="remarks"></a>Poznámky

Parametr *pstrDirName* může být částečně nebo plně kvalifikovaný název souboru vzhledem k aktuálnímu adresáři. Zpětné lomítko (\\) nebo lomítko (/) lze použít jako oddělovač adresáře pro oba názvy. `SetCurrentDirectory`převede oddělovače názvů adresářů na příslušné znaky před jejich použitím.

Pomocí [funkce GetCurrentDirectory](#getcurrentdirectory) určete aktuální pracovní adresář serveru FTP. Nepředpokládejte, že vás vzdálený systém připojil ke kořenovému adresáři.

## <a name="see-also"></a>Viz také

[Třída CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession – třída](../../mfc/reference/cinternetsession-class.md)
