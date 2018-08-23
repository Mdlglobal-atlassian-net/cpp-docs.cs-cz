---
title: Funkce kódování textu ATL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9162c515f4fd451f3e663895953e106bb4e65135
ms.sourcegitcommit: 7f3df9ff0310a4716b8136ca20deba699ca86c6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42464668"
---
# <a name="atl-text-encoding-functions"></a>Funkce kódování textu ATL
Tyto funkce podporují text kódování a dekódování.

|||  
|-|-|  
|[AtlGetHexValue](#atlgethexvalue)|Voláním této funkce získáte číselnou hodnotu šestnáctkové číslice.|   
|[AtlGetVersion](#atlgetversion)|Voláním této funkce se získat verzi knihovny ATL, kterou používáte.  |  
|[AtlHexDecode](#atlhexdecode)|Dekóduje řetězec dat, který byl zakódován jako šestnáctkový text předchozí volání [AtlHexEncode](#atlhexencode).|
|[AtlHexDecodeGetRequiredLength](#atlhexdecodegetrequiredlength)|Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z šestnáctkově zakódovaného řetězce zadané délky.|
|[AtlHexEncode](#atlhexencode)|Voláním této funkce zakódujete data jako řetězec šestnáctkového textu.|
|[AtlHexEncodeGetRequiredLength](#atlhexencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|
|[AtlHexValue](#atlhexvalue)|Voláním této funkce získáte číselnou hodnotu šestnáctkové číslice. |
|[AtlUnicodeToUTF8](#atlunicodetoutf8)|Voláním této funkce převedete řetězec s kódováním Unicode na UTF-8. |
|[BEncode](#bencode)|Voláním této funkce převedete data pomocí kódování B.|
|[BEncodeGetRequiredLength](#bencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|
|[EscapeXML](#escapexml)|Voláním této funkce převedete znaky, které jsou problematické pro použití v kódu XML, na jejich bezpečné ekvivalenty.|
|[GetExtendedChars](#getextendedchars)|Voláním této funkce získáte počet znaků s diakritikou v řetězci.|
|[IsExtendedChar](#isextendedchar)|Voláním této funkce zjistíte, zda daný znak používá diakritiku (je menší než 32, větší než 126 a nejde o tabulátor, odřádkování ani návrat na začátek řádku).|
|[QEncode](#qencode)|Voláním této funkce převedete data pomocí kódování Q.  |
|[QEncodeGetRequiredLength](#qencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|
|[QPDecode](#qpdecode)|Dekóduje řetězec dat, který byl zakódován do formátu quoted-printable, jako předchozí volání [QPEncode](#qpencode).|
|[QPDecodeGetRequiredLength](#qpdecodegetrequiredlength)|Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z řetězce zadané délky zakódovaného ve formátu quoted-printable.|
|[QPEncode](#qpencode)|Voláním této funkce zakódujete data do formátu quoted-printable.|
|[QPEncodeGetRequiredLength](#qpencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|
|[UUDecode](#uudecode)|Dekóduje řetězec dat, která byla funkce, jako předchozí volání [UUEncode](#uuencode).|
|[UUDecodeGetRequiredLength](#uudecodegetrequiredlength)|Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z řetězce zadané délky zakódovaného do kódování UUENCODE.|
|[UUEncode](#uuencode)|Voláním této funkce zakódujete data do kódování UUENCODE. |
|[UUEncodeGetRequiredLength](#uuencodegetrequiredlength)|Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.|

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlenc.h  
 
## <a name="atlgethexvalue"></a> AtlGetHexValue
Voláním této funkce získáte číselnou hodnotu šestnáctkové číslice.  
  
```    
inline char AtlGetHexValue(char chIn) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *chIn*  
 Šestnáctkové kódy znaků "0" – "9", "A"-"F" nebo "a"-"f".  
  
### <a name="return-value"></a>Návratová hodnota  
 Číselná hodnota vstupní znak je interpretován jako hexadecimální číslice. Například vstup '0', vrátí hodnotu 0 a vstup z "A", vrací hodnotu 10. Pokud vstupní znak, který není šestnáctkovou číslicí, tato funkce vrátí hodnotu -1.  
  
## <a name="atlgetversion"></a> AtlGetVersion
Voláním této funkce se získat verzi knihovny ATL, kterou používáte.  
  
```  
ATLAPI_(DWORD) AtlGetVersion(void* pReserved);  
```  
  
### <a name="parameters"></a>Parametry  
 *Zachovány*  
 Vyhrazené ukazatel.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí celočíselnou hodnotu DWORD verze knihovny ATL, která jsou kompilace nebo systémem.  
  
## <a name="example"></a>Příklad  
 Funkce by měla být volána následujícím způsobem.  
  
 [!code-cpp[NVC_ATL_Utilities#95](../../atl/codesnippet/cpp/atl-text-encoding-functions_1.cpp)]  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  

## <a name="atlhexdecode"></a> AtlHexDecode
Dekóduje řetězec dat, který byl zakódován jako šestnáctkový text předchozí volání [AtlHexEncode](#atlhexencode).  
  
```    
inline BOOL AtlHexDecode(  
   LPCSTR pSrcData,  
   int nSrcLen,  
   LPBYTE pbDest,  
   int* pnDestLen) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *pSrcData*  
 Řetězec obsahující data, která mají dekódovat.  
  
 *nSrcLen*  
 Délka ve znacích *pSrcData*.  
  
 *pbDest*  
 Volající – přidělené vyrovnávací paměti pro příjem dekódovaná data.  
  
 *pnDestLen*  
 Ukazatel na proměnnou, která obsahuje délku v bajtech *pbDest*. Pokud funkce uspěje, proměnná přijímá počet bajtů zapsaných do vyrovnávací paměti. Pokud funkce selže, proměnné obdrží má požadovanou délku v bajtech vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
## <a name="atlhexdecodegetrequiredlength"></a> AtlHexDecodeGetRequiredLength
Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z šestnáctkově zakódovaného řetězce zadané délky.  
  
```  
inline int AtlHexDecodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *nSrcLen*  
 Počet znaků v kódovaný řetězec.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bajtů potřebných pro vyrovnávací paměť, která by mohla obsahovat dekódovaný řetězec *nSrcLen* znaků.  
  
## <a name="atlhexencode"></a> AtlHexEncode
Voláním této funkce zakódujete data jako řetězec šestnáctkového textu.  
  
```  
inline BOOL AtlHexEncode(  
   const BYTE * pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
int * pnDestLen) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *pbSrcData*  
 Vyrovnávací paměť obsahující data, která mají být zakódován.  
  
 *nSrcLen*  
 Délka dat kódovaný v bajtech.  
  
 *szDest*  
 Volající – přidělené vyrovnávací paměti pro příjem kódovaná data.  
  
 *pnDestLen*  
 Ukazatel na proměnnou, která obsahuje délky ve znacích *szDest*. Pokud funkce uspěje, proměnná přijímá počet znaků zapsaných do vyrovnávací paměti. Pokud funkce selže, obdrží proměnná požadovaná délka ve znacích, vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Každý bajt zdrojová data kódovaná jako 2 hexadecimálních znaků.  
  
## <a name="atlhexencodegetrequiredlength"></a> AtlHexEncodeGetRequiredLength
Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.  
  
```  
inline int AtlHexEncodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *nSrcLen*  
 Počet bajtů dat kódovaný.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků vyžadovaný pro vyrovnávací paměť, která by mohla obsahovat kódovaný data *nSrcLen* bajtů.  
  
## <a name="atlhexvalue"></a> AtlHexValue
Voláním této funkce získáte číselnou hodnotu šestnáctkové číslice.  
  
```  
inline short AtlHexValue(char chIn) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *chIn*  
 Šestnáctkové kódy znaků "0" – "9", "A"-"F" nebo "a"-"f".  
  
### <a name="return-value"></a>Návratová hodnota  
 Číselná hodnota vstupní znak je interpretován jako hexadecimální číslice. Například vstup '0', vrátí hodnotu 0 a vstup z "A", vrací hodnotu 10. Pokud vstupní znak, který není šestnáctkovou číslicí, tato funkce vrátí hodnotu -1.  
  
## <a name="atlunicodetoutf8"></a> AtlUnicodeToUTF8
Voláním této funkce převedete řetězec s kódováním Unicode na UTF-8.  
  
```  
ATL_NOINLINE inline int AtlUnicodeToUTF8(  
   LPCWSTR wszSrc,  
   int nSrc,  
   LPSTR szDest,  
   int nDest) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *wszSrc*  
 Řetězec znaků Unicode má být převeden  
  
 *nSrc*  
 Délka ve znacích řetězec znaků Unicode.  
  
 *szDest*  
 Volající – přidělené vyrovnávací paměti pro příjem převedený řetězec.  
  
 *nDest*  
 Délka vyrovnávací paměti v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet znaků pro převedený řetězec.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete určit velikost vyrovnávací paměti vyžadované pro převedený řetězec, volejte tuto funkce předávání 0 *szDest* a *nDest*.  
  
## <a name="bencode"></a> BEncode  
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
 *pbSrcData*  
 Vyrovnávací paměť obsahující data, která mají být zakódován.  
  
 *nSrcLen*  
 Délka dat kódovaný v bajtech.  
  
 *szDest*  
 Volající – přidělené vyrovnávací paměti pro příjem kódovaná data.  
  
 *pnDestLen*  
 Ukazatel na proměnnou, která obsahuje délky ve znacích *szDest*. Pokud funkce uspěje, proměnná přijímá počet znaků zapsaných do vyrovnávací paměti. Pokud funkce selže, obdrží proměnná požadovaná délka ve znacích, vyrovnávací paměti.  
  
 *pszCharSet*  
 Znakovou sadu pro převod.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Schéma kódování "B" je popsaná v dokumentu RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).  
  
## <a name="bencodegetrequiredlength"></a> BEncodeGetRequiredLength 
Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.  
  
```  
inline int BEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *nSrcLen*  
 Počet bajtů dat kódovaný.  
  
 *nCharsetLen*  
 Délka ve znacích znakovou sadu pro převod.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků vyžadovaný pro vyrovnávací paměť, která by mohla obsahovat kódovaný data *nSrcLen* bajtů.  
  
### <a name="remarks"></a>Poznámky  
 Schéma kódování "B" je popsaná v dokumentu RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).  
  
## <a name="escapexml"></a> EscapeXML
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
 *szIn*  
 Řetězec, který má být převeden.  
  
 *nSrclen*  
 Délka ve znacích řetězec, který má být převeden.  
  
 *szEsc*  
 Volající – přidělené vyrovnávací paměti pro příjem převedený řetězec.  
  
 *nDestLen*  
 Délka ve znacích volající – přidělené vyrovnávací paměti.  
  
 *dwFlags*  
 ATL_ESC příznaky popisující, jak se má provést převod. 

- ATL_ESC_FLAG_NONE výchozí chování. Nabídka značek a apostrofy nepřevádějí.
- Nabídka ATL_ESC_FLAG_ATTR značek a apostrofy se převedou na `&quot;` a `&apos;` v uvedeném pořadí.


  
### <a name="return-value"></a>Návratová hodnota  
 Délka ve znacích převedený řetězec.  
  
### <a name="remarks"></a>Poznámky  
 V tabulce jsou uvedeny možné převody prováděné tuto funkci:  
  
|Zdroj|cíl|  
|------------|-----------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|'|&apos;|  
|"|&quot;|  
  
## <a name="getextendedchars"></a> GetExtendedChars
Voláním této funkce získáte počet znaků s diakritikou v řetězci.  
  
```  
inline int GetExtendedChars(LPCSTR szSrc, int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *szSrc*  
 Řetězec, který má být analyzován.  
  
 *nSrcLen*  
 Délka řetězce ve znacích.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet rozšířených znaků nalezených v rámci řetězce podle [IsExtendedChar](#isextendedchar).  
  
## <a name="isextendedchar"></a> IsExtendedChar
Voláním této funkce zjistíte, zda daný znak používá diakritiku (je menší než 32, větší než 126 a nejde o tabulátor, odřádkování ani návrat na začátek řádku).  
  
```  
inline int IsExtendedChar(char ch) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *ch*  
 Znak, který má být testována  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud znak je rozšířeno, FALSE v opačném případě.  
  
## <a name="qencode"></a> QEncode
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
 *pbSrcData*  
 Vyrovnávací paměť obsahující data, která mají být zakódován.  
  
 *nSrcLen*  
 Délka dat kódovaný v bajtech.  
  
 *szDest*  
 Volající – přidělené vyrovnávací paměti pro příjem kódovaná data.  
  
 *pnDestLen*  
 Ukazatel na proměnnou, která obsahuje délky ve znacích *szDest*. Pokud funkce uspěje, proměnná přijímá počet znaků zapsaných do vyrovnávací paměti. Pokud funkce selže, obdrží proměnná požadovaná délka ve znacích, vyrovnávací paměti.  
  
 *pszCharSet*  
 Znakovou sadu pro převod.  
  
 *pnNumEncoded*  
 Ukazatel na proměnnou, která při návratu obsahuje počet problematické znaky, do kterých má být převeden.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Schéma kódování "Q" je popsaná v dokumentu RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).  
  
## <a name="qencodegetrequiredlength"></a> QEncodeGetRequiredLength 
Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.  
  
```  
inline int QEncodeGetRequiredLength(int nSrcLen, int nCharsetLen) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *nSrcLen*  
 Počet bajtů dat kódovaný.  
  
 *nCharsetLen*  
 Délka ve znacích znakovou sadu pro převod.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků vyžadovaný pro vyrovnávací paměť, která by mohla obsahovat kódovaný data *nSrcLen* bajtů.  
  
### <a name="remarks"></a>Poznámky  
 Schéma kódování "Q" je popsaná v dokumentu RFC 2047 ([http://www.ietf.org/rfc/rfc2047.txt](http://www.ietf.org/rfc/rfc2047.txt)).  
  
## <a name="qpdecode"></a> QPDecode
Dekóduje řetězec dat, který byl zakódován do formátu quoted-printable, jako předchozí volání [QPEncode](#qpencode).  
  
```  
inline BOOL QPDecode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   LPSTR szDest,  
   int* pnDestLen,  
   DWORD dwFlags = 0) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pbSrcData*  
 Vyrovnávací paměť obsahující data, která mají dekódovat.  
  
 [in] *nSrcLen*  
 Délka v bajtech *pbSrcData*.  
  
 [out] *szDest*  
 Volající – přidělené vyrovnávací paměti pro příjem dekódovaná data.  
  
 [out] *pnDestLen*  
 Ukazatel na proměnnou, která obsahuje délku v bajtech *szDest*. Pokud funkce uspěje, proměnná přijímá počet bajtů zapsaných do vyrovnávací paměti. Pokud funkce selže, proměnné obdrží má požadovanou délku v bajtech vyrovnávací paměti.  
  
 [in] *dwFlags*  
 Příznaky popisující, jak se má provést převod. Zobrazit [ATLSMTP_QPENCODE příznaky](http://msdn.microsoft.com/library/6b15a3ab-8e57-49e4-8104-09b26ebb96c4).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Quoted-printable schéma kódování je popsán v dokumentu RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).  
  
## <a name="qpdecodegetrequiredlength"></a> QPDecodeGetRequiredLength
Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z řetězce zadané délky zakódovaného ve formátu quoted-printable.  
  
```  
inline int QPDecodeGetRequiredLength(int nSrcLen) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *nSrcLen*  
 Počet znaků v kódovaný řetězec.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bajtů potřebných pro vyrovnávací paměť, která by mohla obsahovat dekódovaný řetězec *nSrcLen* znaků.  
  
### <a name="remarks"></a>Poznámky  
 Quoted-printable schéma kódování je popsán v dokumentu RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).  
  
## <a name="qpencode"></a> QPEncode
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
 *pbSrcData*  
 Vyrovnávací paměť obsahující data, která mají být zakódován.  
  
 *nSrcLen*  
 Délka dat kódovaný v bajtech.  
  
 *szDest*  
 Volající – přidělené vyrovnávací paměti pro příjem kódovaná data.  
  
 *pnDestLen*  
 Ukazatel na proměnnou, která obsahuje délky ve znacích *szDest*. Pokud funkce uspěje, proměnná přijímá počet znaků zapsaných do vyrovnávací paměti. Pokud funkce selže, obdrží proměnná požadovaná délka ve znacích, vyrovnávací paměti.  
  
 *dwFlags*  
 ATLSMTP_QPENCODE příznaky popisující, jak se má provést převod. 
- ATLSMTP_QPENCODE_DOT Pokud se zobrazí tečku na začátku řádku, to je přidán do výstupu stejně jako kódování.
- Připojí ATLSMTP_QPENCODE_TRAILING_SOFT `=\r\n` kódovaný řetězec.

Quoted-printable schéma kódování je popsán v [RFC 2045](http://www.ietf.org/rfc/rfc2045.txt).
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Quoted-printable schéma kódování je popsán v dokumentu RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).  
  
## <a name="qpencodegetrequiredlength"></a> QPEncodeGetRequiredLength
Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.  
  
```  
inline int QPEncodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>Parametry  
 *nSrcLen*  
 Počet bajtů dat kódovaný.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků vyžadovaný pro vyrovnávací paměť, která by mohla obsahovat kódovaný data *nSrcLen* bajtů.  
  
### <a name="remarks"></a>Poznámky  
 Quoted-printable schéma kódování je popsán v dokumentu RFC 2045 ([http://www.ietf.org/rfc/rfc2045.txt](http://www.ietf.org/rfc/rfc2045.txt)).  
  
## <a name="uudecode"></a> UUDecode
Dekóduje řetězec dat, která byla funkce, jako předchozí volání [UUEncode](#uuencode).  
  
```  
inline BOOL UUDecode(  
   BYTE* pbSrcData,  
   int nSrcLen,  
   BYTE* pbDest,  
   int* pnDestLen) throw ();  
```  
  
### <a name="parameters"></a>Parametry  
 *pbSrcData*  
 Řetězec obsahující data, která mají dekódovat.  
  
 *nSrcLen*  
 Délka v bajtech *pbSrcData*.  
  
 *pbDest*  
 Volající – přidělené vyrovnávací paměti pro příjem dekódovaná data.  
  
 *pnDestLen*  
 Ukazatel na proměnnou, která obsahuje délku v bajtech *pbDest*. Pokud funkce uspěje, proměnná přijímá počet bajtů zapsaných do vyrovnávací paměti. Pokud funkce selže, proměnné obdrží má požadovanou délku v bajtech vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato implementace uuencoding následuje specifikace POSIX P1003.2b/D11.  
  
## <a name="uudecodegetrequiredlength"></a> UUDecodeGetRequiredLength
Voláním této funkce získáte bajtovou velikost vyrovnávací paměti, která by mohla obsahovat data dekódovaná z řetězce zadané délky zakódovaného do kódování UUENCODE.  
  
```  
inline int UUDecodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>Parametry  
 *nSrcLen*  
 Počet znaků v kódovaný řetězec.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bajtů potřebných pro vyrovnávací paměť, která by mohla obsahovat dekódovaný řetězec *nSrcLen* znaků.  
  
### <a name="remarks"></a>Poznámky  
 Tato implementace uuencoding následuje specifikace POSIX P1003.2b/D11.  
  
## <a name="uuencode"></a> UUEncode
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
 *pbSrcData*  
 Vyrovnávací paměť obsahující data, která mají být zakódován.  
  
 *nSrcLen*  
 Délka dat kódovaný v bajtech.  
  
 *szDest*  
 Volající – přidělené vyrovnávací paměti pro příjem kódovaná data.  
  
 *pnDestLen*  
 Ukazatel na proměnnou, která obsahuje délky ve znacích *szDest*. Pokud funkce uspěje, proměnná přijímá počet znaků zapsaných do vyrovnávací paměti. Pokud funkce selže, obdrží proměnná požadovaná délka ve znacích, vyrovnávací paměti.  
  
 *lpszFile*  
 Soubor, který má přidat do záhlaví, pokud je podle ATLSMTP_UUENCODE_HEADER *dwFlags*.  
  
 *dwFlags*  
 Příznaky řízení chování této funkce. 
- Bude kódována ATLSMTP_UUENCODE_HEADE záhlaví.
- ATLSMTP_UUENCODE_END konci bude kódování.
- ATLSMTP_UUENCODE_DOT Data nádivky bude provádět.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato implementace uuencoding následuje specifikace POSIX P1003.2b/D11.  
  
## <a name="uuencodegetrequiredlength"></a> UUEncodeGetRequiredLength
Voláním této funkce získáte znakovou velikost vyrovnávací paměti, která by mohla obsahovat řetězec zakódovaný z dat zadané velikosti.  
  
```  
inline int UUEncodeGetRequiredLength(int nSrcLen) throw ();  
```  
  
### <a name="parameters"></a>Parametry  
 *nSrcLen*  
 Počet bajtů dat kódovaný.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků vyžadovaný pro vyrovnávací paměť, která by mohla obsahovat kódovaný data *nSrcLen* bajtů.  
  
### <a name="remarks"></a>Poznámky  
 Tato implementace uuencoding následuje specifikace POSIX P1003.2b/D11.  
  
### <a name="see-also"></a>Viz také  
 [Koncepty](../../atl/active-template-library-atl-concepts.md)   
 [Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)   