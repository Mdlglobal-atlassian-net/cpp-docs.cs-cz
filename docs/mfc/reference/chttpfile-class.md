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
ms.openlocfilehash: ff050a89a10c68c639c141891dd51b1b2d58e105
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916001"
---
# <a name="chttpfile-class"></a>CHttpFile – třída

Poskytuje funkce pro vyžádání a čtení souborů na serveru HTTP.

## <a name="syntax"></a>Syntaxe

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name|Popis|
|----------|-----------------|
|[CHttpFile::CHttpFile](#chttpfile)|`CHttpFile` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|Přidá hlavičky do žádosti odeslané na server HTTP.|
|[CHttpFile::EndRequest](#endrequest)|Ukončí požadavek odeslaný na server HTTP pomocí členské funkce [SendRequestEx](#sendrequestex) .|
|[CHttpFile::GetFileURL](#getfileurl)|Získá adresu URL zadaného souboru.|
|[CHttpFile:: GetObject](#getobject)|Získá cílový objekt příkazu v požadavku na server HTTP.|
|[CHttpFile::GetVerb](#getverb)|Získá příkaz, který byl použit v požadavku na server HTTP.|
|[CHttpFile::QueryInfo](#queryinfo)|Vrátí odpověď nebo hlavičku požadavku ze serveru HTTP.|
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|Načte stavový kód přidružený k požadavku HTTP a umístí ho do zadaného `dwStatusCode` parametru.|
|[CHttpFile::SendRequest](#sendrequest)|Odešle požadavek na server HTTP.|
|[CHttpFile::SendRequestEx](#sendrequestex)|Odešle požadavek na server HTTP pomocí metod [Write](../../mfc/reference/cinternetfile-class.md#write) nebo [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) pro `CInternetFile`.|

## <a name="remarks"></a>Poznámky

Pokud vaše Internetová relace čte data ze serveru HTTP, je nutné vytvořit instanci `CHttpFile`.

Další informace o tom, `CHttpFile` jak pracovat s jinými internetovými třídami knihovny MFC, najdete v článku [internetové programování s](../../mfc/win32-internet-extensions-wininet.md)rozhraním Wininet.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CFile –](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet. h

##  <a name="addrequestheaders"></a>CHttpFile::AddRequestHeaders

Voláním této členské funkce přidejte jednu nebo více hlaviček požadavku HTTP do popisovače požadavku HTTP.

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
Ukazatel na řetězec obsahující záhlaví nebo záhlaví, které mají být připojeny k žádosti. Každé záhlaví musí být ukončeno dvojicí CR/LF.

*dwFlags*<br/>
Upraví sémantiku nových hlaviček. Může být jedna z následujících akcí:

- HTTP_ADDREQ_FLAG_COALESCE sloučí záhlaví se stejným názvem a pomocí příznaku přidá první záhlaví nalezené do následující hlavičky. Například "přijmout\*: text/" následovaný textem "přijmout: zvuk/\*" má za následek vytvoření jediné hlavičky "přijmout: text/\*, zvuk/\*". Je až volající aplikace, aby se zajistilo soudržné schéma s ohledem na data přijatá požadavky odesílaná pomocí sloučených nebo oddělených hlaviček.

- HTTP_ADDREQ_FLAG_REPLACE provede odebrání a přidání k nahrazení aktuální hlavičky. Název záhlaví bude použit k odebrání aktuální hlavičky a plná hodnota bude použita k přidání nové hlavičky. Pokud je hodnota hlavičky prázdná a hlavička se najde, odebere se. Pokud není prázdné, bude hodnota hlavičky nahrazena.

- HTTP_ADDREQ_FLAG_ADD_IF_NEW přidá hlavičku pouze v případě, že ještě neexistuje. Pokud nějaký existuje, vrátí se chyba.

- HTTP_ADDREQ_FLAG_ADD se používá s PARAMETRem Replace. Přidá hlavičku, pokud neexistuje.

*dwHeadersLen*<br/>
Délka v *pstrHeaders*znaků. Pokud je to-1L, předpokládá se, že *pstrHeaders* se ukončí nulou a je vypočítána délka.

*str*<br/>
Odkaz na objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující hlavičku požadavku nebo hlavičky, které mají být přidány.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

### <a name="remarks"></a>Poznámky

`AddRequestHeaders`připojí k popisovači požadavku HTTP další hlavičky volného formátu. Je určená pro použití v propracovaných klientech, kteří potřebují podrobnou kontrolu nad přesnou žádostí odeslanou na server HTTP.

> [!NOTE]
>  Aplikace může předat více hlaviček v *pstrHeaders* nebo *str* pro `AddRequestHeaders` volání pomocí HTTP_ADDREQ_FLAG_ADD nebo HTTP_ADDREQ_FLAG_ADD_IF_NEW. Pokud se aplikace pokusí odebrat nebo nahradit záhlaví pomocí HTTP_ADDREQ_FLAG_REMOVE nebo HTTP_ADDREQ_FLAG_REPLACE, lze v *lpszHeaders*zadat pouze jednu hlavičku.

##  <a name="chttpfile"></a>CHttpFile::CHttpFile

Tato členská funkce je volána k vytvoření `CHttpFile` objektu.

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

*hFile*<br/>
Popisovač internetového souboru.

*hSession*<br/>
Popisovač internetové relace.

*pstrObject*<br/>
Ukazatel na řetězec obsahující `CHttpFile` objekt.

*pstrServer*<br/>
Ukazatel na řetězec, který obsahuje název serveru.

*pstrVerb*<br/>
Ukazatel na řetězec obsahující metodu, která má být použita při odeslání požadavku. Může být POST, HEAD nebo GET.

*dwContext*<br/>
Identifikátor kontextu pro `CHttpFile` objekt. Další informace o tomto parametru najdete v části **poznámky** .

*pConnection*<br/>
Ukazatel na objekt [CHttpConnection](../../mfc/reference/chttpconnection-class.md) .

### <a name="remarks"></a>Poznámky

Nikdy nevytvoříte `CHttpFile` objekt přímo; místo toho zavolejte [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) nebo [CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) .

Výchozí hodnota `dwContext` pro je odeslána knihovnou `CHttpFile` MFC do objektu z objektu [CInternetSession](../../mfc/reference/cinternetsession-class.md) , který `CHttpFile` objekt vytvořil. Při volání `CInternetSession::OpenURL` nebo `CHttpConnection` vytvoření `CHttpFile` objektu můžete přepsat výchozí hodnotu pro nastavení identifikátoru kontextu na hodnotu, kterou zvolíte. Identifikátor kontextu je vrácen do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , aby poskytoval stav objektu, se kterým je identifikován. Přečtěte si [článek Internet First Step: Rozhraní](../../mfc/wininet-basics.md) WinInet pro další informace o identifikátoru kontextu.

##  <a name="endrequest"></a>CHttpFile:: EndRequest

Voláním této členské funkce ukončíte požadavek odeslaný na server HTTP pomocí členské funkce [SendRequestEx](#sendrequestex) .

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Příznaky popisující operaci. Seznam příslušných příznaků naleznete v tématu [HttpEndRequest](/windows/desktop/api/wininet/nf-wininet-httpendrequesta) v Windows SDK.

*lpBuffIn*<br/>
Ukazatel na inicializovaný [INTERNET_BUFFERS](/windows/desktop/api/wininet/ns-wininet-internet_buffersa) , který popisuje vstupní vyrovnávací paměť, která se používá pro operaci.

*dwContext*<br/>
Identifikátor `CHttpFile` kontextu operace. Další informace o tomto parametru najdete v části poznámky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud volání selže, určete příčinu selhání zkoumáním vyvolaného objektu [CInternetException](../../mfc/reference/cinternetexception-class.md) .

### <a name="remarks"></a>Poznámky

Výchozí hodnota pro *dwContext* je odeslána knihovnou MFC do `CHttpFile` objektu z objektu [](../../mfc/reference/cinternetsession-class.md) `CHttpFile` CInternetSession, který objekt vytvořil. Když zavoláte [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) nebo [CHttpConnection](../../mfc/reference/chttpconnection-class.md) `CHttpFile` pro vytvoření objektu, můžete přepsat výchozí hodnotu pro nastavení identifikátoru kontextu na hodnotu, kterou zvolíte. Identifikátor kontextu je vrácen do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , aby poskytoval stav objektu, se kterým je identifikován. Viz článek [Internet First Steps: Rozhraní](../../mfc/wininet-basics.md) WinInet pro další informace o identifikátoru kontextu.

##  <a name="getfileurl"></a>  CHttpFile::GetFileURL

Zavolejte tuto členskou funkci, aby se název souboru HTTP získal jako adresa URL.

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující adresu URL, která odkazuje na prostředek přidružený k tomuto souboru.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci použijte až po úspěšném volání [SendRequest](#sendrequest) nebo `CHttpFile` objektu úspěšně vytvořeného pomocí [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

##  <a name="getobject"></a>CHttpFile:: GetObject

Voláním této členské funkce získáte název objektu, který je k tomuto `CHttpFile`objektu přidružen.

```
CString GetObject() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující název objektu.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci použijte až po úspěšném volání [SendRequest](#sendrequest) nebo `CHttpFile` objektu úspěšně vytvořeného pomocí [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

##  <a name="getverb"></a>CHttpFile:: Get– příkaz

Voláním této členské funkce získáte příkaz HTTP (nebo metodu) spojenou s tímto `CHttpFile`.

```
CString GetVerb() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující název příkazu protokolu HTTP (nebo metody).

### <a name="remarks"></a>Poznámky

Tuto členskou funkci použijte až po úspěšném volání [SendRequest](#sendrequest) nebo `CHttpFile` objektu úspěšně vytvořeného pomocí [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

##  <a name="queryinfo"></a>  CHttpFile::QueryInfo

Voláním této členské funkce vrátíte odpovědi nebo hlavičky požadavku z požadavku HTTP.

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
Kombinace atributu pro dotazování a následujících příznaků, které určují typ požadovaných informací:

- HTTP_QUERY_CUSTOM vyhledá název hlavičky a vrátí tuto hodnotu ve výstupu *lpvBuffer* . HTTP_QUERY_CUSTOM vyvolá kontrolní výraz, pokud záhlaví není nalezeno.

- HTTP_QUERY_FLAG_REQUEST_HEADERS se obvykle aplikace dotazuje na hlavičky odpovědí, ale aplikace také může dotazovat hlavičky požadavků pomocí tohoto příznaku.

- HTTP_QUERY_FLAG_SYSTEMTIME pro hlavičky, jejichž hodnota je řetězec data a času, například "čas" Naposledy změněno ", tento příznak vrátí hodnotu hlavičky jako standardní [SYSTEMTIME –](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) strukturu Win32, která nevyžaduje, aby aplikace analyzovala data. Použijete-li tento příznak, je vhodné použít `SYSTEMTIME` přepsání funkce.

- HTTP_QUERY_FLAG_NUMBER pro hlavičky, jejichž hodnota je číslo, jako je například stavový kód, tento příznak vrací data jako 32-bit číslo.

Seznam možných hodnot naleznete v části **poznámky** .

*lpvBuffer*<br/>
Ukazatel na vyrovnávací paměť, která obdrží informace.

*lpdwBufferLength*<br/>
U vstupu odkazuje na hodnotu, která obsahuje délku vyrovnávací paměti dat, v počtu znaků nebo bajtů. Podrobnější informace o tomto parametru najdete v části **poznámky** .

*lpdwIndex*<br/>
Ukazatel na index záhlaví založený na nule. Může mít hodnotu NULL. Pomocí tohoto příznaku můžete vytvořit výčet více hlaviček se stejným názvem. U vstupu *lpdwIndex* označuje index zadaného záhlaví, které se má vrátit. Ve výstupu *lpdwIndex* indikuje index následujícího záhlaví. Pokud se další index nenajde, vrátí se ERROR_HTTP_HEADER_NOT_FOUND.

*str*<br/>
Odkaz na objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který přijímá vrácené informace.

*dwIndex*<br/>
Hodnota indexu. Viz *lpdwIndex*.

*pSysTime*<br/>
Ukazatel na strukturu [SYSTEMTIME –](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) Win32.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci použijte až po úspěšném volání [SendRequest](#sendrequest) nebo `CHttpFile` objektu úspěšně vytvořeného pomocí [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Můžete načíst následující typy dat z `QueryInfo`:

- řetězce (výchozí)

- `SYSTEMTIME`(pro data: vyprší platnost: atd. Headers)

- DWORD (pro STATUS_CODE, CONTENT_LENGTH atd.)

Když je řetězec zapisován do vyrovnávací paměti a členská funkce je úspěšná, `lpdwBufferLength` obsahuje délku řetězce ve znacích minus 1 pro ukončující znak null.

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

##  <a name="queryinfostatuscode"></a>  CHttpFile::QueryInfoStatusCode

Zavolejte tuto členskou funkci pro získání stavového kódu přidruženého k požadavku HTTP a umístěte ho do zadaného parametru *dwStatusCode* .

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>Parametry

*dwStatusCode*<br/>
Odkaz na stavový kód. Stavové kódy označují úspěch nebo neúspěch požadované události. Výběr popisů stavových kódů naleznete v části **poznámky** .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci použijte až po úspěšném volání [SendRequest](#sendrequest) nebo `CHttpFile` objektu úspěšně vytvořeného pomocí [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

Stavové kódy HTTP spadají do skupin indikujících úspěch nebo neúspěch žádosti. Následující tabulky obsahují přehled skupin stavových kódů a nejběžnějších stavových kódů HTTP.

|Skupina|Význam|
|-----------|-------------|
|200-299|Úspěch|
|300-399|Informace o|
|400-499|Chyba žádosti|
|500-599|Chyba serveru|

Běžné stavové kódy HTTP:

|Stavový kód|Význam|
|-----------------|-------------|
|200|Adresa URL, přenos následuje|
|400|Nečitelný požadavek|
|404|Požadovaná adresa URL nebyla nalezena.|
|405|Server nepodporuje požadovanou metodu.|
|500|Neznámá chyba serveru|
|503|Byla dosažena kapacita serveru|

##  <a name="sendrequest"></a>CHttpFile::SendRequest

Tuto členskou funkci zavolejte k odeslání požadavku na server HTTP.

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
Ukazatel na řetězec obsahující název hlaviček k odeslání.

*dwHeadersLen*<br/>
Délka hlaviček identifikovaných pomocí *pstrHeaders*.

*lpOptional*<br/>
Veškerá volitelná data, která se mají poslat hned za hlavičkou žádosti Tato metoda se obecně používá pro operace POST a PUT. Pokud není k odeslání k dispozici žádná volitelná data, může to mít hodnotu NULL.

*dwOptionalLen*<br/>
Délka *lpOptional*.

*strHeaders*<br/>
Řetězec obsahující název záhlaví odesílaného požadavku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud volání selže, určete příčinu selhání zkoumáním vyvolaného objektu [CInternetException](../../mfc/reference/cinternetexception-class.md) .

##  <a name="sendrequestex"></a>CHttpFile::SendRequestEx

Tuto členskou funkci zavolejte k odeslání požadavku na server HTTP.

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
Počet bajtů, které se mají v žádosti odeslat.

*dwFlags*<br/>
Příznaky popisující operaci. Seznam příslušných příznaků naleznete v tématu [HttpSendRequestEx](/windows/desktop/api/wininet/nf-wininet-httpsendrequestexa) v Windows SDK.

*dwContext*<br/>
Identifikátor `CHttpFile` kontextu operace. Další informace o tomto parametru najdete v části poznámky.

*lpBuffIn*<br/>
Ukazatel na inicializovaný [INTERNET_BUFFERS](/windows/desktop/api/wininet/ns-wininet-internet_buffersa) , který popisuje vstupní vyrovnávací paměť, která se používá pro operaci.

*lpBuffOut*<br/>
Ukazatel na inicializovaný INTERNET_BUFFERS, který popisuje výstupní vyrovnávací paměť, která se používá pro operaci.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné. Pokud volání selže, určete příčinu selhání zkoumáním vyvolaného objektu [CInternetException](../../mfc/reference/cinternetexception-class.md) .

### <a name="remarks"></a>Poznámky

Tato funkce umožňuje, aby aplikace odesílala data pomocí metod [Write](../../mfc/reference/cinternetfile-class.md#write) a [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) pro `CInternetFile`. Než zavoláte tuto funkci, musíte znát délku dat, která se mají odeslat. První přepsání umožňuje zadat délku dat, která chcete odeslat. Druhé přepsání akceptuje odkazy na INTERNET_BUFFERS struktury, které lze použít k popsání vyrovnávací paměti v skvělém detailu.

Po zapsání obsahu do souboru volejte metodu [endRequest](#endrequest) pro ukončení operace.

Výchozí hodnota pro *dwContext* je odeslána knihovnou MFC do `CHttpFile` objektu z objektu [](../../mfc/reference/cinternetsession-class.md) `CHttpFile` CInternetSession, který objekt vytvořil. Když zavoláte [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) nebo [CHttpConnection](../../mfc/reference/chttpconnection-class.md) `CHttpFile` pro vytvoření objektu, můžete přepsat výchozí hodnotu pro nastavení identifikátoru kontextu na hodnotu, kterou zvolíte. Identifikátor kontextu je vrácen do [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) , aby poskytoval stav objektu, se kterým je identifikován. Přečtěte si [článek Internet First Step: Rozhraní](../../mfc/wininet-basics.md) WinInet pro další informace o identifikátoru kontextu.

### <a name="example"></a>Příklad

Tento fragment kódu odesílá obsah řetězce do knihovny DLL s názvem MFCISAPI. Knihovna DLL na serveru LOCALHOST. I když tento příklad používá pouze jedno volání `WriteString`, je přijatelné použití více volání k odesílání dat v blocích.

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>Viz také:

[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpConnection – třída](../../mfc/reference/chttpconnection-class.md)
