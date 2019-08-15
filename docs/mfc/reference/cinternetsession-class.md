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
ms.openlocfilehash: c9b8eaf51820dfcd08c1390c8645978fa403931d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505848"
---
# <a name="cinternetsession-class"></a>CInternetSession – třída

Vytvoří a inicializuje jednu nebo několik souběžných internetových relací a v případě potřeby popisuje připojení k proxy server.

## <a name="syntax"></a>Syntaxe

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CInternetSession::CInternetSession](#cinternetsession)|`CInternetSession` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CInternetSession:: Close](#close)|Zavře připojení k Internetu po ukončení relace Internetu.|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|Vytvoří rutinu zpětného volání stavu.|
|[CInternetSession:: GetContext](#getcontext)|Zavře připojení k Internetu po ukončení relace Internetu.|
|[CInternetSession:: GetCookie](#getcookie)|Vrátí soubory cookie pro zadanou adresu URL a všechny její nadřazené adresy URL.|
|[CInternetSession::GetCookieLength](#getcookielength)|Načte proměnnou určující délku souboru cookie uloženého ve vyrovnávací paměti.|
|[CInternetSession::GetFtpConnection](#getftpconnection)|Otevře relaci FTP se serverem. Přihlásí uživatele.|
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Otevře Server gopher pro aplikaci, která se pokouší otevřít připojení.|
|[CInternetSession::GetHttpConnection](#gethttpconnection)|Otevře Server HTTP pro aplikaci, která se pokouší otevřít připojení.|
|[CInternetSession::OnStatusCallback](#onstatuscallback)|Aktualizuje stav operace, když je povolené zpětné volání stavu.|
|[CInternetSession::OpenURL](#openurl)|Analyzuje a otevře adresu URL.|
|[CInternetSession::SetCookie](#setcookie)|Nastaví soubor cookie pro zadanou adresu URL.|
|[CInternetSession:: SetOption](#setoption)|Nastaví možnosti pro internetovou relaci.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CInternetSession:: operator HINTERNET](#operator_hinternet)|Popisovač aktuální internetové relace.|

## <a name="remarks"></a>Poznámky

Pokud je nutné vaše připojení k Internetu udržovat po dobu trvání aplikace, můžete vytvořit `CInternetSession` člena třídy [CWinApp](../../mfc/reference/cwinapp-class.md).

Jakmile vytvoříte internetovou relaci, můžete volat [OpenURL](#openurl). `CInternetSession`pak pro vás analyzuje adresu URL voláním globální funkce [AfxParseURL](internet-url-parsing-globals.md#afxparseurl). Bez ohledu na jeho typ `CInternetSession` protokolu interpretuje adresu URL a spravuje ji za vás. Může zpracovávat požadavky na místní soubory identifikované pomocí prostředku adresy URL "file://". `OpenURL`vrátí ukazatel na objekt [CStdioFile](../../mfc/reference/cstdiofile-class.md) , pokud je název, který předáte, místní soubor.

Pokud otevřete adresu URL na internetovém serveru pomocí nástroje `OpenURL`, můžete si přečíst informace z webu. Pokud chcete provádět akce specifické pro službu (například HTTP, FTP nebo gopher) u souborů umístěných na serveru, je nutné vytvořit příslušné připojení k tomuto serveru. Chcete-li otevřít konkrétní typ připojení přímo ke konkrétní službě, použijte jednu z následujících funkcí členů:

- [GetGopherConnection](#getgopherconnection) otevřete připojení ke službě Gopher.

- [GetHttpConnection](#gethttpconnection) otevřete připojení ke službě HTTP.

- [GetFtpConnection](#getftpconnection) otevřete připojení ke službě FTP.

Možnost [SetOption](#setoption) umožňuje nastavit možnosti dotazu pro relaci, například hodnoty časového limitu, počet opakovaných pokusů atd.

`CInternetSession`Členské funkce [SetCookie](#setcookie), [GetCookie](#getcookie)a [GetCookieLength](#getcookielength) poskytují prostředky pro správu databáze souborů cookie Win32, pomocí kterých servery a skripty udržují informace o stavu pracovní stanice klienta.

Další informace o základních úlohách programování v Internetu najdete v článku [Internet First Step: Rozhraní](../../mfc/wininet-basics.md)WinInet. Obecné informace o použití tříd WinInet knihovny MFC naleznete v článku [internetové programování s](../../mfc/win32-internet-extensions-wininet.md)rozhraním Wininet.

> [!NOTE]
> `CInternetSession`vyvolá [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception) pro nepodporované typy služeb. V současné době jsou podporovány pouze následující typy služeb: FTP, HTTP, gopher a soubor.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet. h

## <a name="cinternetsession"></a>CInternetSession::CInternetSession

Tato členská funkce se volá, `CInternetSession` když se vytvoří objekt.

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
Ukazatel na řetězec, který určuje název aplikace nebo entity volající funkce Internetu (například "Microsoft Internet Browser"). Pokud má *pstrAgent* hodnotu null (výchozí), rozhraní zavolá globální funkci [AfxGetAppName](application-information-and-management.md#afxgetappname), která vrátí řetězec zakončený hodnotou null obsahující název aplikace. Některé protokoly používají tento řetězec k identifikaci vaší aplikace na server.

*dwContext*<br/>
Identifikátor kontextu operace. *dwContext* identifikuje informace o stavu operace vrácené funkcí [CInternetSession:: OnStatusCallback](#onstatuscallback). Výchozí nastavení je 1; Můžete ale explicitně přiřadit konkrétní ID kontextu pro danou operaci. K tomuto ID kontextu bude přidružen objekt a veškerá jeho práce.

*dwAccessType*<br/>
Typ přístupu je povinný. Zde jsou platné hodnoty, které mohou být zadány přesně z nich:

- INTERNET_OPEN_TYPE_PRECONFIG připojit pomocí předkonfigurovaných nastavení v registru. Tento typ přístupu se nastaví jako výchozí. Pokud se chcete připojit prostřednictvím proxy serveru TIS, nastavte na tuto hodnotu *dwAccessType* . Následně nastavíte registr správně.

- INTERNET_OPEN_TYPE_DIRECT se připojit přímo k Internetu.

- INTERNET_OPEN_TYPE_PROXY se připojit prostřednictvím proxy serveru CERN.

Informace o připojení k různým typům proxy serveru najdete v tématu [postup v typické aplikaci klienta FTP](../../mfc/steps-in-a-typical-ftp-client-application.md).

*pstrProxyName*<br/>
Název upřednostňovaného proxy serveru CERN, pokud je *dwAccessType* nastavené na INTERNET_OPEN_TYPE_PROXY. Výchozí hodnota je NULL.

*pstrProxyBypass*<br/>
Ukazatel na řetězec obsahující volitelný seznam adres serverů. Tyto adresy se můžou při použití přístupu k proxy obejít. Pokud je zadána hodnota NULL, seznam obcházení bude načten z registru. Tento parametr je smysluplný pouze v případě, že je *dwAccessType* nastaven na INTERNET_OPEN_TYPE_PROXY.

*dwFlags*<br/>
Označuje různé možnosti ukládání do mezipaměti. Výchozí nastavení je 0. Mezi možné hodnoty patří:

- INTERNET_FLAG_DONT_CACHE data Neukládat do mezipaměti, a to buď místně, nebo na žádném serveru brány.

- Operace stahování INTERNET_FLAG_OFFLINE jsou splněné pouze prostřednictvím trvalé mezipaměti. Pokud položka v mezipaměti neexistuje, vrátí se odpovídající kód chyby. Tento příznak může být kombinován s operátorem or ( **&#124;** ).

### <a name="remarks"></a>Poznámky

`CInternetSession`je první internetovou funkcí volanou aplikací. Inicializuje interní datové struktury a připraví pro budoucí volání z aplikace.

Pokud nelze otevřít žádné připojení k Internetu, `CInternetSession` vyvolá výjimku [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="close"></a>CInternetSession:: Close

Pokud vaše aplikace dokončila použití `CInternetSession` objektu, zavolejte tuto členskou funkci.

```cpp
virtual void Close();
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="enablestatuscallback"></a>CInternetSession::EnableStatusCallback

Zavolejte tuto členskou funkci, aby se aktivovalo zpětné volání stavu.

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
Určuje, jestli je zpětné volání povolené nebo zakázané. Výchozí hodnota je TRUE.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud volání selže, určete příčinu selhání zkoumáním vyvolaného objektu [CInternetException](../../mfc/reference/cinternetexception-class.md) .

### <a name="remarks"></a>Poznámky

Při zpracovávání zpětného volání stavu můžete na stavovém řádku aplikace poskytnout stav o průběhu operace (například překlad názvu, připojení k serveru atd.). Zobrazení stavu operace je obzvláště žádoucí během dlouhodobé operace.

Vzhledem k tomu, že během zpracování žádosti dojde ke zpětnému volání, aplikace by měla ve zpětném volání platit ve chvíli, že by se zabránilo snížení propustnosti dat v síti. Například při zastavování dialogového okna ve zpětném volání může být taková zdlouhavá operace, kterou server požadavek ukončí.

Zpětné volání stavu nelze odebrat, dokud nebudou vyřízena žádná zpětná volání.

K asynchronnímu zpracování všech operací je nutné buď vytvořit vlastní vlákno, nebo použít funkce WinInet bez knihovny MFC.

## <a name="getcontext"></a>CInternetSession:: GetContext

Zavolejte tuto členskou funkci, aby se získala hodnota kontextu pro určitou relaci aplikace.

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Návratová hodnota

Identifikátor kontextu definovaný aplikací

### <a name="remarks"></a>Poznámky

[OnStatusCallback](#onstatuscallback) používá ID kontextu vrácené nástrojem `GetContext` k hlášení stavu konkrétní aplikace. Například když uživatel aktivuje požadavek na Internet, který zahrnuje vrácení informací o stavu, zpětné volání stavu používá ID kontextu k hlášení stavu tohoto konkrétního požadavku. Pokud uživatel aktivuje dva samostatné požadavky na Internet, které zahrnují vracení informací o stavu `OnStatusCallback` , používá identifikátory kontextu k vrácení stavu odpovídajícím žádostem. V důsledku toho se identifikátor kontextu používá pro všechny operace zpětného volání stavu a je spojen s relací, dokud nedojde k ukončení relace.

Další informace o asynchronních operacích najdete v článku [Internet First Step: Rozhraní](../../mfc/wininet-basics.md)WinInet.

## <a name="getcookie"></a>CInternetSession:: GetCookie

Tato členská funkce implementuje chování funkce Win32 [InternetGetCookie](/windows/win32/api/wininet/nf-wininet-internetgetcookiew), jak je popsáno v Windows SDK.

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
Ukazatel na řetězec obsahující název souboru cookie, který má být získán pro zadanou adresu URL.

*pstrCookieData*<br/>
V prvním přetížení je ukazatel na řetězec obsahující adresu vyrovnávací paměti, která přijímá data souborů cookie. Tato hodnota může být NULL. Ve druhém přetížení odkaz na objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) pro příjem dat souboru cookie.

*dwBufLen*<br/>
Proměnná určující velikost *pstrCookieData* vyrovnávací paměti. Pokud je funkce úspěšná, vyrovnávací paměť přijme množství kopírovaných dat do vyrovnávací paměti *pstrCookieData* . Pokud má *pstrCookieData* hodnotu null, tento parametr obdrží hodnotu, která určuje velikost vyrovnávací paměti potřebné ke zkopírování všech dat souboru cookie.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud bylo úspěšné, nebo jinak FALSE. Pokud se volání nepovede, zavolejte funkci Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) a určete příčinu chyby. Platí následující chybové hodnoty:

- ERROR_NO_MORE_ITEMS neexistuje žádný soubor cookie pro zadanou adresu URL a všechny její nadřazené položky.

- ERROR_INSUFFICIENT_BUFFER hodnota předaná v *dwBufLen* není dostatečná ke zkopírování všech dat souboru cookie. Hodnota vrácená v *dwBufLen* je velikost vyrovnávací paměti potřebné k získání všech dat.

### <a name="remarks"></a>Poznámky

Ve druhém přetížení knihovna MFC načte data ze souboru cookie do zadaného `CString` objektu.

## <a name="getcookielength"></a>CInternetSession::GetCookieLength

Zavolejte tuto členskou funkci, aby se získala délka souboru cookie uloženého ve vyrovnávací paměti.

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

Hodnota DWORD udávající délku souboru cookie uloženou ve vyrovnávací paměti. Nula, pokud žádný soubor cookie s názvem, který ukazuje *pstrCookieName* , neexistuje.

### <a name="remarks"></a>Poznámky

Tuto hodnotu používá [soubor GetCookie](#getcookie).

## <a name="getftpconnection"></a>CInternetSession::GetFtpConnection

Zavolejte tuto členskou funkci pro navázání připojení FTP a získání ukazatele na `CFtpConnection` objekt.

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
Ukazatel na řetězec zakončený hodnotou null, který určuje jméno uživatele, který se má přihlásit. Pokud má hodnotu NULL, je výchozí hodnota anonymní.

*pstrPassword*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje heslo, které se má použít pro přihlášení. Pokud mají hodnoty *pstrPassword* i *pstrUserName* hodnotu null, výchozím anonymním heslem je e-mailová adresa uživatele. Pokud má *pstrPassword* hodnotu null (nebo prázdný řetězec), ale *pstrUserName* není null, použije se prázdné heslo. Následující tabulka popisuje chování pro čtyři možná nastavení *pstrUserName* a *pstrPassword*:

| *pstrUserName*  | *pstrPassword*  | Uživatelské jméno odeslané na server FTP | Heslo odeslané na server FTP |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL nebo ""   |   NULL nebo ""   |         Anonymous         |      E-mailová adresa uživatele      |
| Řetězec, který není NULL |   NULL nebo ""   |       *pstrUserName*        |             " "             |
|      NULL       | Řetězec, který není NULL |            CHYBA            |            CHYBA            |
| Řetězec, který není NULL | Řetězec, který není NULL |       *pstrUserName*        |       *pstrPassword*        |

*nPort*<br/>
Číslo určující port TCP/IP, který má být použit na serveru.

*bPassive*<br/>
Určuje pasivní nebo aktivní režim pro tuto relaci FTP. Pokud je nastaveno na true, nastaví Win32 API `dwFlag` na INTERNET_FLAG_PASSIVE.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CFtpConnection](../../mfc/reference/cftpconnection-class.md) . Pokud volání selže, určete příčinu selhání zkoumáním vyvolaného objektu [CInternetException](../../mfc/reference/cinternetexception-class.md) .

### <a name="remarks"></a>Poznámky

`GetFtpConnection`připojí se k serveru FTP a vytvoří a vrátí ukazatel na `CFTPConnection` objekt. Neprovádí na serveru žádnou konkrétní operaci. Pokud máte v úmyslu číst soubory a zapisovat do nich, například je třeba provést tyto operace jako samostatné kroky. Další informace o hledání souborů, otevírání souborů a čtení nebo zápisu do souborů najdete v tématu třídy [CFtpConnection](../../mfc/reference/cftpconnection-class.md) a [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) . Postup, jak provádět běžné úlohy připojení FTP, najdete v článku [internetové programování s](../../mfc/win32-internet-extensions-wininet.md) rozhraním Wininet.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).

## <a name="getgopherconnection"></a>CInternetSession::GetGopherConnection

Voláním této členské funkce navažte nové připojení gopher a získejte ukazatel na `CGopherConnection` objekt.

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Parametry

*pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru Gopher.

*pstrUserName*<br/>
Ukazatel na řetězec obsahující uživatelské jméno.

*pstrPassword*<br/>
Ukazatel na řetězec obsahující přístupové heslo.

*nPort*<br/>
Číslo určující port TCP/IP, který má být použit na serveru.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) . Pokud volání selže, určete příčinu selhání zkoumáním vyvolaného objektu [CInternetException](../../mfc/reference/cinternetexception-class.md) .

### <a name="remarks"></a>Poznámky

`GetGopherConnection`připojí se k serveru gopher a vytvoří a vrátí ukazatel na `CGopherConnection` objekt. Neprovádí na serveru žádnou konkrétní operaci. Pokud máte v úmyslu číst data nebo je zapisovat, například je třeba provést tyto operace jako samostatné kroky. Další informace o hledání souborů, otevírání souborů a čtení nebo zápisu do souborů naleznete v tématech třídy [CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile –](../../mfc/reference/cgopherfile-class.md)a [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) . Informace o procházení serveru FTP najdete v tématu [OpenURL](#openurl)členské funkce. Postup, jak provádět běžné úlohy připojení k protokolu Gopher, najdete v článku [internetové programování s](../../mfc/win32-internet-extensions-wininet.md) rozhraním Wininet.

## <a name="gethttpconnection"></a>CInternetSession::GetHttpConnection

Zavolejte tuto členskou funkci, aby navázala připojení HTTP a získala ukazatel `CHttpConnection` na objekt.

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
Číslo určující port TCP/IP, který má být použit na serveru.

*pstrUserName*<br/>
Ukazatel na řetězec obsahující uživatelské jméno.

*pstrPassword*<br/>
Ukazatel na řetězec obsahující přístupové heslo.

*dwflags*<br/>
Libovolná kombinace `INTERNET_FLAG_*` příznaků. Popis hodnot *dwFlags* najdete v tabulce v části **poznámky** v tématu [CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) .

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CHttpConnection](../../mfc/reference/chttpconnection-class.md) . Pokud volání selže, určete příčinu selhání zkoumáním vyvolaného objektu [CInternetException](../../mfc/reference/cinternetexception-class.md) .

### <a name="remarks"></a>Poznámky

`GetHttpConnection`připojí se k serveru HTTP a vytvoří a vrátí ukazatel na `CHttpConnection` objekt. Neprovádí na serveru žádnou konkrétní operaci. Pokud se chystáte zadat dotaz na hlavičku HTTP, například, musíte tuto operaci provést jako samostatný krok. Informace o operacích, které můžete provádět pomocí připojení k serveru HTTP, najdete v tématu třídy [CHttpConnection](../../mfc/reference/chttpconnection-class.md) a [CHttpFile](../../mfc/reference/chttpfile-class.md) . Informace o procházení lokality HTTP naleznete v tématu členská funkce [OpenURL](#openurl). Postup provádění běžných úloh připojení HTTP najdete v článku [internetové programování s](../../mfc/win32-internet-extensions-wininet.md) rozhraním Wininet.

## <a name="onstatuscallback"></a>CInternetSession::OnStatusCallback

Tato členská funkce je volána rozhraním pro aktualizaci stavu, je-li povoleno zpětné volání stavu a operace čeká na vyřízení.

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>Parametry

*dwContext*<br/>
Hodnota kontextu poskytnutá aplikací

*dwInternetStatus*<br/>
Stavový kód, který označuje, proč je zpětné volání provedeno. Tabulku možných hodnot najdete v části **poznámky** .

*lpvStatusInformation*<br/>
Ukazatel na vyrovnávací paměť obsahující informace, které se vztahují k tomuto zpětnému volání.

*dwStatusInformationLength*<br/>
Velikost *lpvStatusInformation*

### <a name="remarks"></a>Poznámky

Musíte nejdřív volat [EnableStatusCallback](#enablestatuscallback) , abyste mohli využít zpětné volání stavu.

Parametr *dwInternetStatus* označuje prováděnou operaci a určuje, co bude obsah *lpvStatusInformation* . *dwStatusInformationLength* označuje délku dat obsažených v *lpvStatusInformation*. Následující hodnoty stavu pro *dwInternetStatus* jsou definovány takto:

|Value|Význam|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|Vyhledá se IP adresa názvu obsaženého v *lpvStatusInformation*.|
|INTERNET_STATUS_NAME_RESOLVED|Úspěšně se našla IP adresa názvu obsaženého v *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTING_TO_SERVER|Připojení k adrese soketu ([SOCKADDR –](/windows/win32/winsock/sockaddr-2)), na kterou odkazuje *lpvStatusInformation*.|
|INTERNET_STATUS_CONNECTED_TO_SERVER|Úspěšně připojeno k adrese soketu (SOCKADDR –), na kterou odkazovala *lpvStatusInformation*.|
|INTERNET_STATUS_SENDING_REQUEST|Odesílá se žádost o informace na server. Parametr *lpvStatusInformation* má hodnotu null.|
|INTERNET_STATUS_ REQUEST_SENT|Žádost o informace byla úspěšně odeslána na server. Parametr *lpvStatusInformation* má hodnotu null.|
|INTERNET_STATUS_RECEIVING_RESPONSE|Čeká se na odpověď serveru na požadavek. Parametr *lpvStatusInformation* má hodnotu null.|
|INTERNET_STATUS_RESPONSE_RECEIVED|Úspěšně se přijala odpověď ze serveru. Parametr *lpvStatusInformation* má hodnotu null.|
|INTERNET_STATUS_CLOSING_CONNECTION|Zavírá se připojení k serveru. Parametr *lpvStatusInformation* má hodnotu null.|
|INTERNET_STATUS_CONNECTION_CLOSED|Připojení k serveru bylo úspěšně ukončeno. Parametr *lpvStatusInformation* má hodnotu null.|
|INTERNET_STATUS_HANDLE_CREATED|Používá se funkcí Win32 API [InternetConnect](/windows/win32/api/wininet/nf-wininet-internetconnectw) k označení toho, že vytvořil nový popisovač. To umožňuje aplikaci volat funkci Win32 [InternetCloseHandle](/windows/win32/api/wininet/nf-wininet-internetclosehandle) z jiného vlákna, pokud připojení trvá příliš dlouho. Další informace o těchto funkcích najdete v článku o systému Windows SDKfor.|
|INTERNET_STATUS_HANDLE_CLOSING|Hodnota popisovače se úspěšně ukončila.|

Přepište tuto členskou funkci tak, aby vyžadovala nějakou akci předtím, než se provede rutina zpětného volání stavu.

> [!NOTE]
> Zpětná volání stavu vyžadují ochranu stavu vlákna. Pokud používáte knihovnu MFC ve sdílené knihovně, přidejte na začátek přepsání následující řádek:

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

Další informace o asynchronních operacích najdete v článku [Internet First Step: Rozhraní](../../mfc/wininet-basics.md)WinInet.

## <a name="openurl"></a>CInternetSession::OpenURL

Voláním této členské funkce odešlete zadaný požadavek na server HTTP a umožníte klientovi zadat další hlavičky RFC822, MIME nebo HTTP pro odeslání spolu s požadavkem.

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
Ukazatel na název adresy URL, která se má začít číst. Jsou podporovány pouze adresy URL začínající příponou File:, FTP:, gopher: nebo http:. Vyhodnotí, pokud má *pstrURL* hodnotu null.

*dwContext*<br/>
Hodnota definovaná aplikací předaná vráceným popisovačem ve zpětném volání.

*dwFlags*<br/>
Příznaky popisující, jak toto připojení zpracovat. Další informace o platných příznacích naleznete v tématu **poznámky** . Platné příznaky jsou:

- INTERNET_FLAG_TRANSFER_ASCII výchozí. Přeneste soubor jako text ASCII.

- INTERNET_FLAG_TRANSFER_BINARY přenést soubor jako binární soubor.

- INTERNET_FLAG_RELOAD získá data z kabelu i v případě, že je místně uložené v mezipaměti.

- INTERNET_FLAG_DONT_CACHE data Neukládat do mezipaměti, a to buď místně, nebo v žádné bráně.

- INTERNET_FLAG_SECURE tento příznak se vztahuje pouze na požadavky HTTP. Vyžaduje zabezpečené transakce na lince pomocí SSL (Secure Sockets Layer) nebo PCT.

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT Pokud je to možné, znovu použijte existující připojení k serveru pro nové požadavky vygenerované `OpenUrl` místo vytvoření nové relace pro každý požadavek na připojení.

- INTERNET_FLAG_PASSIVE se používá pro server FTP. Používá pasivní sémantiku FTP. Používá se [](../../mfc/reference/cinternetconnection-class.md) s CInternetConnection `OpenURL`.

*pstrHeaders*<br/>
Ukazatel na řetězec obsahující hlavičky, které se mají odeslat na server HTTP.

*dwHeadersLength*<br/>
Délka dalších hlaviček v znacích. Pokud je to-1L a *pstrHeaders* není null, předpokládá se, že *pstrHeaders* se ukončí a délka se vypočítá.

### <a name="return-value"></a>Návratová hodnota

Vrátí popisovač souboru pro služby FTP, GOPHER, HTTP a typu souborů pouze služby sítě Internet. Pokud analýza nebyla úspěšná, vrátí hodnotu NULL.

Ukazatel, který `OpenURL` vrací, závisí na typu služby *pstrURL*. Následující tabulka znázorňuje možné ukazatele `OpenURL` , které mohou vracet.

|Typ adresy URL|Vrací|
|--------------|-------------|
|file://|`CStdioFile*`|
|http://|`CHttpFile*`|
|gopher://|`CGopherFile*`|
|ftp://|`CInternetFile*`|

### <a name="remarks"></a>Poznámky

Parametr *dwFlags* musí zahrnovat buď INTERNET_FLAG_TRANSFER_ASCII, nebo INTERNET_FLAG_TRANSFER_BINARY, ale ne obojí. Zbývající příznaky lze kombinovat s bitovým operátorem **or** ( **&#124;** ).

`OpenURL`, který zabalí funkci `InternetOpenURL`Win32, umožňuje stahovat, načítat a číst data z internetového serveru. `OpenURL`nepovoluje žádnou manipulaci se soubory ve vzdáleném umístění, takže nevyžaduje žádný objekt [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) .

Chcete-li použít funkce specifické pro připojení (které jsou specifické pro protokol), jako je například zápis do souboru, je nutné otevřít relaci, otevřít konkrétní typ připojení a pak pomocí tohoto připojení otevřít soubor v požadovaném režimu. Další `CInternetConnection` informace o funkcích specifických pro připojení najdete v tématu.

## <a name="operator_hinternet"></a>CInternetSession:: operator HINTERNET

Tento operátor použijte k získání popisovače Windows pro aktuální internetovou relaci.

```cpp
operator HINTERNET() const;
```

## <a name="setcookie"></a>CInternetSession::SetCookie

Nastaví soubor cookie pro zadanou adresu URL.

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>Parametry

*pstrUrl*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje adresu URL, pro kterou by měl být nastaven soubor cookie.

*pstrCookieName*<br/>
Ukazatel na řetězec obsahující název souboru cookie.

*pstrCookieData*<br/>
Ukazatel na řetězec obsahující skutečná řetězcová data, která se mají přidružit k adrese URL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud bylo úspěšné, nebo jinak FALSE. Chcete-li získat konkrétní kód chyby, zavolejte`GetLastError.`

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [InternetSetCookie](/windows/win32/api/wininet/nf-wininet-internetsetcookiew), jak je popsáno v Windows SDK.

## <a name="setoption"></a>CInternetSession:: SetOption

Chcete-li nastavit možnosti pro internetovou relaci, zavolejte tuto členskou funkci.

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
Možnost Internetu, která se má nastavit Seznam možných možností najdete v tématu [příznaky možností](/windows/win32/WinInet/option-flags) v systému Windows SDKfor.

*lpBuffer*<br/>
Vyrovnávací paměť, která obsahuje nastavení možnosti.

*dwBufferLength*<br/>
Délka *lpBuffer* nebo velikost *dwValue*.

*dwValue*<br/>
Hodnota DWORD, která obsahuje nastavení možnosti.

*dwFlags*<br/>
Označuje různé možnosti ukládání do mezipaměti. Výchozí nastavení je 0. Mezi možné hodnoty patří:

- INTERNET_FLAG_DONT_CACHE data Neukládat do mezipaměti, a to buď místně, nebo na žádném serveru brány.

- Operace stahování INTERNET_FLAG_OFFLINE jsou splněné pouze prostřednictvím trvalé mezipaměti. Pokud položka v mezipaměti neexistuje, vrátí se odpovídající kód chyby. Tento příznak může být kombinován s operátorem or ( **&#124;** ).

### <a name="return-value"></a>Návratová hodnota

Pokud byla operace úspěšná, vrátí se hodnota TRUE. Pokud dojde k chybě, vrátí se hodnota FALSE. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection – třída](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection – třída](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection – třída](../../mfc/reference/cgopherconnection-class.md)
