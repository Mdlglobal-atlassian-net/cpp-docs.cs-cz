---
title: Funkce nástrojů ATL HTTP
ms.date: 11/04/2016
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
ms.openlocfilehash: 8f26a23190f9358ff8913e35f5ed7274c8b274ea
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449960"
---
# <a name="atl-http-utility-functions"></a>Funkce nástrojů ATL HTTP

Tyto funkce podporují zpracování adresy URL.

|||
|-|-|
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalizes na adresu URL, která zahrnuje převod do řídicích sekvencí problematické znaky a mezery.|
|[AtlCombineUrl](#atlcombineurl)|Kombinuje základní adresu URL a relativní adresu URL do jedné kanonické adresy URL.|
|[AtlEscapeUrl](#atlescapeurl)|Převede všechny problematické znaky na řídicí sekvence.|
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|Získá výchozí číslo portu přidružené k určité Internet protocol nebo schéma.|
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|Určuje, zda znak je bezpečný pro použití v adrese URL.|
|[AtlUnescapeUrl](#atlunescapeurl)|Převede uvozen řídicími znaky, znaky zpět na původní hodnoty.|
|[RGBToHtml](#rgbtohtml)|Převede [COLORREF](/windows/desktop/gdi/colorref) hodnotu na text HTML odpovídající hodnotě této barvy.|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|Voláním této funkce převedete systémový čas na řetězec ve formátu vhodném pro použití v hlavičkách protokolu HTTP.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

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
Adresa URL chcete kanonizovat.

*szCanonicalized*<br/>
Volající – přidělené vyrovnávací paměti pro příjem kanonizovaného adresy URL.

*pdwMaxLength*<br/>
Ukazatel na proměnnou, která obsahuje délky ve znacích *szCanonicalized*. Pokud funkce uspěje, proměnná přijímá počet znaků zapsaných do vyrovnávací paměti, včetně ukončujícího znaku null. Pokud funkce selže, obdrží proměnné má požadovanou délku v bajtech vyrovnávací paměti, včetně místo pro ukončující znak null.

*dwFlags*<br/>
Příznaky ATL_URL řízení chování této funkce.

- ATL_URL_BROWSER_MODE nepodporuje kódování nebo dekódování znaků za "#" nebo "?" a nedojde k odstranění prázdný znak po "?". Pokud tato hodnota není zadaná, je zakódovaný celou adresu URL a odebrat koncové prázdné znaky.

- ATL_URL_DECODE převede všechny % XX sekvence znaků, včetně řídicí sekvence, než adresa URL se zpracuje.

- Zakóduje ATL_URL_ENCODE_PERCENT došlo k jakékoli procenta. Ve výchozím nastavení nejsou kódovaný procenta.

- Zakóduje ATL_URL_ENCODE_SPACES_ONLY pouze mezery.

- Převede ATL_URL_ESCAPE všechny řídicí sekvence (% XX) na jejich odpovídající znaky.

- ATL_URL_NO_ENCODE nepřevádí problematické znaky na řídicí sekvence.

- ATL_URL_NO_META neodebere meta pořadí (jako například "."a"..") z adresy URL.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Se chová jako aktuální verze [InternetCanonicalizeUrl](/windows/desktop/api/wininet/nf-wininet-internetcanonicalizeurla) ale nevyžaduje WinInet nebo Internet Explorer k instalaci.

## <a name="atlcombineurl"></a> AtlCombineUrl

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
Základní adresa URL.

*szRelativeUrl*<br/>
Adresa URL relativní k základní adrese URL.

*szBuffer*<br/>
Volající – přidělené vyrovnávací paměti pro příjem kanonizovaného adresy URL.

*pdwMaxLength*<br/>
Ukazatel na proměnnou, která obsahuje délky ve znacích *szBuffer*. Pokud funkce uspěje, proměnná přijímá počet znaků zapsaných do vyrovnávací paměti, včetně ukončujícího znaku null. Pokud funkce selže, obdrží proměnné má požadovanou délku v bajtech vyrovnávací paměti, včetně místo pro ukončující znak null.

*dwFlags*<br/>
Příznaky řízení chování této funkce. Zobrazit [AtlCanonicalizeUrl](#atlcanonicalizeurl).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Se chová jako aktuální verze [InternetCombineUrl](/windows/desktop/api/wininet/nf-wininet-internetcombineurla) ale nevyžaduje WinInet nebo Internet Explorer k instalaci.

## <a name="atlescapeurl"></a> AtlEscapeUrl

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
Adresa URL má být převeden.

*lpszStringOut*<br/>
Volající – přidělené vyrovnávací paměti do kterého budou zapsány převedený adresy URL.

*pdwStrLen*<br/>
Ukazatel na proměnnou typu DWORD. Pokud funkce uspěje, *pdwStrLen* přijímá počet znaků zapsaných do vyrovnávací paměti, včetně ukončujícího znaku null. Pokud funkce selže, obdrží proměnné má požadovanou délku v bajtech vyrovnávací paměti, včetně místo pro ukončující znak null. Při použití této metody verze širokého znaku *pdwStrLen* přijímá počet znaků, nikoli počet bajtů.

*dwMaxLength*<br/>
Velikost vyrovnávací paměti *lpszStringOut*.

*dwFlags*<br/>
Příznaky ATL_URL řízení chování této funkce. Zobrazit [ATLCanonicalizeUrl](#atlcanonicalizeurl) možných hodnot.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

## <a name="atlgetdefaulturlport"></a> AtlGetDefaultUrlPort

Voláním této funkce získáte výchozí číslo portu přidružené ke konkrétnímu protokolu nebo schématu Internetu.

```
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();
```

### <a name="parameters"></a>Parametry

*m_nScheme*<br/>
[ATL_URL_SCHEME](atl-url-scheme-enum.md) hodnotu identifikaci schéma, pro kterou chcete získat číslo portu.

### <a name="return-value"></a>Návratová hodnota

[ATL_URL_PORT](atl-typedefs.md#atl_url_port) přidružený k zadané schéma nebo ATL_URL_INVALID_PORT_NUMBER, pokud se schéma nerozpozná.

## <a name="atlisunsafeurlchar"></a> AtlIsUnsafeUrlChar

Voláním této funkce zjistíte, zda lze znak bezpečně použít v adrese URL.

```
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();
```

### <a name="parameters"></a>Parametry

*chIn*<br/>
Znak, který má být testovány z hlediska zabezpečení.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud vstupní znak je nebezpečné, FALSE, jinak.

### <a name="remarks"></a>Poznámky

Znaky, které by neměly být použití v adresách URL lze otestovat pomocí této funkce a převeden pomocí [AtlCanonicalizeUrl](#atlcanonicalizeurl).

## <a name="atlunescapeurl"></a> AtlUnescapeUrl

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
Adresa URL má být převeden.

*lpszStringOut*<br/>
Volající – přidělené vyrovnávací paměti do kterého budou zapsány převedený adresy URL.

*pdwStrLen*<br/>
Ukazatel na proměnnou typu DWORD. Pokud funkce uspěje, proměnná přijímá počet znaků zapsaných do vyrovnávací paměti, včetně ukončujícího znaku null. Pokud funkce selže, obdrží proměnné má požadovanou délku v bajtech vyrovnávací paměti, včetně místo pro ukončující znak null.

*dwMaxLength*<br/>
Velikost vyrovnávací paměti *lpszStringOut*.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Obrátí procesu převodu použil(a) [AtlEscapeUrl](#atlescapeurl).

## <a name="rgbtohtml"></a> RGBToHtml

Převede [COLORREF](/windows/desktop/gdi/colorref) hodnotu na text HTML odpovídající hodnotě této barvy.

```cpp
bool inline RGBToHtml(
   COLORREF color,
   LPTSTR pbOut,
   long nBuffer);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Hodnota barvy RGB.

*pbOut*<br/>
Volající – přidělené vyrovnávací paměť pro přijetí textu pro hodnota barvy HTML. Vyrovnávací paměť musí mít prostoru pro alespoň 8 znaků, včetně místa pro ukončovacího znaku null).

*nBuffer*<br/>
Velikost v bajtech vyrovnávací paměti (včetně místa pro ukončovacího znaku null).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Hodnotu barvy HTML je znak křížku, za nímž následuje 6místným číselným šestnáctková hodnota používat číslice od 2 pro všechny komponenty červené, zelené a modré barvy (třeba #FFFFFF je bílé).

## <a name="systemtimetohttpdate"></a> SystemTimeToHttpDate

Voláním této funkce převedete systémový čas na řetězec ve formátu vhodném pro použití v hlavičkách protokolu HTTP.

```cpp
inline void SystemTimeToHttpDate(
   const SYSTEMTIME& st,
   CStringA& strTime);
```

### <a name="parameters"></a>Parametry

*st*<br/>
Systémový čas získána jako řetězec ve formátu HTTP.

*strTime*<br/>
Odkaz na proměnnou s řetězcem přijímat HTTP datum a čas, jak jsou definovány v dokumentu RFC 2616 ([https://www.ietf.org/rfc/rfc2616.txt](https://www.ietf.org/rfc/rfc2616.txt)) a RFC 1123 ([https://www.ietf.org/rfc/rfc1123.txt](https://www.ietf.org/rfc/rfc1123.txt)).

## <a name="see-also"></a>Viz také:

[Koncepty](../active-template-library-atl-concepts.md)<br/>
[Desktopové komponenty ATL objektů COM](../atl-com-desktop-components.md)<br/>
[InternetCanonicalizeUrl](/windows/desktop/api/wininet/nf-wininet-internetcanonicalizeurla)
