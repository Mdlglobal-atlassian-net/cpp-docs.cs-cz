---
title: Třída CUrl
ms.date: 05/06/2019
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
helpviewer_keywords:
- CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
ms.openlocfilehash: 3468e17b031d0a72bc56d915c689fbe4c78859e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330470"
---
# <a name="curl-class"></a>Třída CUrl

Tato třída představuje adresu URL. Umožňuje manipulovat s každým prvkem adresy URL nezávisle na ostatních, zda je analýza existujícího řetězce adresy URL nebo vytvoření řetězce od začátku.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CUrl
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CUrl::CUrl](#curl)|Konstruktor|
|[CUrl::~CUrl](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CUrl::Kanoián](#canonicalize)|Volánítéto metody převést řetězec URL do kanonického formuláře.|
|[CUrl::Vymazat](#clear)|Voláním této metody zrušte všechna pole adresy URL.|
|[CUrl::CrackUrl](#crackurl)|Volání této metody dekódovat a analyzovat adresu URL.|
|[CUrl::Vytvořit adresu Url](#createurl)|Volání této metody k vytvoření adresy URL.|
|[CUrl::ZískatextraInfo](#getextrainfo)|Volání této metody získat další informace (například *text* nebo # *text)* z adresy URL.|
|[CUrl::GetExtraInfoLength](#getextrainfolength)|Volání této metody získat délku další informace (například *text* nebo # *text)* načíst z adresy URL.|
|[curl::GethostName](#gethostname)|Volání této metody získat název hostitele z adresy URL.|
|[curl::GetHostNameLength](#gethostnamelength)|Volání této metody získat délku názvu hostitele.|
|[CUrl::GetPassword](#getpassword)|Volání této metody získat heslo z adresy URL.|
|[CUrl::GetPasswordLength](#getpasswordlength)|Volání této metody získat délku hesla.|
|[CUrl::Číslo GetPort](#getportnumber)|Volání této metody získat číslo portu z hlediska ATL_URL_PORT.|
|[CUrl::GetScheme](#getscheme)|Volání této metody získat schéma URL.|
|[CUrl::GetSchemeName](#getschemename)|Volání této metody získat název schématu ADRESY URL.|
|[CUrl::GetSchemeNameLength](#getschemenamelength)|Volání této metody získat délku názvu schématu URL.|
|[CUrl::GetUrlLength](#geturllength)|Volání této metody získat délku adresy URL.|
|[CUrl::GetUrlPath](#geturlpath)|Volání této metody získat cestu URL.|
|[CUrl::GetUrlPathLength](#geturlpathlength)|Volání této metody získat délku cesty URL.|
|[CUrl::GetUserName](#getusername)|Volání této metody získat uživatelské jméno z adresy URL.|
|[CUrl::GetUserNameLength](#getusernamelength)|Volání této metody získat délku uživatelského jména.|
|[CUrl::SetExtraInfo](#setextrainfo)|Volání této metody nastavit další informace (například *text* nebo # *text)* adresy URL.|
|[curl::SetHostName](#sethostname)|Volání této metody nastavit název hostitele.|
|[CUrl::SetPassword](#setpassword)|Volání této metody nastavit heslo.|
|[CUrl::SetPortNumber](#setportnumber)|Volání této metody nastavit číslo portu z hlediska ATL_URL_PORT.|
|[CUrl::SetScheme](#setscheme)|Volání této metody nastavit schéma adresy URL.|
|[CUrl::SetSchemeName](#setschemename)|Volánítéto metody nastavit název schématu ADRESY URL.|
|[CUrl::SetUrlPath](#seturlpath)|Volánítéto metody nastavit cestu URL.|
|[CUrl::SetUserName](#setusername)|Volání této metody nastavit uživatelské jméno.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CUrl::operátor =](#operator_eq)|Přiřadí zadaný `CUrl` objekt `CUrl` k aktuálnímu objektu.|

## <a name="remarks"></a>Poznámky

`CUrl`umožňuje manipulovat s poli adresy URL, například s cestou nebo číslem portu. `CUrl`rozumí adresám URL následujícího formuláře:

\<Schéma\<>:// uživatelské\<jméno \@ \<>: Heslo\<>>\<HostName: PortNumber>/ UrlPath>\<ExtraInfo>

(Některá pole jsou nepovinná.) Zvažte například tuto adresu URL:

`http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents`

[CUrl::CrackUrl](#crackurl) analyzuje to takto:

- Schéma: "http" nebo [ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)

- Uživatelské jméno: "někdo"

- Heslo: "tajné"

- HostName:`www.microsoft.com`"

- Číslo portu: 80

- UrlPath: "visualc/stuff.htm"

- ExtraInfo: "#contents"

Chcete-li manipulovat s polem UrlPath (například), použijte [geturlpath](#geturlpath), [GetUrlPathLength](#geturlpathlength)a [SetUrlPath](#seturlpath). Pomocí [adresy CreateUrl](#createurl) byste vytvořili úplný řetězec adresy URL.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

## <a name="curlcanonicalize"></a><a name="canonicalize"></a>CUrl::Kanoián

Volánítéto metody převést řetězec URL do kanonického formuláře.

```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Příznaky, které řídí kanonizaci. Pokud nejsou zadány žádné příznaky (*dwFlags* = 0), metoda převede \\všechny nebezpečné znaky \\a metasekvence (například .,\ .., a ...) na únikové sekvence. *dwFlags* může být jedna z následujících hodnot:

- ATL_URL_BROWSER_MODE: Nekóduje ani nedekóduje znaky za "#" nebo "" a neodstraní koncové prázdné místo po "". Pokud tato hodnota není zadána, je zakódována celá adresa URL a je odebráno koncové prázdné místo.

- ATL_URL _DECODE: Převede všechny sekvence %XX na znaky, včetně sekvencí escape, před analýzou adresy URL.

- ATL_URL _ENCODE_PERCENT: Zakóduje všechny znaky, které se objeví. Ve výchozím nastavení nejsou znaky procenta zakódovány.

- ATL_URL _ENCODE_SPACES_ONLY: Zakóduje pouze mezery.

- ATL_URL _NO_ENCODE: Nepřevádí nebezpečné znaky na řídicí sekvence.

- ATL_URL _NO_META: Neodebere metasekvence (například "." a "..") z adresy URL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Převod na kanonický formulář zahrnuje převod nebezpečných znaků a mezer na řídicí sekvence.

## <a name="curlclear"></a><a name="clear"></a>CUrl::Vymazat

Voláním této metody zrušte všechna pole adresy URL.

```
inline void Clear() throw();
```

## <a name="curlcrackurl"></a><a name="crackurl"></a>CUrl::CrackUrl

Volání této metody dekódovat a analyzovat adresu URL.

```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*lpszUrl*<br/>
Adresa URL.

*dwFlags*<br/>
Zadejte ATL_URL_DECODE nebo ATL_URL_ESCAPE převést všechny řídicí znaky v *lpszUrl* na jejich skutečné hodnoty po parsingu. (Před visual c++ 2005 ATL_URL_DECODE před analýzou převést všechny řídicí znaky.)

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="curlcreateurl"></a><a name="createurl"></a>CUrl::Vytvořit adresu Url

Tato metoda vytvoří řetězec ADRESY URL z polí komponent objektu CUrl.

```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```

### <a name="parameters"></a>Parametry

*lpszUrl*<br/>
Vyrovnávací paměť řetězce pro uložení úplného řetězce ADRESY URL.

*pdwMaxLength*<br/>
Maximální délka vyrovnávací paměti řetězce *lpszUrl.*

*dwFlags*<br/>
Zadejte ATL_URL_ESCAPE převést všechny řídicí znaky v *lpszUrl* na jejich skutečné hodnoty.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Tato metoda připojí jeho jednotlivá pole, aby bylo možné vytvořit celý řetězec URL pomocí následujícího formátu:

**\<schéma\<>://>\<uživatele: předat \@ \<>> domény:\<cesta>portu \<>\<další>**

Při volání této metody by měl parametr *pdwMaxLength* zpočátku obsahovat maximální délku vyrovnávací paměti řetězce, na kterou odkazuje parametr *lpszUrl.* Hodnota parametru *pdwMaxLength* bude aktualizována skutečnou délkou řetězce URL.

### <a name="example"></a>Příklad

Tato ukázka ukazuje vytvoření curl objektu a načítání jeho řetězec URL

[!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]

## <a name="curlcurl"></a><a name="curl"></a>CUrl::CUrl

Konstruktor

```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Parametry

*urlThat*<br/>
Objekt, `CUrl` který chcete zkopírovat, chcete-li vytvořit adresu URL.

## <a name="curlcurl"></a><a name="dtor"></a>CUrl::~CUrl

Destruktor.

```
~CUrl() throw();
```

## <a name="curlgetextrainfo"></a><a name="getextrainfo"></a>CUrl::ZískatextraInfo

Volání této metody získat další informace (například *text* nebo # *text)* z adresy URL.

```
inline LPCTSTR GetExtraInfo() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí řetězec obsahující další informace.

## <a name="curlgetextrainfolength"></a><a name="getextrainfolength"></a>CUrl::GetExtraInfoLength

Volání této metody získat délku další informace (například *text* nebo # *text)* načíst z adresy URL.

```
inline DWORD GetExtraInfoLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délku řetězce obsahujícího další informace.

## <a name="curlgethostname"></a><a name="gethostname"></a>curl::GethostName

Volání této metody získat název hostitele z adresy URL.

```
inline LPCTSTR GetHostName() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí název hostitele.

## <a name="curlgethostnamelength"></a><a name="gethostnamelength"></a>curl::GetHostNameLength

Volání této metody získat délku názvu hostitele.

```
inline DWORD GetHostNameLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délku názvu hostitele.

## <a name="curlgetpassword"></a><a name="getpassword"></a>CUrl::GetPassword

Volání této metody získat heslo z adresy URL.

```
inline LPCTSTR GetPassword() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí heslo.

## <a name="curlgetpasswordlength"></a><a name="getpasswordlength"></a>CUrl::GetPasswordLength

Volání této metody získat délku hesla.

```
inline DWORD GetPasswordLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délku hesla.

## <a name="curlgetportnumber"></a><a name="getportnumber"></a>CUrl::Číslo GetPort

Volání této metody získat číslo portu.

```
inline ATL_URL_PORT GetPortNumber() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí číslo portu.

## <a name="curlgetscheme"></a><a name="getscheme"></a>CUrl::GetScheme

Volání této metody získat schéma URL.

```
inline ATL_URL_SCHEME GetScheme() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí [hodnotu ATL_URL_SCHEME](atl-url-scheme-enum.md) popisující schéma adresy URL.

## <a name="curlgetschemename"></a><a name="getschemename"></a>CUrl::GetSchemeName

Volání této metody získat název schématu ADRESY URL.

```
inline LPCTSTR GetSchemeName() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí název schématu adresy URL (například "http" nebo "ftp").

## <a name="curlgetschemenamelength"></a><a name="getschemenamelength"></a>CUrl::GetSchemeNameLength

Volání této metody získat délku názvu schématu URL.

```
inline DWORD GetSchemeNameLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délku názvu schématu adresy URL.

## <a name="curlgeturllength"></a><a name="geturllength"></a>CUrl::GetUrlLength

Volání této metody získat délku adresy URL.

```
inline DWORD GetUrlLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délku adresy URL.

## <a name="curlgeturlpath"></a><a name="geturlpath"></a>CUrl::GetUrlPath

Volání této metody získat cestu URL.

```
inline LPCTSTR GetUrlPath() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí cestu url.

## <a name="curlgeturlpathlength"></a><a name="geturlpathlength"></a>CUrl::GetUrlPathLength

Volání této metody získat délku cesty URL.

```
inline DWORD GetUrlPathLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délku cesty URL.

## <a name="curlgetusername"></a><a name="getusername"></a>CUrl::GetUserName

Volání této metody získat uživatelské jméno z adresy URL.

```
inline LPCTSTR GetUserName() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí uživatelské jméno.

## <a name="curlgetusernamelength"></a><a name="getusernamelength"></a>CUrl::GetUserNameLength

Volání této metody získat délku uživatelského jména.

```
inline DWORD GetUserNameLength() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí délku uživatelského jména.

## <a name="curloperator-"></a><a name="operator_eq"></a>CUrl::operátor =

Přiřadí zadaný `CUrl` objekt `CUrl` k aktuálnímu objektu.

```
CUrl& operator= (const CUrl& urlThat) throw();
```

### <a name="parameters"></a>Parametry

*urlThat*<br/>
Objekt, `CUrl` který chcete zkopírovat do aktuálního objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí odkaz na aktuální objekt.

## <a name="curlsetextrainfo"></a><a name="setextrainfo"></a>CUrl::SetExtraInfo

Volání této metody nastavit další informace (například *text* nebo # *text)* adresy URL.

```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```

### <a name="parameters"></a>Parametry

*lpszInfo*<br/>
Řetězec obsahující další informace, které mají být zahrnuty do adresy URL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="curlsethostname"></a><a name="sethostname"></a>curl::SetHostName

Volání této metody nastavit název hostitele.

```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```

### <a name="parameters"></a>Parametry

*lpszHost*<br/>
Název hostitele.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="curlsetpassword"></a><a name="setpassword"></a>CUrl::SetPassword

Volání této metody nastavit heslo.

```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```

### <a name="parameters"></a>Parametry

*lpszPass*<br/>
Heslo.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="curlsetportnumber"></a><a name="setportnumber"></a>CUrl::SetPortNumber

Volání této metody nastavit číslo portu.

```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```

### <a name="parameters"></a>Parametry

*nPrt*<br/>
Číslo portu

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="curlsetscheme"></a><a name="setscheme"></a>CUrl::SetScheme

Volání této metody nastavit schéma adresy URL.

```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```

### <a name="parameters"></a>Parametry

*nSchéma*<br/>
Jedna z [ATL_URL_SCHEME](atl-url-scheme-enum.md) hodnot pro schéma.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Schéma můžete také nastavit podle názvu (viz [CUrl::SetSchemeName](#setschemename)).

## <a name="curlsetschemename"></a><a name="setschemename"></a>CUrl::SetSchemeName

Volánítéto metody nastavit název schématu ADRESY URL.

```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```

### <a name="parameters"></a>Parametry

*lpszSchm*<br/>
Název schématu adresy URL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Schéma můžete také nastavit pomocí [ATL_URL_SCHEME](atl-url-scheme-enum.md) konstanty (viz [CUrl::SetScheme](#setscheme)).

## <a name="curlseturlpath"></a><a name="seturlpath"></a>CUrl::SetUrlPath

Volánítéto metody nastavit cestu URL.

```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
Cesta url.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="curlsetusername"></a><a name="setusername"></a>CUrl::SetUserName

Volání této metody nastavit uživatelské jméno.

```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```

### <a name="parameters"></a>Parametry

*lpszUser*<br/>
Uživatelské jméno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

## <a name="see-also"></a>Viz také

[Třídy](../../atl/reference/atl-classes.md)
