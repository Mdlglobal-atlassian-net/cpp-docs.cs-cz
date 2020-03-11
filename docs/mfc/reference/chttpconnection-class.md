---
title: CHttpConnection – třída
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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890775"
---
# <a name="chttpconnection-class"></a>CHttpConnection – třída

Spravuje připojení k serveru HTTP.

## <a name="syntax"></a>Syntaxe

```
class CHttpConnection : public CInternetConnection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CHttpConnection::CHttpConnection](#chttpconnection)|Vytvoří objekt `CHttpConnection`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CHttpConnection::OpenRequest](#openrequest)|Otevře požadavek HTTP.|

## <a name="remarks"></a>Poznámky

HTTP je jedním ze tří internetových serverových protokolů implementovaných třídami WinInet knihovny MFC.

Třída `CHttpConnection` obsahuje konstruktor a jednu členskou funkci [OpenRequest](#openrequest), která spravuje připojení k serveru s protokolem HTTP.

Aby bylo možné komunikovat se serverem HTTP, je nutné nejprve vytvořit instanci třídy [CInternetSession](../../mfc/reference/cinternetsession-class.md)a pak vytvořit objekt [CHttpConnection](#chttpconnection) . Nikdy nevytvoříte objekt `CHttpConnection` přímo; místo toho zavolejte [CInternetSession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection), které vytvoří objekt `CHttpConnection` a vrátí ukazatel na něj.

Další informace o tom, jak `CHttpConnection` pracuje s dalšími internetovými třídami knihovny MFC, najdete v článku [internetové programování s](../../mfc/win32-internet-extensions-wininet.md)rozhraním Wininet. Další informace o připojení k serverům pomocí dalších dvou podporovaných protokolů sítě Internet, gopher a FTP naleznete v tématu třídy [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) a [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet. h

##  <a name="chttpconnection"></a>CHttpConnection::CHttpConnection

Tato členská funkce je volána k vytvoření objektu `CHttpConnection`.

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
Ukazatel na objekt [CInternetSession](../../mfc/reference/cinternetsession-class.md) .

*hConnected*<br/>
Popisovač připojení k Internetu.

*pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru.

*dwContext*<br/>
Identifikátor kontextu pro objekt `CInternetConnection`. Další informace o *dwContext*naleznete v části **poznámky** .

*nPort*<br/>
Číslo identifikující Internetový port pro toto připojení.

*pstrUserName*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje jméno uživatele, který se má přihlásit. Pokud má hodnotu NULL, je výchozí hodnota anonymní.

*pstrPassword*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje heslo, které se má použít pro přihlášení. Pokud mají hodnoty *pstrPassword* i *pstrUserName* hodnotu null, výchozím anonymním heslem je e-mailová adresa uživatele. Pokud má *pstrPassword* hodnotu null nebo prázdný řetězec, ale *pstrUserName* není null, použije se prázdné heslo. Následující tabulka popisuje chování pro čtyři možná nastavení *pstrUserName* a *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Uživatelské jméno odeslané na server FTP|Heslo odeslané na server FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL nebo ""|NULL nebo ""|Anonymous|E-mailová adresa uživatele|
|Řetězec, který není NULL|NULL nebo ""|*pstrUserName*|" "|
|NULL |Řetězec, který není NULL|CHYBA|CHYBA|
|Řetězec, který není NULL|Řetězec, který není NULL|*pstrUserName*|*pstrPassword*|

*dwFlags*<br/>
Libovolná kombinace příznaků `INTERNET_FLAG_*`. Popis hodnot *dwFlags* najdete v tabulce v části **poznámky** v tématu [CHttpConnection:: OpenRequest](#openrequest) .

### <a name="remarks"></a>Poznámky

Nikdy nevytvoříte `CHttpConnection` přímo. Místo toho vytvoříte objekt voláním [CInternetSession:: GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection).

##  <a name="openrequest"></a>CHttpConnection::OpenRequest

Zavolejte tuto členskou funkci pro otevření připojení HTTP.

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
Ukazatel na řetězec obsahující příkaz, který má být použit v požadavku. Pokud má hodnotu NULL, použije se "GET".

*pstrObjectName*<br/>
Ukazatel na řetězec obsahující cílový objekt zadaného příkazu. Tento řetězec je obecně název souboru, spustitelný modul nebo specifikátor hledání.

*pstrReferer*<br/>
Ukazatel na řetězec, který určuje adresu (URL) dokumentu, ze kterého byla získána adresa URL v žádosti (*pstrObjectName*). Pokud má hodnotu NULL, není zadána hlavička HTTP.

*dwContext*<br/>
Identifikátor kontextu pro operaci `OpenRequest`. Další informace o *dwContext*naleznete v části poznámky.

*ppstrAcceptTypes*<br/>
Ukazatel na pole zakončené znakem null u ukazatelů LPCTSTR na řetězce indikující typy obsahu, které klient přijal. Pokud má *ppstrAcceptTypes* hodnotu null, servery interpretují, že klient přijímá pouze dokumenty typu "text/*" (tj. pouze textové dokumenty, ne obrázky nebo jiné binární soubory). Typ obsahu je ekvivalentní proměnné CONTENT_TYPE rozhraní CGI, která identifikuje typ dat pro dotazy, které mají připojené informace, například HTTP POST a PUT.

*pstrVersion*<br/>
Ukazatel na řetězec definující verzi protokolu HTTP. Pokud má hodnotu NULL, použije se HTTP/1.0.

*dwFlags*<br/>
Libovolná kombinace příznaků INTERNET_ FLAG_ *. Popis možných hodnot *dwFlags* naleznete v části poznámky.

*nVerb*<br/>
Číslo přidružené k typu požadavku HTTP Může být jedna z následujících akcí:

|Typ požadavku HTTP|hodnota *nVerb*|
|-----------------------|-------------------|
|HTTP_VERB_POST|0|
|HTTP_VERB_GET|1|
|HTTP_VERB_HEAD|2|
|HTTP_VERB_PUT|3|
|HTTP_VERB_LINK|4|
|HTTP_VERB_DELETE|5|
|HTTP_VERB_UNLINK|6|

### <a name="return-value"></a>Návratová hodnota

Byl požadován ukazatel na požadovaný objekt [CHttpFile](../../mfc/reference/chttpfile-class.md) .

### <a name="remarks"></a>Poznámky

*dwFlags* může být jedna z následujících:

|Příznak Internetu|Popis|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|Vynutí stažení požadovaného souboru, objektu nebo seznamu adresářů ze zdrojového serveru, nikoli z mezipaměti.|
|INTERNET_FLAG_DONT_CACHE|Nepřidá vrácenou entitu do mezipaměti.|
|INTERNET_FLAG_MAKE_PERSISTENT|Přidá vrácenou entitu do mezipaměti jako trvalou entitu. Znamená to, že standardní vyčištění mezipaměti, kontrola konzistence nebo uvolňování paměti nemůže odebrat tuto položku z mezipaměti.|
|INTERNET_FLAG_SECURE|Používá sémantiku zabezpečené transakce. Překládá se na použití protokolu SSL/PCT a je smysluplné pouze v případě požadavků HTTP.|
|INTERNET_FLAG_NO_AUTO_REDIRECT|Používá se pouze s protokolem HTTP, určuje, že přesměry by neměly být zpracovány automaticky v [CHttpFile:: SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|

Přepsáním `dwContext` výchozí nastavte identifikátor kontextu na hodnotu, kterou zvolíte. Identifikátor kontextu je přidružen k této konkrétní operaci objektu `CHttpConnection` vytvořeného jeho objektem [CInternetSession](../../mfc/reference/cinternetsession-class.md) . Hodnota se vrátí do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , která poskytne stav operace, se kterou je identifikovaný. Další informace o identifikátoru kontextu najdete v článku [Internet First Steps: WinInet](../../mfc/wininet-basics.md) .

Pomocí této funkce mohou být vyvolány výjimky.

## <a name="see-also"></a>Viz také

[CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpFile – třída](../../mfc/reference/chttpfile-class.md)
