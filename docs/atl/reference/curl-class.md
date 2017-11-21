---
title: "Třída cUrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUrl
- ATLUTIL/ATL::CUrl
- ATLUTIL/ATL::CUrl::CUrl
- ATLUTIL/ATL::CUrl::Canonicalize
- ATLUTIL/ATL::CUrl::Clear
- ATLUTIL/ATL::CUrl::CrackUrl
- ATLUTIL/ATL::CUrl::CreateUrl
- ATLUTIL/ATL::CUrl::GetExtraInfo
- ATLUTIL/ATL::CUrl::GetExtraInfoLength
- ATLUTIL/ATL::CUrl::GetHostName
- ATLUTIL/ATL::CUrl::GetHostNameLength
- ATLUTIL/ATL::CUrl::GetPassword
- ATLUTIL/ATL::CUrl::GetPasswordLength
- ATLUTIL/ATL::CUrl::GetPortNumber
- ATLUTIL/ATL::CUrl::GetScheme
- ATLUTIL/ATL::CUrl::GetSchemeName
- ATLUTIL/ATL::CUrl::GetSchemeNameLength
- ATLUTIL/ATL::CUrl::GetUrlLength
- ATLUTIL/ATL::CUrl::GetUrlPath
- ATLUTIL/ATL::CUrl::GetUrlPathLength
- ATLUTIL/ATL::CUrl::GetUserName
- ATLUTIL/ATL::CUrl::GetUserNameLength
- ATLUTIL/ATL::CUrl::SetExtraInfo
- ATLUTIL/ATL::CUrl::SetHostName
- ATLUTIL/ATL::CUrl::SetPassword
- ATLUTIL/ATL::CUrl::SetPortNumber
- ATLUTIL/ATL::CUrl::SetScheme
- ATLUTIL/ATL::CUrl::SetSchemeName
- ATLUTIL/ATL::CUrl::SetUrlPath
- ATLUTIL/ATL::CUrl::SetUserName
dev_langs: C++
helpviewer_keywords: CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7e05cb6ca1aa9ffd9a827fd9f907fdc39d5bde13
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="curl-class"></a>CUrl – třída
Tato třída představuje adresu URL. Umožňuje pracovat s každý prvek adresy URL nezávisle na ostatních, zda analýza stávající adresy URL řetězec nebo vytváření řetězec od začátku.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CUrl
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CUrl::CUrl](#curl)|Konstruktor|  
|[CUrl:: ~ CUrl](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CUrl::Canonicalize](#canonicalize)|Voláním této metody lze převést na kanonický tvar řetězce adresy URL.|  
|[CUrl::Clear](#clear)|Volejte tuto metodu zrušte všechna pole adresy URL.|  
|[CUrl::CrackUrl](#crackurl)|Volejte tuto metodu za účelem dekódování a analyzovat adresu URL.|  
|[CUrl::CreateUrl](#createurl)|Volejte tuto metodu pro vytvoření adresy URL.|  
|[CUrl::GetExtraInfo](#getextrainfo)|Voláním této metody lze získat další informace (například *text* nebo # *text*) z adresy URL.|  
|[CUrl::GetExtraInfoLength](#getextrainfolength)|Volat tuto metodu za účelem získání délka doplňující informace (například *text* nebo # *text*) pro načtení z adresy URL.|  
|[CUrl::GetHostName](#gethostname)|Voláním této metody lze získat název hostitele z adresy URL.|  
|[CUrl::GetHostNameLength](#gethostnamelength)|Volejte tuto metodu za účelem získání délka názvu hostitele.|  
|[CUrl::GetPassword](#getpassword)|Volejte tuto metodu za účelem získání hesla z adresy URL.|  
|[CUrl::GetPasswordLength](#getpasswordlength)|Volejte tuto metodu za účelem získání délku hesla.|  
|[CUrl::GetPortNumber](#getportnumber)|Volejte tuto metodu za účelem získání číslo portu z hlediska ATL_URL_PORT.|  
|[CUrl::GetScheme](#getscheme)|Volejte tuto metodu za účelem získání schématu adresy URL.|  
|[CUrl::GetSchemeName](#getschemename)|Volejte tuto metodu za účelem získání názvu schéma adresy URL.|  
|[CUrl::GetSchemeNameLength](#getschemenamelength)|Volejte tuto metodu za účelem získání délka názvu schéma adresy URL.|  
|[CUrl::GetUrlLength](#geturllength)|Volejte tuto metodu za účelem získání délky adres URL.|  
|[CUrl::GetUrlPath](#geturlpath)|Volejte tuto metodu za účelem získání cesty adresy URL.|  
|[CUrl::GetUrlPathLength](#geturlpathlength)|Volejte tuto metodu za účelem získání délka cesty adresy URL.|  
|[CUrl::GetUserName](#getusername)|Volejte tuto metodu za účelem získání uživatelského jména z adresy URL.|  
|[CUrl::GetUserNameLength](#getusernamelength)|Volejte tuto metodu za účelem získání délka uživatelského jména.|  
|[CUrl::SetExtraInfo](#setextrainfo)|Volat tuto metodu a nastavit doplňující informace (například *text* nebo # *text*) adresy URL.|  
|[CUrl::SetHostName](#sethostname)|Volejte tuto metodu a nastavit název hostitele.|  
|[CUrl::SetPassword](#setpassword)|Volejte tuto metodu a nastavit heslo.|  
|[CUrl::SetPortNumber](#setportnumber)|Volejte tuto metodu a nastavit číslo portu z hlediska ATL_URL_PORT.|  
|[CUrl::SetScheme](#setscheme)|Volejte tuto metodu a nastavit schématu adresy URL.|  
|[CUrl::SetSchemeName](#setschemename)|Volejte tuto metodu a nastavit název schéma adresy URL.|  
|[CUrl::SetUrlPath](#seturlpath)|Volejte tuto metodu a nastavit cesty URL.|  
|[CUrl::SetUserName](#setusername)|Volejte tuto metodu a nastavit uživatelské jméno.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CUrl::operator =](#operator_eq)|Přiřadí zadaný `CUrl` objektu na aktuální `CUrl` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CUrl`umožňuje pracovat s pole adresu URL, například číslo cestu nebo portu. `CUrl`Jste srozuměni s tím adresy URL v následujícím formátu:  
  
 \<Schéma > ://\<uživatelské jméno >:\<heslo > @\<HostName >:\<ČísloPortu > /\<UrlPath >\<ExtraInfo >  
  
 (Některé pole jsou volitelná.) Představte si třeba tuto adresu URL:  
  
 http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents  
  
 [CUrl::CrackUrl](#crackurl) analyzuje ho následujícím způsobem:  
  
-   Schéma: "http" nebo [ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)  
  
-   Uživatelské jméno: "uživatel"  
  
-   Heslo: "tajný klíč"  
  
-   Název hostitele: "www.microsoft.com"  
  
-   Číslo_portu: 80  
  
-   UrlPath: "visualc/stuff.htm"  
  
-   ExtraInfo: "#contents"  
  
 Chcete-li pracovat s UrlPath pole (například), použijte [GetUrlPath](#geturlpath), [GetUrlPathLength](#geturlpathlength), a [SetUrlPath](#seturlpath). Byste použili [CreateUrl](#createurl) vytvořit úplný řetězec adresy URL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlutil.h  
  
##  <a name="canonicalize"></a>CUrl::Canonicalize  
 Voláním této metody lze převést na kanonický tvar řetězce adresy URL.  
  
```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Příznaky, které řídí kanonizace. Pokud nejsou zadány žádné příznaky ( `dwFlags` = 0), metoda převede všechny znaky unsafe a meta pořadí (například \\., \.., a \\...) abyste se vyhnuli pořadí. `dwFlags`může být jedna z následujících hodnot:  
  
-   ATL_URL_BROWSER_MODE: Kódování nebo dekódování znaků za "#" nebo "" a nedojde k odstranění prázdné znaky po "". Pokud tato hodnota není zadaná, je zakódován úplnou adresu URL a bude odebrán prázdné znaky.  
  
-   ATL_URL _DECODE: převede všech % XX pořadí znaků, včetně řídicí sekvence, než je analyzovat adresu URL.  
  
-   ATL_URL _ENCODE_PERCENT: kóduje všechny znaky procenta došlo. Ve výchozím nastavení nejsou znaky procenta kódování.  
  
-   ATL_URL _ENCODE_SPACES_ONLY: kóduje pouze mezery.  
  
-   ATL_URL _NO_ENCODE: nepřevede řídicí sekvence nebezpečné znaky.  
  
-   ATL_URL _NO_META: neodebere meta pořadí (například "."a"...") z adresy URL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Převádění na kanonický tvar zahrnuje převod nebezpečné znaky a prostory a řídicích sekvencí.  
  
##  <a name="clear"></a>CUrl::Clear  
 Volejte tuto metodu zrušte všechna pole adresy URL.  
  
```
inline void Clear() throw();
```  
  
##  <a name="crackurl"></a>CUrl::CrackUrl  
 Volejte tuto metodu za účelem dekódování a analyzovat adresu URL.  
  
```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszUrl`  
 Adresa URL.  
  
 `dwFlags`  
 Zadejte ATL_URL_DECODE nebo ATL_URL_ESCAPE převést všechny řídicí znaky v `lpszUrl` skutečné hodnoty po analýze. (Před Visual C++ 2005 ATL_URL_DECODE převést všechny řídicí znaky před analýzou.)  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
##  <a name="createurl"></a>CUrl::CreateUrl  
 Tato metoda vytvoří adresa URL řetězec z pole součást objekt CUrl.  
  
```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszUrl*  
 Řetězec vyrovnávací paměť pro dokončení řetězce adresy URL.  
  
 `pdwMaxLength`  
 Maximální délka *lpszUrl* vyrovnávací paměti.  
  
 `dwFlags`  
 Zadejte ATL_URL_ESCAPE převést všechny řídicí znaky v *lpszUrl* skutečné hodnoty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda připojí jeho jednotlivých polí. Chcete-li vytvořit úplný řetězec adresy URL v následujícím formátu:  
  
 **\<schéma > ://\<uživatele >:\<předat > @\<domény >:\<port >\<cesta >\<Další >**  
  
 Při volání této metody `pdwMaxLength` parametr musí obsahovat původně maximální délka vyrovnávací paměti řetězců odkazuje *lpszUrl* parametr. Hodnota `pdwMaxLength` parametr bude aktualizována skutečná délka řetězce adresy URL.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření objektu CUrl nebo načtení jeho řetězce adresy URL  
  
 [!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]  
  
##  <a name="curl"></a>CUrl::CUrl  
 Konstruktor  
  
```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `urlThat`  
 `CUrl` Objekt, který chcete vytvořit adresu URL zkopírovat.  
  
##  <a name="dtor"></a>CUrl:: ~ CUrl  
 Destruktor.  
  
```
~CUrl() throw();
```  
  
##  <a name="getextrainfo"></a>CUrl::GetExtraInfo  
 Voláním této metody lze získat další informace (například *text* nebo # *text*) z adresy URL.  
  
```
inline LPCTSTR GetExtraInfo() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací řetězec obsahující další informace.  
  
##  <a name="getextrainfolength"></a>CUrl::GetExtraInfoLength  
 Volat tuto metodu za účelem získání délka doplňující informace (například *text* nebo # *text*) pro načtení z adresy URL.  
  
```
inline DWORD GetExtraInfoLength() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí délku řetězec obsahující další informace.  
  
##  <a name="gethostname"></a>CUrl::GetHostName  
 Voláním této metody lze získat název hostitele z adresy URL.  
  
```
inline LPCTSTR GetHostName() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí název hostitele.  
  
##  <a name="gethostnamelength"></a>CUrl::GetHostNameLength  
 Volejte tuto metodu za účelem získání délka názvu hostitele.  
  
```
inline DWORD GetHostNameLength() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí délka názvu hostitele.  
  
##  <a name="getpassword"></a>CUrl::GetPassword  
 Volejte tuto metodu za účelem získání hesla z adresy URL.  
  
```
inline LPCTSTR GetPassword() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí heslo.  
  
##  <a name="getpasswordlength"></a>CUrl::GetPasswordLength  
 Volejte tuto metodu za účelem získání délku hesla.  
  
```
inline DWORD GetPasswordLength() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí délku hesla.  
  
##  <a name="getportnumber"></a>CUrl::GetPortNumber  
 Volejte tuto metodu za účelem získání číslo portu.  
  
```
inline ATL_URL_PORT GetPortNumber() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí číslo portu.  
  
##  <a name="getscheme"></a>CUrl::GetScheme  
 Volejte tuto metodu za účelem získání schématu adresy URL.  
  
```
inline ATL_URL_SCHEME GetScheme() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí [ATL_URL_SCHEME](atl-url-scheme-enum.md) hodnota popisující schéma adresy URL.  
  
##  <a name="getschemename"></a>CUrl::GetSchemeName  
 Volejte tuto metodu za účelem získání názvu schéma adresy URL.  
  
```
inline LPCTSTR GetSchemeName() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí název schéma adresy URL (například "http" nebo "ftp").  
  
##  <a name="getschemenamelength"></a>CUrl::GetSchemeNameLength  
 Volejte tuto metodu za účelem získání délka názvu schéma adresy URL.  
  
```
inline DWORD GetSchemeNameLength() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí délka názvu schéma adresy URL.  
  
##  <a name="geturllength"></a>CUrl::GetUrlLength  
 Volejte tuto metodu za účelem získání délky adres URL.  
  
```
inline DWORD GetUrlLength() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí délky adres URL.  
  
##  <a name="geturlpath"></a>CUrl::GetUrlPath  
 Volejte tuto metodu za účelem získání cesty adresy URL.  
  
```
inline LPCTSTR GetUrlPath() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací cestu adresy URL.  
  
##  <a name="geturlpathlength"></a>CUrl::GetUrlPathLength  
 Volejte tuto metodu za účelem získání délka cesty adresy URL.  
  
```
inline DWORD GetUrlPathLength() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí délku cesty adresy URL.  
  
##  <a name="getusername"></a>CUrl::GetUserName  
 Volejte tuto metodu za účelem získání uživatelského jména z adresy URL.  
  
```
inline LPCTSTR GetUserName() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí uživatelské jméno.  
  
##  <a name="getusernamelength"></a>CUrl::GetUserNameLength  
 Volejte tuto metodu za účelem získání délka uživatelského jména.  
  
```
inline DWORD GetUserNameLength() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí délka jména uživatele.  
  
##  <a name="operator_eq"></a>CUrl::operator =  
 Přiřadí zadaný `CUrl` objektu na aktuální `CUrl` objektu.  
  
```
CUrl& operator= (const CUrl& urlThat) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `urlThat`  
 `CUrl` Objekt, který chcete zkopírovat do aktuálního objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na aktuální objekt.  
  
##  <a name="setextrainfo"></a>CUrl::SetExtraInfo  
 Volat tuto metodu a nastavit doplňující informace (například *text* nebo # *text*) adresy URL.  
  
```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszInfo*  
 Řetězec, který obsahuje doplňující informace, které chcete zahrnout do adresy URL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
##  <a name="sethostname"></a>CUrl::SetHostName  
 Volejte tuto metodu a nastavit název hostitele.  
  
```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszHost`  
 Název hostitele.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
##  <a name="setpassword"></a>CUrl::SetPassword  
 Volejte tuto metodu a nastavit heslo.  
  
```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszPass*  
 Heslo.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
##  <a name="setportnumber"></a>CUrl::SetPortNumber  
 Volejte tuto metodu a nastavit číslo portu.  
  
```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nPrt*  
 Číslo portu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
##  <a name="setscheme"></a>CUrl::SetScheme  
 Volejte tuto metodu a nastavit schématu adresy URL.  
  
```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nScheme`  
 Jeden z [ATL_URL_SCHEME](atl-url-scheme-enum.md) hodnoty pro schéma.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Schéma můžete také nastavit podle názvu (viz [CUrl::SetSchemeName](#setschemename)).  
  
##  <a name="setschemename"></a>CUrl::SetSchemeName  
 Volejte tuto metodu a nastavit název schéma adresy URL.  
  
```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszSchm*  
 Název schématu adresy URL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Schéma můžete nastavit také pomocí [ATL_URL_SCHEME](atl-url-scheme-enum.md) konstantní (viz [CUrl::SetScheme](#setscheme)).  
  
##  <a name="seturlpath"></a>CUrl::SetUrlPath  
 Volejte tuto metodu a nastavit cesty URL.  
  
```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszPath`  
 Cesta adresy URL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
##  <a name="setusername"></a>CUrl::SetUserName  
 Volejte tuto metodu a nastavit uživatelské jméno.  
  
```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *lpszUser*  
 Uživatelské jméno  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, v případě úspěchu FALSE při selhání.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../atl/reference/atl-classes.md)
