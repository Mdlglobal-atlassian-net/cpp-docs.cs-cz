---
title: "Třída CInternetSession | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7aad2f6ce26fd5ca9ed0ec323a8fcb05ac17f7c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cinternetsession-class"></a>CInternetSession – třída
Vytvoří a inicializuje jeden nebo několik souběžných relací Internetu a v případě potřeby popisuje připojení k proxy serveru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|[CInternetSession::GetCookieLength](#getcookielength)|Načte proměnnou určující délku souboru cookie uložené ve vyrovnávací paměti.|  
|[CInternetSession::GetFtpConnection](#getftpconnection)|Otevře se relace FTP serveru. Přihlášení uživatele.|  
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Otevře gopher server pro aplikaci, která se pokouší otevřít připojení.|  
|[CInternetSession::GetHttpConnection](#gethttpconnection)|Otevře se server HTTP pro aplikaci, která se pokouší otevřít připojení.|  
|[CInternetSession::OnStatusCallback](#onstatuscallback)|Aktualizuje stav operace, pokud je povoleno stav zpětného volání.|  
|[CInternetSession::OpenURL](#openurl)|Analyzuje a otevře adresu URL.|  
|[CInternetSession::SetCookie](#setcookie)|Nastaví soubor cookie pro zadanou adresu URL.|  
|[CInternetSession::SetOption](#setoption)|Nastaví možnosti pro relaci Internet.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CInternetSession::operator HINTERNET](#operator_hinternet)|Popisovač pro aktuální relaci Internet.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud po dobu trvání aplikace musí být zachovaná připojení k Internetu, můžete vytvořit `CInternetSession` člena třídy [CWinApp](../../mfc/reference/cwinapp-class.md).  
  
 Po vytvoření relace Internetu můžete volat [OpenURL](#openurl). `CInternetSession`potom analyzuje adresu URL pro vás voláním globální funkce [afxparseurl –](internet-url-parsing-globals.md#afxparseurl). Bez ohledu na jeho typ protokolu `CInternetSession` interpretuje adresu URL a spravuje za vás. Ho může zpracovávat požadavky pro místní soubory identifikovaný pomocí adresy URL prostředku "file://". `OpenURL`vrátí ukazatel [CStdioFile](../../mfc/reference/cstdiofile-class.md) objekt, pokud název předat je do místního souboru.  
  
 Pokud otevřete adresu URL na serveru Internetu pomocí `OpenURL`, si můžete přečíst informace z webu. Pokud chcete provádět akce specifické služby (pro příklad, HTTP, FTP nebo gopher) na soubory umístěné na serveru, je potřeba vytvořit na příslušné připojení s tímto serverem. Chcete-li otevřít konkrétní typ připojení přímo na konkrétní službu, použijte jednu z následujících členské funkce:  
  
- [GetGopherConnection](#getgopherconnection) k otevření připojení ke službě gopher.  
  
- [GetHttpConnection](#gethttpconnection) k otevření připojení do služby protokolu HTTP.  
  
- [GetFtpConnection](#getftpconnection) k otevření připojení do služby FTP.  
  
 [SetOption](#setoption) umožňuje nastavit možnosti dotazu vaší relace, jako je například hodnoty časového limitu, počet opakovaných pokusů a tak dále.  
  
 `CInternetSession`Členské funkce [SetCookie](#setcookie), [GetCookie](#getcookie), a [GetCookieLength](#getcookielength) poskytují způsob, jak spravovat databáze Win32 souboru cookie, pomocí kterého se servery a skripty udržovat informace o klientské pracovní stanice stavu.  
  
 Další informace o základních úloh programování Internetu najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md). Obecné informace o používání tříd WinInet knihovny MFC, najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
> [!NOTE]
> `CInternetSession`vyvolá výjimku [afxthrownotsupportedexception –](exception-processing.md#afxthrownotsupportedexception) pro typy nepodporované služby. Aktuálně jsou podporovány pouze následující typy služby: FTP, HTTP, gopher a souboru.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetSession`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
  
##  <a name="cinternetsession"></a>CInternetSession::CInternetSession  
 Tento člen funkce je volána, když `CInternetSession` je vytvořen objekt.  
  
```  
CInternetSession(
    LPCTSTR pstrAgent = NULL,  
    DWORD_PTR dwContext = 1,  
    DWORD dwAccessType = PRE_CONFIG_INTERNET_ACCESS,  
    LPCTSTR pstrProxyName = NULL,  
    LPCTSTR pstrProxyBypass = NULL,  
    DWORD dwFlags = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrAgent`  
 Ukazatel na řetězec, který identifikuje název aplikace nebo entity volání funkcí Internetu (například "Microsoft internetovém prohlížeči"). Pokud `pstrAgent` je **NULL** volá framework (výchozí), globální funkce [afxgetappname –](application-information-and-management.md#afxgetappname), která vrací řetězec ukončené hodnotou null obsahující název aplikace. Některé protokoly, použijte tento řetězec k identifikaci vaší aplikace na server.  
  
 `dwContext`  
 Identifikátor kontextu pro danou operaci. `dwContext`identifikuje vrácené informace o stavu operace [CInternetSession::OnStatusCallback](#onstatuscallback). Ve výchozím nastavení je 1; však můžete explicitně přiřadit konkrétní kontext ID pro operaci. Objekt a všechny práce, kterou dělá bude spojený s ID tohoto kontextu.  
  
 `dwAccessType`  
 Zadejte přístup požadovaný. Platnými hodnotami, právě jeden z nich může být zadána jsou následující:  
  
- **INTERNET_OPEN_TYPE_PRECONFIG** připojení pomocí předem nakonfigurovaných nastavení v registru. Tento typ přístupu je nastaven jako výchozí. Chcete-li připojit prostřednictvím proxy serveru TIS, nastavte `dwAccessType` na tuto hodnotu; pak můžete nastavit registru správně.  
  
- `INTERNET_OPEN_TYPE_DIRECT`Připojte přímo k Internetu.  
  
- `INTERNET_OPEN_TYPE_PROXY`Připojte prostřednictvím proxy serveru CERN.  
  
 Informace o připojení s různými typy proxy najdete v tématu [kroky v typické aplikaci klienta FTP](../../mfc/steps-in-a-typical-ftp-client-application.md).  
  
 *pstrProxyName*  
 Název upřednostňované proxy CERN Pokud `dwAccessType` je nastaven jako `INTERNET_OPEN_TYPE_PROXY`. Výchozí hodnota je **NULL**.  
  
 *pstrProxyBypass*  
 Ukazatel na řetězec obsahující volitelný seznam adres serveru. Tyto adresy mohou obejít, při použití přístup k proxy. Pokud **NULL** je zadána hodnota, seznam obcházení budou číst z registru. Tento parametr má smysl pouze v případě `dwAccessType` je nastaven na `INTERNET_OPEN_TYPE_PROXY`.  
  
 `dwFlags`  
 Označuje různé možnosti ukládání do mezipaměti. Výchozí hodnota je nastavena na hodnotu 0. Možné hodnoty patří:  
  
- `INTERNET_FLAG_DONT_CACHE`Neukládat do mezipaměti dat, buď místně nebo v veškeré servery brány.  
  
- `INTERNET_FLAG_OFFLINE`Při stahování spokojeni prostřednictvím pouze trvalé mezipaměti. Pokud položka v mezipaměti neexistuje, je vrácena odpovídající chybový kód. Tento příznak mohou být kombinovány s bitové hodnotě `OR` ( **&#124;**) operátor.  
  
### <a name="remarks"></a>Poznámky  
 **CInternetSession** je první funkce Internet volání aplikací. Inicializuje interních datových strukturách se a připraví pro budoucí volání z aplikace.  
  
 Pokud lze otevřít žádné připojení k Internetu, `CInternetSession` vyvolá [afxthrowinternetexception –](internet-url-parsing-globals.md#afxthrowinternetexception).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).  
  
##  <a name="close"></a>CInternetSession::Close  
 Volání této funkce člen, když aplikace dokončí, pomocí `CInternetSession` objektu.  
  
```  
virtual void Close();
```  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).  
  
##  <a name="enablestatuscallback"></a>CInternetSession::EnableStatusCallback  
 Volání této funkce člen povolit stav zpětného volání.  
  
```  
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bEnable`  
 Určuje, zda je povoleno zpětného volání. Výchozí hodnota je **TRUE**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, zjistit příčinu selhání na základě vyvolané [CInternetException](../../mfc/reference/cinternetexception-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Při zpracování zpětného volání stav, můžete zadat stav průběh operace (například překladu názvu, připojení k serveru a tak dále) ve stavovém řádku aplikace. Zobrazení stav operace je žádoucí především při dlouhodobé operaci.  
  
 Vzhledem k tomu, že během zpracování žádosti dojde k zpětná volání, musí aplikace tráví co nejméně času v zpětného volání, aby se zabránilo snížení výkonu propustnost dat k síti. Například vložení do dialogového okna v zpětné volání, může být taková časově náročná operace, že server ukončí požadavek.  
  
 Stav zpětného volání nelze odebrat, dokud všechny zpětná volání, které čekají na vyřízení.  
  
 Asynchronně zpracovat žádné operace, musíte vytvořit vlastní vlákno nebo použít funkce WinInet bez MFC.  
  
##  <a name="getcontext"></a>CInternetSession::GetContext  
 Volání této funkce člen má být získána hodnota kontextu pro relaci konkrétní aplikace.  
  
```  
DWORD_PTR GetContext() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Definované aplikací kontext identifikátor.  
  
### <a name="remarks"></a>Poznámky  
 [Onstatuscallback –](#onstatuscallback) pomocí ID kontextu vrátila **getcontext –** nahlásit stav konkrétní aplikace. Například pokud uživatel aktivuje požadavek na Internetu, která zahrnuje vrací informace o stavu, stav zpětného volání používá ID kontextu odesílat zprávy o stavu tohoto konkrétního požadavku. Pokud uživatel aktivuje dva samostatné Internet požadavky, že obojí zahrnuje vrací informace o stavu `OnStatusCallback` používá identifikátory kontextu vrátit stav o jejich odpovídajících požadavků. V důsledku toho kontextu identifikátor se používá pro všechny operace stav zpětného volání a je přidružená k relaci, dokud relace se ukončí.  
  
 Další informace o asynchronních operací, najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md).  
  
##  <a name="getcookie"></a>CInternetSession::GetCookie  
 Tato funkce člen implementuje chování funkce Win32 [InternetGetCookie](http://msdn.microsoft.com/library/windows/desktop/aa384710), jak je popsáno v sadě Windows SDK.  
  
```  
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
 `pstrUrl`  
 Ukazatel na řetězec, který obsahuje adresu URL.  
  
 `pstrCookieName`  
 Ukazatel na řetězec, který obsahuje název souboru cookie, chcete-li získat pro zadané adrese URL.  
  
 `pstrCookieData`  
 V první přetížení ukazatel na řetězec obsahující adresu vyrovnávací paměti, která přijímá data souboru cookie. Tato hodnota může být **NULL**. V druhé přetížení, odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který chcete přijímat data souboru cookie.  
  
 `dwBufLen`  
 Proměnná určení velikosti `pstrCookieData` vyrovnávací paměti. Pokud funkci úspěšné, vyrovnávací paměť obdrží množství dat, které jsou zkopírovány do `pstrCookieData` vyrovnávací paměti. Pokud `pstrCookieData` je **NULL**, tento parametr obdrží hodnotu, která určuje velikost vyrovnávací paměti nezbytné pro všechna data souboru cookie.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu nebo **FALSE** jinak. Pokud volání selže, volání funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) a zjistěte příčinu této chyby. Platí následující hodnoty Chyba:  
  
- **ERROR_NO_MORE_ITEMS** k dispozici není žádný soubor cookie pro zadanou adresu URL a všech jejích nadřazených tříd.  
  
- **ERROR_INSUFFICIENT_BUFFER** předaná hodnota `dwBufLen` je nedostatečná pro všechna data souboru cookie. Hodnota vrácená v `dwBufLen` velikost vyrovnávací paměti je nutné získat všechna data.  
  
### <a name="remarks"></a>Poznámky  
 V druhé přetížení MFC načte cookie data do zadaných `CString` objektu.  
  
##  <a name="getcookielength"></a>CInternetSession::GetCookieLength  
 Volání této funkce člen získat délku souboru cookie uložené ve vyrovnávací paměti.  
  
```  
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,  
    LPCTSTR pstrCookieName);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrUrl`  
 Ukazatel na řetězec, který obsahuje adresu URL  
  
 `pstrCookieName`  
 Ukazatel na řetězec, který obsahuje název souboru cookie.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `DWORD` hodnotu, která udává délku souboru cookie, uložené ve vyrovnávací paměti. Nula, pokud žádný soubor cookie s názvem indikován `pstrCookieName` existuje.  
  
### <a name="remarks"></a>Poznámky  
 Tato hodnota se používá ve [GetCookie](#getcookie).  
  
##  <a name="getftpconnection"></a>CInternetSession::GetFtpConnection  
 Volání této funkce člen k zahájení připojení FTP a získat ukazatel na `CFtpConnection` objektu.  
  
```  
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    BOOL bPassive = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrServer`  
 Ukazatel na řetězec obsahující název serveru FTP.  
  
 `pstrUserName`  
 Ukazatel na řetězec ukončené hodnotou null, který určuje jméno uživatele k přihlášení. Pokud **NULL**, výchozí hodnota je anonymní.  
  
 `pstrPassword`  
 Ukazatel na řetězec ukončené hodnotou null, který určuje heslo pro použití k protokolování. Pokud oba `pstrPassword` a `pstrUserName` jsou **NULL**, výchozí anonymního hesla je uživatelské jméno e-mailu. Pokud `pstrPassword` je **NULL** (nebo prázdný řetězec), ale `pstrUserName` není **NULL**, se používá prázdné heslo. Následující tabulka popisuje chování čtyři možné nastavení `pstrUserName` a `pstrPassword`:  
  
|`pstrUserName`|`pstrPassword`|Uživatelské jméno odeslané na FTP server|Heslo odeslat na FTP server|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**NULL** nebo ""|**NULL** nebo ""|"anonymní"|Uživatelské jméno e-mailu|  
|Není- **NULL** řetězec|**NULL** nebo ""|`pstrUserName`|" "|  
|**NULL** jinou hodnotu než **NULL** řetězec|**CHYBA**|**CHYBA**||  
|Není- **NULL** řetězec|Není- **NULL** řetězec|`pstrUserName`|`pstrPassword`|  
  
 `nPort`  
 Číslo, které identifikuje port TCP/IP použít na serveru.  
  
 `bPassive`  
 Určuje režim pasivní nebo aktivní pro tuto relaci FTP. Pokud nastavena na **TRUE**, nastaví rozhraní API Win32 `dwFlag` k **INTERNET_FLAG_PASSIVE**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CFtpConnection](../../mfc/reference/cftpconnection-class.md) objektu. Pokud volání selže, zjistit příčinu selhání na základě vyvolané [CInternetException](../../mfc/reference/cinternetexception-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 `GetFtpConnection`připojí k serveru FTP a vytvoří a vrátí ukazatel **CFTPConnection** objektu. Neprovede žádné konkrétní operaci na serveru. Pokud máte v úmyslu číst nebo zapisovat do souborů, například musíte provést tyto operace jako samostatné kroky. Viz třídy [CFtpConnection](../../mfc/reference/cftpconnection-class.md) a [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) informace o hledání souborů, otevírání souborů a čtení nebo zápis do souborů. Najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md) kroky při provádění běžných úloh připojení FTP.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md).  
  
##  <a name="getgopherconnection"></a>CInternetSession::GetGopherConnection  
 Volání této funkce člen a vytvořit nové připojení gopher získat ukazatel na `CGopherConnection` objektu.  
  
```  
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrServer`  
 Ukazatel na řetězec obsahující název serveru gopher.  
  
 `pstrUserName`  
 Ukazatel na řetězec obsahující uživatelské jméno.  
  
 `pstrPassword`  
 Ukazatel na řetězec obsahující přístupové heslo.  
  
 `nPort`  
 Číslo, které identifikuje port TCP/IP použít na serveru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objektu. Pokud volání selže, zjistit příčinu selhání na základě vyvolané [CInternetException](../../mfc/reference/cinternetexception-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 `GetGopherConnection`připojí k serveru gopher a vytvoří a vrátí ukazatel na `CGopherConnection` objektu. Neprovede žádné konkrétní operaci na serveru. Pokud máte v úmyslu číst nebo zapisovat data, například musíte provést tyto operace jako samostatné kroky. Viz třídy [CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile](../../mfc/reference/cgopherfile-class.md), a [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) informace o hledání souborů, otevírání souborů a čtení nebo zápis do souborů. Informace o procházení serveru FTP najdete v tématu – členská funkce [OpenURL](#openurl). Najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md) kroky při provádění běžných úloh gopher připojení.  
  
##  <a name="gethttpconnection"></a>CInternetSession::GetHttpConnection  
 Volání této funkce člen k zahájení připojení HTTP a získat ukazatel na `CHttpConnection` objektu.  
  
```  
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
 `pstrServer`  
 Ukazatel na řetězec obsahující název serveru protokolu HTTP.  
  
 `nPort`  
 Číslo, které identifikuje port TCP/IP použít na serveru.  
  
 `pstrUserName`  
 Ukazatel na řetězec obsahující uživatelské jméno.  
  
 `pstrPassword`  
 Ukazatel na řetězec obsahující přístupové heslo.  
  
 *dwFlags*  
 Libovolnou kombinaci **INTERNET_ FLAG_\***  příznaky. Podívejte se na tabulku v **poznámky** části [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) popis `dwFlags` hodnoty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CHttpConnection](../../mfc/reference/chttpconnection-class.md) objektu. Pokud volání selže, zjistit příčinu selhání na základě vyvolané [CInternetException](../../mfc/reference/cinternetexception-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 `GetHttpConnection`připojí k serveru HTTP a vytvoří a vrátí ukazatel na `CHttpConnection` objektu. Neprovede žádné konkrétní operaci na serveru. Pokud máte v úmyslu dotaz záhlaví HTTP, například při provádění této operace v samostatném kroku. Viz třídy [CHttpConnection](../../mfc/reference/chttpconnection-class.md) a [CHttpFile](../../mfc/reference/chttpfile-class.md) informace o operacích, které můžete provádět pomocí připojení k serveru HTTP. Informace o procházení serveru HTTP najdete v tématu – členská funkce [OpenURL](#openurl). Najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md) kroky při provádění běžných úloh připojení HTTP.  
  
##  <a name="onstatuscallback"></a>CInternetSession::OnStatusCallback  
 Tento člen funkce je volána službou framework a aktualizujte stav, když je zapnutý stav zpětného volání a operace čeká na vyřízení.  
  
```  
virtual void OnStatusCallback(
    DWORD_PTR dwContext,  
    DWORD dwInternetStatus,  
    LPVOID lpvStatusInformation,  
    DWORD dwStatusInformationLength);
```  
  
### <a name="parameters"></a>Parametry  
 `dwContext`  
 Hodnota kontextu zadaná aplikací.  
  
 `dwInternetStatus`  
 Stavový kód, který označuje, proč je k zpětné volání. V tématu **poznámky** pro tabulku možných hodnot.  
  
 `lpvStatusInformation`  
 Ukazatel na vyrovnávací paměť obsahující informace týkající se této zpětného volání.  
  
 `dwStatusInformationLength`  
 Velikost `lpvStatusInformation`.  
  
### <a name="remarks"></a>Poznámky  
 Nejprve je třeba volat [EnableStatusCallback](#enablestatuscallback) využívat výhod stav zpětného volání.  
  
 `dwInternetStatus` Parametr označuje prováděnou operaci a určuje, jaké obsah `lpvStatusInformation` bude. `dwStatusInformationLength`Určuje délku dat obsažených v `lpvStatusInformation`. Hodnoty těchto stavů `dwInternetStatus` jsou definovány takto:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|`INTERNET_STATUS_RESOLVING_NAME`|Vyhledávání adresu IP názvu obsažené v `lpvStatusInformation`.|  
|`INTERNET_STATUS_NAME_RESOLVED`|Úspěšně najít IP adresu názvu obsažené v `lpvStatusInformation`.|  
|`INTERNET_STATUS_CONNECTING_TO_SERVER`|Připojování k adresu soketu ( [sockaddr –](../../mfc/reference/sockaddr-structure.md)) na kterou odkazuje `lpvStatusInformation`.|  
|`INTERNET_STATUS_CONNECTED_TO_SERVER`|Úspěšně připojeno k adresu soketu ( `SOCKADDR`) na kterou odkazuje `lpvStatusInformation`.|  
|`INTERNET_STATUS_SENDING_REQUEST`|Odesílání požadavku informace na server. `lpvStatusInformation` Parametr **NULL**.|  
|**INTERNET_STATUS_ REQUEST_SENT**|Úspěšně odeslal žádost o informace na server. `lpvStatusInformation` Parametr **NULL**.|  
|`INTERNET_STATUS_RECEIVING_RESPONSE`|Čekání na odpověď na žádost o serveru. `lpvStatusInformation` Parametr **NULL**.|  
|`INTERNET_STATUS_RESPONSE_RECEIVED`|Úspěšně obdržel odpověď ze serveru. `lpvStatusInformation` Parametr **NULL**.|  
|`INTERNET_STATUS_CLOSING_CONNECTION`|Probíhá ukončování připojení k serveru. `lpvStatusInformation` Parametr **NULL**.|  
|`INTERNET_STATUS_CONNECTION_CLOSED`|Úspěšně ukončila připojení k serveru. `lpvStatusInformation` Parametr **NULL**.|  
|`INTERNET_STATUS_HANDLE_CREATED`|Používá funkce rozhraní Win32 API [InternetConnect](http://msdn.microsoft.com/library/windows/desktop/aa384363) indikující, že bylo vytvořeno nové popisovač. Díky tomu funkce volání Win32 aplikací [InternetCloseHandle](http://msdn.microsoft.com/library/windows/desktop/aa384350) z jiného vlákna, pokud připojení trvá příliš dlouho. Další informace o těchto funkcích najdete v části SDKfor systému Windows.|  
|`INTERNET_STATUS_HANDLE_CLOSING`|Tato hodnota popisovač úspěšně ukončil.|  
  
 Člen funkci tak, aby vyžadovala některá z akcí, než se provádí rutina zpětného volání stavu přepište.  
  
> [!NOTE]
>  Zpětná volání stav potřebují ochranu stav vlákna. Pokud používáte MFC ve sdílené knihovně, přidejte následující řádek na začátek přepsání:  
  
 [!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]  
  
 Další informace o asynchronních operací, najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md).  
  
##  <a name="openurl"></a>CInternetSession::OpenURL  
 Tento člen volání funkce Odeslat zadaný požadavek HTTP serveru a umožňují klientu zadejte další RFC822 MIME nebo hlavičky protokolu HTTP k odeslání společně se žádostí.  
  
```  
CStdioFile* OpenURL(
    LPCTSTR pstrURL,  
    DWORD_PTR dwContext = 1,  
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,  
    LPCTSTR pstrHeaders = NULL,  
    DWORD dwHeadersLength = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *pstrURL*  
 Ukazatel na název adresy URL začínat čtení. Jenom adresy URL počínaje souboru:, ftp:, gopher:, nebo http: jsou podporovány. **Nepodmíněné výrazy** Pokud *pszURL* je **NULL**.  
  
 `dwContext`  
 Hodnotu definované aplikací byla dokončena s Vrácený popisovač v zpětného volání.  
  
 `dwFlags`  
 Příznaky popisující, jak zpracovat toto připojení. V tématu **poznámky** Další informace o platný příznaků. Platné příznaky jsou:  
  
- **INTERNET_FLAG_TRANSFER_ASCII** výchozí hodnota. Přeneste soubor jako ASCII text.  
  
- **INTERNET_FLAG_TRANSFER_BINARY** přeneste soubor jako binární soubor.  
  
- `INTERNET_FLAG_RELOAD`Získáte data z drátového připojení i v případě, že je v místní mezipaměti.  
  
- `INTERNET_FLAG_DONT_CACHE`Neukládat do mezipaměti dat, buď místně nebo v žádné brány.  
  
- `INTERNET_FLAG_SECURE`Tento příznak se vztahuje na pouze požadavky HTTP. Požaduje zabezpečené transakce v drátové síti s Secure Sockets Layer nebo procento  
  
- **INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT** Pokud je to možné, opakovaně používat existující připojení k serveru pro nové žádosti o generované **OpenUrl** místo vytvoření nové relace pro každý požadavek na připojení.  
  
- **INTERNET_FLAG_PASSIVE** použít pro server FTP. Používá pasivní sémantiku FTP. Použít s [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) z `OpenURL`.  
  
 `pstrHeaders`  
 Ukazatel na řetězec obsahující hlavičky k odeslání do serveru protokolu HTTP.  
  
 *dwHeadersLength*  
 Délka ve znacích další záhlaví. Pokud je to L-1 a `pstrHeaders` jinou hodnotu než **NULL**, pak `pstrHeaders` se předpokládá, že být nula ukončena a délka se počítá.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač souboru pro FTP, GOPHER, HTTP a typ souboru internetové služby. Vrátí **NULL** Pokud analýza neúspěšná.  
  
 Ukazatele, `OpenURL` vrátí závisí na *pszURL*na typ služby. Následující tabulka znázorňuje možné ukazatele `OpenURL` může vrátit.  
  
|Typ adresy URL|Vrací|  
|--------------|-------------|  
|File://|**CStdioFile\***|  
|http://|**CHttpFile\***|  
|Gopher://|**CGopherFile\***|  
|FTP: / /|**CInternetFile\***|  
  
### <a name="remarks"></a>Poznámky  
 Parametr `dwFlags` musí obsahovat buď **INTERNET_FLAG_TRANSFER_ASCII** nebo **INTERNET_FLAG_TRANSFER_BINARY**, ale ne obojí. Zbývající příznaků je možné kombinovat s bitové hodnotě `OR` – operátor ( **&#124;**).  
  
 `OpenURL`, který zabalí funkci Win32 **InternetOpenURL**, umožňuje pouze stahování, načítání a čtení dat z internetového serveru. `OpenURL`Umožňuje zpracování žádný soubor ve vzdáleném umístění, takže vyžaduje ne [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) objektu.  
  
 Použít specifickou pro připojení (to znamená, specifické pro protokol) funkce, jako je například zápis do souboru, je nutné otevřít relaci, pak otevřete konkrétní typ připojení a potom používat toto připojení k otevření souboru v režimu požadované. V tématu `CInternetConnection` pro další informace o funkcích specifickou pro připojení.  
  
##  <a name="operator_hinternet"></a>CInternetSession::operator HINTERNET  
 Tento operátor. použijte k získání popisovačů systému Windows pro aktuální relaci Internet.  
  
```  
operator HINTERNET() const;  
```  
  
##  <a name="setcookie"></a>CInternetSession::SetCookie  
 Nastaví soubor cookie pro zadanou adresu URL.  
  
```  
static BOOL SetCookie(
    LPCTSTR pstrUrl,  
    LPCTSTR pstrCookieName,  
    LPCTSTR pstrCookieData);
```  
  
### <a name="parameters"></a>Parametry  
 `pstrUrl`  
 Ukazatel na řetězec ukončené hodnotou null, který určuje adresu URL, u které je třeba nastavit soubor cookie.  
  
 `pstrCookieName`  
 Ukazatel na řetězec, který obsahuje název souboru cookie.  
  
 `pstrCookieData`  
 Ukazatel na řetězec obsahující data konkrétní řetězec k přidružení s adresou URL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu nebo **FALSE** jinak. Chcete-li získat kód chyby, volejte **GetLastError.**  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [InternetSetCookie](http://msdn.microsoft.com/library/windows/desktop/aa385107), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setoption"></a>CInternetSession::SetOption  
 Volání této funkce člena pro nastavení možností pro relaci Internet.  
  
```  
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
 `dwOption`  
 Možnost Internetu nastavit. V tématu [možnost příznaky](http://msdn.microsoft.com/library/windows/desktop/aa385328) v systému Windows SDKfor seznam možných možností.  
  
 `lpBuffer`  
 Vyrovnávací paměť, která obsahuje možnost nastavení.  
  
 *dwBufferLength*  
 Délka `lpBuffer` nebo velikost `dwValue`.  
  
 `dwValue`  
 A `DWORD` obsahující nastavení možnosti.  
  
 `dwFlags`  
 Označuje různé možnosti ukládání do mezipaměti. Výchozí hodnota je nastavena na hodnotu 0. Možné hodnoty patří:  
  
- `INTERNET_FLAG_DONT_CACHE`Neukládat do mezipaměti dat, buď místně nebo v veškeré servery brány.  
  
- `INTERNET_FLAG_OFFLINE`Při stahování spokojeni prostřednictvím pouze trvalé mezipaměti. Pokud položka v mezipaměti neexistuje, je vrácena odpovídající chybový kód. Tento příznak mohou být kombinovány s bitové hodnotě `OR` ( **&#124;**) operátor.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud byla operace úspěšná, hodnota **TRUE** je vrácen. Pokud došlo k chybě, hodnota **FALSE** je vrácen. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)   
 [CHttpConnection – třída](../../mfc/reference/chttpconnection-class.md)   
 [CFtpConnection – třída](../../mfc/reference/cftpconnection-class.md)   
 [CGopherConnection – třída](../../mfc/reference/cgopherconnection-class.md)
