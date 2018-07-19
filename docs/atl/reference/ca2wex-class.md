---
title: Ca2wex – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f19046cc825fabd2a3a41020a9f4c141dc98489e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882816"
---
# <a name="ca2wex-class"></a>Ca2wex – třída
Tato třída se používá makra převodu řetězců CA2TEX, CA2CTEX, CT2WEX a CT2CWEX a definice typedef CA2W.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <int t_nBufferLength = 128>
class CA2WEX
```  
  
#### <a name="parameters"></a>Parametry  
 *t_nBufferLength*  
 Velikost vyrovnávací paměti používané při překladu. Výchozí délka je 128 bajtů.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CA2WEX::CA2WEX](#ca2wex)|Konstruktor|  
|[CA2WEX –:: ~ CA2WEX –](#dtor)|Destruktor.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CA2WEX::Operator LPWSTR](#operator_lpwstr)|Operátor převodu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CA2WEX::m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|  
|[CA2WEX::m_szBuffer](#m_szbuffer)|Statické vyrovnávací paměť, používá k ukládání převedený řetězec.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud není vyžadována další funkce, použijte CA2TEX, CA2CTEX, CT2WEX, CT2CWEX nebo CA2W ve vašem kódu.  
  
 Tato třída obsahuje pevné velikosti vyrovnávací paměti statické, která slouží k uložení výsledku převodu. Pokud je výsledek příliš velký a nevejde do statické vyrovnávací paměti, třída přiděluje paměť pomocí **malloc**, uvolnění paměti, když objekt dostane mimo rozsah. To zajišťuje, že na rozdíl od text makra převodů, které jsou k dispozici v předchozích verzích knihovny ATL, tato třída je bezpečné používat ve smyčkách a že nebudou přetečení zásobníku.  
  
 Pokud třída pokusí o přidělení paměti v haldě a selže, bude volat `AtlThrow` s argumentem E_OUTOFMEMORY.  
  
 Ve výchozím nastavení používají převodu třídy ATL a makra znakovou stránku ANSI aktuální vlákno pro převod. Pokud chcete přepsat toto chování pro konkrétní převod, zadejte jako druhý parametr konstruktoru pro třídu znakovou stránku.  
  
 Následující makra jsou založené na této třídě:  
  
- CA2TEX  
  
- CA2CTEX  
  
- CT2WEX  
  
- CT2CWEX  
  
 Následující definice typedef je založena na této třídě:  
  
- CA2W  
  
 Informace o těchto makrech převodu textu, naleznete v tématu [knihovny ATL a MFC – makra převodu řetězců](string-conversion-macros.md).  
  
## <a name="example"></a>Příklad  
 Zobrazit [knihovny ATL a MFC – makra převodu řetězců](string-conversion-macros.md) příklad použití převodních maker tyto řetězce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlconv.h  
  
##  <a name="ca2wex"></a>  CA2WEX::CA2WEX  
 Konstruktor  
  
```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 *psz*  
 Textový řetězec, který má být převeden.  
  
 *nCodePage*  
 Znaková stránka používá k provedení převodu. Viz diskuze parametr stránky kód pro funkci Windows SDK [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072) další podrobnosti.  
  
### <a name="remarks"></a>Poznámky  
 Přidělí vyrovnávací paměti používané při překladu.  
  
##  <a name="dtor"></a>  CA2WEX –:: ~ CA2WEX –  
 Destruktor.  
  
```
~CA2WEX() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní přidělené vyrovnávací paměti.  
  
##  <a name="m_psz"></a>  CA2WEX::m_psz  
 Datový člen, který ukládá zdrojový řetězec.  
  
```
LPWSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>  CA2WEX::m_szBuffer  
 Statické vyrovnávací paměť, používá k ukládání převedený řetězec.  
  
```
wchar_t m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpwstr"></a>  CA2WEX::Operator LPWSTR  
 Operátor převodu.  
  
```  
operator LPWSTR() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí textový řetězec psaní LPWSTR.  
  
## <a name="see-also"></a>Viz také  
 [Ca2aex – třída](../../atl/reference/ca2aex-class.md)   
 [Ca2caex – třída](../../atl/reference/ca2caex-class.md)   
 [Cw2aex – třída](../../atl/reference/cw2aex-class.md)   
 [Cw2cwex – třída](../../atl/reference/cw2cwex-class.md)   
 [Cw2wex – třída](../../atl/reference/cw2wex-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
