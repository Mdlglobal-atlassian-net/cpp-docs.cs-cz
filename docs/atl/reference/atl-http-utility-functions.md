---
title: "Pomocné funkce ATL HTTP | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4db57ef2-31fa-4696-bbeb-79a9035033ed
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 9cdb12373d93c17258fb615f667d7321e06f6728
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atl-http-utility-functions"></a>Pomocné funkce protokolu HTTP ATL

Tyto funkce podporují zpracování adresy URL.

|||  
|-|-|  
|[AtlCanonicalizeUrl](#atlcanonicalizeurl)|Canonicalizes adresu URL, která zahrnuje řídicí sekvence převodu nebezpečné znaky a mezery.|  
|[AtlCombineUrl](#atlcombineurl)|Kombinuje základní adresu URL a relativní adresa URL na adresu URL jeden, kanonickém tvaru.|  
|[AtlEscapeUrl](#atlescapeurl)|Převede všechny znaky unsafe, abyste se vyhnuli pořadí.|  
|[AtlGetDefaultUrlPort](#atlgetdefaulturlport)|Získá výchozí číslo portu přidružené k určité protokolu IP nebo schéma.|  
|[AtlIsUnsafeUrlChar](#atlisunsafeurlchar)|Určuje, zda znak je bezpečný pro použití v adrese URL.|  
|[AtlUnescapeUrl](#atlunescapeurl)|Převede uvozené znaky zpět na původní hodnoty.|  
|[RGBToHtml](#rgbtohtml)|Převede [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu na text HTML odpovídající této hodnotě barev.|
|[SystemTimeToHttpDate](#systemtimetohttpdate)|Voláním této funkce převedete systémový čas na řetězec ve formátu vhodném pro použití v hlavičkách protokolu HTTP.|

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlutil.h  

## <a name="atlcanonicalizeurl"></a>AtlCanonicalizeUrl
Voláním této funkce převedete adresu URL na kanonický tvar, přičemž problematické znaky a mezery se převedou na řídicí sekvence.  
  
```    
inline BOOL AtlCanonicalizeUrl(  
   LPCTSTR szUrl,  
   LPTSTR szCanonicalized,  
   DWORD* pdwMaxLength,  
   DWORD dwFlags = 0) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `szUrl`  
 Adresa URL chcete kanonizovat.  
  
 `szCanonicalized`  
 Volající přidělit vyrovnávací paměť pro příjem kanonizovaného adresy URL.  
  
 `pdwMaxLength`  
 Ukazatel na proměnné, která obsahuje délka ve znacích `szCanonicalized`. Pokud funkci úspěšné, obdrží proměnnou počet znaků, které jsou zapsány do vyrovnávací paměti, včetně ukončující znak hodnoty null. Pokud funkce selže, obdrží proměnná má požadovanou délku v bajtech vyrovnávací paměti, včetně místa pro ukončující znak hodnoty null.  
  
 `dwFlags`  
 Příznaky ATL_URL řízení chování této funkce. 

- `ATL_URL_BROWSER_MODE`Kódování nebo dekódování znaků za "#" nebo "?" a nedojde k odstranění prázdné znaky po "?". Pokud tato hodnota není zadaná, je zakódován úplnou adresu URL a bude odebrán prázdné znaky.
- `ATL_URL_DECODE`Převede všechny % XX pořadí znaků, včetně řídicí sekvence, než je analyzovat adresu URL.
- `ATL_URL_ENCODE_PERCENT`Kóduje všechny znaky procenta došlo. Ve výchozím nastavení nejsou znaky procenta kódování.
- `ATL_URL_ENCODE_SPACES_ONLY`Kóduje pouze mezery.
- `ATL_URL_ESCAPE`Převede všechny řídicí sekvence (% XX) na jejich odpovídající znaků.
- `ATL_URL_NO_ENCODE`Nepřevádí řídicí sekvence nebezpečné znaky.
- `ATL_URL_NO_META`Nedojde k odebrání meta pořadí (například "."a"...") z adresy URL. 
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Chová se jako aktuální verze [InternetCanonicalizeUrl](http://msdn.microsoft.com/library/windows/desktop/aa384342) ale nevyžaduje WinInet nebo nainstalovaný Internet Explorer.  
  
### <a name="see-also"></a>Viz také  
 [InternetCanonicalizeUrl](http://msdn.microsoft.com/library/windows/desktop/aa384342)

 ## <a name="atlcombineurl"></a>AtlCombineUrl
 Voláním této funkce zkombinujete základní a relativní adresu URL do jedné kanonické adresy URL.  
  
```    
inline BOOL AtlCombineUrl(  
   LPCTSTR szBaseUrl,  
   LPCTSTR szRelativeUrl,  
   LPTSTR szBuffer,  
   DWORD* pdwMaxLength,  
   DWORD dwFlags = 0) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *szBaseUrl*  
 Základní adresu URL.  
  
 *szRelativeUrl*  
 Adresa URL relativní k základní adresu URL.  
  
 `szBuffer`  
 Volající přidělit vyrovnávací paměť pro příjem kanonizovaného adresy URL.  
  
 `pdwMaxLength`  
 Ukazatel na proměnné, která obsahuje délka ve znacích `szBuffer`. Pokud funkci úspěšné, obdrží proměnnou počet znaků, které jsou zapsány do vyrovnávací paměti, včetně ukončující znak hodnoty null. Pokud funkce selže, obdrží proměnná má požadovanou délku v bajtech vyrovnávací paměti, včetně místa pro ukončující znak hodnoty null.  
  
 `dwFlags`  
 Příznaky řízení chování této funkce. V tématu [AtlCanonicalizeUrl](#atlcanonicalizeurl).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Chová se jako aktuální verze [InternetCombineUrl](http://msdn.microsoft.com/library/windows/desktop/aa384355) ale nevyžaduje WinInet nebo nainstalovaný Internet Explorer.  
  
## <a name="atlescapeurl"></a>AtlEscapeUrl
 Voláním této funkce převedete všechny problematické znaky na řídicí sekvence.  
  
```    
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
 `lpszStringIn`  
 Adresa URL má být převeden.  
  
 `lpszStringOut`  
 Volající přidělit vyrovnávací paměť ke kterému se zapíšou převedený adresy URL.  
  
 `pdwStrLen`  
 Ukazatel na proměnnou DWORD. Pokud funkci úspěšné, `pdwStrLen` obdrží počet znaků, které jsou zapsány do vyrovnávací paměti, včetně ukončující znak hodnoty null. Pokud funkce selže, obdrží proměnná má požadovanou délku v bajtech vyrovnávací paměti, včetně místa pro ukončující znak hodnoty null. Při použití této metody verze široká znaková `pdwStrLen` obdrží počet znaků, ne počet bajtů.  
  
 `dwMaxLength`  
 Velikost vyrovnávací paměti `lpszStringOut`.  
  
 `dwFlags`  
 Příznaky ATL_URL řízení chování této funkce. V tématu [ATLCanonicalizeUrl](#atlcanonicalizeurl) pro možné hodnoty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
## <a name="atlgetdefaulturlport"></a> 
 Voláním této funkce získáte výchozí číslo portu přidružené ke konkrétnímu protokolu nebo schématu Internetu.  
  
```  
inline ATL_URL_PORT AtlGetDefaultUrlPort(ATL_URL_SCHEME m_nScheme) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *m_nScheme*  
 [ATL_URL_SCHEME](atl-url-scheme-enum.md) hodnotu identifikace schéma, pro které chcete získat číslo portu.  
  
### <a name="return-value"></a>Návratová hodnota  
 [ATL_URL_PORT](atl-typedefs.md#atl_url_port) přidružený k zadané schéma nebo ATL_URL_INVALID_PORT_NUMBER Pokud schéma nebyl rozpoznán.  

## <a name="atlisunsafeurlchar"></a>AtlIsUnsafeUrlChar
 Voláním této funkce zjistíte, zda lze znak bezpečně použít v adrese URL.  
  
```  
inline BOOL AtlIsUnsafeUrlChar(char chIn) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `chIn`  
 Znak, který má být testována pro zabezpečení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** Pokud vstupní znak nebezpečné, **FALSE** jinak.  
  
### <a name="remarks"></a>Poznámky  
 Znaky, které by neměly být použití v adresách URL lze otestovat pomocí této funkce a převést pomocí [AtlCanonicalizeUrl](#atlcanonicalizeurl).  
  
## <a name="atlunescapeurl"></a>AtlUnescapeUrl
 Voláním této funkce převedete řídicí znaky zpět na jejich původní hodnoty.  
  
```    
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
 `lpszStringIn`  
 Adresa URL má být převeden.  
  
 `lpszStringOut`  
 Volající přidělit vyrovnávací paměť ke kterému se zapíšou převedený adresy URL.  
  
 `pdwStrLen`  
 Ukazatel na proměnnou DWORD. Pokud funkci úspěšné, obdrží proměnnou počet znaků, které jsou zapsány do vyrovnávací paměti, včetně ukončující znak hodnoty null. Pokud funkce selže, obdrží proměnná má požadovanou délku v bajtech vyrovnávací paměti, včetně místa pro ukončující znak hodnoty null.  
  
 `dwMaxLength`  
 Velikost vyrovnávací paměti `lpszStringOut`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Obrátí proces převodu používaný službou [AtlEscapeUrl](#atlescapeurl).  
  
## <a name="rgbtohtml"></a>RGBToHtml
Převede [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu na text HTML odpovídající této hodnotě barev.  
  
```  
bool inline RGBToHtml(  
   COLORREF color,  
   LPTSTR pbOut,  
   long nBuffer);  
```  
  
### <a name="parameters"></a>Parametry  
 `color`  
 Hodnotu barva RGB.  
  
 `pbOut`  
 Volající přidělit vyrovnávací paměť pro příjem text pro hodnoty barvy HTML. Vyrovnávací paměti musí mít prostor pro dlouhé alespoň 8 znaků včetně místa pro ukončení hodnotu null).  
  
 *nBuffer*  
 Velikost v bajtech vyrovnávací paměti (včetně místa pro ukončení null).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Hodnotu barvy HTML je znak křížku následuje 6 číslic šestnáctkové hodnoty pomocí 2 číslic pro všechny komponenty červené, zelené a modré barvy (například #FFFFFF je bílé).  
  
## <a name="systemtimetohttpdate"></a>SystemTimeToHttpDate
Voláním této funkce převedete systémový čas na řetězec ve formátu vhodném pro použití v hlavičkách protokolu HTTP.  
  
```  
inline void SystemTimeToHttpDate( 
   const SYSTEMTIME& st,  
   CStringA& strTime);  
```  
  
### <a name="parameters"></a>Parametry  
 `st`  
 Systémový čas na získat jako řetězec formátu protokolu HTTP.  
  
 *strtime –*  
 Odkaz na proměnnou string přijímat HTTP datum a čas, jak jsou definovány v dokumentu RFC 2616 ([http://www.ietf.org/rfc/rfc2616.txt](http://www.ietf.org/rfc/rfc2616.txt)) a RFC 1123 ([http://www.ietf.org/rfc/rfc1123.txt](http://www.ietf.org/rfc/rfc1123.txt)).  
  
## <a name="see-also"></a>Viz také  
 [Koncepty](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM plochy součásti](../../atl/atl-com-desktop-components.md)   

