---
title: Chttpconnection – třída
ms.date: 03/27/2019
f1_keywords:
- CHttpConnection
- AFXINET/CHttpConnection
- AFXINET/CHttpConnection::CHttpConnection
- AFXINET/CHttpConnection::OpenRequest
helpviewer_keywords:
- CHttpConnection [MFC], CHttpConnection
- CHttpConnection [MFC], OpenRequest
ms.assetid: a402b662-c445-4988-800d-c8278551babe
ms.openlocfilehash: 1941af1e16a897235dd90db509d6ed29c2d9a875
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237566"
---
# <a name="chttpconnection-class"></a>Chttpconnection – třída

Spravuje připojení k serveru HTTP.

## <a name="syntax"></a>Syntaxe

```
class CHttpConnection : public CInternetConnection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CHttpConnection::CHttpConnection](#chttpconnection)|Vytvoří `CHttpConnection` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CHttpConnection::OpenRequest](#openrequest)|Otevře se požadavek HTTP.|

## <a name="remarks"></a>Poznámky

HTTP je jedním ze tří protokolů serveru Internet pomocí tříd WinInet knihovny MFC implementovat.

Třída `CHttpConnection` obsahuje konstruktor a jednu členskou funkci, [OpenRequest](#openrequest), který spravuje připojení k serveru pomocí protokolu HTTP.

Ke komunikaci se serverem protokolu HTTP, musíte nejprve vytvořit instanci [cinternetsession –](../../mfc/reference/cinternetsession-class.md)a pak vytvořte [chttpconnection –](#chttpconnection) objektu. Nikdy nevytvářejte `CHttpConnection` objektu přímo; místo toho volat [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection), která vytvoří `CHttpConnection` objekt a vrátí ukazatel na něj.

Další informace o tom, `CHttpConnection` funguje s jinými třídami MFC Internetu najdete v článku [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md). Další informace o připojení k serverům pomocí další dvě podporované Internetové protokoly, gopher a protokolu FTP, viz třídy [cgopherconnection –](../../mfc/reference/cgopherconnection-class.md) a [cftpconnection –](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

##  <a name="chttpconnection"></a>  CHttpConnection::CHttpConnection

Tato členská funkce je volána k sestavení kompletních `CHttpConnection` objektu.

```
CHttpConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CHttpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 1);

CHttpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pSession*<br/>
Ukazatel [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objektu.

*hConnected*<br/>
Popisovač pro připojení k Internetu.

*pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru.

*dwContext*<br/>
Identifikátor kontextu `CInternetConnection` objektu. Další informace o *dwContext*, najdete v článku **poznámky** oddílu.

*nPort*<br/>
Číslo, které identifikuje port Internet pro toto připojení.

*pstrUserName*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje jméno uživatele k přihlášení. Pokud má hodnotu NULL, výchozí hodnota je anonymous.

*pstrPassword*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje heslo, které používáte k přihlášení. Pokud mají oba *pstrPassword* a *pstrUserName* hodnotu Null, je výchozí heslo anonymní uživatelské jméno e-mailu. Pokud *pstrPassword* má hodnotu NULL nebo prázdný řetězec, ale *pstrUserName* nemá hodnotu NULL, prázdné heslo se používá. Následující tabulka popisuje chování pro čtyři možných nastavení *pstrUserName* a *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Uživatelské jméno odeslané na FTP server|Heslo odeslaných na FTP server|
|--------------------|--------------------|---------------------------------|---------------------------------|
|Hodnotu NULL nebo ""|Hodnotu NULL nebo ""|"anonymní"|Uživatelské jméno e-mailu|
|Řetězec NENULOVÉ|Hodnotu NULL nebo ""|*pstrUserName*|" "|
|NULL |Řetězec NENULOVÉ|CHYBA|CHYBA|
|Řetězec NENULOVÉ|Řetězec NENULOVÉ|*pstrUserName*|*pstrPassword*|

*dwFlags*<br/>
Libovolnou kombinaci `INTERNET_FLAG_*` příznaky. Viz tabulka **poznámky** část [CHttpConnection::OpenRequest](#openrequest) popis *dwFlags* hodnoty.

### <a name="remarks"></a>Poznámky

Nikdy nevytvářejte `CHttpConnection` přímo. Místo toho vytvořit objekt voláním [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection).

##  <a name="openrequest"></a>  CHttpConnection::OpenRequest

Voláním této členské funkce a otevřete připojení HTTP.

```
CHttpFile* OpenRequest(
    LPCTSTR pstrVerb,
    LPCTSTR pstrObjectName,
    LPCTSTR pstrReferer = NULL,
    DWORD_PTR dwContext = 1,
    LPCTSTR* ppstrAcceptTypes = NULL,
    LPCTSTR pstrVersion = NULL,
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);

CHttpFile* OpenRequest(
    int nVerb,
    LPCTSTR pstrObjectName,
    LPCTSTR pstrReferer = NULL,
    DWORD_PTR dwContext = 1,
    LPCTSTR* ppstrAcceptTypes = NULL,
    LPCTSTR pstrVersion = NULL,
    DWORD dwFlags = INTERNET_FLAG_EXISTING_CONNECT);
```

### <a name="parameters"></a>Parametry

*pstrVerb*<br/>
Ukazatel na řetězec obsahující příkaz pro použití v požadavku. Pokud má hodnotu NULL, je použít "GET".

*pstrObjectName*<br/>
Ukazatel na řetězec obsahující zadaný příkaz cílového objektu. Tento řetězec je obvykle název souboru, spustitelného souboru modulu nebo specifikátor vyhledávání.

*pstrReferer*<br/>
Ukazatel na řetězec, který určuje adresu (URL) dokumentu, ze které adresu URL v požadavku (*pstrObjectName*) byl získán. Pokud má hodnotu NULL, je určena žádné záhlaví HTTP.

*dwContext*<br/>
Identifikátor kontextu `OpenRequest` operace. Další informace o *dwContext*, naleznete v části poznámky.

*ppstrAcceptTypes*<br/>
Ukazatel na pole zakončené znakem null LPCTSTR ukazatelů na řetězce, které označují typy obsahu, klient přijal. Pokud *ppstrAcceptTypes* má hodnotu NULL, servery interpretovat, klient přijímá pouze dokumentů typu "text / *" (to znamená, jenom textové dokumenty a obrázky ani jiných binárních souborů). Typ obsahu je ekvivalentní k proměnné CONTENT_TYPE CGI, která identifikuje typ dat pro dotazy, které obsahují připojené informace, jako je například HTTP POST a PUT.

*pstrVersion*<br/>
Ukazatel na řetězec definice verze protokolu HTTP. Pokud má hodnotu NULL, použije se "HTTP verze 1.0".

*dwFlags*<br/>
Jakékoli kombinace příznaků INTERNET_ FLAG_ *. V části poznámky popis možných *dwFlags* hodnoty.

*nVerb*<br/>
Číslo přidružené k typu požadavku HTTP. Může být jedna z následujících akcí:

|Typ požadavku HTTP|*nVerb* value|
|-----------------------|-------------------|
|HTTP_VERB_POST|0|
|HTTP_VERB_GET|1|
|HTTP_VERB_HEAD|2|
|HTTP_VERB_PUT|3|
|HTTP_VERB_LINK|4|
|HTTP_VERB_DELETE|5|
|HTTP_VERB_UNLINK|6|

### <a name="return-value"></a>Návratová hodnota

Ukazatel [chttpfile –](../../mfc/reference/chttpfile-class.md) požadovaný objekt.

### <a name="remarks"></a>Poznámky

*dwFlags* může být jedna z následujících akcí:

|Příznak Internet|Popis|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|Vynutí stahování požadovaného souboru, objekt nebo výpis adresáře ze zdrojového serveru, nikoli z mezipaměti.|
|INTERNET_FLAG_DONT_CACHE|Nepřidává vrácenou entitu do mezipaměti.|
|INTERNET_FLAG_MAKE_PERSISTENT|Jako trvalé entita přidá vrácenou entitu do mezipaměti. To znamená, že standardní mezipaměti čištění, kontrola konzistence nebo uvolňování paměti nelze odstranit tuto položku z mezipaměti.|
|INTERNET_FLAG_SECURE|Používá sémantiku zabezpečené transakce. Přeloží na používání protokolu SSL a PCT a pouze má smysl v požadavcích HTTP|
|INTERNET_FLAG_NO_AUTO_REDIRECT|Použít pouze s protokolem HTTP, určuje, že přesměrování by neměl být zpracována automaticky v [CHttpFile::SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|

Přepsat `dwContext` výchozí identifikátor kontextu nastavena na hodnotu podle vašeho výběru. Identifikátor kontextu souvisí s tuto konkrétní operaci `CHttpConnection` objekt vytvořený pomocí jeho [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objektu. Hodnota se vrátí do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) kvůli stavu na operaci, se kterým je identifikován. Přečtěte si článek [Internet první kroky: WinInet](../../mfc/wininet-basics.md) Další informace o identifikátor kontextu.

Pomocí této funkce může být vyvoláno výjimek.

## <a name="see-also"></a>Viz také:

[CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpFile – třída](../../mfc/reference/chttpfile-class.md)
