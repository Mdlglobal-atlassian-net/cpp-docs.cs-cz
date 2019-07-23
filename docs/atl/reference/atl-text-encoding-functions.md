---
title: Funkce kódování textu ATL
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlGetHexValue
- atlbase/ATL::AtlGetVersion
- atlenc/ATL::AtlHexDecode
- atlenc/ATL::AtlHexDecodeGetRequiredLength
- atlenc/ATL::AtlHexEncode
- atlenc/ATL::AtlHexEncodeGetRequiredLength
- atlenc/ATL::AtlHexValue
- atlenc/ATL::BEncode
- atlenc/ATL::BEncodeGetRequiredLength
- atlenc/ATL::EscapeXML
- atlenc/ATL::GetExtendedChars
- atlenc/ATL::IsExtendedChar
- atlenc/ATL::QEncode
- atlenc/ATL::QEncodeGetRequiredLength
- atlenc/ATL::QPDecode
- atlenc/ATL::QPDecodeGetRequiredLength
- atlenc/ATL::QPEncode
- atlenc/ATL::QPEncodeGetRequiredLength
- atlenc/ATL::UUDecode
- atlenc/ATL::UUDecodeGetRequiredLength
- atlenc/ATL::UUEncode
- atlenc/ATL::UUEncodeGetRequiredLength
ms.assetid: 2ae1648b-2b87-4112-92aa-0069fcfd23da
ms.openlocfilehash: 1380d33c485c1ac895558bbcaf86c902c6074cd4
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375891"
---
# <a name="atl-text-encoding-functions"></a>Funkce kódování textu ATL

Tyto funkce podporují kódování textu a dekódování.

