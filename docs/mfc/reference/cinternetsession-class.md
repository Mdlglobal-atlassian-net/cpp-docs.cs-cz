---
title: Cinternetsession – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 06/20/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CInternetSession
- AFXINET/CInternetSession
- AFXINET/CInternetSession::CInternetSession
- AFXINET/CInternetSession::Close
- AFXINET/CInternetSession::EnableStatusCallback
- AFXINET/CInternetSession::GetContext
- AFXINET/CInternetSession::GetCookie
- AFXINET/CInternetSession::GetCookieLength
- AFXINET/CInternetSession::GetFtpConnection
- AFXINET/CInternetSession::GetGopherConnection
- AFXINET/CInternetSession::GetHttpConnection
- AFXINET/CInternetSession::OnStatusCallback
- AFXINET/CInternetSession::OpenURL
- AFXINET/CInternetSession::SetCookie
- AFXINET/CInternetSession::SetOption
dev_langs:
- C++
helpviewer_keywords:
- CInternetSession [MFC], CInternetSession
- CInternetSession [MFC], Close
- CInternetSession [MFC], EnableStatusCallback
- CInternetSession [MFC], GetContext
- CInternetSession [MFC], GetCookie
- CInternetSession [MFC], GetCookieLength
- CInternetSession [MFC], GetFtpConnection
- CInternetSession [MFC], GetGopherConnection
- CInternetSession [MFC], GetHttpConnection
- CInternetSession [MFC], OnStatusCallback
- CInternetSession [MFC], OpenURL
- CInternetSession [MFC], SetCookie
- CInternetSession [MFC], SetOption
ms.assetid: ef54feb4-9d0f-4e65-a45d-7a4cf6c40e51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a519d9b978f5b48377b1a85d52274cba35c9d075
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401800"
---
# <a name="cinternetsession-class"></a>Cinternetsession – třída

Vytvoří a inicializuje jednu nebo několik souběžných relací Internetu a v případě potřeby popisuje připojení k proxy serveru.

