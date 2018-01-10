---
title: "Internetové adresy URL globální funkce pro analýzu a pomocníky | Microsoft Docs"
ms.custom: 
ms.date: 04/03/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros.isapi
dev_langs: C++
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e29ae754e7f5b078c23f0cdf27c0a280cd28b40a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="internet-url-parsing-globals-and-helpers"></a>Internetové adresy URL globální funkce pro analýzu a pomocníky
Když klient odešle dotaz na server Internet, můžete jednu adresu URL, globální funkce pro analýzu extrahovat informace o klientovi. Podpůrné funkce nabízí jiné funkce Internetu.
  
## <a name="internet-url-parsing-globals"></a>Globální funkce pro analýzu internetových adres URL  
  
|||  
|-|-|  
|[Afxparseurl –](#afxparseurl)|Analyzuje řetězce adresy URL a vrátí typ služby a jeho součástí.|  
|[Afxparseurlex –](#afxparseurlex)|Analyzuje řetězce adresy URL a vrátí typ služby a jeho komponenty, a také poskytnutí uživatelského jména a hesla.|  

## <a name="other-internet-helpers"></a>Další pomocníci Internetu
|||
|-|-|
|[Afxthrowinternetexception –](#afxthrowinternetexception)|Vyvolá výjimku týkající se připojení k Internetu.|
|[Afxgetinternethandletype –](#afxgetinternethandletype)|Určuje typ internetového popisovače.|
  
##  <a name="afxparseurl"></a>Afxparseurl –  
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
 *pstrURL*  
 Ukazatel na řetězec obsahující analyzovat adresu URL.  
  
 `dwServiceType`  
 Určuje typ služby sítě Internet. Možné hodnoty jsou následující:  
  
-   AFX_INET_SERVICE_FTP  
  
-   AFX_INET_SERVICE_HTTP  
  
-   AFX_INET_SERVICE_HTTPS  
  
-   AFX_INET_SERVICE_GOPHER  
  
-   AFX_INET_SERVICE_FILE  
  
-   AFX_INET_SERVICE_MAILTO  
  
-   AFX_INET_SERVICE_NEWS  
  
-   AFX_INET_SERVICE_NNTP  
  
-   AFX_INET_SERVICE_TELNET  
  
-   AFX_INET_SERVICE_WAIS  
  
-   AFX_INET_SERVICE_MID  
  
-   AFX_INET_SERVICE_CID  
  
-   AFX_INET_SERVICE_PROSPERO  
  
-   AFX_INET_SERVICE_AFS  
  
-   AFX_INET_SERVICE_UNK  
  
 `strServer`  
 První segment adresy URL následující typ služby.  
  
 `strObject`  
 Objekt, který odkazuje adresu URL (může být prázdný).  
  
 `nPort`  
 Určit ze serveru nebo objekt části adresy URL, pokud buď existuje.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl úspěšně analyzovat adresu URL; jinak hodnota 0, pokud je prázdný nebo neobsahuje známý typ služby sítě Internet.  
  
### <a name="remarks"></a>Poznámky  
 Ho analyzuje řetězce adresy URL a vrací typ služby a jeho součástí.  
  
 Například `AfxParseURL` analyzuje adresy URL ve formátu **service://server/dir/dir/object.ext:port** a vrátí jeho komponenty uložené následujícím způsobem:  
  
 `strServer`== "server"  
  
 `strObject`== "/ dir/dir/object/object.ext"  
  
 `nPort`== #port  
  
 `dwServiceType`== #service  
  
> [!NOTE]
>  Pro volání této funkce, musí obsahovat projektu AFXINET. H.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxinet.h  
  
##  <a name="afxparseurlex"></a>Afxparseurlex –  
 Globální funkce je rozšířené verze [afxparseurl –](#afxparseurl) a používá se v [CInternetSession::OpenURL](../../mfc/reference/cinternetsession-class.md#openurl).  
  
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
 *pstrURL*  
 Ukazatel na řetězec obsahující analyzovat adresu URL.  
  
 `dwServiceType`  
 Určuje typ služby sítě Internet. Možné hodnoty jsou následující:  
  
-   AFX_INET_SERVICE_FTP  
  
-   AFX_INET_SERVICE_HTTP  
  
-   AFX_INET_SERVICE_HTTPS  
  
-   AFX_INET_SERVICE_GOPHER  
  
-   AFX_INET_SERVICE_FILE  
  
-   AFX_INET_SERVICE_MAILTO  
  
-   AFX_INET_SERVICE_NEWS  
  
-   AFX_INET_SERVICE_NNTP  
  
-   AFX_INET_SERVICE_TELNET  
  
-   AFX_INET_SERVICE_WAIS  
  
-   AFX_INET_SERVICE_MID  
  
-   AFX_INET_SERVICE_CID  
  
-   AFX_INET_SERVICE_PROSPERO  
  
-   AFX_INET_SERVICE_AFS  
  
-   AFX_INET_SERVICE_UNK  
  
 `strServer`  
 První segment adresy URL následující typ služby.  
  
 `strObject`  
 Objekt, který odkazuje adresu URL (může být prázdný).  
  
 `nPort`  
 Určit ze serveru nebo objekt části adresy URL, pokud buď existuje.  
  
 *strUsername*  
 Odkaz na `CString` objekt, který obsahuje jméno uživatele.  
  
 `strPassword`  
 Odkaz na `CString` objekt obsahující heslo uživatele.  
  
 `dwFlags`  
 Příznaky řízení jak analyzovat adresu URL. Může být kombinací následujícího:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|**ICU_DECODE**|Převeďte % XX řídicí sekvence znaků.|  
|**ICU_NO_ENCODE**|Nepřevádějí řídicí sekvence nebezpečné znaky.|  
|**ICU_NO_META**|Neodebírejte meta pořadí (například "\". a "\...") z adresy URL.|  
|**ICU_ENCODE_SPACES_ONLY**|Zakódujte pouze mezery.|  
|**ICU_BROWSER_MODE**|Kódování nebo dekódování znaků za znakem '#' nebo "a neodeberete prázdné znaky po". Pokud tato hodnota není zadaná, je zakódován úplnou adresu URL a bude odebrán prázdné znaky.|  
  
 Pokud použijete výchozí MFC, což je žádné příznaky, funkce převede všechny znaky unsafe a meta pořadí (například \\., \.., a \\...) abyste se vyhnuli pořadí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl úspěšně analyzovat adresu URL; jinak hodnota 0, pokud je prázdný nebo neobsahuje známý typ služby sítě Internet.  
  
### <a name="remarks"></a>Poznámky  
 Ho analyzuje řetězce adresy URL a vrátí typ služby a jeho komponenty, a také poskytnutí uživatelského jména a hesla. V příznacích znamenat jak nebezpečné znaky jsou zpracovávány.  
  
> [!NOTE]
>  Pro volání této funkce, musí obsahovat projektu AFXINET. H.  

### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxinet.h  
    
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
 
## <a name="afxgetinternethandletype"></a>Afxgetinternethandletype –
Pomocí této globální funkce můžete určit typ internetového popisovače.  
   
### <a name="syntax"></a>Syntaxe  
  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );  
```
### <a name="parameters"></a>Parametry  
 `hQuery`  
 Popisovač pro dotaz Internetu.  
   
### <a name="return-value"></a>Návratová hodnota  
 Jakýkoli z typů služby Internet definované WININET. H. Najdete v části poznámky seznam těchto služeb sítě Internet. Pokud popisovač je prázdný nebo nebyl rozpoznán, funkce vrátí hodnotu AFX_INET_SERVICE_UNK.  
   
### <a name="remarks"></a>Poznámky  
 Následující seznam obsahuje možné typy Internet vrácený `AfxGetInternetHandleType`.  
  
-   INTERNET_HANDLE_TYPE_INTERNET  
  
-   INTERNET_HANDLE_TYPE_CONNECT_FTP  
  
-   INTERNET_HANDLE_TYPE_CONNECT_GOPHER  
  
-   INTERNET_HANDLE_TYPE_CONNECT_HTTP  
  
-   INTERNET_HANDLE_TYPE_FTP_FIND  
  
-   INTERNET_HANDLE_TYPE_FTP_FIND_HTML  
  
-   INTERNET_HANDLE_TYPE_FTP_FILE  
  
-   INTERNET_HANDLE_TYPE_FTP_FILE_HTML  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FIND  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FIND_HTML  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FILE  
  
-   INTERNET_HANDLE_TYPE_GOPHER_FILE_HTML  
  
-   INTERNET_HANDLE_TYPE_HTTP_REQUEST  
  
> [!NOTE]
>  Chcete-li volání této funkce, musí obsahovat projektu AFXINET. H.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [Afxparseurl –](internet-url-parsing-globals.md#afxparseurl)
 
## <a name="afxthrowinternetexception"></a>Afxthrowinternetexception –
Vyvolá výjimku Internetu.  
   
### <a name="syntax"></a>Syntaxe    
```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );  
```
### <a name="parameters"></a>Parametry  
 `dwContext`  
 Identifikátor kontextu pro danou operaci, která způsobila chybu. Výchozí hodnota `dwContext` je původně zadaný v [CInternetSession](cinternetsession-class.md) a je předán [CInternetConnection](cinternetconnection-class.md)- a [CInternetFile](cinternetfile-class.md)-odvozených třídách. Pro konkrétní operace prováděné na připojení nebo soubor, obvykle přepsat výchozí nastavení s `dwContext` vlastní. Tato hodnota je pak vrácen do [CInternetSession::OnStatusCallback](cinternetsession-class.md#onstatuscallback) k identifikaci stavu konkrétní operaci. 
  
 `dwError`  
 Chyba, která způsobila výjimku.  
   
### <a name="remarks"></a>Poznámky  
 Jste zodpovědní za určení příčina podle kód chyby operačního systému.  
  
> [!NOTE]
>  Pro volání této funkce, musí obsahovat projektu AFXINET. H.  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
 [CInternetException – třída](cinternetexception-class.md)   
 [THROW](#throw)
 

