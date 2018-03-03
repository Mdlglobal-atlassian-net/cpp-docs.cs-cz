---
title: "Třída CW2CWEX | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
dev_langs:
- C++
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a83f0fefed5e2393c303038346e3b84ec1a3d570
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cw2cwex-class"></a>CW2CWEX – třída
Tato třída se používá ve makra převodů řetězec `CW2CTEX` a `CT2CWEX`a typedef `CW2W`.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<int t_nBufferLength = 128>  
class CW2CWEX
```  
  
#### <a name="parameters"></a>Parametry  
 `t_nBufferLength`  
 Velikost vyrovnávací paměti používané v procesu překladu. Výchozí délka je 128 bajtů.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CW2CWEX::CW2CWEX](#cw2cwex)|Konstruktor|  
|[CW2CWEX:: ~ CW2CWEX](#dtor)|Destruktor.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CW2CWEX::Operator LPCWSTR](#operator_lpcwstr)|Operátor převodu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CW2CWEX::m_psz](#m_psz)|Data člena, který ukládá zdrojový řetězec.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je potřeba další funkce, používat `CW2CTEX`, `CT2CWEX`, nebo `CW2W` ve vašem kódu.  
  
 Tato třída je bezpečné pro použití v smyčky a nebude přetečení zásobníku. Ve výchozím nastavení používají převod ATL – třídy a makra aktuální vlákno ANSI znaková stránka pro převod.  
  
 Následující makra je založena na této třídě:  
  
- `CW2CTEX`  
  
- `CT2CWEX`  
  
 Následující definice typu je založena na této třídě:  
  
- `CW2W`  
  
 Informace o těchto makra převodů text, najdete v části [ATL a MFC makra převodů řetězec](string-conversion-macros.md).  
  
## <a name="example"></a>Příklad  
 V tématu [ATL a MFC makra převodů řetězec](string-conversion-macros.md) příklad použití převodních maker tyto řetězce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlconv.h  
  
##  <a name="cw2cwex"></a>CW2CWEX::CW2CWEX  
 Konstruktor  
  
```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);  
CW2CWEX(LPCWSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Textový řetězec, který má být převeden.  
  
 `nCodePage`  
 Znaková stránka. Nepoužívá se v této třídě.  
  
### <a name="remarks"></a>Poznámky  
 Přiděluje vyrovnávací paměti používané v procesu překladu.  
  
##  <a name="dtor"></a>CW2CWEX:: ~ CW2CWEX  
 Destruktor.  
  
```
~CW2CWEX() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní přidělené vyrovnávací paměti.  
  
##  <a name="m_psz"></a>CW2CWEX::m_psz  
 Data člena, který ukládá zdrojový řetězec.  
  
```
LPCWSTR m_psz;
```  
  
##  <a name="operator_lpcwstr"></a>CW2CWEX::Operator LPCWSTR  
 Operátor převodu.  
  
```  
operator LPCWSTR() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí textový řetězec jako typ **LPCWSTR.**  
  
## <a name="see-also"></a>Viz také  
 [CA2AEX – třída](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX – třída](../../atl/reference/ca2caex-class.md)   
 [CA2WEX – třída](../../atl/reference/ca2wex-class.md)   
 [CW2AEX – třída](../../atl/reference/cw2aex-class.md)   
 [CW2WEX – třída](../../atl/reference/cw2wex-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
