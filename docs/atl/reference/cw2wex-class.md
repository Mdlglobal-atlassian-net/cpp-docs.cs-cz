---
title: Cw2wex – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CW2WEX
- ATLCONV/ATL::CW2WEX
- ATLCONV/ATL::CW2WEX::CW2WEX
- ATLCONV/ATL::CW2WEX::m_psz
- ATLCONV/ATL::CW2WEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CW2WEX class
ms.assetid: 46262e56-e0d2-41fe-855b-0b67ecc8fcd7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7710856f05204dbbbc2bc15e2e62056123cd85cc
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884071"
---
# <a name="cw2wex-class"></a>Cw2wex – třída
Tato třída se používá makra převodu řetězců CW2TEX CT2WEX a definice typedef CW2W.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <int t_nBufferLength = 128>  
class CW2WEX
```  
  
#### <a name="parameters"></a>Parametry  
 *t_nBufferLength*  
 Velikost vyrovnávací paměti používané při překladu. Výchozí délka je 128 bajtů.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CW2WEX::CW2WEX](#cw2wex)|Konstruktor|  
|[CW2WEX –:: ~ CW2WEX –](#dtor)|Destruktor.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CW2WEX::Operator LPWSTR](#operator_lpwstr)|Operátor převodu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CW2WEX::m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|  
|[CW2WEX::m_szBuffer](#m_szbuffer)|Statické vyrovnávací paměť, používá k ukládání převedený řetězec.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud není vyžadována další funkce, použití CW2TEX, CT2WEX nebo CW2W ve vašem kódu.  
  
 Tato třída obsahuje pevné velikosti vyrovnávací paměti statické, která slouží k uložení výsledku převodu. Pokud je výsledek příliš velký a nevejde do statické vyrovnávací paměti, třída přiděluje paměť pomocí **malloc**, uvolnění paměti, když objekt dostane mimo rozsah. To zajišťuje, že na rozdíl od text makra převodů, které jsou k dispozici v předchozích verzích knihovny ATL, tato třída je bezpečné používat ve smyčkách a že nebudou přetečení zásobníku.  
  
 Pokud třída pokusí o přidělení paměti v haldě a selže, bude volat `AtlThrow` s argumentem E_OUTOFMEMORY.  
  
 Ve výchozím nastavení používají převodu třídy ATL a makra znakovou stránku ANSI aktuální vlákno pro převod.  
  
 Následující makra jsou založené na této třídě:  
  
- CW2TEX  
  
- CT2WEX  
  
 Následující definice typedef je založena na této třídě:  
  
- CW2W  
  
 Informace o těchto makrech převodu textu, naleznete v tématu [knihovny ATL a MFC – makra převodu řetězců](string-conversion-macros.md).  
  
## <a name="example"></a>Příklad  
 Zobrazit [knihovny ATL a MFC – makra převodu řetězců](string-conversion-macros.md) příklad použití převodních maker tyto řetězce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlconv.h  
  
##  <a name="cw2wex"></a>  CW2WEX::CW2WEX  
 Konstruktor  
  
```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *psz*  
 Textový řetězec, který má být převeden.  
  
 *nCodePage*  
 Znakovou stránku. Nepoužívá se v této třídě.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří vyrovnávací paměti vyžadované pro převod.  
  
##  <a name="dtor"></a>  CW2WEX –:: ~ CW2WEX –  
 Destruktor...  
  
```
~CW2WEX() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní přidělené vyrovnávací paměti.  
  
##  <a name="m_psz"></a>  CW2WEX::m_psz  
 Datový člen, který ukládá zdrojový řetězec.  
  
```
LPWSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>  CW2WEX::m_szBuffer  
 Statické vyrovnávací paměť, používá k ukládání převedený řetězec.  
  
```
wchar_t m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpwstr"></a>  CW2WEX::Operator LPWSTR  
 Operátor přetypování.  
  
```  
operator LPWSTR() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí textový řetězec psaní LPWSTR.  
  
## <a name="see-also"></a>Viz také  
 [Ca2aex – třída](../../atl/reference/ca2aex-class.md)   
 [Ca2caex – třída](../../atl/reference/ca2caex-class.md)   
 [Ca2wex – třída](../../atl/reference/ca2wex-class.md)   
 [Cw2aex – třída](../../atl/reference/cw2aex-class.md)   
 [Cw2cwex – třída](../../atl/reference/cw2cwex-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
