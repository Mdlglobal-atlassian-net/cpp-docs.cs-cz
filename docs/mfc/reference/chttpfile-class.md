---
title: CHttpFile – třída
ms.date: 11/04/2016
f1_keywords:
- CHttpFile
- AFXINET/CHttpFile
- AFXINET/CHttpFile::CHttpFile
- AFXINET/CHttpFile::AddRequestHeaders
- AFXINET/CHttpFile::EndRequest
- AFXINET/CHttpFile::GetFileURL
- AFXINET/CHttpFile::GetObject
- AFXINET/CHttpFile::GetVerb
- AFXINET/CHttpFile::QueryInfo
- AFXINET/CHttpFile::QueryInfoStatusCode
- AFXINET/CHttpFile::SendRequest
- AFXINET/CHttpFile::SendRequestEx
helpviewer_keywords:
- CHttpFile [MFC], CHttpFile
- CHttpFile [MFC], AddRequestHeaders
- CHttpFile [MFC], EndRequest
- CHttpFile [MFC], GetFileURL
- CHttpFile [MFC], GetObject
- CHttpFile [MFC], GetVerb
- CHttpFile [MFC], QueryInfo
- CHttpFile [MFC], QueryInfoStatusCode
- CHttpFile [MFC], SendRequest
- CHttpFile [MFC], SendRequestEx
ms.assetid: 399e7c68-bbce-4374-8c55-206e9c7baac6
ms.openlocfilehash: cba3ba7d86577703de2bf5709d66bbd5e0298863
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368396"
---
# <a name="chttpfile-class"></a>CHttpFile – třída

Poskytuje funkce pro vyžádání a čtení souborů na serveru HTTP.

