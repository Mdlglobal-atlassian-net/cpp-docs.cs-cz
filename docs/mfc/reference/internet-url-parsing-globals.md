---
title: InternetOVÁ analýza adres URL Globals and Helpers
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 742b381ecb55c433d0f384174b7612fcc21e9716
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356611"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>InternetOVÁ analýza adres URL Globals and Helpers

Když klient odešle dotaz na internetový server, můžete k extrahování informací o klientovi použít jednu z globálních analýz adresy URL. Pomocné funkce poskytují další funkce internetu.

## <a name="internet-url-parsing-globals"></a>Globální funkce pro analýzu internetových adres URL

|||
|-|-|
|[AfxParseURL](#afxparseurl)|Analyzuje řetězec adresy URL a vrátí typ služby a její součásti.|
|[AfxParseURLEx](#afxparseurlex)|Analyzuje řetězec adresy URL a vrátí typ služby a její součásti a také zadá uživatelské jméno a heslo.|

## <a name="other-internet-helpers"></a>Další internetoví pomocníci

|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|Vyvolá výjimku související s připojením k internetu.|
|[AfxGetInternetHandleTyp](#afxgetinternethandletype)|Určuje typ popisovače Sítě Internet.|

## <a name="afxparseurl"></a><a name="afxparseurl"></a>AfxParseURL

Tento globální se používá v [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

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

*dwServiceTyp*<br/>
Označuje typ internetové služby. Možné hodnoty jsou následující:

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
První segment adresy URL následující za typem služby.

*strObjekt*<br/>
Objekt, na který odkazuje adresa URL (může být prázdný).

*nPort*<br/>
Určeno ze serverových nebo objektových částí adresy URL, pokud existuje.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla adresa URL úspěšně analyzována; v opačném případě 0, pokud je prázdný nebo neobsahuje známý typ služby Sítě Internet.

### <a name="remarks"></a>Poznámky

Analyzuje řetězec adresy URL a vrátí typ služby a její součásti.

Například `AfxParseURL` analyzuje adresy URL formuláře *service://server/dir/dir/object.ext:port* a vrátí jeho součásti uložené následujícím způsobem:

*strServer* == "server"

*strObject* == "/dir/dir/object/object.ext"

*nPort* == #port

*dwServiceType* == #service

> [!NOTE]
> Chcete-li volat tuto funkci, váš projekt musí obsahovat AFXINET. H.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxinet.h

## <a name="afxparseurlex"></a><a name="afxparseurlex"></a>AfxParseURLEx

Tato globální funkce je rozšířená verze [AfxParseURL](#afxparseurl) a používá se v [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

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

*dwServiceTyp*<br/>
Označuje typ internetové služby. Možné hodnoty jsou následující:

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
První segment adresy URL následující za typem služby.

*strObjekt*<br/>
Objekt, na který odkazuje adresa URL (může být prázdný).

*nPort*<br/>
Určeno ze serverových nebo objektových částí adresy URL, pokud existuje.

*StrUsername*<br/>
Odkaz na `CString` objekt obsahující jméno uživatele.

*strPassword*<br/>
Odkaz na `CString` objekt obsahující heslo uživatele.

*dwFlags*<br/>
Příznaky, které řídí, jak analyzovat adresu URL. Může být kombinací následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|ICU_DECODE|Převeďte %XX řídicích sekvencí na znaky.|
|ICU_NO_ENCODE|Nepřevádí nebezpečné znaky escape sekvence.|
|ICU_NO_META|Neodstraňujte metasekvence (například "\" . a "\ ..") z adresy URL.|
|ICU_ENCODE_SPACES_ONLY|Zakódujte pouze mezery.|
|ICU_BROWSER_MODE|Nekódujte ani nedekódujte znaky za '#' nebo '' a neodstraňujte koncové prázdné místo po ''. Pokud tato hodnota není zadána, je zakódována celá adresa URL a je odebráno koncové prázdné místo.|

Pokud použijete výchozí knihovnu MFC, což není žádné příznaky, funkce převede \\všechny nebezpečné znaky \\a metasekvence (například .,\ .., a ...) na únikové sekvence.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla adresa URL úspěšně analyzována; v opačném případě 0, pokud je prázdný nebo neobsahuje známý typ služby Sítě Internet.

### <a name="remarks"></a>Poznámky

Analyzuje řetězec adresy URL a vrátí typ služby a její součásti a také zadá jméno a heslo uživatele. Příznaky označují, jak jsou zpracovány nebezpečné znaky.

> [!NOTE]
> Chcete-li volat tuto funkci, váš projekt musí obsahovat AFXINET. H.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxinet.h

## <a name="afxgetinternethandletype"></a><a name="afxgetinternethandletype"></a>AfxGetInternetHandleTyp

Tato globální funkce slouží k určení typu popisovače Sítě Internet.

### <a name="syntax"></a>Syntaxe

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>Parametry

*hDotaz*<br/>
Popisovač internetového dotazu.

### <a name="return-value"></a>Návratová hodnota

Všechny typy internetových služeb definované sítí WININET. H. Seznam těchto internetových služeb naleznete v části Poznámky. Pokud je popisovač null nebo není rozpoznán, funkce vrátí AFX_INET_SERVICE_UNK.

### <a name="remarks"></a>Poznámky

Následující seznam obsahuje možné typy `AfxGetInternetHandleType`Internetu vrácené aplikací .

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
> Chcete-li volat tuto funkci, váš projekt musí obsahovat AFXINET. H.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="afxthrowinternetexception"></a><a name="afxthrowinternetexception"></a>AfxThrowInternetException

Vyvolá výjimku internetu.

### <a name="syntax"></a>Syntaxe

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>Parametry

*dwKontext*<br/>
Identifikátor kontextu pro operaci, která způsobila chybu. Výchozí hodnota *dwContext* je původně zadána v [CInternetSession](cinternetsession-class.md) a je předána třídám [CInternetConnection](cinternetconnection-class.md)- a [CInternetFile](cinternetfile-class.md)-derived. Pro konkrétní operace prováděné na připojení nebo souboru obvykle přepsat výchozí *s dwContext* vlastní. Tato hodnota je pak vrácena [CInternetSession::OnStatusCallback](cinternetsession-class.md#onstatuscallback) k identifikaci stavu konkrétní operace.

*chyba dwError*<br/>
Chyba, která způsobila výjimku.

### <a name="remarks"></a>Poznámky

Jste zodpovědní za určení příčiny na základě kódu chyby operačního systému.

> [!NOTE]
> Chcete-li volat tuto funkci, váš projekt musí obsahovat AFXINET. H.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="see-also"></a>Viz také

[Makra a globální](mfc-macros-and-globals.md)<br/>
[Třída CInternetException](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
