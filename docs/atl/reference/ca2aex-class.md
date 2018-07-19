---
title: Ca2aex – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CA2AEX
- ATLCONV/ATL::CA2AEX
- ATLCONV/ATL::CA2AEX::CA2AEX
- ATLCONV/ATL::CA2AEX::m_psz
- ATLCONV/ATL::CA2AEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CA2AEX class
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94e9c33fb69b439cc6c99d87d00d24f60e87d780
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882127"
---
# <a name="ca2aex-class"></a>Ca2aex – třída
Tato třída se používá makra převodu řetězců CA2TEX CT2AEX a definice typedef CA2A.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <int t_nBufferLength = 128>
class CA2AEX
```  
  
#### <a name="parameters"></a>Parametry  
 *t_nBufferLength*  
 Velikost vyrovnávací paměti používané při překladu. Výchozí délka je 128 bajtů.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CA2AEX::CA2AEX](#ca2aex)|Konstruktor|  
|[CA2AEX –:: ~ CA2AEX –](#dtor)|Destruktor.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CA2AEX::Operator LPSTR](#operator_lpstr)|Operátor převodu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CA2AEX::m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|  
|[CA2AEX::m_szBuffer](#m_szbuffer)|Statické vyrovnávací paměť, používá k ukládání převedený řetězec.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud není vyžadována další funkce, pomocí CA2TEX, CT2AEX nebo CA2A ve svém vlastním kódu.  
  
 Tato třída obsahuje pevné velikosti vyrovnávací paměti statické, která slouží k uložení výsledku převodu. Pokud je výsledek příliš velký a nevejde do statické vyrovnávací paměti, třída přiděluje paměť pomocí **malloc**, uvolnění paměti, když objekt dostane mimo rozsah. To zajišťuje, že na rozdíl od text makra převodů, které jsou k dispozici v předchozích verzích knihovny ATL, tato třída je bezpečné používat ve smyčkách a že nebudou přetečení zásobníku.  
  
 Pokud třída pokusí o přidělení paměti v haldě a selže, bude volat `AtlThrow` s argumentem E_OUTOFMEMORY.  
  
 Ve výchozím nastavení používají převodu třídy ATL a makra znakovou stránku ANSI aktuální vlákno pro převod.  
  
 Následující makra jsou založené na této třídě:  
  
- CA2TEX  
  
- CT2AEX  
  
 Následující definice typedef je založena na této třídě:  
  
- CA2A  
  
 Informace o těchto makrech převodu textu, naleznete v tématu [knihovny ATL a MFC – makra převodu řetězců](string-conversion-macros.md).  
  
## <a name="example"></a>Příklad  
 Zobrazit [knihovny ATL a MFC – makra převodu řetězců](string-conversion-macros.md) příklad použití převodních maker tyto řetězce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlconv.h  
  
##  <a name="ca2aex"></a>  CA2AEX::CA2AEX  
 Konstruktor  
  
```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *psz*  
 Textový řetězec, který má být převeden.  
  
 *nCodePage*  
 Nepoužívané v této třídě.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří vyrovnávací paměti vyžadované pro převod.  
  
##  <a name="dtor"></a>  CA2AEX –:: ~ CA2AEX –  
 Destruktor.  
  
```
~CA2AEX() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní přidělené vyrovnávací paměti.  
  
##  <a name="m_psz"></a>  CA2AEX::m_psz  
 Datový člen, který ukládá zdrojový řetězec.  
  
```
LPSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>  CA2AEX::m_szBuffer  
 Statické vyrovnávací paměť, používá k ukládání převedený řetězec.  
  
```
char m_szBuffer[ t_nBufferLength];
```  
  
##  <a name="operator_lpstr"></a>  CA2AEX::Operator LPSTR  
 Operátor převodu.  
  
```
operator LPSTR() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí textový řetězec jako typu LPSTR.  
  
## <a name="see-also"></a>Viz také  
 [Ca2caex – třída](../../atl/reference/ca2caex-class.md)   
 [Ca2wex – třída](../../atl/reference/ca2wex-class.md)   
 [Cw2aex – třída](../../atl/reference/cw2aex-class.md)   
 [Cw2cwex – třída](../../atl/reference/cw2cwex-class.md)   
 [Cw2wex – třída](../../atl/reference/cw2wex-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)