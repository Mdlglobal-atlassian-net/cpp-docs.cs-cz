---
title: Funkce nástrojů ATL HTTP
ms.date: 11/04/2016
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
ms.openlocfilehash: ca6dfdfb02f5ef629c6eb523744260f177a3309b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497964"
---
# <a name="atl-http-utility-functions"></a>Funkce nástrojů ATL HTTP

Tyto funkce podporují manipulaci s adresami URL.

|||
|-|-|
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalizes adresu URL, která zahrnuje převod nebezpečných znaků a mezer do řídicích sekvencí.|
|[AtlCombineUrl](#atlcombineurl)|Kombinuje základní adresu URL a relativní adresu URL do jedné kanonické adresy URL.|
|[AtlEscapeUrl](#atlescapeurl)|Převede všechny nezabezpečené znaky na řídicí sekvence.|
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|Získá výchozí číslo portu přidružené ke konkrétnímu protokolu sítě Internet nebo schématu.|
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|Určuje, zda je znak bezpečný pro použití v adrese URL.|
|[AtlUnescapeUrl](#atlunescapeurl)|Převede řídicí znaky zpět na původní hodnoty.|
|[RGBToHtml](#rgbtohtml)|Převede hodnotu [COLORREF](/windows/win32/gdi/colorref) na text HTML odpovídající této hodnotě barvy.|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|Voláním této funkce převedete systémový čas na řetězec ve formátu vhodném pro použití v hlavičkách protokolu HTTP.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil. h

## <a name="atlcanonicalizeurl"></a> AtlCanonicalizeUrl

Voláním této funkce převedete adresu URL na kanonický tvar, přičemž problematické znaky a mezery se převedou na řídicí sekvence.

```cpp
inline BOOL AtlCanonicalizeUrl(
   LPCTSTR szUrl,
   LPTSTR szCanonicalized,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*szUrl*<br/>
Adresa URL, která má být kanonicka.

*szCanonicalized*<br/>
Vyrovnávací paměť přidělená volajícímu pro příjem kanonické adresy URL

*pdwMaxLength*<br/>
Ukazatel na proměnnou, která obsahuje délku ve znacích *szCanonicalized*. Pokud je funkce úspěšná, proměnná přijme počet znaků zapsaných do vyrovnávací paměti včetně ukončujícího znaku null. Pokud dojde k chybě funkce, proměnná obdrží požadovanou délku v bajtech vyrovnávací paměti včetně místa pro ukončující znak null.

*dwFlags*<br/>
ATL_URL příznaky ovládající chování této funkce.

- ATL_URL_BROWSER_MODE nekóduje ani dekóduje znaky za znakem "#" nebo "?" a neodebírá koncovou mezeru za znakem "?". Pokud tato hodnota není zadaná, celá adresa URL se zakóduje a na konci se odeberou prázdné znaky.

- ATL_URL_DECODE převede všechny sekvence% XX na znaky, včetně řídicích sekvencí, před analýzou adresy URL.

- ATL_URL_ENCODE_PERCENT zakóduje všechny zjištěné znaky procent. Ve výchozím nastavení nejsou znaménka procent kódována.

- ATL_URL_ENCODE_SPACES_ONLY zakóduje pouze mezery.

- ATL_URL_ESCAPE převede všechny řídicí sekvence (% XX) na odpovídající znaky.

- ATL_URL_NO_ENCODE nepřevádí nebezpečné znaky na řídicí sekvence.

- ATL_URL_NO_META z adresy URL neodebere meta sekvence (například "." a "..").

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Se chová jako aktuální verze [InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw) , ale nevyžaduje instalaci rozhraní WinInet nebo Internet Explorer.

## <a name="atlcombineurl"></a>AtlCombineUrl

Voláním této funkce zkombinujete základní a relativní adresu URL do jedné kanonické adresy URL.

```cpp
inline BOOL AtlCombineUrl(
   LPCTSTR szBaseUrl,
   LPCTSTR szRelativeUrl,
   LPTSTR szBuffer,
   DWORD* pdwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*szBaseUrl*<br/>
Základní adresa URL

*szRelativeUrl*<br/>
Adresa URL relativní k základní adrese URL

*szBuffer*<br/>
Vyrovnávací paměť přidělená volajícímu pro příjem kanonické adresy URL

*pdwMaxLength*<br/>
Ukazatel na proměnnou, která obsahuje délku ve znacích *szBuffer*. Pokud je funkce úspěšná, proměnná přijme počet znaků zapsaných do vyrovnávací paměti včetně ukončujícího znaku null. Pokud dojde k chybě funkce, proměnná obdrží požadovanou délku v bajtech vyrovnávací paměti včetně místa pro ukončující znak null.

*dwFlags*<br/>
Příznaky ovládající chování této funkce. Viz [AtlCanonicalizeUrl](#atlcanonicalizeurl).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Se chová jako aktuální verze [InternetCombineUrl](/windows/win32/api/wininet/nf-wininet-internetcombineurlw) , ale nevyžaduje instalaci rozhraní WinInet nebo Internet Explorer.

## <a name="atlescapeurl"></a>AtlEscapeUrl

Voláním této funkce převedete všechny problematické znaky na řídicí sekvence.

```cpp
inline BOOL AtlEscapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();

inline BOOL AtlEscapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   DWORD* pdwStrLen,
   DWORD dwMaxLength,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*lpszStringIn*<br/>
Adresa URL, která má být převedena.

*lpszStringOut*<br/>
Vyrovnávací paměť přidělená volajícímu, do které bude napsána převedená adresa URL.

*pdwStrLen*<br/>
Ukazatel na proměnnou DWORD. Pokud je funkce úspěšná, *pdwStrLen* přijme počet znaků zapsaných do vyrovnávací paměti včetně ukončujícího znaku null. Pokud dojde k chybě funkce, proměnná obdrží požadovanou délku v bajtech vyrovnávací paměti včetně místa pro ukončující znak null. Při použití verze s širším znakem této metody *pdwStrLen* přijímá počet požadovaných znaků, nikoli počet bajtů.

*dwMaxLength*<br/>
Velikost *lpszStringOut*vyrovnávací paměti.

*dwFlags*<br/>
ATL_URL příznaky ovládající chování této funkce. Možné hodnoty najdete v tématu [ATLCanonicalizeUrl](#atlcanonicalizeurl) .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

## <a name="atlgetdefaulturlport"></a>AtlGetDefaultUrlPort

Voláním této funkce získáte výchozí číslo portu přidružené ke konkrétnímu protokolu nebo schématu Internetu.

```
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();
```

### <a name="parameters"></a>Parametry

*m_nScheme*<br/>
Hodnota [ATL_URL_SCHEME](atl-url-scheme-enum.md) identifikující schéma, pro které chcete získat číslo portu.

### <a name="return-value"></a>Návratová hodnota

[ATL_URL_PORT](atl-typedefs.md#atl_url_port) přidružené k zadanému schématu nebo ATL_URL_INVALID_PORT_NUMBER, pokud schéma není rozpoznáno.

## <a name="atlisunsafeurlchar"></a> AtlIsUnsafeUrlChar

Voláním této funkce zjistíte, zda lze znak bezpečně použít v adrese URL.

```
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();
```

### <a name="parameters"></a>Parametry

*chIn*<br/>
Znak, který má být testován pro bezpečnost.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je vstupní znak nebezpečný, jinak FALSE.

### <a name="remarks"></a>Poznámky

Znaky, které by neměly být použity v adresách URL, lze testovat pomocí této funkce a převést pomocí [AtlCanonicalizeUrl](#atlcanonicalizeurl).

## <a name="atlunescapeurl"></a>AtlUnescapeUrl

Voláním této funkce převedete řídicí znaky zpět na jejich původní hodnoty.

```cpp
inline BOOL AtlUnescapeUrl(
   LPCSTR szStringIn,
   LPSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();

inline BOOL AtlUnescapeUrl(
   LPCWSTR szStringIn,
   LPWSTR szStringOut,
   LPDWORD pdwStrLen,
   DWORD dwMaxLength) throw();
```

### <a name="parameters"></a>Parametry

*lpszStringIn*<br/>
Adresa URL, která má být převedena.

*lpszStringOut*<br/>
Vyrovnávací paměť přidělená volajícímu, do které bude napsána převedená adresa URL.

*pdwStrLen*<br/>
Ukazatel na proměnnou DWORD. Pokud je funkce úspěšná, proměnná přijme počet znaků zapsaných do vyrovnávací paměti včetně ukončujícího znaku null. Pokud dojde k chybě funkce, proměnná obdrží požadovanou délku v bajtech vyrovnávací paměti včetně místa pro ukončující znak null.

*dwMaxLength*<br/>
Velikost *lpszStringOut*vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Obrátí proces převodu, který používá [AtlEscapeUrl](#atlescapeurl).

## <a name="rgbtohtml"></a> RGBToHtml

Převede hodnotu [COLORREF](/windows/win32/gdi/colorref) na text HTML odpovídající této hodnotě barvy.

```cpp
bool inline RGBToHtml(
   COLORREF color,
   LPTSTR pbOut,
   long nBuffer);
```

### <a name="parameters"></a>Parametry

*barevných*<br/>
Hodnota barvy RGB.

*pbOut*<br/>
Vyrovnávací paměť přidělená volajícímu pro příjem textu pro hodnotu barvy HTML. Vyrovnávací paměť musí mít mezeru alespoň pro 8 znaků, včetně mezery pro ukončovací znak null).

*nBuffer*<br/>
Velikost vyrovnávací paměti v bajtech (včetně místa pro ukončovací znak null).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Hodnota barvy HTML je znak křížku následovaný hexadecimální hodnotou o hodnotě 6 číslic pomocí 2 číslic pro každou z červených, zelených a modrých komponent barvy (například #FFFFFF je bílá).

## <a name="systemtimetohttpdate"></a> SystemTimeToHttpDate

Voláním této funkce převedete systémový čas na řetězec ve formátu vhodném pro použití v hlavičkách protokolu HTTP.

```cpp
inline void SystemTimeToHttpDate(
   const SYSTEMTIME& st,
   CStringA& strTime);
```

### <a name="parameters"></a>Parametry

*st*<br/>
Systémový čas, který má být získán jako řetězec formátu HTTP.

*strTime*<br/>
Odkaz na proměnnou řetězce pro příjem data a času protokolu HTTP, jak je definován v dokumentu RFC[https://www.ietf.org/rfc/rfc2616.txt](https://www.ietf.org/rfc/rfc2616.txt)2616 () a RFC[https://www.ietf.org/rfc/rfc1123.txt](https://www.ietf.org/rfc/rfc1123.txt)1123 ().

## <a name="see-also"></a>Viz také:

[Charakteristiky](../active-template-library-atl-concepts.md)<br/>
[Desktopové komponenty ATL objektů COM](../atl-com-desktop-components.md)<br/>
[InternetCanonicalizeUrl](/windows/win32/api/wininet/nf-wininet-internetcanonicalizeurlw)
