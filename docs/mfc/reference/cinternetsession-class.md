---
title: CInternetSession – třída
ms.date: 06/20/2018
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
ms.openlocfilehash: ddd7ca6676805e6de1b7afb5ebc77733701dfef9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372384"
---
# <a name="cinternetsession-class"></a>CInternetSession – třída

Vytvoří a inicializuje jednu nebo více souběžných internetových relací a v případě potřeby popisuje připojení k proxy serveru.

## <a name="syntax"></a>Syntaxe

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CInternetSession::CInternetSession](#cinternetsession)|Vytvoří `CInternetSession` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CInternetSession::Zavřít](#close)|Po ukončení relace Internetu ukončí připojení k Internetu.|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|Vytvoří rutinu zpětného volání stavu.|
|[CInternetSession::GetContext](#getcontext)|Po ukončení relace Internetu ukončí připojení k Internetu.|
|[CInternetSession::GetCookie](#getcookie)|Vrátí soubory cookie pro zadanou adresu URL a všechny její nadřazené adresy URL.|
|[CInternetSession::GetCookieLength](#getcookielength)|Načte proměnnou určující délku souboru cookie uloženého ve vyrovnávací paměti.|
|[CInternetSession::GetFtpConnection](#getftpconnection)|Otevře relaci FTP se serverem. Přihlásí uživatele.|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Otevře server gopher pro aplikaci, která se pokouší otevřít připojení.|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|Otevře server HTTP pro aplikaci, která se pokouší otevřít připojení.|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|Aktualizuje stav operace, pokud je povoleno zpětné volání stavu.|
|[CInternetSession::OpenURL](#openurl)|Analyzuje a otevře adresu URL.|
|[CInternetSession::SetCookie](#setcookie)|Nastaví soubor cookie pro zadanou adresu URL.|
|[CInternetSession::SetOption](#setoption)|Nastaví možnosti pro relaci Internetu.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CInternetSession::operátor HINTERNET](#operator_hinternet)|Popisovač aktuální relace Internetu.|

## <a name="remarks"></a>Poznámky

Pokud musí být připojení k Internetu udržováno po dobu `CInternetSession` trvání aplikace, můžete vytvořit člena třídy [CWinApp](../../mfc/reference/cwinapp-class.md).

Jakmile jste vytvořili relaci internetu, můžete volat [OpenURL](#openurl). `CInternetSession`pak analyzuje adresu URL za vás voláním globální funkce [AfxParseURL](internet-url-parsing-globals.md#afxparseurl). Bez ohledu na typ `CInternetSession` protokolu interpretuje adresu URL a spravuje ji za vás. Dokáže zpracovat požadavky na místní soubory označené zdrojem adresy URL "file://". `OpenURL`vrátí ukazatel na [cstdiofile](../../mfc/reference/cstdiofile-class.md) objektu, pokud název, který mu předáte je místní soubor.

Pokud otevřete adresu URL na `OpenURL`internetovém serveru pomocí aplikace , můžete číst informace z webu. Chcete-li u souborů umístěných na serveru provádět akce specifické pro danou službu (například HTTP, FTP nebo gopher), je nutné navázat příslušné připojení k tomuto serveru. Chcete-li otevřít určitý druh připojení přímo k určité službě, použijte jednu z následujících členských funkcí:

- [GetGopherConnection](#getgopherconnection) otevřít připojení ke službě gopher.

- [ZískejtehttpConnection](#gethttpconnection) pro otevření připojení ke službě HTTP.

- [GetFtpConnection](#getftpconnection) pro otevření připojení ke službě FTP.

[SetOption](#setoption) umožňuje nastavit možnosti dotazu relace, jako jsou například hodnoty časového limitu, počet opakování a tak dále.

`CInternetSession`členské funkce [SetCookie](#setcookie), [GetCookie](#getcookie)a [GetCookieLength](#getcookielength) poskytují prostředky pro správu databáze souborů cookie Win32, pomocí kterých servery a skripty udržují informace o stavu klientské pracovní stanice.

Další informace o základních úlohách programování v Internetu naleznete v článku [První kroky internetu: WinInet](../../mfc/wininet-basics.md). Obecné informace o použití tříd WinInet knihovny MFC naleznete v článku [Programování internetu pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).

> [!NOTE]
> `CInternetSession`vyvolá [afxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception) pro nepodporované typy služeb. V současné době jsou podporovány pouze následující typy služeb: FTP, HTTP, gopher a soubor.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="cinternetsessioncinternetsession"></a><a name="cinternetsession"></a>CInternetSession::CInternetSession

Tato členská funkce `CInternetSession` je volána při vytvoření objektu.

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
Ukazatel na řetězec, který identifikuje název aplikace nebo entity volající internetové funkce (například "Internetový prohlížeč Společnosti Microsoft"). Pokud *pstrAgent* je NULL (výchozí), rozhraní volá globální funkce [AfxGetAppName](application-information-and-management.md#afxgetappname), který vrátí řetězec ukončený null obsahující název aplikace. Některé protokoly používají tento řetězec k identifikaci aplikace na serveru.

*dwKontext*<br/>
Identifikátor kontextu pro operaci. *dwContext* identifikuje informace o stavu operace vrácené [CInternetSession::OnStatusCallback](#onstatuscallback). Výchozí hodnota je nastavena na hodnotu 1. můžete však explicitně přiřadit konkrétní ID kontextu pro operaci. Objekt a všechny práce, které provede, budou přidruženy k tomuto ID kontextu.

*dwAccessType*<br/>
Je vyžadován typ přístupu. Následující jsou platné hodnoty, přesně jednu z nich mohou být dodány:

- INTERNET_OPEN_TYPE_PRECONFIG Připojit pomocí předkonfigurovaných nastavení v registru. Tento typ přístupu je nastaven jako výchozí. Chcete-li se připojit prostřednictvím proxy serveru TIS, nastavte *dwAccessType* na tuto hodnotu; potom odpovídajícím způsobem nastavíte registr.

- INTERNET_OPEN_TYPE_DIRECT Připojte se přímo k Internetu.

- INTERNET_OPEN_TYPE_PROXY Connect prostřednictvím proxy serveru CERN.

Informace o připojení k různým typům proxy serverů naleznete [v tématu Kroky v typické klientské aplikaci FTP](../../mfc/steps-in-a-typical-ftp-client-application.md).

*pstrProxyName*<br/>
Název upřednostňovaného proxy serveru CERN, pokud je *dwAccessType* nastaven jako INTERNET_OPEN_TYPE_PROXY. Výchozí hodnota je NULL.

*pstrProxyBypass*<br/>
Ukazatel na řetězec obsahující volitelný seznam adres serveru. Tyto adresy mohou být vynechány při použití přístupu k serveru proxy. Pokud je zadána hodnota NULL, seznam obtoku bude přečten z registru. Tento parametr je smysluplný pouze v *případě, že dwAccessType* je nastavena na INTERNET_OPEN_TYPE_PROXY.

*dwFlags*<br/>
Označuje různé možnosti ukládání do mezipaměti. Výchozí hodnota je nastavena na hodnotu 0. Mezi možné hodnoty patří:

- INTERNET_FLAG_DONT_CACHE Neukládat data do mezipaměti, místně ani na žádných serverech brány.

- INTERNET_FLAG_OFFLINE operace stahování jsou splněny pouze prostřednictvím trvalé mezipaměti. Pokud položka v mezipaměti neexistuje, je vrácen příslušný kód chyby. Tento příznak může být kombinován s bitovým operátorem **OR** ( **&#124;). **

### <a name="remarks"></a>Poznámky

`CInternetSession`je první funkce Internetu volaná aplikací. Inicializuje vnitřní datové struktury a připravuje se na budoucí volání z aplikace.

Pokud nelze otevřít žádné `CInternetSession` připojení k Internetu, vyvolá [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

### <a name="example"></a>Příklad

Viz příklad pro [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessionclose"></a><a name="close"></a>CInternetSession::Zavřít

Volání této členské funkce po dokončení `CInternetSession` aplikace pomocí objektu.

```cpp
virtual void Close();
```

### <a name="example"></a>Příklad

Viz příklad pro [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessionenablestatuscallback"></a><a name="enablestatuscallback"></a>CInternetSession::EnableStatusCallback

Volání této členské funkce povolit zpětné volání stavu.

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, zda je zpětné volání povoleno nebo zakázáno. Výchozí hodnota je TRUE.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, zjistěte příčinu selhání kontrolou objektu [CInternetException.](../../mfc/reference/cinternetexception-class.md)

### <a name="remarks"></a>Poznámky

Při zpracování stavu zpětného volání, můžete poskytnout stav o průběhu operace (například překlad názvu, připojení k serveru a tak dále) ve stavovém řádku aplikace. Zobrazení provozního stavu je zvláště žádoucí při dlouhodobém provozu.

Vzhledem k tomu, že volání dojít během zpracování požadavku, aplikace by měla strávit co nejméně času v zpětném volání, aby se zabránilo zhoršení propustnost dat do sítě. Například umístění dialogového okna v zpětném volání může být tak zdlouhavá operace, že server ukončí požadavek.

Zpětné volání stavu nelze odebrat, pokud všechna zpětná volání čekají na vyřízení.

Chcete-li zpracovat všechny operace asynchronně, musíte buď vytvořit vlastní vlákno nebo použít wininet funkce bez knihovny MFC.

## <a name="cinternetsessiongetcontext"></a><a name="getcontext"></a>CInternetSession::GetContext

Volání této členské funkce získat hodnotu kontextu pro konkrétní relace aplikace.

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor kontextu definované aplikací.

### <a name="remarks"></a>Poznámky

[OnStatusCallback](#onstatuscallback) používá ID kontextu `GetContext` vrácené k nahlášení stavu určité aplikace. Pokud například uživatel aktivuje požadavek na Internet, který zahrnuje vrácení informací o stavu, zpětné volání stavu použije ID kontextu k hlášení stavu daného požadavku. Pokud uživatel aktivuje dva samostatné požadavky sítě Internet, které `OnStatusCallback` oba zahrnují vrácení informací o stavu, použije identifikátory kontextu k vrácení stavu odpovídajících požadavků. V důsledku toho se identifikátor kontextu používá pro všechny operace zpětného volání stavu a je přidružen k relaci, dokud není relace ukončena.

Další informace o asynchronních operacích naleznete v článku [Internet First Steps: WinInet](../../mfc/wininet-basics.md).

## <a name="cinternetsessiongetcookie"></a><a name="getcookie"></a>CInternetSession::GetCookie

Tato členská funkce implementuje chování funkce Win32 [InternetGetCookie](/windows/win32/api/wininet/nf-wininet-internetgetcookiew), jak je popsáno v sadě Windows SDK.

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

*název pstrCookieName*<br/>
Ukazatel na řetězec obsahující název souboru cookie získat pro zadanou adresu URL.

*pstrCookieData*<br/>
V prvním přetížení ukazatel na řetězec obsahující adresu vyrovnávací paměti, která přijímá data souboru cookie. Tato hodnota může být NULL. V druhé přetížení odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt přijímat data cookie.

*dwBufLen*<br/>
Proměnná určující velikost vyrovnávací paměti *pstrCookieData.* Pokud je funkce úspěšná, vyrovnávací paměť obdrží množství dat zkopírovaných do vyrovnávací paměti *pstrCookieData.* Pokud *pstrCookieData* je NULL, tento parametr obdrží hodnotu, která určuje velikost vyrovnávací paměti nezbytné ke zkopírování všech dat souboru cookie.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je úspěšná, jinak nehodnotit. Pokud se volání nezdaří, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) k určení příčiny chyby. Platí následující chybové hodnoty:

- ERROR_NO_MORE_ITEMS Pro zadanou adresu URL a všechny její rodiče neexistuje žádný soubor cookie.

- ERROR_INSUFFICIENT_BUFFER Hodnota předaná v *dwBufLen* je nedostatečná ke kopírování všech dat souboru cookie. Hodnota vrácená v *dwBufLen* je velikost vyrovnávací paměti nezbytné získat všechna data.

### <a name="remarks"></a>Poznámky

Při druhém přetížení knihovna MFC načte `CString` data souborů cookie do zadaného objektu.

## <a name="cinternetsessiongetcookielength"></a><a name="getcookielength"></a>CInternetSession::GetCookieLength

Volání této členské funkce získat délku souboru cookie uložené ve vyrovnávací paměti.

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>Parametry

*pstrUrl*<br/>
Ukazatel na řetězec obsahující adresu URL

*název pstrCookieName*<br/>
Ukazatel na řetězec obsahující název souboru cookie.

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD označující délku souboru cookie uložená ve vyrovnávací paměti. Nula, pokud neexistuje žádný soubor cookie s názvem označeným *pstrCookieName.*

### <a name="remarks"></a>Poznámky

Tato hodnota je používána [GetCookie](#getcookie).

## <a name="cinternetsessiongetftpconnection"></a><a name="getftpconnection"></a>CInternetSession::GetFtpConnection

Volání této členské funkce navázat připojení FTP a `CFtpConnection` získat ukazatel na objekt.

```cpp
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>Parametry

*server pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru FTP.

*pstrUserName*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který určuje jméno uživatele, který se má přihlásit. Pokud null, výchozí hodnota je anonymní.

*pstrPassword*<br/>
Ukazatel na řetězec s nulovým ukončením, který určuje heslo, které se má použít k přihlášení. Pokud jsou *hodnota pstrPassword* i *pstrUserName* null, je výchozím anonymním heslem e-mailové jméno uživatele. Pokud *pstrPassword* je NULL (nebo prázdný řetězec), ale *pstrUserName* není NULL, je použito prázdné heslo. Následující tabulka popisuje chování pro čtyři možná nastavení *pstrUserName* a *pstrPassword*:

| *pstrUserName*  | *pstrPassword*  | Uživatelské jméno odeslané serveru FTP | Heslo odeslané na server FTP |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   Null nebo " "   |   Null nebo " "   |         "anonymní"         |      E-mailová značka uživatele      |
| Řetězec bez hodnoty NULL |   Null nebo " "   |       *pstrUserName*        |             " "             |
|      NULL       | Řetězec bez hodnoty NULL |            ERROR            |            ERROR            |
| Řetězec bez hodnoty NULL | Řetězec bez hodnoty NULL |       *pstrUserName*        |       *pstrPassword*        |

*nPort*<br/>
Číslo, které identifikuje port TCP/IP, který má být na serveru používán.

*bPasivní*<br/>
Určuje pasivní nebo aktivní režim pro tuto relaci FTP. Pokud je nastavena na hodnotu `dwFlag` TRUE, nastaví rozhraní API Win32 na INTERNET_FLAG_PASSIVE.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CFtpConnection.](../../mfc/reference/cftpconnection-class.md) Pokud se volání nezdaří, zjistěte příčinu selhání kontrolou objektu [CInternetException.](../../mfc/reference/cinternetexception-class.md)

### <a name="remarks"></a>Poznámky

`GetFtpConnection`připojí k serveru FTP a vytvoří a vrátí `CFTPConnection` ukazatel na objekt. Neprovádí žádnou konkrétní operaci na serveru. Pokud máte v úmyslu číst nebo zapisovat do souborů, například, je nutné provést tyto operace jako samostatné kroky. Informace o hledání souborů, otevírání souborů a čtení nebo zápisu do souborů naleznete v třídách [CFtpConnection](../../mfc/reference/cftpconnection-class.md) a [CFtpFileFind.](../../mfc/reference/cftpfilefind-class.md) Postup provádění běžných úloh připojení FTP naleznete v článku [Internetové programování pomocí wininetu.](../../mfc/win32-internet-extensions-wininet.md)

### <a name="example"></a>Příklad

Viz příklad pro [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="cinternetsessiongetgopherconnection"></a><a name="getgopherconnection"></a>CInternetSession::GetGopherConnection

Volání této členské funkce vytvořit nové připojení gopher `CGopherConnection` a získat ukazatel na objekt.

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Parametry

*server pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru gopher.

*pstrUserName*<br/>
Ukazatel na řetězec obsahující uživatelské jméno.

*pstrPassword*<br/>
Ukazatel na řetězec obsahující přístupové heslo.

*nPort*<br/>
Číslo, které identifikuje port TCP/IP, který má být na serveru používán.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CGopherConnection.](../../mfc/reference/cgopherconnection-class.md) Pokud se volání nezdaří, zjistěte příčinu selhání kontrolou objektu [CInternetException.](../../mfc/reference/cinternetexception-class.md)

### <a name="remarks"></a>Poznámky

`GetGopherConnection`připojí k serveru gopher a vytvoří a vrátí `CGopherConnection` ukazatel na objekt. Neprovádí žádnou konkrétní operaci na serveru. Pokud máte v úmyslu například číst nebo zapisovat data, je nutné provést tyto operace jako samostatné kroky. Informace o hledání souborů, otevírání souborů a čtení nebo zápisu do souborů naleznete v třídách [CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile](../../mfc/reference/cgopherfile-class.md)a [CGopherFileFind.](../../mfc/reference/cgopherfilefind-class.md) Informace o procházení serveru FTP naleznete v členské funkci [OpenURL](#openurl). Postup při provádění běžných úloh připojení gopher naleznete v článku [Internetové programování s wininetem.](../../mfc/win32-internet-extensions-wininet.md)

## <a name="cinternetsessiongethttpconnection"></a><a name="gethttpconnection"></a>CInternetSession::GetHttpConnection

Volání této členské funkce navázat připojení HTTP a `CHttpConnection` získat ukazatel na objekt.

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

*server pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru HTTP.

*nPort*<br/>
Číslo, které identifikuje port TCP/IP, který má být na serveru používán.

*pstrUserName*<br/>
Ukazatel na řetězec obsahující uživatelské jméno.

*pstrPassword*<br/>
Ukazatel na řetězec obsahující přístupové heslo.

*dwflags*<br/>
Jakákoliv kombinace `INTERNET_FLAG_*` vlajek. Popis hodnot *dwFlags* naleznete v tabulce v části **Poznámky** [v chttpconnection::OpenRequest.](../../mfc/reference/chttpconnection-class.md#openrequest)

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CHttpConnection.](../../mfc/reference/chttpconnection-class.md) Pokud se volání nezdaří, zjistěte příčinu selhání kontrolou objektu [CInternetException.](../../mfc/reference/cinternetexception-class.md)

### <a name="remarks"></a>Poznámky

`GetHttpConnection`připojí k serveru HTTP a vytvoří a vrátí `CHttpConnection` ukazatel objektu. Neprovádí žádnou konkrétní operaci na serveru. Pokud máte v úmyslu dotaz na hlavičku HTTP, například, je nutné provést tuto operaci jako samostatný krok. Informace o operacích, které lze provádět pomocí připojení k http serveru, naleznete v třídách [CHttpConnection](../../mfc/reference/chttpconnection-class.md) a [CHttpFile.](../../mfc/reference/chttpfile-class.md) Informace o procházení webu HTTP naleznete v členské funkci [OpenURL](#openurl). Postup provádění běžných úloh připojení HTTP naleznete v článku Programování v Internetu [pomocí wininetu.](../../mfc/win32-internet-extensions-wininet.md)

## <a name="cinternetsessiononstatuscallback"></a><a name="onstatuscallback"></a>CInternetSession::OnStatusCallback

Tato členská funkce je volána rozhraním pro aktualizaci stavu, když je povoleno zpětné volání stavu a operace čeká na vyřízení.

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>Parametry

*dwKontext*<br/>
Hodnota kontextu dodaná aplikací.

*dwInternetStatus*<br/>
Stavový kód, který označuje, proč je zpětné volání právě provádí. Tabulka možných hodnot obsahuje následující informace **o poznámkách.**

*lpvStatusInformace*<br/>
Ukazatel na vyrovnávací paměť obsahující informace týkající se tohoto zpětného volání.

*dwStatusInformationLength*<br/>
Velikost *lpvStatusInformation*.

### <a name="remarks"></a>Poznámky

Chcete-li využít výhod zpětného volání stavu, musíte nejprve zavolat [EnableStatusCallback.](#enablestatuscallback)

Parametr *dwInternetStatus* označuje prováděnou operaci a určuje, jaký bude obsah *lpvStatusInformation.* *dwStatusInformationLength* označuje délku dat obsažených v *lpvStatusInformation*. Následující hodnoty stavu *pro dwInternetStatus* jsou definovány takto:

|Hodnota|Význam|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|Vyhledání IP adresy názvu obsaženého v *lpvStatusInformation*.|
|INTERNET_STATUS_NAME_RESOLVED|Adresa IP názvu obsaženého v *protokolu lpvStatusInformation byla úspěšně nalezena.*|
|INTERNET_STATUS_CONNECTING_TO_SERVER|Připojení k adrese soketu ([SOCKADDR),](/windows/win32/winsock/sockaddr-2)na které poukazuje *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTED_TO_SERVER|Úspěšně připojen k adrese soketu (SOCKADDR) ukázal *podle lpvStatusInformation*.|
|INTERNET_STATUS_SENDING_REQUEST|Odeslání žádosti o informace na server. Parametr *lpvStatusInformation* má hodnotu NULL.|
|INTERNET_STATUS_ REQUEST_SENT|Požadavek na informace byl úspěšně odeslán na server. Parametr *lpvStatusInformation* má hodnotu NULL.|
|INTERNET_STATUS_RECEIVING_RESPONSE|Čekání na server reagovat na požadavek. Parametr *lpvStatusInformation* má hodnotu NULL.|
|INTERNET_STATUS_RESPONSE_RECEIVED|Ze serveru byla úspěšně přijata odpověď. Parametr *lpvStatusInformation* má hodnotu NULL.|
|INTERNET_STATUS_CLOSING_CONNECTION|Ukončení připojení k serveru. Parametr *lpvStatusInformation* má hodnotu NULL.|
|INTERNET_STATUS_CONNECTION_CLOSED|Připojení k serveru bylo úspěšně ukončeno. Parametr *lpvStatusInformation* má hodnotu NULL.|
|INTERNET_STATUS_HANDLE_CREATED|Používá win32 api funkce [InternetConnect](/windows/win32/api/wininet/nf-wininet-internetconnectw) k označení, že vytvořil nový popisovač. To umožňuje aplikaci volat win32 funkce [InternetCloseHandle](/windows/win32/api/wininet/nf-wininet-internetclosehandle) z jiného vlákna, pokud připojení trvá příliš dlouho. Další informace o těchto funkcích naleznete v souboru Windows SDK.|
|INTERNET_STATUS_HANDLE_CLOSING|Tato hodnota popisovače byla úspěšně ukončena.|

Přepsat tuto členská funkci vyžadovat některé akce před provedením rutiny zpětného volání stavu.

> [!NOTE]
> Volání stavu vyžadují ochranu stavu vlákna. Pokud používáte knihovnu MFC ve sdílené knihovně, přidejte na začátek přepsání následující řádek:

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

Další informace o asynchronních operacích naleznete v článku [Internet First Steps: WinInet](../../mfc/wininet-basics.md).

## <a name="cinternetsessionopenurl"></a><a name="openurl"></a>CInternetSession::OpenURL

Volání této členské funkce odeslat zadaný požadavek na server HTTP a umožnit klientovi zadat další RFC822, MIME nebo HTTP záhlaví odeslat spolu s požadavkem.

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
Ukazatel na název adresy URL začít číst. Podporovány jsou pouze adresy URL začínající na file:, ftp:, gopher:, nebo http: jsou podporovány. Nepodmíněný, pokud *je hodnota* null.

*dwKontext*<br/>
Hodnota definovaná aplikací předaná s vráceným popisovačem v zpětném volání.

*dwFlags*<br/>
Příznaky popisující, jak zpracovat toto připojení. Další informace o platných vlajkách naleznete v **tématu Poznámky.** Platné příznaky jsou:

- INTERNET_FLAG_TRANSFER_ASCII Výchozí nastavení. Přeneste soubor jako text ASCII.

- INTERNET_FLAG_TRANSFER_BINARY Přenést soubor jako binární soubor.

- INTERNET_FLAG_RELOAD Získejte data z drátu, i když je místně uložena do mezipaměti.

- INTERNET_FLAG_DONT_CACHE Neukládat data do mezipaměti, místně ani v žádné braně.

- INTERNET_FLAG_SECURE Tento příznak se vztahuje pouze na požadavky HTTP. Požaduje zabezpečené transakce na lince pomocí sschlovací vrstvy nebo PCT.

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT Pokud je to možné, znovu použijte existující připojení `OpenUrl` k serveru pro nové požadavky generované namísto vytvoření nové relace pro každý požadavek na připojení.

- INTERNET_FLAG_PASSIVE Používá se pro server FTP. Používá pasivní ftp sémantiku. Používá se s `OpenURL` [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) of .

*hlavičky str*<br/>
Ukazatel na řetězec obsahující záhlaví, která mají být odeslána na server HTTP.

*dwHeadersLength*<br/>
Délka, ve znacích, další záhlaví. Pokud je to -1L a *pstrHeaders* je non-NULL, pak *pstrHeaders* se předpokládá, že nula ukončena a délka je vypočtena.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač souboru pouze pro internetové služby TYPU FTP, GOPHER, HTTP a FILE. Vrátí hodnotu NULL, pokud byla analýza neúspěšná.

Ukazatel, `OpenURL` který vrátí, závisí na typu služby *pstrURL.* Níže uvedená tabulka ukazuje `OpenURL` možné ukazatele mohou vrátit.

|Typ adresy URL|Vrací|
|--------------|-------------|
|`file://`|`CStdioFile*`|
|`http://`|`CHttpFile*`|
|`gopher://`|`CGopherFile*`|
|`ftp://`|`CInternetFile*`|

### <a name="remarks"></a>Poznámky

Parametr *dwFlags* musí obsahovat buď INTERNET_FLAG_TRANSFER_ASCII nebo INTERNET_FLAG_TRANSFER_BINARY, ale ne obojí. Zbývající příznaky lze kombinovat s bitovým operátorem **OR** ( **&#124;**).

`OpenURL`, který zabalí funkci `InternetOpenURL`Win32 , umožňuje pouze stahování, načítání a čtení dat z internetového serveru. `OpenURL`neumožňuje žádnou manipulaci se soubory ve vzdáleném umístění, takže nevyžaduje žádný objekt [CInternetConnection.](../../mfc/reference/cinternetconnection-class.md)

Chcete-li použít funkce specifické pro připojení (tj. specifické pro protokol), jako je například zápis do souboru, musíte otevřít relaci a potom otevřít určitý druh připojení a potom toto připojení použít k otevření souboru v požadovaném režimu. Další `CInternetConnection` informace o funkcích specifických pro připojení naleznete v tématu.

## <a name="cinternetsessionoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetSession::operátor HINTERNET

Pomocí tohoto operátoru získáte popisovač systému Windows pro aktuální relaci Internetu.

```cpp
operator HINTERNET() const;
```

## <a name="cinternetsessionsetcookie"></a><a name="setcookie"></a>CInternetSession::SetCookie

Nastaví soubor cookie pro zadanou adresu URL.

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>Parametry

*pstrUrl*<br/>
Ukazatel na řetězec s nulovým ukončením, který určuje adresu URL, pro kterou by měl být soubor cookie nastaven.

*název pstrCookieName*<br/>
Ukazatel na řetězec obsahující název souboru cookie.

*pstrCookieData*<br/>
Ukazatel na řetězec obsahující skutečná data řetězce, která chcete přidružit k adrese URL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je úspěšná, jinak nehodnotit. Chcete-li získat konkrétní kód chyby, zavolejte`GetLastError.`

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [InternetSetCookie](/windows/win32/api/wininet/nf-wininet-internetsetcookiew), jak je popsáno v sadě Windows SDK.

## <a name="cinternetsessionsetoption"></a><a name="setoption"></a>CInternetSession::SetOption

Voláním této členské funkce nastavte možnosti pro relaci Internetu.

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

*Dwoption*<br/>
Možnost Internetu nastavit. Seznam [možných](/windows/win32/WinInet/option-flags) možností najdete v tématu Příznaky možností v sadě Windows SDK.

*lpBuffer*<br/>
Vyrovnávací paměť, která obsahuje nastavení možnosti.

*dwBufferLength*<br/>
Délka *lpBuffer* nebo velikost *dwValue*.

*dwValue*<br/>
DWORD, který obsahuje nastavení možnosti.

*dwFlags*<br/>
Označuje různé možnosti ukládání do mezipaměti. Výchozí hodnota je nastavena na hodnotu 0. Mezi možné hodnoty patří:

- INTERNET_FLAG_DONT_CACHE Neukládat data do mezipaměti, místně ani na žádných serverech brány.

- INTERNET_FLAG_OFFLINE operace stahování jsou splněny pouze prostřednictvím trvalé mezipaměti. Pokud položka v mezipaměti neexistuje, je vrácen příslušný kód chyby. Tento příznak může být kombinován s bitovým operátorem **OR** ( **&#124;). **

### <a name="return-value"></a>Návratová hodnota

Pokud byla operace úspěšná, je vrácena hodnota TRUE. Pokud došlo k chybě, je vrácena hodnota FALSE. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Třída Připojení Chttp](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection – třída](../../mfc/reference/cftpconnection-class.md)<br/>
[Třída CGopherConnection](../../mfc/reference/cgopherconnection-class.md)
