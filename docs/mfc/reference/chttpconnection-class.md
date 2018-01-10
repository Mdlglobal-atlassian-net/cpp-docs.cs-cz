---
title: "Třída CHttpConnection | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHttpConnection
- AFXINET/CHttpConnection
- AFXINET/CHttpConnection::CHttpConnection
- AFXINET/CHttpConnection::OpenRequest
dev_langs: C++
helpviewer_keywords:
- CHttpConnection [MFC], CHttpConnection
- CHttpConnection [MFC], OpenRequest
ms.assetid: a402b662-c445-4988-800d-c8278551babe
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5a5236a4a957c742074a1305ba2d4359da3ed967
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
|[CHttpConnection::CHttpConnection](#chttpconnection)|Vytvoří `CHttpConnection` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CHttpConnection::OpenRequest](#openrequest)|Otevře se požadavek HTTP.|  
  
## <a name="remarks"></a>Poznámky  
 HTTP je jedním ze tří protokolů serveru Internet realizován pomocí tříd WinInet knihovny MFC.  
  
 Třída `CHttpConnection` obsahuje konstruktor a jednoho člena funkce [OpenRequest](#openrequest), která spravuje připojení k serveru pomocí protokolu HTTP.  
  
 Ke komunikaci se serverem protokolu HTTP, musíte nejdřív vytvořit instanci [CInternetSession](../../mfc/reference/cinternetsession-class.md)a pak vytvořte [CHttpConnection](#_mfc_chttpconnection) objektu. Nikdy vytvoříte `CHttpConnection` objektu přímo; místo toho volat [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection), která vytvoří `CHttpConnection` objektu a vrátí ukazatel na ni.  
  
 Další informace o tom, `CHttpConnection` funguje s ostatní třídy MFC Internetu najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md). Další informace o připojení k serverům jiných dva pomocí podporované Internetové protokoly, gopher a FTP, viz třídy [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) a [CFtpConnection](../../mfc/reference/cftpconnection-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CHttpConnection`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
  
##  <a name="chttpconnection"></a>CHttpConnection::CHttpConnection  
 Tato funkce člen je volána k sestavení `CHttpConnection` objektu.  
  
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
 `pSession`  
 Ukazatel [CInternetSession](../../mfc/reference/cinternetsession-class.md) objektu.  
  
 `hConnected`  
 Popisovač pro připojení k Internetu.  
  
 `pstrServer`  
 Ukazatel na řetězec obsahující název serveru.  
  
 `dwContext`  
 Identifikátor kontext pro `CInternetConnection` objektu. V tématu **poznámky** Další informace o `dwContext`.  
  
 `nPort`  
 Číslo, které identifikuje port Internetu pro toto připojení.  
  
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
  
 `dwFlags`  
 Libovolnou kombinaci **INTERNET_ FLAG_\***  příznaky. Podívejte se na tabulku v **poznámky** části [CHttpConnection::OpenRequest](#openrequest) popis `dwFlags` hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Nikdy vytvoříte `CHttpConnection` přímo. Místo toho vytvořte objekt voláním [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection).  
  
##  <a name="openrequest"></a>CHttpConnection::OpenRequest  
 Volání této funkce člen otevřete připojení HTTP.  
  
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
 `pstrVerb`  
 Ukazatel na řetězec obsahující příkaz, který má používat v požadavku. Pokud `NULL`, "GET" se používá.  
  
 `pstrObjectName`  
 Ukazatel na řetězec obsahující cílový objekt zadaný příkaz. Obecně je název souboru, spustitelný soubor modulu nebo specifikátor vyhledávání.  
  
 `pstrReferer`  
 Ukazatel na řetězec, který určuje adresu (URL) dokumentu, ze které adresu URL v požadavku ( `pstrObjectName`) byl získán. Pokud `NULL`, je zadána žádné záhlaví HTTP.  
  
 `dwContext`  
 Identifikátor kontextu `OpenRequest` operaci. Najdete v části poznámky Další informace `dwContext`.  
  
 `ppstrAcceptTypes`  
 Ukazatel na ukončené hodnotou null pole `LPCTSTR` ukazatele na řetězce, které označují typy obsahu akceptovat klienta. Pokud `ppstrAcceptTypes` je `NULL`, servery interpretovat klienta přijímá pouze dokumenty typu "text / *" (to znamená, dokumenty pouze text a není obrázky nebo jiné binární soubory). Typ obsahu je ekvivalentní typ_obsahu proměnné CGI, která identifikuje typu dat pro dotazy, které obsahují připojené informace, jako je například HTTP POST a PUT.  
  
 `pstrVersion`  
 Ukazatel na řetězec definování verzi protokolu HTTP. Pokud `NULL`, se používá "HTTP/1.0".  
  
 `dwFlags`  
 Libovolnou kombinaci příznaky INTERNET_ FLAG_ *. Najdete v části poznámky popis možné `dwFlags` hodnoty.  
  
 `nVerb`  
 Počet, přidružený typ požadavku HTTP. Může být jedna z následujících akcí:  
  
|Typ požadavku HTTP|`nVerb`Hodnota|  
|-----------------------|-------------------|  
|`HTTP_VERB_POST`|0|  
|`HTTP_VERB_GET`|1|  
|`HTTP_VERB_HEAD`|2|  
|`HTTP_VERB_PUT`|3|  
|`HTTP_VERB_LINK`|4|  
|`HTTP_VERB_DELETE`|5|  
|`HTTP_VERB_UNLINK`|6|  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CHttpFile](../../mfc/reference/chttpfile-class.md) požadovaný objekt.  
  
### <a name="remarks"></a>Poznámky  
 `dwFlags`může být jedna z následujících akcí:  
  
|Příznak Internetu|Popis|  
|-------------------|-----------------|  
|`INTERNET_FLAG_RELOAD`|Vynutí stahování požadovaný soubor, objektu nebo adresářů ze zdrojového serveru, ne z mezipaměti.|  
|`INTERNET_FLAG_DONT_CACHE`|Nepřidává žádné další vrácenou entitu do mezipaměti.|  
|`INTERNET_FLAG_MAKE_PERSISTENT`|Přidá vrácenou entitu do mezipaměti jako trvalé entity. To znamená, že vyčištění standardní mezipaměti, kontrolu konzistence nebo uvolňování paměti nelze odebrat tuto položku z mezipaměti.|  
|`INTERNET_FLAG_SECURE`|Sémantika používá zabezpečené transakce. To znamená, že k používání protokolu SSL/PCT a má smysl v požadavcích HTTP pouze|  
|`INTERNET_FLAG_NO_AUTO_REDIRECT`|Použít pouze s protokolem HTTP, určuje, že by neměl být automaticky zpracovávat přesměrování v [CHttpFile::SendRequest](../../mfc/reference/chttpfile-class.md#sendrequest).|  
  
 Přepsání `dwContext` výchozí identifikátor kontextu nastavit na hodnotu dle vlastního výběru. Identifikátor kontextu je přidružen tento konkrétní operace `CHttpConnection` objekt vytvořený jeho [CInternetSession](../../mfc/reference/cinternetsession-class.md) objektu. Hodnota je vrácen do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytovat stav na operace, pomocí kterého se identifikuje. Najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o kontextu identifikátor.  
  
 Pomocí této funkce můžou být vyvolány výjimky.  
  
## <a name="see-also"></a>Viz také  
 [CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)   
 [CHttpFile – třída](../../mfc/reference/chttpfile-class.md)
