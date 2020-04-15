---
title: Třída Připojení Chttp
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
ms.openlocfilehash: af402b532b3aba28bdfefea5afa67331765db4c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351819"
---
# <a name="chttpconnection-class"></a>Třída Připojení Chttp

Spravuje připojení k serveru HTTP.

## <a name="syntax"></a>Syntaxe

```
class CHttpConnection : public CInternetConnection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[ChttpConnection::Připojení Chttp](#chttpconnection)|Vytvoří `CHttpConnection` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[ChttpConnection::OpenRequest](#openrequest)|Otevře požadavek HTTP.|

## <a name="remarks"></a>Poznámky

HTTP je jedním ze tří protokolů serveru Sítě Internet implementovaných třídami WinInet knihovny MFC.

Třída `CHttpConnection` obsahuje konstruktor a jednu členovou funkci [OpenRequest](#openrequest), která spravuje připojení k serveru s protokolem HTTP.

Chcete-li komunikovat se serverem HTTP, musíte nejprve vytvořit instanci [CInternetSession](../../mfc/reference/cinternetsession-class.md)a potom vytvořit objekt [CHttpConnection.](#chttpconnection) Nikdy nevytváříte `CHttpConnection` objekt přímo; místo toho volání [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection) `CHttpConnection` , který vytvoří objekt a vrátí mu ukazatel.

Další informace o `CHttpConnection` práci s ostatními třídami MFC Internet naleznete v článku [Internetové programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md). Další informace o připojení k serverům pomocí dalších dvou podporovaných internetových protokolů, gopher a FTP, naleznete v třídách [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) a [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CHttpConnection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="chttpconnectionchttpconnection"></a><a name="chttpconnection"></a>ChttpConnection::Připojení Chttp

Tato členská funkce je `CHttpConnection` volána k vytvoření objektu.

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

*pRelace*<br/>
Ukazatel na objekt [CInternetSession.](../../mfc/reference/cinternetsession-class.md)

*hPřipojeno*<br/>
Popisovač připojení k Internetu.

*server pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru.

*dwKontext*<br/>
Identifikátor kontextu pro `CInternetConnection` objekt. Další informace o *dwContext*naleznete v části **Poznámky.**

*nPort*<br/>
Číslo, které identifikuje internetový port pro toto připojení.

*pstrUserName*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který určuje jméno uživatele, který se má přihlásit. Pokud null, výchozí hodnota je anonymní.

*pstrPassword*<br/>
Ukazatel na řetězec s nulovým ukončením, který určuje heslo, které se má použít k přihlášení. Pokud jsou *hodnota pstrPassword* i *pstrUserName* null, je výchozím anonymním heslem e-mailové jméno uživatele. Pokud *pstrPassword* je NULL nebo prázdný řetězec, ale *pstrUserName* není NULL, je použito prázdné heslo. Následující tabulka popisuje chování pro čtyři možná nastavení *pstrUserName* a *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Uživatelské jméno odeslané serveru FTP|Heslo odeslané na server FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|Null nebo " "|Null nebo " "|"anonymní"|E-mailová značka uživatele|
|Řetězec bez hodnoty NULL|Null nebo " "|*pstrUserName*|" "|
|NULL |Řetězec bez hodnoty NULL|ERROR|ERROR|
|Řetězec bez hodnoty NULL|Řetězec bez hodnoty NULL|*pstrUserName*|*pstrPassword*|

*dwFlags*<br/>
Jakákoliv kombinace `INTERNET_FLAG_*` vlajek. Popis hodnot *dwFlags* naleznete v tabulce v části **Poznámky** [v chttpconnection::OpenRequest.](#openrequest)

### <a name="remarks"></a>Poznámky

Nikdy nevytváříte `CHttpConnection` přímo. Místo toho vytvoříte objekt voláním [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection).

## <a name="chttpconnectionopenrequest"></a><a name="openrequest"></a>ChttpConnection::OpenRequest

Volání této členské funkce otevřete připojení HTTP.

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
Ukazatel na řetězec obsahující sloveso, které má být v požadavku použít. Pokud null, "GET" se používá.

*pstrObjectName*<br/>
Ukazatel na řetězec obsahující cílový objekt zadaného slovesa. Tento řetězec je obecně název souboru, spustitelný modul nebo specifikátor hledání.

*pstrReferer*<br/>
Ukazatel na řetězec, který určuje adresu (URL) dokumentu, ze kterého byla získána adresa URL v požadavku *(pstrObjectName).* Pokud null, není zadána žádná hlavička HTTP.

*dwKontext*<br/>
Identifikátor kontextu pro `OpenRequest` operaci. Další informace o *dwContext*naleznete v části Poznámky.

*ppstrAcceptTypes*<br/>
Ukazatel na pole lPCTSTR ukončené s nulou na řetězce označující typy obsahu přijaté klientem. Pokud *ppstrAcceptTypes* je NULL, servery interpretovat, že klient přijímá pouze dokumenty typu "text/*" (to znamená, že pouze textové dokumenty a ne obrázky nebo jiné binární soubory). Typ obsahu je ekvivalentní proměnné CGI CONTENT_TYPE, která identifikuje typ dat pro dotazy, které mají připojené informace, jako je například HTTP POST a PUT.

*pstrVersion*<br/>
Ukazatel na řetězec definující verzi HTTP. Pokud null, "HTTP/1.0" se používá.

*dwFlags*<br/>
Libovolná kombinace příznaků INTERNET_ FLAG_*. Popis možných hodnot *dwFlags* naleznete v části Poznámky.

*nSVNože*<br/>
Číslo přidružené k typu požadavku HTTP. Může to být jedna z následujících možností:

|Typ požadavku HTTP|*nSLovečná* hodnota|
|-----------------------|-------------------|
|HTTP_VERB_POST|0|
|HTTP_VERB_GET|1|
|HTTP_VERB_HEAD|2|
|HTTP_VERB_PUT|3|
|HTTP_VERB_LINK|4|
|HTTP_VERB_DELETE|5|
|HTTP_VERB_UNLINK|6|

### <a name="return-value"></a>Návratová hodnota

Ukazatel na požadovaný objekt [CHttpFile.](../../mfc/reference/chttpfile-class.md)

### <a name="remarks"></a>Poznámky

*dwFlags* může být jedna z následujících možností:

|Internetový příznak|Popis|
|-------------------|-----------------|
|INTERNET_FLAG_RELOAD|Vynutí stažení požadovaného souboru, objektu nebo výpisu adresáře ze zdrojového serveru, nikoli z mezipaměti.|
|INTERNET_FLAG_DONT_CACHE|Nepřidá vrácenou entitu do mezipaměti.|
|INTERNET_FLAG_MAKE_PERSISTENT|Přidá vrácenou entitu do mezipaměti jako trvalou entitu. To znamená, že standardní vyčištění mezipaměti, kontrola konzistence nebo uvolňování paměti nelze odebrat tuto položku z mezipaměti.|
|INTERNET_FLAG_SECURE|Používá zabezpečenou sémantiku transakcí. To se promítá do použití SSL/PCT a je pouze smysluplné v požadavcích HTTP|
|INTERNET_FLAG_NO_AUTO_REDIRECT|Používá se pouze s protokolem HTTP, určuje, že přesměrování by neměla být zpracována automaticky v [CHttpFile::SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|

Přepište `dwContext` výchozí nastavení identifikátoru kontextu na hodnotu podle vašeho výběru. Identifikátor kontextu je spojen s touto `CHttpConnection` konkrétní operací objektu vytvořeného jeho objektem [CInternetSession.](../../mfc/reference/cinternetsession-class.md) Hodnota je vrácena [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav operace, s níž je identifikován. Další informace o identifikátoru kontextu naleznete v článku [První kroky Internetu: WinInet.](../../mfc/wininet-basics.md)

S touto funkcí mohou být vyvolány výjimky.

## <a name="see-also"></a>Viz také

[Třída CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpFile – třída](../../mfc/reference/chttpfile-class.md)
