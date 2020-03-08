---
title: Analýza adres URL pro Internet a globální a pomocníky
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 310e4ffb3fc207d874e97ba1fac65f6f8cb41a31
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865805"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Analýza adres URL pro Internet a globální a pomocníky

Když klient pošle dotaz na internetový server, můžete k extrakci informací o klientovi použít jednu z adres URL pro analýzu globálních informací. Pomocné funkce poskytují další funkce Internetu.

## <a name="internet-url-parsing-globals"></a>Globální funkce pro analýzu internetových adres URL

|||
|-|-|
|[AfxParseURL](#afxparseurl)|Analyzuje řetězec adresy URL a vrátí typ služby a její součásti.|
|[AfxParseURLEx](#afxparseurlex)|Analyzuje řetězec adresy URL a vrátí typ služby a její součásti a také zadání uživatelského jména a hesla.|

## <a name="other-internet-helpers"></a>Další pomocníky Internetu

|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|Vyvolá výjimku související s připojením k Internetu.|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|Určuje typ internetového popisovače.|

##  <a name="afxparseurl"></a>AfxParseURL

Tato globální aplikace se používá v [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

```
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort);
```

### <a name="parameters"></a>Parametry

*pstrURL*<br/>
Ukazatel na řetězec obsahující adresu URL, která má být analyzována.

*dwServiceType*<br/>
Určuje typ služby sítě Internet. Možné hodnoty jsou následující:

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer*<br/>
První segment adresy URL následující po typu služby.

*strObject*<br/>
Objekt, na který adresa URL odkazuje (může být prázdná).

*nPort*<br/>
Určeno z částí adresy URL serveru nebo objektu, pokud buď existují.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se adresa URL úspěšně analyzovala; v opačném případě 0, pokud je prázdný nebo neobsahuje známý typ internetové služby.

### <a name="remarks"></a>Poznámky

Analyzuje řetězec adresy URL a vrátí typ služby a její součásti.

Například `AfxParseURL` analyzuje adresy URL formuláře *Service://server/Dir/dir/Object.ext:port* a vrátí jeho komponenty uložené následujícím způsobem:

*strServer* = = "Server"

*strObject* = = "/dir/dir/Object/Object.ext"

*NPort* = = #port

*dwServiceType* = = #service

> [!NOTE]
>  Pro volání této funkce musí projekt zahrnovat AFXINET. Y.

### <a name="requirements"></a>Požadavky

  **Header** afxinet. h

##  <a name="afxparseurlex"></a>AfxParseURLEx

Tato globální funkce je rozšířená verze [AfxParseURL](#afxparseurl) a používá se v [CInternetSession:: OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

```
BOOL AFXAPI AfxParseURLEx(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort,
    CString& strUsername,
    CString& strPassword,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parametry

*pstrURL*<br/>
Ukazatel na řetězec obsahující adresu URL, která má být analyzována.

*dwServiceType*<br/>
Určuje typ služby sítě Internet. Možné hodnoty jsou následující:

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer*<br/>
První segment adresy URL následující po typu služby.

*strObject*<br/>
Objekt, na který adresa URL odkazuje (může být prázdná).

*nPort*<br/>
Určeno z částí adresy URL serveru nebo objektu, pokud buď existují.

*strUsername*<br/>
Odkaz na objekt `CString` obsahující jméno uživatele.

*strPassword*<br/>
Odkaz na objekt `CString`, který obsahuje heslo uživatele.

*dwFlags*<br/>
Příznaky, které řídí, jak analyzovat adresu URL. Může být kombinací následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|ICU_DECODE|Převede% XX řídicí sekvence na znaky.|
|ICU_NO_ENCODE|Neprovádějte převod nebezpečných znaků na řídicí sekvenci.|
|ICU_NO_META|Neodstraňujte meta sekvence (například "\." a "\..") z adresy URL.|
|ICU_ENCODE_SPACES_ONLY|Zakódovat pouze mezery.|
|ICU_BROWSER_MODE|Nekódovat ani dekódovat znaky za znakem "#" nebo "" a neodstraňujte koncové prázdné znaky po ' '. Pokud tato hodnota není zadaná, celá adresa URL se zakóduje a na konci se odeberou prázdné znaky.|

Použijete-li výchozí knihovnu MFC, což není žádný příznak, funkce převede všechny nezabezpečené znaky a meta sekvence (například \\., \.. a \\...) na řídicí sekvence.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se adresa URL úspěšně analyzovala; v opačném případě 0, pokud je prázdný nebo neobsahuje známý typ internetové služby.

### <a name="remarks"></a>Poznámky

Analyzuje řetězec adresy URL a vrací typ služby a její součásti a poskytuje uživatelské jméno a heslo. Příznaky označují, jak jsou zpracovávány nebezpečné znaky.

> [!NOTE]
>  Pro volání této funkce musí projekt zahrnovat AFXINET. Y.

### <a name="requirements"></a>Požadavky

  **Header** afxinet. h

## <a name="afxgetinternethandletype"></a>AfxGetInternetHandleType

Tuto globální funkci použijte k určení typu internetového popisovače.

### <a name="syntax"></a>Syntaxe

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>Parametry

*hQuery*<br/>
Popisovač pro dotaz na Internet.

### <a name="return-value"></a>Návratová hodnota

Libovolný typ služby pro Internet definovaný v rozhraní WININET. Y. Seznam těchto služeb sítě Internet najdete v části s poznámkami. Pokud má popisovač hodnotu NULL nebo není rozpoznán, funkce vrátí AFX_INET_SERVICE_UNK.

### <a name="remarks"></a>Poznámky

Následující seznam obsahuje možné typy Internetu vrácené `AfxGetInternetHandleType`.

- INTERNET_HANDLE_TYPE_INTERNET

- INTERNET_HANDLE_TYPE_CONNECT_FTP

- INTERNET_HANDLE_TYPE_CONNECT_GOPHER

- INTERNET_HANDLE_TYPE_CONNECT_HTTP

- INTERNET_HANDLE_TYPE_FTP_FIND

- INTERNET_HANDLE_TYPE_FTP_FIND_HTML

- INTERNET_HANDLE_TYPE_FTP_FILE

- INTERNET_HANDLE_TYPE_FTP_FILE_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FIND

- INTERNET_HANDLE_TYPE_GOPHER_FIND_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FILE

- INTERNET_HANDLE_TYPE_GOPHER_FILE_HTML

- INTERNET_HANDLE_TYPE_HTTP_REQUEST

> [!NOTE]
>  Aby bylo možné zavolat tuto funkci, projekt musí zahrnovat AFXINET. Y.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet. h

## <a name="afxthrowinternetexception"></a>AfxThrowInternetException

Vyvolá výjimku z Internetu.

### <a name="syntax"></a>Syntaxe

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>Parametry

*dwContext*<br/>
Identifikátor kontextu operace, která způsobila chybu. Výchozí hodnota *dwContext* je určena původně v [CInternetSession](cinternetsession-class.md) a je předávána třídám odvozeným od [CInternetConnection](cinternetconnection-class.md)-a [CInternetFile](cinternetfile-class.md). Pro konkrétní operace prováděné s připojením nebo souborem obvykle potlačíte výchozí *dwContext* . Tato hodnota se pak vrátí do [CInternetSession:: OnStatusCallback](cinternetsession-class.md#onstatuscallback) a určí stav konkrétní operace.

*dwError*<br/>
Chyba, která způsobila výjimku.

### <a name="remarks"></a>Poznámky

Zodpovídáte za zjištění příčiny na základě kódu chyby operačního systému.

> [!NOTE]
>  Pro volání této funkce musí projekt zahrnovat AFXINET. Y.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet. h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[CInternetException – třída](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
