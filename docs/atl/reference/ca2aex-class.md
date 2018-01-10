---
title: "Třída CA2AEX | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CA2AEX
- ATLCONV/ATL::CA2AEX
- ATLCONV/ATL::CA2AEX::CA2AEX
- ATLCONV/ATL::CA2AEX::m_psz
- ATLCONV/ATL::CA2AEX::m_szBuffer
dev_langs: C++
helpviewer_keywords: CA2AEX class
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ec54e698723b801823d58a3bad2a53e6f1708369
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ca2aex-class"></a>CA2AEX – třída
Tato třída se používá ve makra převodů řetězec `CA2TEX` a `CT2AEX`a typedef **CA2A**.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <int t_nBufferLength = 128>
class CA2AEX
```  
  
#### <a name="parameters"></a>Parametry  
 `t_nBufferLength`  
 Velikost vyrovnávací paměti používané v procesu překladu. Výchozí délka je 128 bajtů.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CA2AEX::CA2AEX](#ca2aex)|Konstruktor|  
|[CA2AEX:: ~ CA2AEX](#dtor)|Destruktor.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CA2AEX::Operator LPSTR](#operator_lpstr)|Operátor převodu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CA2AEX::m_psz](#m_psz)|Data člena, který ukládá zdrojový řetězec.|  
|[CA2AEX::m_szBuffer](#m_szbuffer)|Statické vyrovnávací paměť, používá k ukládání převedený řetězec.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je potřeba další funkce, používat `CA2TEX`, `CT2AEX`, nebo **CA2A** v kódu.  
  
 Tato třída obsahuje statické vyrovnávací pevné velikosti, která se používá k ukládání výsledek převodu. Pokud je výsledek příliš velký pro uložení do statických vyrovnávací paměti, třída přiděluje paměti pomocí `malloc`, uvolnění paměti při opuštění oboru. To zajišťuje, že na rozdíl od text makra převodů k dispozici v předchozích verzích nástroje ATL, tato třída je bezpečné pro použití v smyčky a že ji nebude přetečení zásobníku.  
  
 Pokud třída pokusí o přidělení paměti haldy a selže, bude volat `AtlThrow` s argument **E_OUTOFMEMORY**.  
  
 Ve výchozím nastavení používají převod ATL – třídy a makra aktuální vlákno ANSI znaková stránka pro převod.  
  
 Následující makra je založena na této třídě:  
  
- `CA2TEX`  
  
- `CT2AEX`  
  
 Následující definice typu je založena na této třídě:  
  
- **CA2A**  
  
 Informace o těchto makra převodů text, najdete v části [ATL a MFC makra převodů řetězec](string-conversion-macros.md).  
  
## <a name="example"></a>Příklad  
 V tématu [ATL a MFC makra převodů řetězec](string-conversion-macros.md) příklad použití převodních maker tyto řetězce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlconv.h  
  
##  <a name="ca2aex"></a>CA2AEX::CA2AEX  
 Konstruktor  
  
```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Textový řetězec, který má být převeden.  
  
 `nCodePage`  
 Nepoužívá se v této třídě.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří vyrovnávací paměti vyžadované pro překlad.  
  
##  <a name="dtor"></a>CA2AEX:: ~ CA2AEX  
 Destruktor.  
  
```
~CA2AEX() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní přidělené vyrovnávací paměti.  
  
##  <a name="m_psz"></a>CA2AEX::m_psz  
 Data člena, který ukládá zdrojový řetězec.  
  
```
LPSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>CA2AEX::m_szBuffer  
 Statické vyrovnávací paměť, používá k ukládání převedený řetězec.  
  
```
char m_szBuffer[ t_nBufferLength];
```  
  
##  <a name="operator_lpstr"></a>CA2AEX::Operator LPSTR  
 Operátor převodu.  
  
```
operator LPSTR() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí textový řetězec jako typ **LPSTR**.  
  
## <a name="see-also"></a>Viz také  
 [CA2CAEX – třída](../../atl/reference/ca2caex-class.md)   
 [CA2WEX – třída](../../atl/reference/ca2wex-class.md)   
 [CW2AEX – třída](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX – třída](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX – třída](../../atl/reference/cw2wex-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)