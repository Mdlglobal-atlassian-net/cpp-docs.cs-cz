---
title: Chttpfile – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5aef38ffe35f8aaf059ca88a0833b9e04b0c0ee9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077488"
---
# <a name="chttpfile-class"></a>Chttpfile – třída

Poskytuje funkce pro vyžádání a čtení souborů na HTTP server.

## <a name="syntax"></a>Syntaxe

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CHttpFile::CHttpFile](#chttpfile)|Vytvoří `CHttpFile` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|Přidá hlavičky požadavku odeslaného do serveru HTTP.|
|[CHttpFile::EndRequest](#endrequest)|Ukončení požadavku odeslaného do serveru HTTP se [SendRequestEx](#sendrequestex) členskou funkci.|
|[CHttpFile::GetFileURL](#getfileurl)|Získá adresu URL pro zadaný soubor.|
|[CHttpFile::GetObject](#getobject)|Získá cílový objekt operace v požadavku na HTTP server.|
|[CHttpFile::GetVerb](#getverb)|Načte příkaz, který byl použit v požadavku na HTTP server.|
|[CHttpFile::QueryInfo](#queryinfo)|Vrátí hlavičky odpovědi nebo abychom si vyžádali ze serveru HTTP.|
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|Získá stavový kód, který je přidružený k požadavku HTTP a umístí jej do zadané `dwStatusCode` parametru.|
|[CHttpFile::SendRequest](#sendrequest)|Odešle požadavek na HTTP server.|
|[CHttpFile::SendRequestEx](#sendrequestex)|Odešle požadavek na server HTTP pomocí [zápisu](../../mfc/reference/cinternetfile-class.md#write) nebo [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) metody `CInternetFile`.|

## <a name="remarks"></a>Poznámky

Pokud vaše relace Internet čte data ze serveru HTTP, musíte vytvořit instanci `CHttpFile`.

Další informace o tom, `CHttpFile` funguje s jinými třídami MFC Internetu najdete v článku [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cfile –](../../mfc/reference/cfile-class.md)

[Cstdiofile –](../../mfc/reference/cstdiofile-class.md)

[Cinternetfile –](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

##  <a name="addrequestheaders"></a>  CHttpFile::AddRequestHeaders

Voláním této členské funkce, aby vám ho přidal nebo zpracovávat další hlavičky požadavků HTTP na požadavek HTTP.

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

*pstrHeaders*<br/>
Ukazatel na řetězec obsahující záhlaví a záhlaví pro připojení k požadavku. Každá hlavička musí být ukončen pár znaků CR/LF.

*dwFlags*<br/>
Změní sémantiku nové hlavičky. Může být jedna z následujících akcí:

- Sloučí HTTP_ADDREQ_FLAG_COALESCE hlavičky se stejným názvem, pomocí příznaku přidáte první záhlaví nalezeno následující záhlaví. Například "přijmout: text /\*" následované "přijmout: zvuku /\*" výsledkem je tvorba jedné hlavičce "přijmout: text /\*, audio /\*". Je volající aplikace k zajištění získá na ucelenosti schéma s ohledem na data přijatá podle požadavků odeslaných sloučené nebo samostatné hlavičky.

- HTTP_ADDREQ_FLAG_REPLACE provádí odebrat a přidat k nahrazení aktuální záhlaví. Název záhlaví se použije k odebrání aktuální záhlaví a naplno se použije k přidání nové záhlaví. Pokud se nachází záhlaví hodnota hlavičky je prázdný, odebere se současně. Není-li prázdné, hodnota hlavičky se nahradí.

- Pouze HTTP_ADDREQ_FLAG_ADD_IF_NEW přidá hlavičku, pokud ještě neexistuje. Pokud takové existuje, vrátí se chyba.

- HTTP_ADDREQ_FLAG_ADD používá nahradit. Přidá hlavičku, pokud neexistuje.

*dwHeadersLen*<br/>
Délka ve znacích, z *pstrHeaders*. Pokud je to L hodnota-1, pak *pstrHeaders* předpokládá, že je ukončován nulou a délka je vypočítán.

*str*<br/>
Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje hlavičku požadavku nebo záhlaví, které mají být přidány.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.

### <a name="remarks"></a>Poznámky

`AddRequestHeaders` připojí další, uvolněte formát hlavičky obslužná rutina požadavků HTTP. Je určena pro použití sofistikované klienty, kteří potřebují mít podrobnou kontrolu nad přesné požadavku odeslaného do serveru HTTP.

> [!NOTE]
>  Aplikace můžete předat více záhlaví v *pstrHeaders* nebo *str* pro `AddRequestHeaders` zavolat pomocí HTTP_ADDREQ_FLAG_ADD nebo HTTP_ADDREQ_FLAG_ADD_IF_NEW. Pokud se aplikace pokusí odeberte nebo nahraďte záhlaví s použitím HTTP_ADDREQ_FLAG_REMOVE nebo HTTP_ADDREQ_FLAG_REPLACE, lze zadat pouze jedno záhlaví v *lpszHeaders*.

##  <a name="chttpfile"></a>  CHttpFile::CHttpFile

Tato členská funkce je volána k sestavení kompletních `CHttpFile` objektu.

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

*hfile –*<br/>
Popisovač souboru k Internetu.

*hSession*<br/>
Popisovač pro relaci Internet.

*pstrObject*<br/>
Ukazatel na řetězec obsahující `CHttpFile` objektu.

*pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru.

*pstrVerb*<br/>
Ukazatel na řetězec obsahující metodu, která se použije při odesílání požadavku. Můžete být příspěvek, HEAD, nebo získat.

*dwContext*<br/>
Identifikátor kontextu `CHttpFile` objektu. Zobrazit **poznámky** Další informace o tomto parametru.

*pConnection*<br/>
Ukazatel [chttpconnection –](../../mfc/reference/chttpconnection-class.md) objektu.

### <a name="remarks"></a>Poznámky

Nikdy sestavit `CHttpFile` objektu přímo; místo toho volat [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) nebo [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) místo.

Výchozí hodnota pro `dwContext` odesílají knihovny MFC pro `CHttpFile` objektu z [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objekt vytvořený `CHttpFile` objektu. Při volání `CInternetSession::OpenURL` nebo `CHttpConnection` k vytvoření `CHttpFile` objektu, můžete přepsat výchozí identifikátor kontextu nastavena na hodnotu podle vašeho výběru. Identifikátor kontextu se vrátí do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav objektu, pomocí kterého je identifikován. Najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o identifikátor kontextu.

##  <a name="endrequest"></a>  CHttpFile::EndRequest

Zavolat tuto členskou funkci na konec požadavku odeslaného do serveru HTTP se [SendRequestEx](#sendrequestex) členskou funkci.

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Příznaky popisující operace. Seznam příslušnými příznaky najdete v tématu [HttpEndRequest](/windows/desktop/api/wininet/nf-wininet-httpendrequesta) v sadě Windows SDK.

*lpBuffIn*<br/>
Ukazatel na inicializovali [INTERNET_BUFFERS](/windows/desktop/api/wininet/ns-wininet-_internet_buffersa) , který popisuje vstupní vyrovnávací paměti použité pro tuto operaci.

*dwContext*<br/>
Identifikátor kontextu `CHttpFile` operace. Další informace o tomto parametru najdete v článku poznámky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, zjistěte příčinu selhání tím, že kontroluje, k této výjimce dojde [cinternetexception –](../../mfc/reference/cinternetexception-class.md) objektu.

### <a name="remarks"></a>Poznámky

Výchozí hodnota pro *dwContext* odesílají knihovny MFC pro `CHttpFile` objektu z [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objekt vytvořený `CHttpFile` objektu. Při volání [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) nebo [chttpconnection –](../../mfc/reference/chttpconnection-class.md) k vytvoření `CHttpFile` objektu, můžete přepsat výchozí identifikátor kontextu nastavena na hodnotu podle vašeho výběru. Identifikátor kontextu se vrátí do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav objektu, pomocí kterého je identifikován. Najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o identifikátor kontextu.

##  <a name="getfileurl"></a>  CHttpFile::GetFileURL

Voláním této členské funkce a získat tak název souboru protokolu HTTP jako adresu URL.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Návratová hodnota

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje adresu URL odkazující na prostředků přidružené k tomuto souboru.

### <a name="remarks"></a>Poznámky

Tuto funkci člena použít až po úspěšném volání [Odesilani](#sendrequest) nebo `CHttpFile` úspěšně vytvořil objekt [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

##  <a name="getobject"></a>  CHttpFile::GetObject

Voláním této členské funkce a získat tak název přidružený k tomuto objektu `CHttpFile`.

```
CString GetObject() const;
```

### <a name="return-value"></a>Návratová hodnota

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje název objektu.

### <a name="remarks"></a>Poznámky

Tuto funkci člena použít až po úspěšném volání [Odesilani](#sendrequest) nebo `CHttpFile` úspěšně vytvořil objekt [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

##  <a name="getverb"></a>  CHttpFile::GetVerb

Voláním této členské funkce, příkaz HTTP (nebo metoda) přidružený k tomuto `CHttpFile`.

```
CString GetVerb() const;
```

### <a name="return-value"></a>Návratová hodnota

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje název příkazem HTTP příkaz (nebo metoda).

### <a name="remarks"></a>Poznámky

Tuto funkci člena použít až po úspěšném volání [Odesilani](#sendrequest) nebo `CHttpFile` úspěšně vytvořil objekt [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

##  <a name="queryinfo"></a>  CHttpFile::QueryInfo

Voláním této členské funkce vrátí odpověď nebo hlavičky požadavku z požadavku HTTP.

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
Kombinace atribut, který chcete dotaz a následující příznaky, které určují typ požadované informace:

- HTTP_QUERY_CUSTOM najde název hlavičky a vrátí tuto hodnotu v *lpvBuffer* na výstupu. HTTP_QUERY_CUSTOM vyvolá kontrolní výraz, pokud hlavička nebyla nalezena.

- Obvykle HTTP_QUERY_FLAG_REQUEST_HEADERS aplikace dotazy hlaviček odpovědí, ale aplikace můžete také zadávat dotazy hlavičky žádosti pomocí tohoto příznaku.

- HTTP_QUERY_FLAG_SYSTEMTIME pro tyto hlavičky, jehož hodnota je řetězec data a času, například "Poslední upravil běhu," Tento příznak vrací hodnotu hlavičky jako standardním Win32 [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktura, která nevyžaduje, aby aplikace analyzovat data. Pokud použijete tento příznak, můžete použít `SYSTEMTIME` přepsání funkce.

- HTTP_QUERY_FLAG_NUMBER pro tyto hlavičky, jehož hodnota je číslo, například stavový kód, tento příznak vrátí data jako 32bitová čísla.

Zobrazit **poznámky** najdete seznam možných hodnot.

*lpvBuffer*<br/>
Ukazatel do vyrovnávací paměti, která přijímá informace.

*lpdwBufferLength*<br/>
V položce to odkazuje na hodnotu obsahující délku vyrovnávací paměť dat v počtu znaků nebo bajtů. Zobrazit **poznámky** části Podrobné informace o tomto parametru.

*lpdwIndex*<br/>
Ukazatel na index založený na nule záhlaví. Může mít hodnotu NULL. Pomocí tohoto příznaku se vytvořit výčet více záhlaví s tímto názvem. Na vstupu *lpdwIndex* Určuje index Zadaná hlavička se vraťte. Na výstupu *lpdwIndex* Určuje index další záhlaví. Pokud nelze najít další index, je vrácena ERROR_HTTP_HEADER_NOT_FOUND.

*str*<br/>
Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt příjem vrácených informací.

*dwIndex*<br/>
Hodnota indexu. Zobrazit *lpdwIndex*.

*pSysTime*<br/>
Ukazatel na Win32 [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950) struktury.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.

### <a name="remarks"></a>Poznámky

Tuto funkci člena použít až po úspěšném volání [Odesilani](#sendrequest) nebo `CHttpFile` úspěšně vytvořil objekt [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Můžete načíst následující typy dat z `QueryInfo`:

- řetězce (výchozí)

- `SYSTEMTIME` (pro "Data:" "platnost vyprší:" etc, hlavičky)

- DWORD (pro STATUS_CODE CONTENT_LENGTH, atd.)

Pokud řetězec je zapsán do vyrovnávací paměti a členské funkce uspěje, `lpdwBufferLength` obsahuje délku řetězce ve znacích odečte 1. pro ukončující znak NULL.

Možné *dwInfoLevel* mezi hodnoty patří:

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

##  <a name="queryinfostatuscode"></a>  CHttpFile::QueryInfoStatusCode

Voláním této členské funkce získání stavového kódu přidružené k požadavku HTTP a umístěte ji do zadané *dwStatusCode* parametru.

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>Parametry

*dwStatusCode*<br/>
Odkaz na stavový kód. Stavové kódy indikuje úspěch nebo neúspěch požadované události. Zobrazit **poznámky** pro výběr kódu popis stavu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.

### <a name="remarks"></a>Poznámky

Tuto funkci člena použít až po úspěšném volání [Odesilani](#sendrequest) nebo `CHttpFile` úspěšně vytvořil objekt [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Stavové kódy HTTP patří do skupiny udávající úspěch nebo selhání požadavku. Následující tabulky popisují stav skupiny kódu a nejběžnější stavové kódy HTTP.

|Skupina|Význam|
|-----------|-------------|
|200-299|Úspěch|
|300-399|Informace o|
|400-499|Chyba žádosti|
|500-599|Chyba serveru|

Běžné kódy stavu HTTP:

|Stavový kód|Význam|
|-----------------|-------------|
|200|Adresa URL umístěný, přenosem odpovídá|
|400|Nesrozumitelný žádosti|
|404|Požadovaná adresa URL nebyla nalezena.|
|405|Server nepodporuje požadované – metoda|
|500|Neznámou chybu serveru|
|503|Bylo dosaženo kapacity serveru|

##  <a name="sendrequest"></a>  CHttpFile::SendRequest

Voláním této členské funkce Odeslat požadavek na HTTP server.

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

*pstrHeaders*<br/>
Ukazatel na řetězec obsahující název hlavičky k odeslání.

*dwHeadersLen*<br/>
Délka hlavičky identifikovaný *pstrHeaders*.

*lpOptional*<br/>
Libovolné volitelné data k odeslání ihned po hlavičky žádosti. Obecně se používá pro operace POST a PUT. To může mít hodnotu NULL, pokud neexistuje žádné volitelné data k odeslání.

*dwOptionalLen*<br/>
Délka *lpOptional*.

*strHeaders*<br/>
Řetězec obsahující název záhlaví pro žádost o odeslání.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, zjistěte příčinu selhání tím, že kontroluje, k této výjimce dojde [cinternetexception –](../../mfc/reference/cinternetexception-class.md) objektu.

##  <a name="sendrequestex"></a>  CHttpFile::SendRequestEx

Voláním této členské funkce Odeslat požadavek na HTTP server.

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
Počet bajtů k odeslání v požadavku.

*dwFlags*<br/>
Příznaky popisující operace. Seznam příslušnými příznaky najdete v tématu [HttpSendRequestEx](/windows/desktop/api/wininet/nf-wininet-httpsendrequestexa) v sadě Windows SDK.

*dwContext*<br/>
Identifikátor kontextu `CHttpFile` operace. Další informace o tomto parametru najdete v článku poznámky.

*lpBuffIn*<br/>
Ukazatel na inicializovali [INTERNET_BUFFERS](/windows/desktop/api/wininet/ns-wininet-_internet_buffersa) , který popisuje vstupní vyrovnávací paměti použité pro tuto operaci.

*lpBuffOut*<br/>
Ukazatele inicializované INTERNET_BUFFERS, který popisuje výstupní vyrovnávací paměť, používá pro operaci.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. Pokud volání selže, zjistěte příčinu selhání tím, že kontroluje, k této výjimce dojde [cinternetexception –](../../mfc/reference/cinternetexception-class.md) objektu.

### <a name="remarks"></a>Poznámky

Tato funkce umožňuje aplikaci posílat data pomocí [zápisu](../../mfc/reference/cinternetfile-class.md#write) a [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) metody `CInternetFile`. Musíte vědět, délka dat k odeslání před voláním této funkce buď přepsat. První přepsání můžete zadat délku dat, které chcete odeslat. Druhý přepsání přijímá ukazatele na INTERNET_BUFFERS struktury, které je možné použít k popisu vyrovnávací paměť příliš podrobně.

Poté, co je napsán obsah do souboru, volejte [EndRequest](#endrequest) pro ukončení operace.

Výchozí hodnota pro *dwContext* odesílají knihovny MFC pro `CHttpFile` objektu z [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objekt vytvořený `CHttpFile` objektu. Při volání [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) nebo [chttpconnection –](../../mfc/reference/chttpconnection-class.md) k vytvoření `CHttpFile` objektu, můžete přepsat výchozí identifikátor kontextu nastavena na hodnotu podle vašeho výběru. Identifikátor kontextu se vrátí do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav objektu, pomocí kterého je identifikován. Najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o identifikátor kontextu.

### <a name="example"></a>Příklad

Tento fragment kódu odesílá obsah řetězce do knihovny DLL s názvem MFCISAPI. Knihovna DLL na serveru LOCALHOST. Při tomto příkladu se používá pouze jedno volání `WriteString`, použití více volání k odesílání dat do bloků je přijatelné.

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>Viz také

[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpConnection – třída](../../mfc/reference/chttpconnection-class.md)
