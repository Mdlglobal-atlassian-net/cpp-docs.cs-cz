---
title: CGopherConnection – třída
ms.date: 11/04/2016
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
ms.openlocfilehash: f5d655aa7fd2eb9e41c15c60a71492c24ba43c43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506198"
---
# <a name="cgopherconnection-class"></a>CGopherConnection – třída

Spravuje připojení k internetovému serveru Gopher.

> [!NOTE]
>  Třídy `CGopherConnection` `CGopherFile` ,`CGopherLocator` , a jejich členové jsou zastaralí, protože nefungují na platformě Windows XP, ale budou fungovat i na `CGopherFileFind`starších platformách.

## <a name="syntax"></a>Syntaxe

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CGopherConnection::CGopherConnection](#cgopherconnection)|`CGopherConnection` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CGopherConnection::CreateLocator](#createlocator)|Vytvoří objekt [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) pro hledání souborů na serveru Gopher.|
|[CGopherConnection:: Get– atribut](#getattribute)|Načte informace o atributu objektu Gopher.|
|[CGopherConnection::OpenFile](#openfile)|Otevře soubor protokolu Gopher.|

## <a name="remarks"></a>Poznámky

Služba gopher představuje jednu ze tří služeb sítě Internet rozpoznávaných třídami WinInet knihovny MFC.

Třída `CGopherConnection` obsahuje konstruktor a tři další členské funkce, které spravují službu gopher: [OpenFile](#openfile), [CreateLocator](#createlocator)a [GetAttribute](#getattribute).

Abyste mohli komunikovat s internetovým serverem gopher, musíte nejdřív vytvořit instanci [CInternetSession](../../mfc/reference/cinternetsession-class.md)a pak zavolat [CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), `CGopherConnection` který vytvoří objekt a vrátí ukazatel na něj. `CGopherConnection` Objekt nikdy nevytvoříte přímo.

Další informace o tom, `CGopherConnection` jak pracovat s jinými internetovými třídami knihovny MFC, najdete v článku [internetové programování s](../../mfc/win32-internet-extensions-wininet.md)rozhraním Wininet. Další informace o používání dalších dvou podporovaných služeb sítě Internet najdete na stránce třídy [CHttpConnection](../../mfc/reference/chttpconnection-class.md) a [CFtpConnection](../../mfc/reference/cftpconnection-class.md)v tématu věnovaném službám FTP a http.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet. h

##  <a name="cgopherconnection"></a>CGopherConnection::CGopherConnection

Tato členská funkce je volána k vytvoření `CGopherConnection` objektu.

```
CGopherConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CGopherConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 0,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
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

### <a name="remarks"></a>Poznámky

Nikdy nevytvářejte `CGopherConnection` přímo. Místo toho zavolejte [CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), který vytvoří `CGopherConnection` objekt a vrátí ukazatel na něj.

##  <a name="createlocator"></a>CGopherConnection::CreateLocator

Voláním této členské funkce vytvoříte Lokátor protokolu Gopher pro vyhledání nebo identifikaci souboru na serveru Gopher.

```
CGopherLocator CreateLocator(
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType);

static CGopherLocator CreateLocator(LPCTSTR pstrLocator);

static CGopherLocator CreateLocator(
    LPCTSTR pstrServerName,
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Parametry

*pstrDisplayString*<br/>
Ukazatel na řetězec obsahující název dokumentu nebo adresáře protokolu Gopher, který má být načten. Pokud má parametr *pstrDisplayString* hodnotu null, vrátí se výchozí adresář serveru Gopher.

*pstrSelectorString*<br/>
Ukazatel na řetězec selektoru, který má být odeslán na server gopher, aby bylo možné načíst položku. *pstrSelectorString* může mít hodnotu null.

*dwGopherType*<br/>
Určuje, zda *pstrSelectorString* odkazuje na adresář nebo dokument a zda se jedná o požadavek Gopher nebo Gopher +. Podívejte se na atributy struktury [GOPHER_FIND_DATA](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw) v Windows SDK.

*pstrLocator*<br/>
Ukazatel na řetězec identifikující soubor, který se má otevřít Obecně je tento řetězec vrácený voláním metody [CGopherFileFind:: GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator).

*pstrServerName*<br/>
Ukazatel na řetězec obsahující název serveru Gopher.

*nPort*<br/>
Číslo identifikující Internetový port pro toto připojení.

### <a name="return-value"></a>Návratová hodnota

Objekt [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

### <a name="remarks"></a>Poznámky

Statická verze členské funkce vyžaduje, abyste určili Server, zatímco nestatická verze používá název serveru z objektu Connection.

Aby bylo možné načíst informace ze serveru gopher, musí nejdřív aplikace získat Lokátor protokolu Gopher. Aplikace musí následně považovat Lokátor za neprůhledný token (to znamená, že aplikace může použít lokátor, ale ne přímo ji manipulovat nebo porovnat). Normálně aplikace používá Lokátor pro volání členské funkce [CGopherFileFind:: FindFile –](../../mfc/reference/cgopherfilefind-class.md#findfile) , která načte konkrétní informace.

##  <a name="getattribute"></a>CGopherConnection:: Get– atribut

Zavolejte tuto členskou funkci, aby se načetly informace o konkrétním atributu položky ze serveru Gopher.

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>Parametry

*refLocator*<br/>
Odkaz na objekt [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

*strRequestedAttributes*<br/>
Mezerou oddělený řetězec určující názvy požadovaných atributů.

*strResult*<br/>
Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který přijímá typ lokátoru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

##  <a name="openfile"></a>CGopherConnection:: OpenFile

Tuto členskou funkci volejte pro otevření souboru na serveru Gopher.

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*refLocator*<br/>
Odkaz na objekt [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

*dwFlags*<br/>
Libovolná kombinace příznaků INTERNET_FLAG_ *. Další informace o příznacích INTERNET_FLAG_\* naleznete v tématu [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) .

*pstrView*<br/>
Ukazatel na řetězec zobrazení souboru. Pokud na serveru existuje několik zobrazení souboru, tento parametr určuje, které zobrazení souboru má být otevřeno. Pokud má *pstrView* hodnotu null, použije se výchozí zobrazení souboru.

*dwContext*<br/>
ID kontextu otevřeného souboru. Další informace o *dwContext*najdete v tématu **poznámky** .

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CGopherFile –](../../mfc/reference/cgopherfile-class.md) , který má být otevřen.

### <a name="remarks"></a>Poznámky

Přepsáním výchozí *dwContext* nastavte identifikátor kontextu na hodnotu, kterou zvolíte. Identifikátor kontextu je spojen s touto konkrétní operací `CGopherConnection` objektu vytvořeného jeho objektem [CInternetSession](../../mfc/reference/cinternetsession-class.md) . Hodnota se vrátí do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , která poskytne stav operace, se kterou se identifikuje. Přečtěte si [článek Internet First Step: Rozhraní](../../mfc/wininet-basics.md) WinInet pro další informace o identifikátoru kontextu.

## <a name="see-also"></a>Viz také:

[CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection – třída](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection – třída](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator – třída](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession – třída](../../mfc/reference/cinternetsession-class.md)
