---
title: CUrl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
dev_langs:
- C++
helpviewer_keywords:
- CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0babb0932fc059a91fd8da79f649039bcaebc457
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753726"
---
# <a name="curl-class"></a>CUrl – třída

Tato třída představuje adresu URL. To umožňuje pracovat s každý prvek adresu URL nezávisle na ostatních, zda analýza stávající adresy URL řetězec nebo vytváření řetězec od začátku.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

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
|[CUrl::Canonicalize](#canonicalize)|Volání této metody pro převod řetězce adresy URL na kanonický tvar.|
|[CUrl::Clear](#clear)|Voláním této metody lze vymazat všechna pole adresy URL.|
|[CUrl::CrackUrl](#crackurl)|Volejte tuto metodu za účelem dekódování a analyzovat adresu URL.|
|[CUrl::CreateUrl](#createurl)|Volejte tuto metodu za účelem vytvoření adresy URL.|
|[CUrl::GetExtraInfo](#getextrainfo)|Voláním této metody lze získat další informace (například *text* nebo # *text*) z adresy URL.|
|[CUrl::GetExtraInfoLength](#getextrainfolength)|Volat tuto metodu za účelem získání délky dodatečné informace (například *text* nebo # *text*) pro načtení z adresy URL.|
|[CUrl::GetHostName](#gethostname)|Volejte tuto metodu za účelem získání názvu hostitele z adresy URL.|
|[CUrl::GetHostNameLength](#gethostnamelength)|Volejte tuto metodu za účelem získání délky názvu hostitele.|
|[CUrl::GetPassword](#getpassword)|Volejte tuto metodu za účelem získání hesla z adresy URL.|
|[CUrl::GetPasswordLength](#getpasswordlength)|Volejte tuto metodu za účelem získání délky hesla.|
|[CUrl::GetPortNumber](#getportnumber)|Volejte tuto metodu za účelem získání číslo portu z hlediska ATL_URL_PORT.|
|[CUrl::GetScheme](#getscheme)|Volejte tuto metodu za účelem získání schéma adresy URL.|
|[CUrl::GetSchemeName](#getschemename)|Volejte tuto metodu za účelem získání názvu schéma adresy URL.|
|[CUrl::GetSchemeNameLength](#getschemenamelength)|Volejte tuto metodu za účelem získání délky název schéma adresy URL.|
|[CUrl::GetUrlLength](#geturllength)|Volejte tuto metodu za účelem získání délky adresy URL.|
|[CUrl::GetUrlPath](#geturlpath)|Volejte tuto metodu za účelem získání cesty adresy URL.|
|[CUrl::GetUrlPathLength](#geturlpathlength)|Volejte tuto metodu za účelem získání délky cesty adresy URL.|
|[CUrl::GetUserName](#getusername)|Volejte tuto metodu za účelem získání uživatelského jména z adresy URL.|
|[CUrl::GetUserNameLength](#getusernamelength)|Volejte tuto metodu za účelem získání délky uživatelské jméno.|
|[CUrl::SetExtraInfo](#setextrainfo)|Voláním této metody lze nastavit další informace (například *text* nebo # *text*) adresy URL.|
|[CUrl::SetHostName](#sethostname)|Voláním této metody lze nastavit název hostitele.|
|[CUrl::SetPassword](#setpassword)|Voláním této metody lze nastavit heslo.|
|[CUrl::SetPortNumber](#setportnumber)|Voláním této metody nastavte číslo portu z hlediska ATL_URL_PORT.|
|[CUrl::SetScheme](#setscheme)|Voláním této metody nastavte schéma adresy URL.|
|[CUrl::SetSchemeName](#setschemename)|Voláním této metody nastavte název schéma adresy URL.|
|[CUrl::SetUrlPath](#seturlpath)|Volejte tuto metodu použijte k nastavení cesty adresy URL.|
|[CUrl::SetUserName](#setusername)|Voláním této metody nastavte uživatelské jméno.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CUrl::operator =](#operator_eq)|Přiřadí zadaný `CUrl` objektů na aktuální `CUrl` objektu.|

## <a name="remarks"></a>Poznámky

`CUrl` umožňuje manipulaci s poli Adresa URL, jako je například cesta nebo port číslo. `CUrl` rozumí adresy URL v následujícím formátu:

\<Schéma > ://\<uživatelské jméno >:\<heslo > @\<název_hostitele >:\<číslo_portu > /\<UrlPath >\<ExtraInfo >

(Některá pole jsou volitelná.) Zvažte například tuto adresu URL:

http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents

[CUrl::CrackUrl](#crackurl) analyzuje následujícím způsobem:

- Schéma: "http" nebo [ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)

- Uživatelské jméno: "uživatel"

- Heslo: "tajný klíč"

- Název hostitele: "www.microsoft.com"

- Číslo_portu: 80

- UrlPath: "visualc/stuff.htm"

- ExtraInfo: "#contents"

K manipulaci s poli UrlPath (například), můžete využít [GetUrlPath](#geturlpath), [GetUrlPathLength](#geturlpathlength), a [SetUrlPath](#seturlpath). Můžete využít [CreateUrl](#createurl) k vytvoření kompletního řetězce adresy URL.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

##  <a name="canonicalize"></a>  CUrl::Canonicalize

Volání této metody pro převod řetězce adresy URL na kanonický tvar.

```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*dwFlags*  
Příznaky, které řídí převodu do kanonického tvaru. Pokud nejsou zadány žádné příznaky (*dwFlags* = 0), metoda převede všechny problematické znaky a meta pořadí (jako například \\., \.., a \\...) dostala mimo pořadí. *dwFlags* může být jedna z následujících hodnot:

- ATL_URL_BROWSER_MODE: Kódování nebo dekódování znaků za "#" nebo "" a neodebere prázdný znak po "". Pokud tato hodnota není zadaná, je zakódovaný celou adresu URL a odebrat koncové prázdné znaky.

- ATL_URL _DECODE: převede všechny % XX sekvence znaků, včetně řídicí sekvence, než adresa URL se zpracuje.

- ATL_URL _ENCODE_PERCENT: kóduje došlo k procenta. Ve výchozím nastavení nejsou kódovaný procenta.

- ATL_URL _ENCODE_SPACES_ONLY: zakóduje pouze mezery.

- ATL_URL _NO_ENCODE: nejde převést problematické znaky na řídicí sekvence.

- ATL_URL _NO_META: neodebere meta pořadí (jako například "."a"..") z adresy URL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Převod do kanonického tvaru zahrnuje problematické znaky a mezery pro řídicí sekvence.

##  <a name="clear"></a>  CUrl::Clear

Voláním této metody lze vymazat všechna pole adresy URL.

```
inline void Clear() throw();
```

##  <a name="crackurl"></a>  CUrl::CrackUrl

Volejte tuto metodu za účelem dekódování a analyzovat adresu URL.

```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*lpszUrl*  
Adresa URL.

*dwFlags*  
Zadejte ATL_URL_DECODE nebo ATL_URL_ESCAPE převést všechny řídicí znaky v *lpszUrl* na skutečné hodnoty po analýze. (Před Visual C++ 2005 ATL_URL_DECODE převést všechny řídicí znaky před dokončením analýzy.)

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="createurl"></a>  CUrl::CreateUrl

Tato metoda vytvoří řetězec adresy URL z polí objekt CUrl komponenty.

```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```

### <a name="parameters"></a>Parametry

*lpszUrl*  
Vyrovnávací paměti řetězce pro uložení kompletního řetězce adresy URL.

*pdwMaxLength*  
Maximální délka *lpszUrl* vyrovnávací paměti pro řetězec.

*dwFlags*  
Zadejte ATL_URL_ESCAPE převést všechny řídicí znaky v *lpszUrl* na skutečné hodnoty.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda přidá jeho jednotlivých polí. aby bylo možné vytvořit kompletního řetězce adresy URL v následujícím formátu:

**\<schéma > ://\<uživatele >:\<předat > @\<domény >:\<port >\<cesta >\<Další >**

Při volání této metody *pdwMaxLength* parametr by měl obsahovat zpočátku maximální délka vyrovnávací paměti pro řetězec odkazuje *lpszUrl* parametru. Hodnota *pdwMaxLength* parametr aktualizuje skutečnou délku řetězce adresy URL.

### <a name="example"></a>Příklad

Tento příklad ukazuje vytvoření objektu CUrl a načítání jeho řetězce adresy URL

[!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]

##  <a name="curl"></a>  CUrl::CUrl

Konstruktor

```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Parametry

*urlThat*  
`CUrl` Objektu, který chcete zkopírovat do vytvořit adresu URL.

##  <a name="dtor"></a>  CUrl:: ~ CUrl

Destruktor.

```
~CUrl() throw();
```

##  <a name="getextrainfo"></a>  CUrl::GetExtraInfo

Voláním této metody lze získat další informace (například *text* nebo # *text*) z adresy URL.

```
inline LPCTSTR GetExtraInfo() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí řetězec obsahující další informace.

##  <a name="getextrainfolength"></a>  CUrl::GetExtraInfoLength

Volat tuto metodu za účelem získání délky dodatečné informace (například *text* nebo # *text*) pro načtení z adresy URL.

```
inline DWORD GetExtraInfoLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délku řetězce, který obsahuje další informace.

##  <a name="gethostname"></a>  CUrl::GetHostName

Volejte tuto metodu za účelem získání názvu hostitele z adresy URL.

```
inline LPCTSTR GetHostName() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí název hostitele.

##  <a name="gethostnamelength"></a>  CUrl::GetHostNameLength

Volejte tuto metodu za účelem získání délky názvu hostitele.

```
inline DWORD GetHostNameLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délka názvu hostitele.

##  <a name="getpassword"></a>  CUrl::GetPassword

Volejte tuto metodu za účelem získání hesla z adresy URL.

```
inline LPCTSTR GetPassword() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí heslo.

##  <a name="getpasswordlength"></a>  CUrl::GetPasswordLength

Volejte tuto metodu za účelem získání délky hesla.

```
inline DWORD GetPasswordLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délku hesla.

##  <a name="getportnumber"></a>  CUrl::GetPortNumber

Volejte tuto metodu za účelem získání číslo portu.

```
inline ATL_URL_PORT GetPortNumber() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí číslo portu.

##  <a name="getscheme"></a>  CUrl::GetScheme

Volejte tuto metodu za účelem získání schéma adresy URL.

```
inline ATL_URL_SCHEME GetScheme() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí [ATL_URL_SCHEME](atl-url-scheme-enum.md) hodnotu popisující schéma adresy URL.

##  <a name="getschemename"></a>  CUrl::GetSchemeName

Volejte tuto metodu za účelem získání názvu schéma adresy URL.

```
inline LPCTSTR GetSchemeName() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí název schéma adresy URL (například "http" nebo "ftp").

##  <a name="getschemenamelength"></a>  CUrl::GetSchemeNameLength

Volejte tuto metodu za účelem získání délky název schéma adresy URL.

```
inline DWORD GetSchemeNameLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délku názvu schéma adresy URL.

##  <a name="geturllength"></a>  CUrl::GetUrlLength

Volejte tuto metodu za účelem získání délky adresy URL.

```
inline DWORD GetUrlLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délku adresy URL.

##  <a name="geturlpath"></a>  CUrl::GetUrlPath

Volejte tuto metodu za účelem získání cesty adresy URL.

```
inline LPCTSTR GetUrlPath() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrací cestu adresy URL.

##  <a name="geturlpathlength"></a>  CUrl::GetUrlPathLength

Volejte tuto metodu za účelem získání délky cesty adresy URL.

```
inline DWORD GetUrlPathLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délku cesty adresy URL.

##  <a name="getusername"></a>  CUrl::GetUserName

Volejte tuto metodu za účelem získání uživatelského jména z adresy URL.

```
inline LPCTSTR GetUserName() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí uživatelské jméno.

##  <a name="getusernamelength"></a>  CUrl::GetUserNameLength

Volejte tuto metodu za účelem získání délky uživatelské jméno.

```
inline DWORD GetUserNameLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délka jména uživatele.

##  <a name="operator_eq"></a>  CUrl::operator =

Přiřadí zadaný `CUrl` objektů na aktuální `CUrl` objektu.

```
CUrl& operator= (const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Parametry

*urlThat*  
`CUrl` Objektu, který chcete zkopírovat do aktuálního objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na aktuální objekt.

##  <a name="setextrainfo"></a>  CUrl::SetExtraInfo

Voláním této metody lze nastavit další informace (například *text* nebo # *text*) adresy URL.

```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```

### <a name="parameters"></a>Parametry

*lpszInfo*  
Řetězec obsahující další informace, včetně v adrese URL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="sethostname"></a>  CUrl::SetHostName

Voláním této metody lze nastavit název hostitele.

```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```

### <a name="parameters"></a>Parametry

*lpszHost*  
Název hostitele.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="setpassword"></a>  CUrl::SetPassword

Voláním této metody lze nastavit heslo.

```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```

### <a name="parameters"></a>Parametry

*lpszPass*  
Heslo.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="setportnumber"></a>  CUrl::SetPortNumber

Voláním této metody nastavte číslo portu.

```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```

### <a name="parameters"></a>Parametry

*nPrt*  
Číslo portu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="setscheme"></a>  CUrl::SetScheme

Voláním této metody nastavte schéma adresy URL.

```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```

### <a name="parameters"></a>Parametry

*nScheme*  
Jeden z [ATL_URL_SCHEME](atl-url-scheme-enum.md) hodnoty pro schéma.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Schéma můžete také nastavit podle názvu (viz [CUrl::SetSchemeName](#setschemename)).

##  <a name="setschemename"></a>  CUrl::SetSchemeName

Voláním této metody nastavte název schéma adresy URL.

```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```

### <a name="parameters"></a>Parametry

*lpszSchm*  
Název schématu adresy URL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Schéma můžete nastavit také pomocí [ATL_URL_SCHEME](atl-url-scheme-enum.md) konstantní (viz [CUrl::SetScheme](#setscheme)).

##  <a name="seturlpath"></a>  CUrl::SetUrlPath

Volejte tuto metodu použijte k nastavení cesty adresy URL.

```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```

### <a name="parameters"></a>Parametry

*lpszPath*  
Cesta adresy URL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

##  <a name="setusername"></a>  CUrl::SetUserName

Voláním této metody nastavte uživatelské jméno.

```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```

### <a name="parameters"></a>Parametry

*lpszUser*  
Uživatelské jméno

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

## <a name="see-also"></a>Viz také

[Třídy](../../atl/reference/atl-classes.md)
