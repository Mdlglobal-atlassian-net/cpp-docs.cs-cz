---
title: "Třída CA2CAEX | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
dev_langs: C++
helpviewer_keywords: CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f579716cff70d0c9f20ea0fa0133dcb4d86c8db3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ca2caex-class"></a>CA2CAEX – třída
Tato třída se používá ve makra převodů řetězec `CA2CTEX` a `CT2CAEX`a typedef **CA2CA**.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<int t_nBufferLength = 128>  
class CA2CAEX
```  
  
#### <a name="parameters"></a>Parametry  
 `t_nBufferLength`  
 Velikost vyrovnávací paměti používané v procesu překladu. Výchozí délka je 128 bajtů.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CA2CAEX::CA2CAEX](#ca2caex)|Konstruktor|  
|[CA2CAEX:: ~ CA2CAEX](#dtor)|Destruktor.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CA2CAEX::Operator LPCSTR](#operator_lpcstr)|Operátor převodu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CA2CAEX::m_psz](#m_psz)|Data člena, který ukládá zdrojový řetězec.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je potřeba další funkce, používat `CA2CTEX`, `CT2CAEX`, nebo **CA2CA** v kódu.  
  
 Tato třída je bezpečné pro použití v smyčky a nebude přetečení zásobníku. Ve výchozím nastavení převod ATL – třídy a makra použije aktuální vlákno ANSI znaková stránka pro převod.  
  
 Následující makra je založena na této třídě:  
  
- `CA2CTEX`  
  
- `CT2CAEX`  
  
 Následující definice typu je založena na této třídě:  
  
- **CA2CA**  
  
 Informace o těchto makra převodů text, najdete v části [ATL a MFC makra převodů řetězec](string-conversion-macros.md).  
  
## <a name="example"></a>Příklad  
 V tématu [ATL a MFC makra převodů řetězec](string-conversion-macros.md) příklad použití převodních maker tyto řetězce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlconv.h  
  
##  <a name="ca2caex"></a>CA2CAEX::CA2CAEX  
 Konstruktor  
  
```
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Textový řetězec, který má být převeden.  
  
 `nCodePage`  
 Nepoužívá se v této třídě.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří vyrovnávací paměti vyžadované pro překlad.  
  
##  <a name="dtor"></a>CA2CAEX:: ~ CA2CAEX  
 Destruktor.  
  
```
~CA2CAEX() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní přidělené vyrovnávací paměti.  
  
##  <a name="m_psz"></a>CA2CAEX::m_psz  
 Data člena, který ukládá zdrojový řetězec.  
  
```
LPCSTR m_psz;
```  
  
##  <a name="operator_lpcstr"></a>CA2CAEX::Operator LPCSTR  
 Operátor převodu.  
  
```  
operator LPCSTR() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí textový řetězec jako typ `LPCSTR`.  
  
## <a name="see-also"></a>Viz také  
 [CA2AEX – třída](../../atl/reference/ca2aex-class.md)   
 [CA2WEX – třída](../../atl/reference/ca2wex-class.md)   
 [CW2AEX – třída](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX – třída](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX – třída](../../atl/reference/cw2wex-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