|||
|-|-|
|[AtlGetHexValue](#atlgethexvalue)|Voláním této funkce získáte číselnou hodnotu šestnáctkové číslice.|
|[AtlGetVersion](#atlgetversion)|Voláním této funkce získáte verzi knihovny ATL, kterou používáte.  |
|[AtlHexDecode](#atlhexdecode)|Dekóduje řetězec dat, který byl kódován jako šestnáctkový text, například předchozí volání [AtlHexEncode](#atlhexencode).|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z šestnáctkově zakódovaného řetězce zadané délky.|
|[AtlHexEncode](#atlhexencode)|Voláním této funkce zakódujete data jako řetězec šestnáctkového textu.|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|
|[AtlHexValue](#atlhexvalue)|Voláním této funkce získáte číselnou hodnotu šestnáctkové číslice. |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|Voláním této funkce převedete řetězec s kódováním Unicode na UTF-8. |
|[BEncode](#bencode)|Voláním této funkce převedete data pomocí kódování B.|
|[BEncodeGetRequiredLength](#bencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|
|[EscapeXML](#escapexml)|Voláním této funkce převedete znaky, které jsou problematické pro použití v kódu XML, na jejich bezpečné ekvivalenty.|
|[GetExtendedChars](#getextendedchars)|Voláním této funkce získáte počet znaků s diakritikou v řetězci.|
|[IsExtendedChar](#isextendedchar)|Voláním této funkce zjistíte, zda je daný znak rozšířený znak (menší než 32, větší než 126, a ne karta, posun řádku nebo návrat vozíku).|
|[QEncode](#qencode)|Voláním této funkce převedete data pomocí kódování Q.  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|
|[QPDecode](#qpdecode)|Dekóduje řetězec dat, která byla zakódována v formátu v uvozovkách, například předchozí volání [QPEncode](#qpencode).|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z řetězce zadané délky zakódovaného ve formátu quoted-printable.|
|[QPEncode](#qpencode)|Voláním této funkce zakódujete data do formátu quoted-printable.|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|
|[UUDecode](#uudecode)|Dekóduje řetězec dat, který byl uuencode jako předchozí volání do [kódování uuencode](#uuencode).|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z řetězce zadané délky zakódovaného do kódování UUENCODE.|
|[Kódování](#uuencode)|Voláním této funkce zakódujete data do kódování UUENCODE. |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlenc. h

## <a name="atlgethexvalue"></a>AtlGetHexValue

Voláním této funkce získáte číselnou hodnotu šestnáctkové číslice.

```
inline char AtlGetHexValue(char chIn) throw();
```

### <a name="parameters"></a>Parametry

*chIn*<br/>
Hexadecimální znak 0-"9", "a-'F" nebo "a-'F".

### <a name="return-value"></a>Návratová hodnota

Číselná hodnota vstupního znaku interpretována jako šestnáctková číslice. Například vstup ' 0 ' vrátí hodnotu 0 a vstup ' A ' vrátí hodnotu 10. Pokud vstupní znak není hexadecimální číslice, vrátí tato funkce hodnotu-1.

## <a name="atlgetversion"></a>AtlGetVersion

Voláním této funkce získáte verzi knihovny ATL, kterou používáte.

```
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);
```

### <a name="parameters"></a>Parametry

*pReserved*<br/>
Vyhrazený ukazatel.

### <a name="return-value"></a>Návratová hodnota

Vrátí celočíselnou hodnotu DWORD verze knihovny ATL, kterou kompilujete nebo spouštíte.

## <a name="example"></a>Příklad

Funkce by měla být volána následujícím způsobem.

[!code-cpp[NVC_ATL_Utilities#95](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="atlhexdecode"></a>AtlHexDecode

Dekóduje řetězec dat, který byl kódován jako šestnáctkový text, například předchozí volání [AtlHexEncode](#atlhexencode).

```
inline BOOL AtlHexDecode(
   LPCSTR pSrcData,
   int nSrcLen,
   LPBYTE pbDest,
   int* pnDestLen) throw();
```

### <a name="parameters"></a>Parametry

*pSrcData*<br/>
Řetězec obsahující data, která mají být dekódovat.

*nSrcLen*<br/>
Délka ve znacích *pSrcData*

*pbDest*<br/>
Vyrovnávací paměť přidělená volajícímu pro příjem dekódování dat.

*pnDestLen*<br/>
Ukazatel na proměnnou, která obsahuje délku v bajtech *pbDest*. Pokud je funkce úspěšná, proměnná přijme počet bajtů zapsaných do vyrovnávací paměti. Pokud dojde k chybě funkce, proměnná obdrží požadovanou délku v bajtech vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

## <a name="atlhexdecodegetrequiredlength"></a>AtlHexDecodeGetRequiredLength

Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z šestnáctkově zakódovaného řetězce zadané délky.

```
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Počet znaků v zakódovaném řetězci.

### <a name="return-value"></a>Návratová hodnota

Počet bajtů vyžadovaných pro vyrovnávací paměť, která by mohla obsahovat Dekódovatelné řetězce *nSrcLen* znaků.

## <a name="atlhexencode"></a>AtlHexEncode

Voláním této funkce zakódujete data jako řetězec šestnáctkového textu.

```
inline BOOL AtlHexEncode(
   const BYTE * pbSrcData,
   int nSrcLen,
   LPSTR szDest,
int * pnDestLen) throw();
```

### <a name="parameters"></a>Parametry

*pbSrcData*<br/>
Vyrovnávací paměť obsahující data, která mají být zakódována.

*nSrcLen*<br/>
Délka dat, která mají být zakódována v bajtech.

*szDest*<br/>
Vyrovnávací paměť přidělená volajícímu pro příjem kódovaných dat

*pnDestLen*<br/>
Ukazatel na proměnnou, která obsahuje délku ve znacích *szDest*. Pokud je funkce úspěšná, proměnná přijme počet znaků zapsaných do vyrovnávací paměti. Pokud dojde k chybě funkce, proměnná obdrží požadovanou délku ve znacích vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Každý bajt zdrojových dat je kódovaný jako 2 šestnáctkové znaky.

## <a name="atlhexencodegetrequiredlength"></a>AtlHexEncodeGetRequiredLength

Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.

```
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Počet bajtů dat, která mají být zakódována.

### <a name="return-value"></a>Návratová hodnota

Počet znaků vyžadovaných pro vyrovnávací paměť, která by mohla uchovávat kódovaná data *nSrcLen* bajtů.

## <a name="atlhexvalue"></a>AtlHexValue

Voláním této funkce získáte číselnou hodnotu šestnáctkové číslice.

```
inline short AtlHexValue(char chIn) throw();
```

### <a name="parameters"></a>Parametry

*chIn*<br/>
Hexadecimální znak 0-"9", "a-'F" nebo "a-'F".

### <a name="return-value"></a>Návratová hodnota

Číselná hodnota vstupního znaku interpretována jako šestnáctková číslice. Například vstup ' 0 ' vrátí hodnotu 0 a vstup ' A ' vrátí hodnotu 10. Pokud vstupní znak není hexadecimální číslice, vrátí tato funkce hodnotu-1.

## <a name="atlunicodetoutf8"></a>AtlUnicodeToUTF8

Voláním této funkce převedete řetězec s kódováním Unicode na UTF-8.

```
ATL_NOINLINE inline int AtlUnicodeToUTF8(
   LPCWSTR wszSrc,
   int nSrc,
   LPSTR szDest,
   int nDest) throw();
```

### <a name="parameters"></a>Parametry

*wszSrc*<br/>
Řetězec Unicode, který se má převést

*nSrc*<br/>
Délka řetězce znaků Unicode.

*szDest*<br/>
Vyrovnávací paměť přidělená volajícímu pro příjem převedeného řetězce

*nDest*<br/>
Délka vyrovnávací paměti v bajtech.

### <a name="return-value"></a>Návratová hodnota

Vrátí počet znaků pro převedený řetězec.

### <a name="remarks"></a>Poznámky

Chcete-li určit velikost vyrovnávací paměti vyžadované pro převedený řetězec, zavolejte tuto funkci předávání 0 pro *szDest* a *nDest*.

## <a name="bencode"></a>BEncode

Voláním této funkce převedete data pomocí kódování B.

```
inline BOOL BEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet) throw();
```

### <a name="parameters"></a>Parametry

*pbSrcData*<br/>
Vyrovnávací paměť obsahující data, která mají být zakódována.

*nSrcLen*<br/>
Délka dat, která mají být zakódována v bajtech.

*szDest*<br/>
Vyrovnávací paměť přidělená volajícímu pro příjem kódovaných dat

*pnDestLen*<br/>
Ukazatel na proměnnou, která obsahuje délku ve znacích *szDest*. Pokud je funkce úspěšná, proměnná přijme počet znaků zapsaných do vyrovnávací paměti. Pokud dojde k chybě funkce, proměnná obdrží požadovanou délku ve znacích vyrovnávací paměti.

*pszCharSet*<br/>
Znaková sada, která má být použita pro převod.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Schéma kódování "B" je popsané v dokumentu RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)).

## <a name="bencodegetrequiredlength"></a>BEncodeGetRequiredLength

Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.

```
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Počet bajtů dat, která mají být zakódována.

*nCharsetLen*<br/>
Délka znaků znakové sady, která má být použita pro převod.

### <a name="return-value"></a>Návratová hodnota

Počet znaků vyžadovaných pro vyrovnávací paměť, která by mohla uchovávat kódovaná data *nSrcLen* bajtů.

### <a name="remarks"></a>Poznámky

Schéma kódování "B" je popsané v dokumentu RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)).

## <a name="escapexml"></a>EscapeXML

Voláním této funkce převedete znaky, které jsou problematické pro použití v kódu XML, na jejich bezpečné ekvivalenty.

```
inline int EscapeXML(
   const wchar_t * szIn,
   int nSrcLen,
   wchar_t * szEsc,
   int nDestLen,
   DWORD dwFlags = ATL_ESC_FLAG_NONE) throw();
```

### <a name="parameters"></a>Parametry

*szIn*<br/>
Řetězec, který má být převeden.

*nSrclen*<br/>
Délka řetězce, který má být převeden.

*szEsc*<br/>
Vyrovnávací paměť přidělená volajícímu pro příjem převedeného řetězce

*nDestLen*<br/>
Délka ve znacích vyrovnávací paměti přidělené volajícímu.

*dwFlags*<br/>
ATL_ESC příznaky popisující, jak má být proveden převod.

- ATL_ESC_FLAG_NONE výchozí chování. Uvozovky a apostrofy nejsou převedeny.
- ATL_ESC_FLAG_ATTR uvozovky a apostrofy se převedou `&quot;` na `&apos;` a v uvedeném pořadí.

### <a name="return-value"></a>Návratová hodnota

Délka převedené řetězce ve znacích

### <a name="remarks"></a>Poznámky

Možné převody provedené touto funkcí jsou uvedeny v tabulce:

|Source|Cíl|
|------------|-----------------|
|\<|&lt;|
|>|&gt;|
|&|&amp;|
|'|&apos;|
|"|&quot;|

## <a name="getextendedchars"></a>GetExtendedChars

Voláním této funkce získáte počet znaků s diakritikou v řetězci.

```
inline int GetExtendedChars(LPCSTR szSrc, int nSrcLen) throw();
```

### <a name="parameters"></a>Parametry

*szSrc*<br/>
Řetězec, který má být analyzován.

*nSrcLen*<br/>
Délka řetězce ve znacích.

### <a name="return-value"></a>Návratová hodnota

Vrátí počet rozšířených znaků nalezených v rámci řetězce, který určuje [IsExtendedChar](#isextendedchar).

## <a name="isextendedchar"></a>IsExtendedChar

Voláním této funkce zjistíte, zda je daný znak rozšířený znak (menší než 32, větší než 126, a ne karta, posun řádku nebo návrat vozíku).

```
inline int IsExtendedChar(char ch) throw();
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Testovaný znak

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je znak rozšířený, jinak FALSE.

## <a name="qencode"></a>QEncode

Voláním této funkce převedete data pomocí kódování Q.

```
inline BOOL QEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCSTR pszCharSet,
   int* pnNumEncoded = NULL) throw();
```

### <a name="parameters"></a>Parametry

*pbSrcData*<br/>
Vyrovnávací paměť obsahující data, která mají být zakódována.

*nSrcLen*<br/>
Délka dat, která mají být zakódována v bajtech.

*szDest*<br/>
Vyrovnávací paměť přidělená volajícímu pro příjem kódovaných dat

*pnDestLen*<br/>
Ukazatel na proměnnou, která obsahuje délku ve znacích *szDest*. Pokud je funkce úspěšná, proměnná přijme počet znaků zapsaných do vyrovnávací paměti. Pokud dojde k chybě funkce, proměnná obdrží požadovanou délku ve znacích vyrovnávací paměti.

*pszCharSet*<br/>
Znaková sada, která má být použita pro převod.

*pnNumEncoded*<br/>
Ukazatel na proměnnou, která vrací, obsahuje počet nebezpečných znaků, které musely být převedeny.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Schéma kódování "Q" je popsané v dokumentu RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)).

## <a name="qencodegetrequiredlength"></a>QEncodeGetRequiredLength

Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.

```
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Počet bajtů dat, která mají být zakódována.

*nCharsetLen*<br/>
Délka znaků znakové sady, která má být použita pro převod.

### <a name="return-value"></a>Návratová hodnota

Počet znaků vyžadovaných pro vyrovnávací paměť, která by mohla uchovávat kódovaná data *nSrcLen* bajtů.

### <a name="remarks"></a>Poznámky

Schéma kódování "Q" je popsané v dokumentu RFC 2047 ([https://www.ietf.org/rfc/rfc2047.txt](https://www.ietf.org/rfc/rfc2047.txt)).

## <a name="qpdecode"></a>QPDecode

Dekóduje řetězec dat, která byla zakódována v formátu v uvozovkách, například předchozí volání [QPEncode](#qpencode).

```
inline BOOL QPDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>Parametry

*pbSrcData*<br/>
pro Vyrovnávací paměť obsahující data, která mají být dekódovat.

*nSrcLen*<br/>
pro Délka v bajtech pro *pbSrcData*.

*szDest*<br/>
mimo Vyrovnávací paměť přidělená volajícímu pro příjem dekódování dat.

*pnDestLen*<br/>
mimo Ukazatel na proměnnou, která obsahuje délku v bajtech *szDest*. Pokud je funkce úspěšná, proměnná přijme počet bajtů zapsaných do vyrovnávací paměti. Pokud dojde k chybě funkce, proměnná obdrží požadovanou délku v bajtech vyrovnávací paměti.

*dwFlags*<br/>
pro ATLSMTP_QPENCODE příznaky popisující, jak má být proveden převod.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Schéma kódování v uvozovkách je popsané v dokumentu RFC 2045 ([https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)).

## <a name="qpdecodegetrequiredlength"></a>QPDecodeGetRequiredLength

Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z řetězce zadané délky zakódovaného ve formátu quoted-printable.

```
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Počet znaků v zakódovaném řetězci.

### <a name="return-value"></a>Návratová hodnota

Počet bajtů vyžadovaných pro vyrovnávací paměť, která by mohla obsahovat Dekódovatelné řetězce *nSrcLen* znaků.

### <a name="remarks"></a>Poznámky

Schéma kódování v uvozovkách je popsané v dokumentu RFC 2045 ([https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)).

## <a name="qpencode"></a>QPEncode

Voláním této funkce zakódujete data do formátu quoted-printable.

```
inline BOOL QPEncode(
   BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>Parametry

*pbSrcData*<br/>
Vyrovnávací paměť obsahující data, která mají být zakódována.

*nSrcLen*<br/>
Délka dat, která mají být zakódována v bajtech.

*szDest*<br/>
Vyrovnávací paměť přidělená volajícímu pro příjem kódovaných dat

*pnDestLen*<br/>
Ukazatel na proměnnou, která obsahuje délku ve znacích *szDest*. Pokud je funkce úspěšná, proměnná přijme počet znaků zapsaných do vyrovnávací paměti. Pokud dojde k chybě funkce, proměnná obdrží požadovanou délku ve znacích vyrovnávací paměti.

*dwFlags*<br/>
ATLSMTP_QPENCODE příznaky popisující, jak má být proveden převod.

- ATLSMTP_QPENCODE_DOT Pokud se na začátku řádku objeví tečka, přidá se do výstupu i jako kódovaný.

- ATLSMTP_QPENCODE_TRAILING_SOFT připojí `=\r\n` k zakódovanému řetězci.

Schéma kódování v uvozovkách je popsané v [dokumentu RFC 2045](https://www.ietf.org/rfc/rfc2045.txt).

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Schéma kódování v uvozovkách je popsané v dokumentu RFC 2045 ([https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)).

## <a name="qpencodegetrequiredlength"></a>QPEncodeGetRequiredLength

Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.

```
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Počet bajtů dat, která mají být zakódována.

### <a name="return-value"></a>Návratová hodnota

Počet znaků vyžadovaných pro vyrovnávací paměť, která by mohla uchovávat kódovaná data *nSrcLen* bajtů.

### <a name="remarks"></a>Poznámky

Schéma kódování v uvozovkách je popsané v dokumentu RFC 2045 ([https://www.ietf.org/rfc/rfc2045.txt](https://www.ietf.org/rfc/rfc2045.txt)).

## <a name="uudecode"></a>UUDecode

Dekóduje řetězec dat, který byl uuencode jako předchozí volání do [kódování uuencode](#uuencode).

```
inline BOOL UUDecode(
   BYTE* pbSrcData,
   int nSrcLen,
   BYTE* pbDest,
   int* pnDestLen) throw ();
```

### <a name="parameters"></a>Parametry

*pbSrcData*<br/>
Řetězec obsahující data, která mají být dekódovat.

*nSrcLen*<br/>
Délka v bajtech pro *pbSrcData*.

*pbDest*<br/>
Vyrovnávací paměť přidělená volajícímu pro příjem dekódování dat.

*pnDestLen*<br/>
Ukazatel na proměnnou, která obsahuje délku v bajtech *pbDest*. Pokud je funkce úspěšná, proměnná přijme počet bajtů zapsaných do vyrovnávací paměti. Pokud dojde k chybě funkce, proměnná obdrží požadovanou délku v bajtech vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Tato implementace uuencoding se řídí specifikací POSIX P 1003.2 b/D11.

## <a name="uudecodegetrequiredlength"></a> UUDecodeGetRequiredLength

Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z řetězce zadané délky zakódovaného do kódování UUENCODE.

```
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Počet znaků v zakódovaném řetězci.

### <a name="return-value"></a>Návratová hodnota

Počet bajtů vyžadovaných pro vyrovnávací paměť, která by mohla obsahovat Dekódovatelné řetězce *nSrcLen* znaků.

### <a name="remarks"></a>Poznámky

Tato implementace uuencoding se řídí specifikací POSIX P 1003.2 b/D11.

## <a name="uuencode"></a>Kódování

Voláním této funkce zakódujete data do kódování UUENCODE.

```
inline BOOL UUEncode(
   const BYTE* pbSrcData,
   int nSrcLen,
   LPSTR szDest,
   int* pnDestLen,
   LPCTSTR lpszFile = _T("file"),
   DWORD dwFlags = 0) throw ();
```

### <a name="parameters"></a>Parametry

*pbSrcData*<br/>
Vyrovnávací paměť obsahující data, která mají být zakódována.

*nSrcLen*<br/>
Délka dat, která mají být zakódována v bajtech.

*szDest*<br/>
Vyrovnávací paměť přidělená volajícímu pro příjem kódovaných dat

*pnDestLen*<br/>
Ukazatel na proměnnou, která obsahuje délku ve znacích *szDest*. Pokud je funkce úspěšná, proměnná přijme počet znaků zapsaných do vyrovnávací paměti. Pokud dojde k chybě funkce, proměnná obdrží požadovanou délku ve znacích vyrovnávací paměti.

*lpszFile*<br/>
Soubor, který má být přidán do záhlaví, je-li v *dwFlags*ZADÁN parametr ATLSMTP_UUENCODE_HEADER.

*dwFlags*<br/>
Příznaky ovládající chování této funkce.

- ATLSMTP_UUENCODE_HEADE hlavičky se zakódují.

- ATLSMTP_UUENCODE_END se zakódováním konce.

- Budou provedeny ATLSMTP_UUENCODE_DOTcí datové věci.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Tato implementace uuencoding se řídí specifikací POSIX P 1003.2 b/D11.

## <a name="uuencodegetrequiredlength"></a>UUEncodeGetRequiredLength

Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.

```
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();
```

### <a name="parameters"></a>Parametry

*nSrcLen*<br/>
Počet bajtů dat, která mají být zakódována.

### <a name="return-value"></a>Návratová hodnota

Počet znaků vyžadovaných pro vyrovnávací paměť, která by mohla uchovávat kódovaná data *nSrcLen* bajtů.

### <a name="remarks"></a>Poznámky

Tato implementace uuencoding se řídí specifikací POSIX P 1003.2 b/D11.

## <a name="see-also"></a>Viz také:

[Charakteristiky](../active-template-library-atl-concepts.md)<br/>
[Desktopové komponenty ATL objektů COM](../atl-com-desktop-components.md)