## <a name="syntax"></a>Syntaxe

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Soubor Chttp::soubor ChttpFile](#chttpfile)|Vytvoří `CHttpFile` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[ChttpFile::AddRequestHeaders](#addrequestheaders)|Přidá záhlaví požadavku odeslaného na server HTTP.|
|[ChttpFile::EndRequest](#endrequest)|Ukončí požadavek odeslaný na server HTTP pomocí členské funkce [SendRequestEx.](#sendrequestex)|
|[ChttpFile::GetFileURL](#getfileurl)|Získá adresu URL pro zadaný soubor.|
|[ChttpFile::GetObject](#getobject)|Získá cílový objekt slovesa v požadavku na server HTTP.|
|[ChttpFile::GetVerb](#getverb)|Získá sloveso, který byl použit v požadavku na http server.|
|[ChttpFile::QueryInfo](#queryinfo)|Vrátí záhlaví odpovědí nebo požadavků ze serveru HTTP.|
|[ChttpFile::Kód InfoStatusCode QueryInfo](#queryinfostatuscode)|Načte stavový kód přidružený k požadavku HTTP `dwStatusCode` a umístí jej do zadaného parametru.|
|[ChttpFile::Požadavek na odeslání](#sendrequest)|Odešle požadavek na server HTTP.|
|[ChttpFile::SendRequestEx](#sendrequestex)|Odešle požadavek na server HTTP pomocí metod `CInternetFile` [Write](../../mfc/reference/cinternetfile-class.md#write) nebo [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) aplikace .|

## <a name="remarks"></a>Poznámky

Pokud vaše relace V Internetu čte data ze serveru `CHttpFile`HTTP, je nutné vytvořit instanci aplikace .

Další informace o `CHttpFile` práci s ostatními třídami MFC Internet naleznete v článku [Internetové programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Soubor C](../../mfc/reference/cfile-class.md)

[Soubor CStdio](../../mfc/reference/cstdiofile-class.md)

[Soubor CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="chttpfileaddrequestheaders"></a><a name="addrequestheaders"></a>ChttpFile::AddRequestHeaders

Volání této členské funkce přidat jeden nebo více hlavičky požadavku HTTP do popisovače požadavku HTTP.

```
BOOL AddRequestHeaders(
    LPCTSTR pstrHeaders,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW,
    int dwHeadersLen = -1);

BOOL AddRequestHeaders(
    CString& str,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW);
```

### <a name="parameters"></a>Parametry

*hlavičky str*<br/>
Ukazatel na řetězec obsahující záhlaví nebo záhlaví připojit k požadavku. Každá hlavička musí být ukončena dvojicí CR/LF.

*dwFlags*<br/>
Upravuje sémantiku nových záhlaví. Může to být jedna z následujících možností:

- HTTP_ADDREQ_FLAG_COALESCE Sloučí záhlaví se stejným názvem a pomocí příznaku přidáte první nalezenou hlavičku do následující hlavičky. Například\*"Přijmout: text/ " následovaný "Přijmout: audio/\*" má za následek vytvoření\*jediného\*záhlaví "Přijmout: text/ , audio/ ". Je na volající aplikaci, aby zajistila soudržné schéma, pokud jde o údaje přijaté na základě žádostí zaslaných se soupozovanými nebo samostatnými hlavičkami.

- HTTP_ADDREQ_FLAG_REPLACE Provede odebrání a přidání nahradit aktuální záhlaví. Název záhlaví bude použit k odebrání aktuálníhlavičky a úplná hodnota bude použita k přidání nového záhlaví. Pokud je hodnota záhlaví prázdná a záhlaví je nalezeno, je odebrána. Pokud není prázdný, hodnota záhlaví je nahrazena.

- HTTP_ADDREQ_FLAG_ADD_IF_NEW Pouze přidá záhlaví, pokud ještě neexistuje. Pokud jeden existuje, je vrácena chyba.

- HTTP_ADDREQ_FLAG_ADD Používá se s REPLACE. Přidá záhlaví, pokud neexistuje.

*dwHeadersLen*<br/>
Délka, ve znacích, *pstrHeaders*. Pokud je to -1L, pak *pstrHeaders* se předpokládá, že nula ukončena a délka je vypočítána.

*Str*<br/>
Odkaz na [cstring](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující hlavičku požadavku nebo hlavičky, které mají být přidány.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

### <a name="remarks"></a>Poznámky

`AddRequestHeaders`připojí další, volné formátzáhlaví popisovač požadavku HTTP. Je určen pro sofistikované klienty, kteří potřebují podrobnou kontrolu nad přesným požadavkem odeslanou na HTTP server.

> [!NOTE]
> Aplikace může předat více záhlaví v *pstrHeaders* nebo *str* pro `AddRequestHeaders` volání pomocí HTTP_ADDREQ_FLAG_ADD nebo HTTP_ADDREQ_FLAG_ADD_IF_NEW. Pokud se aplikace pokusí odebrat nebo nahradit záhlaví pomocí HTTP_ADDREQ_FLAG_REMOVE nebo HTTP_ADDREQ_FLAG_REPLACE, lze v *lpszHeaders*poskytnout pouze jednu hlavičku .

## <a name="chttpfilechttpfile"></a><a name="chttpfile"></a>Soubor Chttp::soubor ChttpFile

Tato členská funkce je `CHttpFile` volána k vytvoření objektu.

```
CHttpFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrObject,
    LPCTSTR pstrServer,
    LPCTSTR pstrVerb,
    DWORD_PTR dwContext);

CHttpFile(
    HINTERNET hFile,
    LPCTSTR pstrVerb,
    LPCTSTR pstrObject,
    CHttpConnection* pConnection);
```

### <a name="parameters"></a>Parametry

*hSoubor*<br/>
Popisovač k souboru internetu.

*hRelace*<br/>
Popisovač relace Internetu.

*objekt pstrObject*<br/>
Ukazatel na řetězec obsahující `CHttpFile` objekt.

*server pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru.

*pstrVerb*<br/>
Ukazatel na řetězec obsahující metodu, která má být použita při odesílání požadavku. Může být POST, HEAD nebo GET.

*dwKontext*<br/>
Identifikátor kontextu pro `CHttpFile` objekt. Další informace o tomto parametru naleznete v **tématu Poznámky.**

*pPřipojení*<br/>
Ukazatel na objekt [CHttpConnection.](../../mfc/reference/chttpconnection-class.md)

### <a name="remarks"></a>Poznámky

Nikdy postavit `CHttpFile` objekt přímo; spíše volat [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) nebo [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) místo.

Výchozí hodnota `dwContext` pro je odeslána `CHttpFile` knihovnou MFC do objektu `CHttpFile` z objektu [CInternetSession,](../../mfc/reference/cinternetsession-class.md) který objekt vytvořil. Při volání `CInternetSession::OpenURL` `CHttpConnection` nebo vytvoření `CHttpFile` objektu můžete přepsat výchozí nastavení identifikátoru kontextu na hodnotu podle vašeho výběru. Identifikátor kontextu je [vrácena CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav na objekt, se kterým je identifikován. Další informace o identifikátoru kontextu naleznete v článku [První kroky Internetu: WinInet.](../../mfc/wininet-basics.md)

## <a name="chttpfileendrequest"></a><a name="endrequest"></a>ChttpFile::EndRequest

Volání této členské funkce ukončit požadavek odeslaný na http server s [SendRequestEx](#sendrequestex) členské funkce.

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Příznaky popisující operaci. Seznam příslušných příznaků naleznete v [tématu HttpEndRequest](/windows/win32/api/wininet/nf-wininet-httpendrequestw) v sadě Windows SDK.

*lpBuffIn*<br/>
Ukazatel na inicializovaný [INTERNET_BUFFERS,](/windows/win32/api/wininet/ns-wininet-internet_buffersw) který popisuje vstupní vyrovnávací paměť použitou pro operaci.

*dwKontext*<br/>
Identifikátor kontextu pro `CHttpFile` operaci. Další informace o tomto parametru naleznete v tématu Poznámky.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, zjistěte příčinu selhání kontrolou objektu [CInternetException.](../../mfc/reference/cinternetexception-class.md)

### <a name="remarks"></a>Poznámky

Výchozí hodnota pro *dwContext* je odeslána `CHttpFile` knihovnou MFC do objektu z objektu [CInternetSession,](../../mfc/reference/cinternetsession-class.md) který `CHttpFile` objekt vytvořil. Když zavoláte [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) nebo [CHttpConnection](../../mfc/reference/chttpconnection-class.md) k vytvoření objektu, `CHttpFile` můžete přepsat výchozí nastavení identifikátoru kontextu na hodnotu podle vašeho výběru. Identifikátor kontextu je [vrácena CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav na objekt, se kterým je identifikován. Další informace o identifikátoru kontextu naleznete v článku [První kroky Internetu: WinInet.](../../mfc/wininet-basics.md)

## <a name="chttpfilegetfileurl"></a><a name="getfileurl"></a>ChttpFile::GetFileURL

Volání této členské funkce získat název souboru HTTP jako URL.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující adresu URL odkazující na prostředek přidružený k tomuto souboru.

### <a name="remarks"></a>Poznámky

Tuto člennou funkci použijte pouze po úspěšném `CHttpFile` volání [SendRequest](#sendrequest) nebo na objektu úspěšně vytvořeném [adresou OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

## <a name="chttpfilegetobject"></a><a name="getobject"></a>ChttpFile::GetObject

Volání této členské funkce získat název objektu `CHttpFile`přidruženého k této .

```
CString GetObject() const;
```

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující název objektu.

### <a name="remarks"></a>Poznámky

Tuto člennou funkci použijte pouze po úspěšném `CHttpFile` volání [SendRequest](#sendrequest) nebo na objektu úspěšně vytvořeném [adresou OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

## <a name="chttpfilegetverb"></a><a name="getverb"></a>ChttpFile::GetVerb

Volání této členské funkce získat http sloveso `CHttpFile`(nebo metoda) s tím spojené .

```
CString GetVerb() const;
```

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující název slovesa HTTP (nebo metody).

### <a name="remarks"></a>Poznámky

Tuto člennou funkci použijte pouze po úspěšném `CHttpFile` volání [SendRequest](#sendrequest) nebo na objektu úspěšně vytvořeném [adresou OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

## <a name="chttpfilequeryinfo"></a><a name="queryinfo"></a>ChttpFile::QueryInfo

Volání této členské funkce vrátit odpovědi nebo hlavičky požadavku z požadavku HTTP.

```
BOOL QueryInfo(
    DWORD dwInfoLevel,
    LPVOID lpvBuffer,
    LPDWORD lpdwBufferLength,
    LPDWORD lpdwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    CString& str,
    LPDWORD dwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    SYSTEMTIME* pSysTime,
    LPDWORD dwIndex = NULL) const;
```

### <a name="parameters"></a>Parametry

*dwInfoLevel*<br/>
Kombinace atributu query a následujících příznaků, které určují typ požadovaných informací:

- HTTP_QUERY_CUSTOM Najde název záhlaví a vrátí tuto hodnotu v *lpvBuffer* na výstupu. HTTP_QUERY_CUSTOM vyvolá kontrolní výraz, pokud záhlaví není nalezen.

- HTTP_QUERY_FLAG_REQUEST_HEADERS Aplikace obvykle dotazuje záhlaví odpovědí, ale aplikace může také dotazovat záhlaví požadavků pomocí tohoto příznaku.

- HTTP_QUERY_FLAG_SYSTEMTIME Pro záhlaví, jejichž hodnota je řetězec data a času, například "Last-Modified-Time", tento příznak vrátí hodnotu záhlaví jako standardní strukturu Win32 [SYSTEMTIME,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) která nevyžaduje, aby aplikace analyzovat data. Pokud použijete tento příznak, můžete `SYSTEMTIME` použít přepsání funkce.

- HTTP_QUERY_FLAG_NUMBER Pro záhlaví, jejichž hodnota je číslo, například stavový kód, tento příznak vrátí data jako 32bitové číslo.

Seznam možných hodnot naleznete v části **Poznámky.**

*lpvBuffer*<br/>
Ukazatel na vyrovnávací paměť, která přijímá informace.

*lpdwBufferLength*<br/>
Při vstupu to odkazuje na hodnotu obsahující délku vyrovnávací paměti dat, počet znaků nebo bajtů. Podrobnější informace o tomto parametru naleznete v části **Poznámky.**

*lpdwIndex*<br/>
Ukazatel na index záhlaví založené na nule. Může být NULL. Tento příznak slouží k vytvoření výčtu více záhlaví se stejným názvem. Na vstupu *lpdwIndex* označuje index zadané hlavičky vrátit. Na výstupu *lpdwIndex* označuje index další záhlaví. Pokud nelze najít další index, je vrácena ERROR_HTTP_HEADER_NOT_FOUND.

*Str*<br/>
Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt upřijetí vrácené informace.

*dwIndex*<br/>
Hodnota indexu. Viz *lpdwIndex*.

*pSysTime*<br/>
Ukazatel na strukturu Win32 [SYSTEMTIME.](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

### <a name="remarks"></a>Poznámky

Tuto člennou funkci použijte pouze po úspěšném `CHttpFile` volání [SendRequest](#sendrequest) nebo na objektu úspěšně vytvořeném [adresou OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Můžete načíst následující typy `QueryInfo`dat z :

- řetězce (výchozí)

- `SYSTEMTIME`(pro "Data:" "Vyprší:" atd., záhlaví)

- DWORD (pro STATUS_CODE, CONTENT_LENGTH atd.)

Pokud je řetězec zapsán do vyrovnávací paměti a `lpdwBufferLength` členská funkce je úspěšná, obsahuje délku řetězce ve znacích mínus 1 pro ukončující znak NULL.

Možné hodnoty *dwInfoLevel* zahrnují:

- HTTP_QUERY_MIME_VERSION

- HTTP_QUERY_CONTENT_TYPE

- HTTP_QUERY_CONTENT_TRANSFER_ENCODING

- HTTP_QUERY_CONTENT_ID

- HTTP_QUERY_CONTENT_DESCRIPTION

- HTTP_QUERY_CONTENT_LENGTH

- HTTP_QUERY_ALLOWED_METHODS

- HTTP_QUERY_PUBLIC_METHODS

- HTTP_QUERY_DATE

- HTTP_QUERY_EXPIRES

- HTTP_QUERY_LAST_MODIFIED

- HTTP_QUERY_MESSAGE_ID

- HTTP_QUERY_URI

- HTTP_QUERY_DERIVED_FROM

- HTTP_QUERY_LANGUAGE

- HTTP_QUERY_COST

- HTTP_QUERY_WWW_LINK

- HTTP_QUERY_PRAGMA

- HTTP_QUERY_VERSION

- HTTP_QUERY_STATUS_CODE

- HTTP_QUERY_STATUS_TEXT

- HTTP_QUERY_RAW_HEADERS

- HTTP_QUERY_RAW_HEADERS_CRLF

## <a name="chttpfilequeryinfostatuscode"></a><a name="queryinfostatuscode"></a>ChttpFile::Kód InfoStatusCode QueryInfo

Volání této členské funkce získat stavový kód přidružený k požadavku HTTP a umístit jej do zadaného parametru *dwStatusCode.*

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>Parametry

*dwStatusCode*<br/>
Odkaz na stavový kód. Stavové kódy označují úspěch nebo neúspěch požadované události. Viz **Poznámky** pro výběr popisů stavového kódu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

### <a name="remarks"></a>Poznámky

Tuto člennou funkci použijte pouze po úspěšném `CHttpFile` volání [SendRequest](#sendrequest) nebo na objektu úspěšně vytvořeném [adresou OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Stavové kódy HTTP spadají do skupin označujících úspěch nebo neúspěch požadavku. Následující tabulky popisují skupiny stavového kódu a nejběžnější stavové kódy HTTP.

|Skupina|Význam|
|-----------|-------------|
|200-299|Úspěch|
|300-399|Informace|
|400-499|Chyba požadavku|
|500-599|Chyba serveru|

Společné kódy stavu HTTP:

|Kód stavu|Význam|
|-----------------|-------------|
|200|URL nachází, přenos takto|
|400|Nesrozumitelná žádost|
|404|Požadovaná adresa URL nebyla nalezena.|
|405|Server nepodporuje požadovanou metodu|
|500|Neznámá chyba serveru|
|503|Bylo dosaženo kapacity serveru.|

## <a name="chttpfilesendrequest"></a><a name="sendrequest"></a>ChttpFile::Požadavek na odeslání

Volání této členské funkce odeslat požadavek na server HTTP.

```
BOOL SendRequest(
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLen = 0,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);

BOOL SendRequest(
    CString& strHeaders,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);
```

### <a name="parameters"></a>Parametry

*hlavičky str*<br/>
Ukazatel na řetězec obsahující název záhlaví k odeslání.

*dwHeadersLen*<br/>
Délka záhlaví identifikované *strHeaders*.

*lpNepovinné*<br/>
Všechna volitelná data, která mají být odeslána ihned po hlavičkách požadavku. To se obecně používá pro operace POST a PUT. To může být NULL, pokud neexistuje žádná volitelná data k odeslání.

*dwOptionalLen*<br/>
Délka *lpOptional*.

*strZáhlaví*<br/>
Řetězec obsahující název záhlaví odesílaného požadavku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, zjistěte příčinu selhání kontrolou objektu [CInternetException.](../../mfc/reference/cinternetexception-class.md)

## <a name="chttpfilesendrequestex"></a><a name="sendrequestex"></a>ChttpFile::SendRequestEx

Volání této členské funkce odeslat požadavek na server HTTP.

```
BOOL SendRequestEx(
    DWORD dwTotalLen,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);

BOOL SendRequestEx(
    LPINTERNET_BUFFERS lpBuffIn,
    LPINTERNET_BUFFERS lpBuffOut,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*dwTotalLen*<br/>
Počet bajtů, které mají být odeslány v požadavku.

*dwFlags*<br/>
Příznaky popisující operaci. Seznam příslušných příznaků naleznete v [tématu HttpSendRequestEx](/windows/win32/api/wininet/nf-wininet-httpsendrequestexw) v sadě Windows SDK.

*dwKontext*<br/>
Identifikátor kontextu pro `CHttpFile` operaci. Další informace o tomto parametru naleznete v tématu Poznámky.

*lpBuffIn*<br/>
Ukazatel na inicializovaný [INTERNET_BUFFERS,](/windows/win32/api/wininet/ns-wininet-internet_buffersw) který popisuje vstupní vyrovnávací paměť použitou pro operaci.

*lpBuffOut*<br/>
Ukazatel na inicializovaný INTERNET_BUFFERS, který popisuje výstupní vyrovnávací paměť použitou pro operaci.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná. Pokud se volání nezdaří, zjistěte příčinu selhání kontrolou objektu [CInternetException.](../../mfc/reference/cinternetexception-class.md)

### <a name="remarks"></a>Poznámky

Tato funkce umožňuje aplikaci odesílat data pomocí `CInternetFile`write [a](../../mfc/reference/cinternetfile-class.md#write) [writestring](../../mfc/reference/cinternetfile-class.md#writestring) metody . Před voláním buď přepsání této funkce je nutné znát délku dat, která mají být odeslána. První přepsání umožňuje určit délku dat, která chcete odeslat. Druhé přepsání přijímá ukazatele na INTERNET_BUFFERS struktury, které lze použít k popisu vyrovnávací paměti velmi podrobně.

Po zápisu obsahu do souboru ukončujete operaci [voláním EndRequest.](#endrequest)

Výchozí hodnota pro *dwContext* je odeslána `CHttpFile` knihovnou MFC do objektu z objektu [CInternetSession,](../../mfc/reference/cinternetsession-class.md) který `CHttpFile` objekt vytvořil. Když zavoláte [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) nebo [CHttpConnection](../../mfc/reference/chttpconnection-class.md) k vytvoření objektu, `CHttpFile` můžete přepsat výchozí nastavení identifikátoru kontextu na hodnotu podle vašeho výběru. Identifikátor kontextu je [vrácena CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav na objekt, se kterým je identifikován. Další informace o identifikátoru kontextu naleznete v článku [První kroky Internetu: WinInet.](../../mfc/wininet-basics.md)

### <a name="example"></a>Příklad

Tento fragment kódu odešle obsah řetězce do knihovny DLL s názvem MFCISAPI. DLL na serveru LOCALHOST. Zatímco tento příklad používá `WriteString`pouze jedno volání , použití více volání k odesílání dat v blocích je přijatelné.

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>Viz také

[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)<br/>
[Třída Připojení Chttp](../../mfc/reference/chttpconnection-class.md)
