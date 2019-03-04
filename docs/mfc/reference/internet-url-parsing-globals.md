---
title: Analýzu internetových adres URL a pomocné rutiny
ms.date: 04/03/2017
f1_keywords:
- vc.mfc.macros.isapi
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 0831d94f1a6f0293d3605a5e2e9ebde0564baf24
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293469"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Analýzu internetových adres URL a pomocné rutiny

Když klient odešle dotaz na Internet server, můžete použít jednu adresu URL, globální funkce pro analýzu pro extrakci informací o klientovi. Pomocné funkce poskytují další funkce internet.

## <a name="internet-url-parsing-globals"></a>Globální funkce pro analýzu internetových adres URL

|||
|-|-|
|[AfxParseURL](#afxparseurl)|Analyzuje řetězec adresy URL a vrátí typu a jeho komponenty.|
|[AfxParseURLEx](#afxparseurlex)|Analyzuje řetězec adresy URL a vrátí typ služby a jeho komponenty, jakož i uživatelské jméno a heslo.|

## <a name="other-internet-helpers"></a>Další pomocníci Internet

|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|Vyvolá výjimku týkající se připojení k Internetu.|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|Určuje typ internetového popisovače.|

##  <a name="afxparseurl"></a>  AfxParseURL

Tuto globální se používá v [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

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
Ukazatel na řetězec obsahující adresu URL, který se má analyzovat.

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
První segment adresy URL následující typ služby.

*strObject*<br/>
Adresa URL odkazující na objekt (může být prázdné).

*nPort*<br/>
Určit ze serveru nebo objektu části adresy URL, pokud buď existuje.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud adresa URL bylo úspěšně parsováno; v opačném případě 0, pokud je prázdný nebo neobsahuje známý typ služby sítě Internet.

### <a name="remarks"></a>Poznámky

Analyzuje řetězec adresy URL a vrátí typu a jeho komponenty.

Například `AfxParseURL` analyzuje adresy URL ve formátu *service://server/dir/dir/object.ext:port* a vrátí jeho komponenty ukládané následujícím způsobem:

*strServer* == "server"

*strObject* == "/dir/dir/object/object.ext"

*nPort* == #port

*dwServiceType* == #service

> [!NOTE]
>  Volání této funkce, váš projekt musí obsahovat AFXINET. H.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxinet.h

##  <a name="afxparseurlex"></a>  AfxParseURLEx

Tato globální funkce je rozšířenou verzi [afxparseurl –](#afxparseurl) a používá se [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).

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
Ukazatel na řetězec obsahující adresu URL, který se má analyzovat.

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
První segment adresy URL následující typ služby.

*strObject*<br/>
Adresa URL odkazující na objekt (může být prázdné).

*nPort*<br/>
Určit ze serveru nebo objektu části adresy URL, pokud buď existuje.

*strUsername*<br/>
Odkaz na `CString` objekt, který obsahuje jméno uživatele.

*strPassword*<br/>
Odkaz na `CString` objekt, který obsahuje heslo uživatele.

*dwFlags*<br/>
Příznaky řízení jak analyzovat adresu URL. Může být kombinací následujícího:

|Hodnota|Význam|
|-----------|-------------|
|ICU_DECODE|Převeďte % XX řídicí sekvence znaků.|
|ICU_NO_ENCODE|Nelze převést problematické znaky na řídicí sekvence.|
|ICU_NO_META|Neodebírejte meta pořadí (jako je například maska "\". a "\"..) z adresy URL.|
|ICU_ENCODE_SPACES_ONLY|Kódování pouze mezery.|
|ICU_BROWSER_MODE|Kódování nebo dekódování znaků za "#" nebo "a neodstraňujte prázdný znak po". Pokud tato hodnota není zadaná, je zakódovaný celou adresu URL a odebrat koncové prázdné znaky.|

Pokud používáte výchozí knihovny MFC, což je žádné příznaky, funkce převede všechny problematické znaky a meta pořadí (jako například \\., \.., a \\...) dostala mimo pořadí.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud adresa URL bylo úspěšně parsováno; v opačném případě 0, pokud je prázdný nebo neobsahuje známý typ služby sítě Internet.

### <a name="remarks"></a>Poznámky

Analyzuje řetězec adresy URL a vrátí typ služby a jeho komponenty, jakož i poskytnutí uživatelského jména a hesla. Příznaky označení jak problematické znaky jsou zpracovávány.

> [!NOTE]
>  Volání této funkce, váš projekt musí obsahovat AFXINET. H.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxinet.h

## <a name="afxgetinternethandletype"></a>  AfxGetInternetHandleType

Pomocí této globální funkce určit typ internetového popisovače.

### <a name="syntax"></a>Syntaxe

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>Parametry

*hQuery*<br/>
Popisovač na Internetu dotaz.

### <a name="return-value"></a>Návratová hodnota

Některý z typů služeb Internetu definované rozhraní WININET. H. V části poznámky pro seznam těchto služeb sítě Internet. Pokud je popisovač je NULL nebo nebylo rozpoznáno, funkce vrátí AFX_INET_SERVICE_UNK.

### <a name="remarks"></a>Poznámky

Následující seznam obsahuje možných typů Internet vrácený `AfxGetInternetHandleType`.

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
>  Abyste mohli volat tuto funkci, váš projekt musí obsahovat AFXINET. H.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="afxthrowinternetexception"></a>  AfxThrowInternetException

Vyvolá výjimku Internet.

### <a name="syntax"></a>Syntaxe

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>Parametry

*dwContext*<br/>
Identifikátor kontextu operace, která způsobila chybu. Výchozí hodnota *dwContext* původně určen ve [cinternetsession –](cinternetsession-class.md) a je předán [cinternetconnection –](cinternetconnection-class.md)– a [cinternetfile –](cinternetfile-class.md)-odvozené třídy. Pro konkrétní operace provedené na připojení nebo soubor, obvykle přepsat výchozí nastavení se *dwContext* vlastní. Tato hodnota je pak vrácen do [CInternetSession::OnStatusCallback](cinternetsession-class.md#onstatuscallback) k určení stavu konkrétní operace.

*dwError*<br/>
Chyba, která způsobila výjimku.

### <a name="remarks"></a>Poznámky

Je odpovědností zjistit příčinu založené na kód chyby operačního systému.

> [!NOTE]
>  Volání této funkce, váš projekt musí obsahovat AFXINET. H.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[CInternetException – třída](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
