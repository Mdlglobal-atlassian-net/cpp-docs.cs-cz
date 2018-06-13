---
title: Třída CHttpFile | Microsoft Docs
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
ms.openlocfilehash: 7a7fbdb3baff7531aa4e391e5d7e936c39e38fc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372616"
---
# <a name="chttpfile-class"></a>CHttpFile – třída
Poskytuje funkce pro žádosti a číst soubory na serveru HTTP.  
  
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
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|Přidá hlavičky požadavek odeslaný na HTTP server.|  
|[CHttpFile::EndRequest](#endrequest)|Ukončí požadavek HTTP serveru se odesílají [SendRequestEx](#sendrequestex) – členská funkce.|  
|[CHttpFile::GetFileURL](#getfileurl)|Získá adresu URL pro zadaný soubor.|  
|[CHttpFile::GetObject](#getobject)|Získá cílový objekt operace v požadavku na HTTP server.|  
|[CHttpFile::GetVerb](#getverb)|Získá akci, která byla použita v požadavku na HTTP server.|  
|[CHttpFile::QueryInfo](#queryinfo)|Vrátí hlavičky odpovědi nebo žádostí o ze serveru HTTP.|  
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|Načte kód stavu, který je přidružený požadavku HTTP a umístí jej do zadaných `dwStatusCode` parametr.|  
|[CHttpFile::SendRequest](#sendrequest)|Odešle požadavek na HTTP server.|  
|[CHttpFile::SendRequestEx](#sendrequestex)|Odešle požadavek na server HTTP pomocí [zápisu](../../mfc/reference/cinternetfile-class.md#write) nebo [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) metody `CInternetFile`.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud vaše relace Internet čte data z HTTP server, musíte vytvořit instanci `CHttpFile`.  
  
 Další informace o tom, `CHttpFile` funguje s ostatní třídy MFC Internetu najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CHttpFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
  
##  <a name="addrequestheaders"></a>  CHttpFile::AddRequestHeaders  
 Volání této funkce člen přidat jeden nebo více hlavičkách žádosti protokolu HTTP na požadavek HTTP zpracovat.  
  
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
 `pstrHeaders`  
 Ukazatel na řetězec obsahující záhlaví nebo hlavičky připojit k žádosti. Každá hlavička musí být ukončen pár CR/LF.  
  
 `dwFlags`  
 Změní sémantiku na záhlaví nového. Může být jedna z následujících akcí:  
  
- `HTTP_ADDREQ_FLAG_COALESCE` Sloučí hlavičky se stejným názvem, pomocí příznaku přidat hlavičku první pro následné hlavička najít. Například "přijmout: text / *" následované "přijmout: zvuk nebo\*" výsledkem je tvorba jeden hlavičky "přijmout: text /\*, zvuk nebo\*". Je volající aplikace k zajištění získá na ucelenosti schéma s ohledem na data, která přijímá požadavky odeslané s záhlaví sloučené nebo samostatné.  
  
- `HTTP_ADDREQ_FLAG_REPLACE` Provede odebrat a přidejte do nahradit aktuální záhlaví. Název hlavičky se použije k odebrat aktuální záhlaví a úplná hodnota se použije pro přidání nové záhlaví. Pokud je hodnota hlavičky prázdný a se nachází záhlaví, bude odebrán. Pokud není prázdná, je hodnota hlavičky nahrazena.  
  
- `HTTP_ADDREQ_FLAG_ADD_IF_NEW` Přidá hlavičku, pouze pokud ještě neexistuje. Pokud existuje, je vrácena chyba.  
  
- `HTTP_ADDREQ_FLAG_ADD` Použít s nahradit. Přidá hlavičku, pokud neexistuje.  
  
 `dwHeadersLen`  
 Délka ve znacích, z `pstrHeaders`. Pokud je to L-1, pak `pstrHeaders` bude ukončen nula hodnota a délka je počítaný.  
  
 `str`  
 Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující hlavička požadavku nebo hlavičky, které chcete přidat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
### <a name="remarks"></a>Poznámky  
 `AddRequestHeaders` připojí další, volného formátu hlavičky k obslužná rutina požadavků HTTP. Je určena pro použití sofistikované klienty, kteří potřebují podrobnou kontrolu nad přesný požadavek odeslaný na server HTTP.  
  
> [!NOTE]
>  Aplikace můžete předat více záhlaví v `pstrHeaders` nebo `str` pro `AddRequestHeaders` volat pomocí `HTTP_ADDREQ_FLAG_ADD` nebo `HTTP_ADDREQ_FLAG_ADD_IF_NEW`. Pokud se aplikace pokusí odeberte nebo nahraďte záhlaví pomocí **HTTP_ADDREQ_FLAG_REMOVE** nebo `HTTP_ADDREQ_FLAG_REPLACE`, můžete zadat pouze jedno záhlaví v `lpszHeaders`.  
  
##  <a name="chttpfile"></a>  CHttpFile::CHttpFile  
 Tato funkce člen je volána k sestavení `CHttpFile` objektu.  
  
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
 `hFile`  
 Popisovač pro soubor Internetu.  
  
 `hSession`  
 Popisovač pro relaci Internet.  
  
 *pstrObject*  
 Ukazatel na řetězec obsahující `CHttpFile` objektu.  
  
 `pstrServer`  
 Ukazatel na řetězec, který obsahuje název serveru.  
  
 `pstrVerb`  
 Ukazatel na řetězec obsahující metoda má být použit při odesílání požadavku. Může být **POST**, **HEAD**, nebo `GET`.  
  
 dwContext  
 Identifikátor kontext pro `CHttpFile` objektu. V tématu **poznámky** Další informace o tomto parametru.  
  
 `pConnection`  
 Ukazatel [CHttpConnection](../../mfc/reference/chttpconnection-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Nikdy vytvoříte `CHttpFile` objektu přímo; místo volání [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) nebo [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) místo.  
  
 Výchozí hodnota pro `dwContext` odesílají MFC k `CHttpFile` objektu z [CInternetSession](../../mfc/reference/cinternetsession-class.md) objekt vytvořený `CHttpFile` objektu. Při volání `CInternetSession::OpenURL` nebo `CHttpConnection` k vytvoření `CHttpFile` objekt, můžete přepsat výchozí identifikátor kontextu nastavit na hodnotu dle vlastního výběru. Identifikátor kontextu je vrácen do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytovat stav na objekt, ke kterému se identifikuje. Najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o kontextu identifikátor.  
  
##  <a name="endrequest"></a>  CHttpFile::EndRequest  
 Volání této funkce člena na konec požadavek HTTP serveru se odesílají [SendRequestEx](#sendrequestex) – členská funkce.  
  
```  
BOOL EndRequest(
    DWORD dwFlags = 0,  
    LPINTERNET_BUFFERS lpBuffIn = NULL,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Příznaky, které popisují operaci. Seznam příslušnými příznaky, naleznete v části [HttpEndRequest](http://msdn.microsoft.com/library/windows/desktop/aa384230) ve Windows SDK.  
  
 `lpBuffIn`  
 Ukazatel na inicializovali [INTERNET_BUFFERS](http://msdn.microsoft.com/library/windows/desktop/aa385132) , který popisuje vstupní vyrovnávací paměť pro operaci použít.  
  
 `dwContext`  
 Identifikátor kontextu `CHttpFile` operaci. Další informace o tomto parametru najdete v části poznámky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, zjistit příčinu selhání na základě vyvolané [CInternetException](../../mfc/reference/cinternetexception-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí hodnota pro `dwContext` odesílají MFC k `CHttpFile` objektu z [CInternetSession](../../mfc/reference/cinternetsession-class.md) objekt vytvořený `CHttpFile` objektu. Při volání [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) nebo [CHttpConnection](../../mfc/reference/chttpconnection-class.md) k vytvoření `CHttpFile` objekt, můžete přepsat výchozí identifikátor kontextu nastavit na hodnotu dle vlastního výběru. Identifikátor kontextu je vrácen do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytovat stav na objekt, ke kterému se identifikuje. Najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o kontextu identifikátor.  
  
##  <a name="getfileurl"></a>  CHttpFile::GetFileURL  
 Volání této funkce člen získat název souboru protokolu HTTP jako adresu URL.  
  
```  
virtual CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje adresu URL odkazující na prostředek přidružené k tomuto souboru.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce člen až po úspěšném volání [Odesilani](#sendrequest) nebo na `CHttpFile` objekt úspěšně vytvořený [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
##  <a name="getobject"></a>  CHttpFile::GetObject  
 Volání této funkce člen získat název přidružený k tomuto objektu `CHttpFile`.  
  
```  
CString GetObject() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující název objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce člen až po úspěšném volání [Odesilani](#sendrequest) nebo na `CHttpFile` objekt úspěšně vytvořený [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
##  <a name="getverb"></a>  CHttpFile::GetVerb  
 Volání této funkce člen získat akce HTTP (ani metody) přidružený k tomuto `CHttpFile`.  
  
```  
CString GetVerb() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující název akce HTTP (nebo metodu).  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce člen až po úspěšném volání [Odesilani](#sendrequest) nebo na `CHttpFile` objekt úspěšně vytvořený [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
##  <a name="queryinfo"></a>  CHttpFile::QueryInfo  
 Volání této funkce člen vrátí odpověď nebo hlavičky požadavku z požadavku HTTP.  
  
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
 `dwInfoLevel`  
 Kombinace atribut, který se dotaz a následující příznaky, které určují typ požadované informace:  
  
- **HTTP_QUERY_CUSTOM** najde název hlavičky a vrátí tuto hodnotu v `lpvBuffer` na výstup. **HTTP_QUERY_CUSTOM** vyvolá kontrolní výrazy, pokud hlavička nebyla nalezena.  
  
- **HTTP_QUERY_FLAG_REQUEST_HEADERS** obvykle se aplikace dotazuje hlavičky odpovědi, ale aplikace může také dotazovat hlavičky žádosti pomocí tento příznak.  
  
- **HTTP_QUERY_FLAG_SYSTEMTIME** pro tyto hlavičky, jehož hodnota je řetězec datum a čas, jako je například "Poslední upravit běhu," Tento příznak vrací hodnotu hlavičky jako standardní Win32 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura, která nevyžaduje aplikace se analyzovat data. Pokud chcete použít tento příznak, můžete chtít použít `SYSTEMTIME` přepsat funkce.  
  
- **HTTP_QUERY_FLAG_NUMBER** pro tyto hlavičky, jehož hodnota je číslo, například kód stavu tento příznak vrátí data jako 32bitové číslo.  
  
 Najdete v článku **poznámky** části seznamu možných hodnot.  
  
 `lpvBuffer`  
 Ukazatel do vyrovnávací paměti, která přijímá informace.  
  
 `lpdwBufferLength`  
 V položce to ukazuje na hodnotu obsahující délka vyrovnávací paměť dat v počtu znaků nebo bajtů. Najdete v článku **poznámky** části pro podrobnější informace o tomto parametru.  
  
 `lpdwIndex`  
 Ukazatel na index počítaný od nuly záhlaví. Může být **NULL**. Pomocí tohoto příznaku se vytvořit výčet více záhlaví se stejným názvem. Na vstupu `lpdwIndex` značí index Zadaná hlavička vrátit. Na výstupu `lpdwIndex` značí index další záhlaví. Pokud nelze nalézt další index, **ERROR_HTTP_HEADER_NOT_FOUND** je vrácen.  
  
 `str`  
 Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt přijetí vrácené informace.  
  
 `dwIndex`  
 Hodnota indexu. V tématu `lpdwIndex`.  
  
 *pSysTime*  
 Ukazatel na Win32 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce člen až po úspěšném volání [Odesilani](#sendrequest) nebo na `CHttpFile` objekt úspěšně vytvořený [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
 Můžete načíst následující typy dat z `QueryInfo`:  
  
-   řetězce (výchozí)  
  
- `SYSTEMTIME` (pro "Data:" "Expires:" apod, hlavičky)  
  
- `DWORD` (pro **STATUS_CODE**, **CONTENT_LENGTH**atd.)  
  
 Pokud řetězec je zapsán do vyrovnávací paměti a členské funkce úspěšné, `lpdwBufferLength` obsahuje délku řetězce ve znacích minus 1 pro ukončení **NULL** znak.  
  
 Možné `dwInfoLevel` hodnoty patří:  
  
- **HTTP_QUERY_MIME_VERSION**  
  
- **HTTP_QUERY_CONTENT_TYPE**  
  
- **HTTP_QUERY_CONTENT_TRANSFER_ENCODING**  
  
- **HTTP_QUERY_CONTENT_ID**  
  
- **HTTP_QUERY_CONTENT_DESCRIPTION**  
  
- **HTTP_QUERY_CONTENT_LENGTH**  
  
- **HTTP_QUERY_ALLOWED_METHODS**  
  
- **HTTP_QUERY_PUBLIC_METHODS**  
  
- **HTTP_QUERY_DATE**  
  
- **HTTP_QUERY_EXPIRES**  
  
- **HTTP_QUERY_LAST_MODIFIED**  
  
- **HTTP_QUERY_MESSAGE_ID**  
  
- **HTTP_QUERY_URI**  
  
- **HTTP_QUERY_DERIVED_FROM**  
  
- **HTTP_QUERY_LANGUAGE**  
  
- **HTTP_QUERY_COST**  
  
- **HTTP_QUERY_WWW_LINK**  
  
- **HTTP_QUERY_PRAGMA**  
  
- **HTTP_QUERY_VERSION**  
  
- **HTTP_QUERY_STATUS_CODE**  
  
- **HTTP_QUERY_STATUS_TEXT**  
  
- **HTTP_QUERY_RAW_HEADERS**  
  
- **HTTP_QUERY_RAW_HEADERS_CRLF**  
  
##  <a name="queryinfostatuscode"></a>  CHttpFile::QueryInfoStatusCode  
 Volání této funkce člen k získání stavového kódu přidružené k požadavku HTTP a umístěte ji do zadané `dwStatusCode` parametr.  
  
```  
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `dwStatusCode`  
 Odkaz na stavový kód. Stavové kódy udávající úspěch nebo selhání požadovaná událost. V tématu **poznámky** pro výběr popisů kód stavu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce člen až po úspěšném volání [Odesilani](#sendrequest) nebo na `CHttpFile` objekt úspěšně vytvořený [OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
 Stavové kódy HTTP spadají do skupin, která udává úspěch nebo selhání žádosti. Následující tabulky popisují skupiny kódu stavu a nejběžnější stavové kódy HTTP.  
  
|Skupina|Význam|  
|-----------|-------------|  
|200-299|Úspěch|  
|300-399|Informace o|  
|400-499|Žádost o chybě|  
|500-599|Chyba serveru|  
  
 Běžné kódy stavu HTTP:  
  
|Stavový kód|Význam|  
|-----------------|-------------|  
|200|Adresa URL umístěný, způsobem přenosu|  
|400|Nesrozumitelné požadavku|  
|404|Požadovaná adresa URL nebyla nalezena.|  
|405|Server nepodporuje požadovaný – metoda|  
|500|Neznámou chybu serveru|  
|503|Dosaženo kapacity serveru|  
  
##  <a name="sendrequest"></a>  CHttpFile::SendRequest  
 Volání této funkce člen odeslat požadavek na HTTP server.  
  
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
 `pstrHeaders`  
 Ukazatel na řetězec, který obsahuje název hlavičky k odeslání.  
  
 `dwHeadersLen`  
 Délka záhlaví identifikovaný `pstrHeaders`.  
  
 `lpOptional`  
 Všechny volitelné data k odeslání ihned po hlavičky žádosti. To se obvykle používá pro **POST** a **PUT** operace. To může být **NULL** Pokud neexistují žádné volitelné data k odeslání.  
  
 *dwOptionalLen*  
 Délka `lpOptional`.  
  
 `strHeaders`  
 Řetězec obsahující název hlavičky pro žádost o odeslání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, zjistit příčinu selhání na základě vyvolané [CInternetException](../../mfc/reference/cinternetexception-class.md) objektu.  
  
##  <a name="sendrequestex"></a>  CHttpFile::SendRequestEx  
 Volání této funkce člen odeslat požadavek na HTTP server.  
  
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
 *dwTotalLen*  
 Počet bajtů, které mají být odeslaných v požadavku.  
  
 `dwFlags`  
 Příznaky, které popisují operaci. Seznam příslušnými příznaky, naleznete v části [HttpSendRequestEx](http://msdn.microsoft.com/library/windows/desktop/aa384318) ve Windows SDK.  
  
 `dwContext`  
 Identifikátor kontextu `CHttpFile` operaci. Další informace o tomto parametru najdete v části poznámky.  
  
 `lpBuffIn`  
 Ukazatel na inicializovali [INTERNET_BUFFERS](http://msdn.microsoft.com/library/windows/desktop/aa385132) , který popisuje vstupní vyrovnávací paměť pro operaci použít.  
  
 *lpBuffOut*  
 Ukazatel na inicializovali **INTERNET_BUFFERS** , který popisuje výstupní vyrovnávací paměť pro operaci použít.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu. Pokud volání selže, zjistit příčinu selhání na základě vyvolané [CInternetException](../../mfc/reference/cinternetexception-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce umožňuje vaší aplikace posílat data pomocí [zápisu](../../mfc/reference/cinternetfile-class.md#write) a [WriteString](../../mfc/reference/cinternetfile-class.md#writestring) metody `CInternetFile`. Je nutné znát délka data k odeslání před voláním buď přepsání této funkce. První přepsání můžete zadat data, která se má odeslat. Druhý přepsání přijímá ukazatele na **INTERNET_BUFFERS** struktur, která slouží k vyrovnávací paměť příliš podrobně popisují.  
  
 Poté, co je zapisován obsah souboru, volejte [EndRequest](#endrequest) pro ukončení operace.  
  
 Výchozí hodnota pro `dwContext` odesílají MFC k `CHttpFile` objektu z [CInternetSession](../../mfc/reference/cinternetsession-class.md) objekt vytvořený `CHttpFile` objektu. Při volání [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl) nebo [CHttpConnection](../../mfc/reference/chttpconnection-class.md) k vytvoření `CHttpFile` objekt, můžete přepsat výchozí identifikátor kontextu nastavit na hodnotu dle vlastního výběru. Identifikátor kontextu je vrácen do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytovat stav na objekt, ke kterému se identifikuje. Najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o kontextu identifikátor.  
  
### <a name="example"></a>Příklad  
 Tento fragment kódu odešle obsah řetězec s názvem MFCISAPI knihovny DLL. Knihovny DLL na serveru LOCALHOST. Při tomto příkladě se používá pouze jednoho volání `WriteString`, pomocí více k odesílání dat do bloků je přijatelná.  
  
 [!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CInternetFile – třída](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)   
 [CHttpConnection – třída](../../mfc/reference/chttpconnection-class.md)
