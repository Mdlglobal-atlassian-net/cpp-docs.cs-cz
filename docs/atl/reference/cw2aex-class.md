---
title: "Třída CW2AEX | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
dev_langs: C++
helpviewer_keywords: CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: da63f817ab5e6b867d76d59248f5f887d0a7aea5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cw2aex-class"></a>CW2AEX – třída
Tato třída se používá ve makra převodů řetězec `CT2AEX`, `CW2TEX`, `CW2CTEX`, a `CT2CAEX`a typedef **CW2A**.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<int t_nBufferLength = 128>  
class CW2AEX
```  
  
#### <a name="parameters"></a>Parametry  
 `t_nBufferLength`  
 Velikost vyrovnávací paměti používané v procesu překladu. Výchozí délka je 128 bajtů.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CW2AEX::CW2AEX](#cw2aex)|Konstruktor|  
|[CW2AEX:: ~ CW2AEX](#dtor)|Destruktor.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CW2AEX::Operator LPSTR](#operator_lpstr)|Operátor převodu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CW2AEX::m_psz](#m_psz)|Data člena, který ukládá zdrojový řetězec.|  
|[CW2AEX::m_szBuffer](#m_szbuffer)|Statické vyrovnávací paměť, používá k ukládání převedený řetězec.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je potřeba další funkce, používat `CT2AEX`, `CW2TEX`, `CW2CTEX`, `CT2CAEX`, nebo **CW2A** ve vašem kódu.  
  
 Tato třída obsahuje statické vyrovnávací pevné velikosti, která se používá k ukládání výsledek převodu. Pokud je výsledek příliš velký pro uložení do statických vyrovnávací paměti, třída přiděluje paměti pomocí `malloc`, uvolnění paměti při opuštění oboru. To zajišťuje, že na rozdíl od text makra převodů k dispozici v předchozích verzích nástroje ATL, tato třída je bezpečné pro použití v smyčky a že ji nebude přetečení zásobníku.  
  
 Pokud třída pokusí o přidělení paměti haldy a selže, bude volat `AtlThrow` s argument **E_OUTOFMEMORY**.  
  
 Ve výchozím nastavení používají převod ATL – třídy a makra aktuální vlákno ANSI znaková stránka pro převod. Pokud chcete k přepsání tohoto chování pro konkrétní převod, zadejte jako druhý parametr konstruktoru pro třídu znaková stránka.  
  
 Následující makra je založena na této třídě:  
  
- `CT2AEX`  
  
- `CW2TEX`  
  
- `CW2CTEX`  
  
- `CT2CAEX`  
  
 Následující definice typu je založena na této třídě:  
  
- **CW2A**  
  
 Informace o těchto makra převodů text, najdete v části [ATL a MFC makra převodů řetězec](string-conversion-macros.md).  
  
## <a name="example"></a>Příklad  
 V tématu [ATL a MFC makra převodů řetězec](string-conversion-macros.md) příklad použití převodních maker tyto řetězce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlconv.h  
  
##  <a name="cw2aex"></a>CW2AEX::CW2AEX  
 Konstruktor  
  
```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);  
CW2AEX(LPCWSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Textový řetězec, který má být převeden.  
  
 `nCodePage`  
 Znaková stránka používá k provádění převod. Viz popis kódu stránky parametr pro funkci Windows SDK [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072) další podrobnosti.  
  
### <a name="remarks"></a>Poznámky  
 Přiděluje vyrovnávací paměti používané v procesu překladu.  
  
##  <a name="dtor"></a>CW2AEX:: ~ CW2AEX  
 Destruktor.  
  
```
~CW2AEX() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní přidělené vyrovnávací paměti.  
  
##  <a name="m_psz"></a>CW2AEX::m_psz  
 Data člena, který ukládá zdrojový řetězec.  
  
```
LPSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>CW2AEX::m_szBuffer  
 Statické vyrovnávací paměť, používá k ukládání převedený řetězec.  
  
```
char m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpstr"></a>CW2AEX::Operator LPSTR  
 Operátor převodu.  
  
```  
operator LPSTR() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí textový řetězec jako typ **LPSTR.**  
  
## <a name="see-also"></a>Viz také  
 [CA2AEX – třída](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX – třída](../../atl/reference/ca2caex-class.md)   
 [CA2WEX – třída](../../atl/reference/ca2wex-class.md)   
 [CW2CWEX – třída](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX – třída](../../atl/reference/cw2wex-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
