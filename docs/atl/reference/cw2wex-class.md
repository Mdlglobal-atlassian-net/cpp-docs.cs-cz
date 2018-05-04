---
title: Třída CW2WEX | Microsoft Docs
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
ms.openlocfilehash: e70ba1fdf42ea2f00b057d9b95105b34d9eff5a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cw2wex-class"></a>CW2WEX – třída
Tato třída se používá ve makra převodů řetězec `CW2TEX` a `CT2WEX`a typedef `CW2W`.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <int t_nBufferLength = 128>  
class CW2WEX
```  
  
#### <a name="parameters"></a>Parametry  
 `t_nBufferLength`  
 Velikost vyrovnávací paměti používané v procesu překladu. Výchozí délka je 128 bajtů.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CW2WEX::CW2WEX](#cw2wex)|Konstruktor|  
|[CW2WEX:: ~ CW2WEX](#dtor)|Destruktor.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CW2WEX::Operator LPWSTR](#operator_lpwstr)|Operátor převodu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CW2WEX::m_psz](#m_psz)|Data člena, který ukládá zdrojový řetězec.|  
|[CW2WEX::m_szBuffer](#m_szbuffer)|Statické vyrovnávací paměť, používá k ukládání převedený řetězec.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je potřeba další funkce, používat `CW2TEX`, `CT2WEX`, nebo `CW2W` ve vašem kódu.  
  
 Tato třída obsahuje statické vyrovnávací pevné velikosti, která se používá k ukládání výsledek převodu. Pokud je výsledek příliš velký pro uložení do statických vyrovnávací paměti, třída přiděluje paměti pomocí `malloc`, uvolnění paměti při opuštění oboru. To zajišťuje, že na rozdíl od text makra převodů k dispozici v předchozích verzích nástroje ATL, tato třída je bezpečné pro použití v smyčky a že ji nebude přetečení zásobníku.  
  
 Pokud třída pokusí o přidělení paměti haldy a selže, bude volat `AtlThrow` s argument **E_OUTOFMEMORY**.  
  
 Ve výchozím nastavení používají převod ATL – třídy a makra aktuální vlákno ANSI znaková stránka pro převod.  
  
 Následující makra je založena na této třídě:  
  
- `CW2TEX`  
  
- `CT2WEX`  
  
 Následující definice typu je založena na této třídě:  
  
- `CW2W`  
  
 Informace o těchto makra převodů text, najdete v části [ATL a MFC makra převodů řetězec](string-conversion-macros.md).  
  
## <a name="example"></a>Příklad  
 V tématu [ATL a MFC makra převodů řetězec](string-conversion-macros.md) příklad použití převodních maker tyto řetězce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlconv.h  
  
##  <a name="cw2wex"></a>  CW2WEX::CW2WEX  
 Konstruktor  
  
```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Textový řetězec, který má být převeden.  
  
 `nCodePage`  
 Znaková stránka. Nepoužívá se v této třídě.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří vyrovnávací paměti vyžadované pro překlad.  
  
##  <a name="dtor"></a>  CW2WEX:: ~ CW2WEX  
 Destruktor...  
  
```
~CW2WEX() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní přidělené vyrovnávací paměti.  
  
##  <a name="m_psz"></a>  CW2WEX::m_psz  
 Data člena, který ukládá zdrojový řetězec.  
  
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
 Vrátí textový řetězec jako typ `LPWSTR`.  
  
## <a name="see-also"></a>Viz také  
 [CA2AEX – třída](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX – třída](../../atl/reference/ca2caex-class.md)   
 [CA2WEX – třída](../../atl/reference/ca2wex-class.md)   
 [CW2AEX – třída](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX – třída](../../atl/reference/cw2cwex-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