## <a name="syntax"></a>Syntaxe

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CInternetSession::CInternetSession](#cinternetsession)|Vytvoří `CInternetSession` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CInternetSession::Close](#close)|Zavře připojení k Internetu Internet relace je ukončena.|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|Vytváří rutina zpětného volání stavu.|
|[CInternetSession::GetContext](#getcontext)|Zavře připojení k Internetu Internet relace je ukončena.|
|[CInternetSession::GetCookie](#getcookie)|Vrátí soubory cookie pro zadanou adresu URL a všechny jeho nadřazený objekt adresy URL.|
|[CInternetSession::GetCookieLength](#getcookielength)|Načte proměnnou určující délku souboru cookie uloženého ve vyrovnávací paměti.|
|[CInternetSession::GetFtpConnection](#getftpconnection)|Otevře se relace FTP se serverem. Přihlášení uživatele.|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Otevře se gopher serveru pro aplikaci, která se pokouší otevřít připojení.|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|Otevře se server HTTP pro aplikace, která se pokouší otevřít připojení.|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|Aktualizuje stav operace, když je povolený stav zpětného volání.|
|[CInternetSession::OpenURL](#openurl)|Analyzuje a otevře adresu URL.|
|[CInternetSession::SetCookie](#setcookie)|Nastaví soubor cookie pro zadanou adresu URL.|
|[CInternetSession::SetOption](#setoption)|Nastaví možnosti pro relaci Internet.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CInternetSession::operator HINTERNET](#operator_hinternet)|Popisovač s aktuální relací Internetu.|

## <a name="remarks"></a>Poznámky

Pokud vaše připojení k Internetu, musí být zachována po dobu trvání aplikace, můžete vytvořit `CInternetSession` člena třídy [CWinApp](../../mfc/reference/cwinapp-class.md).

Jakmile ověříte relace k Internetu, můžete volat [OpenURL](#openurl). `CInternetSession` pak analyzuje adresu URL pro vás voláním globální funkce [afxparseurl –](internet-url-parsing-globals.md#afxparseurl). Bez ohledu na její typ protokolu `CInternetSession` interpretuje adresu URL a spravuje za vás. To může zpracovávat požadavky pro místní soubory identifikované pomocí adresy URL prostředku "file://". `OpenURL` vrátí ukazatel [cstdiofile –](../../mfc/reference/cstdiofile-class.md) objektu, pokud název předat je do místního souboru.

Pokud je otevřít na adresu URL na serveru Internetu pomocí `OpenURL`, si můžete přečíst informace z webu. Pokud chcete provádět konkrétní službu (pro příklad, protokolu HTTP, FTP nebo gopher) na soubory umístěné na serveru, je potřeba vytvořit na příslušné připojení s tímto serverem. Pokud chcete otevřít konkrétní typ připojení přímo do konkrétní služby, použijte jednu z následujících členské funkce:

- [GetGopherConnection](#getgopherconnection) k otevření připojení ke službě gopher.

- [GetHttpConnection](#gethttpconnection) k otevření připojení ke službě HTTP.

- [GetFtpConnection](#getftpconnection) k otevření připojení ke službě FTP.

[SetOption –](#setoption) umožňuje nastavit možnosti dotazu relace, jako jsou hodnoty časového limitu, počet opakovaných pokusů a tak dále.

`CInternetSession` Členské funkce [SetCookie](#setcookie), [GetCookie](#getcookie), a [GetCookieLength](#getcookielength) poskytují způsob, jak spravovat databázi souboru cookie Win32, pomocí kterého spravovat servery a skripty informace o klientské pracovní stanice stavu.

Další informace o základní Internet programovacích úloh, najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md). Obecné informace o pomocí tříd WinInet knihovny MFC, najdete v článku [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).

> [!NOTE]
> `CInternetSession` vyvolá výjimku [afxthrownotsupportedexception –](exception-processing.md#afxthrownotsupportedexception) pro typy nepodporované služeb. Aktuálně jsou podporovány pouze následující typy služeb: FTP, HTTP, gopher a soubor.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="cinternetsession"></a> CInternetSession::CInternetSession

Tato členská funkce je volána, když `CInternetSession` je vytvořen objekt.

```cpp
CInternetSession(
    LPCTSTR pstrAgent = NULL,
    DWORD_PTR dwContext = 1,
    DWORD dwAccessType = PRE_CONFIG_INTERNET_ACCESS,
    LPCTSTR pstrProxyName = NULL,
    LPCTSTR pstrProxyBypass = NULL,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parametry

*pstrAgent*<br/>
Ukazatel na řetězec, který určuje název aplikace nebo entity volání funkcí Internetu (například "Microsoft internetovém prohlížeči"). Pokud *pstrAgent* má hodnotu NULL (výchozí), rámec volá funkci globální [afxgetappname –](application-information-and-management.md#afxgetappname), která vrací řetězec zakončený hodnotou null obsahující název aplikace. Některé protokoly použít tento řetězec k identifikaci vaší aplikace na server.

*dwContext*<br/>
Identifikátor kontextu operace. *dwContext* identifikuje informace o stavu operace vracené [CInternetSession::OnStatusCallback](#onstatuscallback). Výchozí hodnota je nastavená na 1; Můžete však explicitně přiřadit konkrétní kontext ID operace. Objekt a veškerou práci, kterou provádí bude spojená s ID tohoto kontextu.

*dwAccessType*<br/>
Typ přístupu vyžaduje. Následují platné hodnoty, může být zadána přesně jeden z nich:

- INTERNET_OPEN_TYPE_PRECONFIG připojení pomocí předem nakonfigurovaných nastavení v registru. Tento typ přístupu je nastaven jako výchozí. Připojit přes proxy server je čas nastavit *dwAccessType* na tuto hodnotu; poté nastavíte registru odpovídajícím způsobem.

- INTERNET_OPEN_TYPE_DIRECT připojit přímo k Internetu.

- Připojte se přes proxy server CERN INTERNET_OPEN_TYPE_PROXY.

Informace o připojení s různými typy proxy serverů najdete v tématu [postup v typické aplikaci klienta FTP](../../mfc/steps-in-a-typical-ftp-client-application.md).

*pstrProxyName*<br/>
Název proxy upřednostňované CERN Pokud *dwAccessType* je nastaven jako INTERNET_OPEN_TYPE_PROXY. Výchozí hodnota je NULL.

*pstrProxyBypass*<br/>
Ukazatel na řetězec obsahující volitelný seznam adres serveru. Tyto adresy může obejít, při použití proxy serveru přístup. Pokud není zadána hodnota NULL, seznam obcházení bude číst z registru. Tento parametr má smysl pouze v případě *dwAccessType* je nastavena na INTERNET_OPEN_TYPE_PROXY.

*dwFlags*<br/>
Určuje různé možnosti ukládání do mezipaměti. Výchozí hodnota je nastavena na hodnotu 0. Možné hodnoty:

- INTERNET_FLAG_DONT_CACHE Neukládat do mezipaměti dat, místně nebo v veškeré servery brány.

- Stáhnout INTERNET_FLAG_OFFLINE operace jsou splněny prostřednictvím trvalého mezipaměti. Pokud položka v mezipaměti neexistuje, vrátí se odpovídající chybový kód. Tento příznak může kombinované pomocí bitového **nebo** ( **&#124;**) – operátor.

### <a name="remarks"></a>Poznámky

`CInternetSession` první funkce Internet volány aplikace. Inicializuje interních datových struktur a připraví pro budoucí volání z aplikace.

Pokud můžete otevřít žádné připojení k Internetu, `CInternetSession` vyvolá [afxthrowinternetexception –](internet-url-parsing-globals.md#afxthrowinternetexception).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [cftpfilefind –](../../mfc/reference/cftpfilefind-class.md).

## <a name="close"></a>  CInternetSession::Close

Po dokončení vaší aplikace pomocí zavolat tuto členskou funkci `CInternetSession` objektu.

```cpp
virtual void Close();
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [cftpfilefind –](../../mfc/reference/cftpfilefind-class.md).

## <a name="enablestatuscallback"></a>  CInternetSession::EnableStatusCallback

Voláním této členské funkce umožňující stav zpětného volání.

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, zda je povoleno zpětného volání. Výchozí hodnota je TRUE.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, zjistěte příčinu selhání tím, že kontroluje, k této výjimce dojde [cinternetexception –](../../mfc/reference/cinternetexception-class.md) objektu.

### <a name="remarks"></a>Poznámky

Při zpracovávání zpětného volání stav, můžete zadat informace o průběhu operace (například překladu názvu, připojení k serveru a tak dále) stavu ve stavovém řádku aplikace. Zobrazení stavu operace je žádoucí, zejména v průběhu dlouhodobé operace.

Vzhledem k tomu, že zpětná volání, k nimž došlo při zpracování požadavku, by měla aplikace tráví několika času je možné zpětné volání, aby se zabránilo snížení propustnosti dat k síti. Nabízení dialogovému oknu ve zpětném volání může třeba tyto operace může trvat dlouho, že server ukončí žádost.

Stav zpětného volání nelze odebrat, pokud jsou všechny zpětná volání čekající na vyřízení.

Na zpracování jakékoli operace asynchronně, musíte vytvořit vlastní vlákno nebo používají funkce rozhraní WinInet bez knihovny MFC.

## <a name="getcontext"></a>  CInternetSession::GetContext

Voláním této členské funkce má být získána hodnota kontext pro konkrétní aplikaci relace.

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Návratová hodnota

Definované aplikací kontextu identifikátor.

### <a name="remarks"></a>Poznámky

[Onstatuscallback –](#onstatuscallback) používá vrácené ID kontextu `GetContext` informuje o stavu konkrétní aplikaci. Například když uživatel aktivuje požadavek na Internetu, která zahrnuje vracení informací o stavu, stav zpětného volání používá ID kontextu účelem nahlášení stavu tohoto konkrétního požadavku. Pokud uživatel aktivuje dva samostatné Internet požadavků, obojí zahrnuje vracení informací o stavu `OnStatusCallback` pomocí identifikátorů kontextu návratový stav týkající se jejich odpovídajících požadavků. V důsledku toho identifikátor kontextu se používá pro všechny operace stav zpětného volání a je přidružená k relaci, dokud relace se ukončí.

Další informace o asynchronních operací, najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md).

## <a name="getcookie"></a>  CInternetSession::GetCookie

Tato členská funkce implementuje chování funkce Win32 [InternetGetCookie](/windows/desktop/api/wininet/nf-wininet-internetgetcookiea), jak je popsáno v sadě Windows SDK.

```cpp
static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPTSTR pstrCookieData,
    DWORD dwBufLen);


static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    CString& strCookieData);
```

### <a name="parameters"></a>Parametry

*pstrUrl*<br/>
Ukazatel na řetězec obsahující adresu URL.

*pstrCookieName*<br/>
Ukazatel na řetězec obsahující název souboru cookie, chcete-li získat pro zadané adresy URL.

*pstrCookieData*<br/>
V první přetížení ukazatel na řetězec obsahující adresu vyrovnávací paměti, která přijímá data souborů cookie. Tato hodnota může být NULL. V druhé přetížení, odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu pro příjem dat souboru cookie.

*dwBufLen*<br/>
Proměnná, určení velikosti *pstrCookieData* vyrovnávací paměti. Pokud funkce uspěje, vyrovnávací paměti přijímá množství dat, které jsou zkopírovány do *pstrCookieData* vyrovnávací paměti. Pokud *pstrCookieData* má hodnotu NULL, tento parametr přijímá hodnotu, která určuje velikost vyrovnávací paměti, která je nezbytná pro zkopírování všech dat souboru cookie.

### <a name="return-value"></a>Návratová hodnota

V opačném případě vrátí hodnotu PRAVDA, pokud je úspěšná, nebo FALSE. Pokud volání selže, zavolejte funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) a zjistěte příčinu chyby. Platí následující hodnoty Chyba:

- ERROR_NO_MORE_ITEMS neexistuje žádný soubor cookie pro zadanou adresu URL a všech jejích nadřazených tříd.

- Hodnota předaná v ERROR_INSUFFICIENT_BUFFER *dwBufLen* nepostačuje pro zkopírování všech dat souboru cookie. Hodnota vrácená v *dwBufLen* velikost vyrovnávací paměti je nezbytné získat všechna data.

### <a name="remarks"></a>Poznámky

V druhé přetížení MFC načítá data souborů cookie do zadané `CString` objektu.

## <a name="getcookielength"></a>  CInternetSession::GetCookieLength

Voláním této členské funkce získání délky souboru cookie uloženého ve vyrovnávací paměti.

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>Parametry

*pstrUrl*<br/>
Ukazatel na řetězec obsahující adresu URL

*pstrCookieName*<br/>
Ukazatel na řetězec obsahující název souboru cookie.

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD identifikující délku souboru cookie, uloženy ve vyrovnávací paměti. Nula, pokud žádný soubor cookie s názvem indikován *pstrCookieName* existuje.

### <a name="remarks"></a>Poznámky

Tato hodnota se používá ve [GetCookie](#getcookie).

## <a name="getftpconnection"></a>  CInternetSession::GetFtpConnection

Voláním této funkce připojení FTP a získání ukazatele na člena `CFtpConnection` objektu.

```cpp
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>Parametry

*pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru FTP.

*pstrUserName*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje jméno uživatele k přihlášení. Pokud má hodnotu NULL, výchozí hodnota je anonymous.

*pstrPassword*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje heslo pro použití k protokolování. Pokud mají oba *pstrPassword* a *pstrUserName* hodnotu Null, je výchozí heslo anonymní uživatelské jméno e-mailu. Pokud *pstrPassword* má hodnotu NULL (nebo prázdný řetězec), ale *pstrUserName* nemá hodnotu NULL, prázdné heslo se používá. Následující tabulka popisuje chování pro čtyři možných nastavení *pstrUserName* a *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Uživatelské jméno odeslané na FTP server|Heslo odeslaných na FTP server|
|--------------------|--------------------|---------------------------------|---------------------------------|
|Hodnotu NULL nebo ""|Hodnotu NULL nebo ""|"anonymní"|Uživatelské jméno e-mailu|
|Řetězec NENULOVÉ|Hodnotu NULL nebo ""|*pstrUserName*|" "|
|NULL|Řetězec NENULOVÉ|CHYBA|CHYBA||
|Řetězec NENULOVÉ|Řetězec NENULOVÉ|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Číslo, které identifikuje port TCP/IP pro použití na serveru.

*bPassive*<br/>
Určuje režim pasivní nebo aktivní pro tuto relaci serveru FTP. Pokud je nastavena na hodnotu TRUE, nastaví rozhraní API systému Win32 `dwFlag` k INTERNET_FLAG_PASSIVE.

### <a name="return-value"></a>Návratová hodnota

Ukazatel [cftpconnection –](../../mfc/reference/cftpconnection-class.md) objektu. Pokud volání selže, zjistěte příčinu selhání tím, že kontroluje, k této výjimce dojde [cinternetexception –](../../mfc/reference/cinternetexception-class.md) objektu.

### <a name="remarks"></a>Poznámky

`GetFtpConnection` se připojí k serveru FTP a vytvoří a vrátí ukazatel `CFTPConnection` objektu. Neprovede žádné konkrétní operaci na serveru. Pokud máte v úmyslu čtení nebo zápis do souborů, například je nutné provést tyto operace jako samostatné kroky. Zobrazit třídy [cftpconnection –](../../mfc/reference/cftpconnection-class.md) a [cftpfilefind –](../../mfc/reference/cftpfilefind-class.md) informace o vyhledávání souborů, otevírání souborů, čtení a zápis do souborů. Přečtěte si článek [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md) postup při provádění běžných úkolů připojení FTP.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [cftpfilefind –](../../mfc/reference/cftpfilefind-class.md).

## <a name="getgopherconnection"></a>  CInternetSession::GetGopherConnection

Voláním této funkce vytvořit nové připojení gopher a získání ukazatele na člena `CGopherConnection` objektu.

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Parametry

*pstrServer*<br/>
Ukazatel na řetězec obsahující název gopher serveru.

*pstrUserName*<br/>
Ukazatel na řetězec obsahující uživatelské jméno.

*pstrPassword*<br/>
Ukazatel na řetězec obsahující přístupové heslo.

*nPort*<br/>
Číslo, které identifikuje port TCP/IP pro použití na serveru.

### <a name="return-value"></a>Návratová hodnota

Ukazatel [cgopherconnection –](../../mfc/reference/cgopherconnection-class.md) objektu. Pokud volání selže, zjistěte příčinu selhání tím, že kontroluje, k této výjimce dojde [cinternetexception –](../../mfc/reference/cinternetexception-class.md) objektu.

### <a name="remarks"></a>Poznámky

`GetGopherConnection` připojí k serveru gopher a vytvoří a vrátí ukazatel `CGopherConnection` objektu. Neprovede žádné konkrétní operaci na serveru. Pokud chcete číst ani zapisovat data, například je nutné provést tyto operace jako samostatné kroky. Zobrazit třídy [cgopherconnection –](../../mfc/reference/cgopherconnection-class.md), [cgopherfile –](../../mfc/reference/cgopherfile-class.md), a [cgopherfilefind –](../../mfc/reference/cgopherfilefind-class.md) informace o vyhledávání souborů, otevírání souborů, čtení a zápis do souborů. Informace o procházení serveru FTP, naleznete v členské funkci [OpenURL](#openurl). Přečtěte si článek [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md) postup při provádění běžných úkolů gopher připojení.

## <a name="gethttpconnection"></a>  CInternetSession::GetHttpConnection

Voláním této funkce připojení HTTP a získání ukazatele na člena `CHttpConnection` objektu.

```cpp
CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);

CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);
```

### <a name="parameters"></a>Parametry

*pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru HTTP.

*nPort*<br/>
Číslo, které identifikuje port TCP/IP pro použití na serveru.

*pstrUserName*<br/>
Ukazatel na řetězec obsahující uživatelské jméno.

*pstrPassword*<br/>
Ukazatel na řetězec obsahující přístupové heslo.

*dwFlags*<br/>
Libovolnou kombinaci `INTERNET_FLAG_*` příznaky. Viz tabulka **poznámky** část [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) popis *dwFlags* hodnoty.

### <a name="return-value"></a>Návratová hodnota

Ukazatel [chttpconnection –](../../mfc/reference/chttpconnection-class.md) objektu. Pokud volání selže, zjistěte příčinu selhání tím, že kontroluje, k této výjimce dojde [cinternetexception –](../../mfc/reference/cinternetexception-class.md) objektu.

### <a name="remarks"></a>Poznámky

`GetHttpConnection` se připojí k serveru HTTP a vytvoří a vrátí ukazatel `CHttpConnection` objektu. Neprovede žádné konkrétní operaci na serveru. Pokud máte v úmyslu dotazování hlavičky protokolu HTTP, například musíte provést tuto operaci jako samostatný krok. Zobrazit třídy [chttpconnection –](../../mfc/reference/chttpconnection-class.md) a [chttpfile –](../../mfc/reference/chttpfile-class.md) informace o operacích, které můžete provést pomocí připojení k serveru HTTP. Informace o procházení serveru HTTP, naleznete v členské funkci [OpenURL](#openurl). Přečtěte si článek [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md) postup při provádění běžných úkolů připojení HTTP.

## <a name="onstatuscallback"></a>  CInternetSession::OnStatusCallback

Tato členská funkce se volá se rozhraním pro aktualizaci stavu, pokud je zapnuto stav zpětného volání a operace čeká na vyřízení.

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>Parametry

*dwContext*<br/>
Hodnota kontextového poskytnuté aplikací.

*dwInternetStatus*<br/>
Stavový kód, který označuje, proč je nastaven zpětného volání. Zobrazit **poznámky** pro tabulku možných hodnot.

*lpvStatusInformation*<br/>
Ukazatel do vyrovnávací paměti, který obsahuje informace, které jsou relevantní pro toto zpětné volání.

*dwStatusInformationLength*<br/>
Velikost *lpvStatusInformation*.

### <a name="remarks"></a>Poznámky

Nejprve je třeba volat [EnableStatusCallback](#enablestatuscallback) výhod stav zpětného volání.

*DwInternetStatus* parametr označuje právě prováděnou operaci a určuje, jaký obsah *lpvStatusInformation* bude. *dwStatusInformationLength* označuje délku dat zahrnutých v nabídce *lpvStatusInformation*. Následující stav hodnoty *dwInternetStatus* jsou definovány takto:

|Hodnota|Význam|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|Vyhledávání IP adresu jméno obsažené v *lpvStatusInformation*.|
|INTERNET_STATUS_NAME_RESOLVED|Úspěšně našli adresu IP názvu součástí *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTING_TO_SERVER|Připojení k soketu adresu ([sockaddr –](../../mfc/reference/sockaddr-structure.md)) ukazuje *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTED_TO_SERVER|Úspěšně připojeno k adresy soketu (sockaddr –), na které odkazuje *lpvStatusInformation*.|
|INTERNET_STATUS_SENDING_REQUEST|Žádost o informace se odesílají na server. *LpvStatusInformation* parametr hodnotu NULL.|
|INTERNET_STATUS_ REQUEST_SENT|Úspěšně se odeslal žádost o informace k serveru. *LpvStatusInformation* parametr hodnotu NULL.|
|INTERNET_STATUS_RECEIVING_RESPONSE|Čekání na odpověď na žádost o serveru. *LpvStatusInformation* parametr hodnotu NULL.|
|INTERNET_STATUS_RESPONSE_RECEIVED|Úspěšně obdržel odpověď ze serveru. *LpvStatusInformation* parametr hodnotu NULL.|
|INTERNET_STATUS_CLOSING_CONNECTION|Probíhá ukončování připojení k serveru. *LpvStatusInformation* parametr hodnotu NULL.|
|INTERNET_STATUS_CONNECTION_CLOSED|Připojení k serveru se úspěšně zavřelo. *LpvStatusInformation* parametr hodnotu NULL.|
|INTERNET_STATUS_HANDLE_CREATED|Používá funkce rozhraní Win32 API [InternetConnect](/windows/desktop/api/wininet/nf-wininet-internetconnecta) k označení, že byl vytvořen nový popisovač. Volání rozhraní Win32 funkce aplikací díky tomu [InternetCloseHandle](/windows/desktop/api/wininet/nf-wininet-internetclosehandle) z jiného vlákna, pokud připojení trvá moc dlouho. Další informace o těchto funkcích naleznete v tématu Windows SDKfor.|
|INTERNET_STATUS_HANDLE_CLOSING|Tato hodnota popisovač úspěšně ukončil.|

Potlačí tuto členskou funkci tak, aby vyžadovala některé akce před spuštěním rutiny stav zpětného volání.

> [!NOTE]
> Zpětná volání stav potřeba chránit stav vlákna. Pokud používáte knihovnu MFC ve sdílené knihovně, přidejte následující řádek na začátek přepsání:

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

Další informace o asynchronních operací, najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md).

## <a name="openurl"></a>  CInternetSession::OpenURL

Tento člen volání funkce Odeslat zadaný požadavek HTTP server a povolit klienta k určení dalších RFC822 MIME nebo hlavičky protokolu HTTP k odeslání společně se žádostí.

```cpp
CStdioFile* OpenURL(
    LPCTSTR pstrURL,
    DWORD_PTR dwContext = 1,
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLength = 0);
```

### <a name="parameters"></a>Parametry

*pstrURL*<br/>
Ukazatel na název adresy URL má začínat čtení. Pouze adresy URL začínající souborem:, ftp:, gopher:, nebo http: jsou podporovány. Vyhodnotí, pokud *pstrURL* má hodnotu NULL.

*dwContext*<br/>
Hodnotu definovaného aplikací se dokončila s Vrácený popisovač ve zpětném volání.

*dwFlags*<br/>
Příznaky popisující, jak zpracovávat toto připojení. Zobrazit **poznámky** Další informace o platné příznaky. Platný příznaky jsou:

- INTERNET_FLAG_TRANSFER_ASCII výchozí. Přeneste soubor jako ASCII text.

- INTERNET_FLAG_TRANSFER_BINARY přenos souboru jako binární soubor.

- INTERNET_FLAG_RELOAD získat data z přenosu i v případě, že je v místní mezipaměti.

- INTERNET_FLAG_DONT_CACHE Neukládat do mezipaměti dat, místně nebo v žádné brány.

- INTERNET_FLAG_SECURE tento příznak se vztahuje pouze na požadavky HTTP. Požadavky zabezpečení transakcí na lince Secure Sockets Layer nebo v PROC.

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT Pokud je to možné, opakovaně používat existující připojení k serveru pro nové požadavkům vygenerovaným rozhraním `OpenUrl` místo vytvoření nové relace pro každý požadavek na připojení.

- INTERNET_FLAG_PASSIVE použít pro server FTP. Používá sémantiku pasivního protokolu FTP. Použít s [cinternetconnection –](../../mfc/reference/cinternetconnection-class.md) z `OpenURL`.

*pstrHeaders*<br/>
Ukazatel na řetězec obsahující hlavičky k odeslání na HTTP server.

*dwHeadersLength*<br/>
Délka ve znacích, další záhlaví. Pokud je to L hodnota-1 a *pstrHeaders* je jiná než NULL, pak *pstrHeaders* se předpokládá, že nulovém ukončena a délka se počítá.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač souboru pro FTP, GOPHER, HTTP a typ souboru internetové služby. Vrátí hodnotu NULL, pokud byla analýza neúspěšných.

Ukazatel, který `OpenURL` vrátí závisí na *pstrURL*typ služby. Následující tabulka uvádí možné ukazatele `OpenURL` může vrátit.

|Typ adresy URL|Vrací|
|--------------|-------------|
|File://|`CStdioFile*`|
|http://|`CHttpFile*`|
|Gopher://|`CGopherFile*`|
|FTP: / /|`CInternetFile*`|

### <a name="remarks"></a>Poznámky

Parametr *dwFlags* musí obsahovat INTERNET_FLAG_TRANSFER_ASCII nebo INTERNET_FLAG_TRANSFER_BINARY, ale ne obojí. Zbývající příznaků je možné kombinovat s bitový **nebo** – operátor ( **&#124;**).

`OpenURL`, která zabalí funkci Win32 `InternetOpenURL`, umožňuje pouze stahování, načtení a čtení dat z internetového serveru. `OpenURL` umožňuje manipulaci s žádný soubor ve vzdáleném umístění, takže nevyžaduje žádné [cinternetconnection –](../../mfc/reference/cinternetconnection-class.md) objektu.

Použít specifickou pro připojení (to znamená, specifické pro protokol) funkce, jako je například zápis do souboru, musíte otevřete relaci, potom otevřete určitého druhu připojení a použít toto připojení k otevření souboru v požadovaného režimu. Zobrazit `CInternetConnection` Další informace o připojení specifické funkce.

## <a name="operator_hinternet"></a>  CInternetSession::operator HINTERNET

Tento operátor se získat popisovač Windows pro aktuální relaci Internet.

```cpp
operator HINTERNET() const;
```

## <a name="setcookie"></a>  CInternetSession::SetCookie

Nastaví soubor cookie pro zadanou adresu URL.

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>Parametry

*pstrUrl*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje adresu URL, u které je třeba nastavit soubor cookie.

*pstrCookieName*<br/>
Ukazatel na řetězec obsahující název souboru cookie.

*pstrCookieData*<br/>
Ukazatel na řetězec obsahující aktuální řetězcovou data k přidružení s adresou URL.

### <a name="return-value"></a>Návratová hodnota

V opačném případě vrátí hodnotu PRAVDA, pokud je úspěšná, nebo FALSE. Chcete-li získat chybový kód, zavolejte `GetLastError.`

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [InternetSetCookie](/windows/desktop/api/wininet/nf-wininet-internetsetcookiea), jak je popsáno v sadě Windows SDK.

## <a name="setoption"></a>  CInternetSession::SetOption

Voláním této členské funkce pro nastavení možností pro relaci Internet.

```cpp
BOOL SetOption(
    DWORD dwOption,
    LPVOID lpBuffer,
    DWORD dwBufferLength,
    DWORD dwFlags = 0);


BOOL SetOption(
    DWORD dwOption,
    DWORD dwValue,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parametry

*dwOption*<br/>
Internet možnost nastavit. Zobrazit [možnost příznaky](/windows/desktop/WinInet/option-flags) ve Windows SDKfor seznam dostupných možností.

*lpBuffer.*<br/>
Vyrovnávací paměť, která obsahuje nastavení možnosti.

*dwBufferLength*<br/>
Délka *lpBuffer* nebo velikost *dwValue*.

*dwValue*<br/>
DWORD, který obsahuje nastavení možnosti.

*dwFlags*<br/>
Určuje různé možnosti ukládání do mezipaměti. Výchozí hodnota je nastavena na hodnotu 0. Možné hodnoty:

- INTERNET_FLAG_DONT_CACHE Neukládat do mezipaměti dat, místně nebo v veškeré servery brány.

- Stáhnout INTERNET_FLAG_OFFLINE operace jsou splněny prostřednictvím trvalého mezipaměti. Pokud položka v mezipaměti neexistuje, vrátí se odpovídající chybový kód. Tento příznak může kombinované pomocí bitového **nebo** ( **&#124;**) – operátor.

### <a name="return-value"></a>Návratová hodnota

Pokud byla operace úspěšná, vrátí hodnotu true. Pokud došlo k chybě, vrátí se hodnota FALSE. Pokud volání selže, funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection – třída](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection – třída](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection – třída](../../mfc/reference/cgopherconnection-class.md)
