---
title: Třída CA2WEX | Microsoft Docs
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
ms.openlocfilehash: 218e0d8f5e93a9e6c41ff855ff086cc7bfa6c766
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358743"
---
# <a name="ca2wex-class"></a>CA2WEX – třída
Tato třída se používá ve makra převodů řetězec `CA2TEX`, `CA2CTEX`, `CT2WEX`, a `CT2CWEX`a typedef **CA2W**.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <int t_nBufferLength = 128>
class CA2WEX
```  
  
#### <a name="parameters"></a>Parametry  
 `t_nBufferLength`  
 Velikost vyrovnávací paměti používané v procesu překladu. Výchozí délka je 128 bajtů.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CA2WEX::CA2WEX](#ca2wex)|Konstruktor|  
|[CA2WEX:: ~ CA2WEX](#dtor)|Destruktor.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CA2WEX::Operator LPWSTR](#operator_lpwstr)|Operátor převodu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CA2WEX::m_psz](#m_psz)|Data člena, který ukládá zdrojový řetězec.|  
|[CA2WEX::m_szBuffer](#m_szbuffer)|Statické vyrovnávací paměť, používá k ukládání převedený řetězec.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je potřeba další funkce, používat `CA2TEX`, `CA2CTEX`, `CT2WEX`, `CT2CWEX`, nebo **CA2W** ve vašem kódu.  
  
 Tato třída obsahuje statické vyrovnávací pevné velikosti, která se používá k ukládání výsledek převodu. Pokud je výsledek příliš velký pro uložení do statických vyrovnávací paměti, třída přiděluje paměti pomocí `malloc`, uvolnění paměti při opuštění oboru. To zajišťuje, že na rozdíl od text makra převodů k dispozici v předchozích verzích nástroje ATL, tato třída je bezpečné pro použití v smyčky a že ji nebude přetečení zásobníku.  
  
 Pokud třída pokusí o přidělení paměti haldy a selže, bude volat `AtlThrow` s argument **E_OUTOFMEMORY**.  
  
 Ve výchozím nastavení používají převod ATL – třídy a makra aktuální vlákno ANSI znaková stránka pro převod. Pokud chcete k přepsání tohoto chování pro konkrétní převod, zadejte jako druhý parametr konstruktoru pro třídu znaková stránka.  
  
 Následující makra je založena na této třídě:  
  
- `CA2TEX`  
  
- `CA2CTEX`  
  
- `CT2WEX`  
  
- `CT2CWEX`  
  
 Následující definice typu je založena na této třídě:  
  
- **CA2W**  
  
 Informace o těchto makra převodů text, najdete v části [ATL a MFC makra převodů řetězec](string-conversion-macros.md).  
  
## <a name="example"></a>Příklad  
 V tématu [ATL a MFC makra převodů řetězec](string-conversion-macros.md) příklad použití převodních maker tyto řetězce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlconv.h  
  
##  <a name="ca2wex"></a>  CA2WEX::CA2WEX  
 Konstruktor  
  
```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Textový řetězec, který má být převeden.  
  
 `nCodePage`  
 Znaková stránka používá k provádění převod. Viz popis kódu stránky parametr pro funkci Windows SDK [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072) další podrobnosti.  
  
### <a name="remarks"></a>Poznámky  
 Přiděluje vyrovnávací paměti používané v procesu překladu.  
  
##  <a name="dtor"></a>  CA2WEX:: ~ CA2WEX  
 Destruktor.  
  
```
~CA2WEX() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní přidělené vyrovnávací paměti.  
  
##  <a name="m_psz"></a>  CA2WEX::m_psz  
 Data člena, který ukládá zdrojový řetězec.  
  
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
 Vrátí textový řetězec jako typ **LPWSTR.**  
  
## <a name="see-also"></a>Viz také  
 [CA2AEX – třída](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX – třída](../../atl/reference/ca2caex-class.md)   
 [CW2AEX – třída](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX – třída](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX – třída](../../atl/reference/cw2wex-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
