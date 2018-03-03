---
title: "Třída CFixedStringT | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
dev_langs:
- C++
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f66749272649fe230b31e770a175e0b94441b90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cfixedstringt-class"></a>CFixedStringT – třída
Tato třída reprezentuje objekt řetězec s pevnou znak vyrovnávací paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```  
  
#### <a name="parameters"></a>Parametry  
 `StringType`  
 Použít jako základní třída pro objekt pevné řetězce a může být libovolná `CStringT`– na základě typu. Mezi příklady patří `CString`, `CStringA`, a `CStringW`.  
  
 *t_nChars*  
 Počet znaků, které jsou uložené ve vyrovnávací paměti.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFixedStringT::CFixedStringT](#cfixedstringt)|V konstruktoru pro objekt řetězce.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFixedStringT::operator =](#eq)|Přiřadí novou hodnotu k `CFixedStringT` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída je příkladem třídu vlastní řetězec na základě `CStringT`. I když je velmi podobné, se liší v implementaci dvou tříd. Hlavní rozdíly mezi `CFixedStringT` a `CStringT` jsou:  
  
-   Vyrovnávací paměť počáteční znak je přidělená v rámci objektu a má velikost *t_nChars*. To umožňuje **CFixedString** objektu tak, aby zabíral bloku souvislé paměti pro účely výkonu. Ale pokud obsah `CFixedStringT` objekt zvětšování nad rámec *t_nChars*, vyrovnávací paměť je přiřazen dynamicky.  
  
-   Znak vyrovnávací paměti pro `CFixedStringT` objekt je vždy stejnou délku ( *t_nChars*). Neexistuje žádné omezení velikosti vyrovnávací paměti pro `CStringT` objekty.  
  
-   Správce paměti pro `CFixedStringT` je přizpůsobit tak, aby sdílení [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) objektu mezi dvěma nebo více `CFixedStringT` objectsis není povoleno. `CStringT`objekty není nutné toto omezení.  
  
 Další informace o možnosti vlastního nastavení `CFixedStringT` a obecně platí, najdete v části Správa paměti pro objekty řetězec [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IAtlStringMgr`  
  
 `StringType`  
  
 `CFixedStringMgr`  
  
 `CFixedStringT`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** cstringt.h  
  
##  <a name="cfixedstringt"></a>CFixedStringT::CFixedStringT  
 Vytvoří `CFixedStringT` objektu.  
  
```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT(const StringType& str);
CFixedStringT(const StringType::XCHAR* psz);
explicit CFixedStringT(const StringType::YCHAR* psz);
explicit CFixedStringT(const unsigned char* psz);
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Řetězce ukončené hodnotou null zkopírovat do této `CFixedStringT` objektu.  
  
 `str`  
 Existující `CFixedStringT` objekt, který se má zkopírovat do této `CFixedStringT` objektu.  
  
 `pStringMgr`  
 Ukazatel na správce paměti `CFixedStringT` objektu. Další informace o `IAtlStringMgr` a správa paměti pro `CFixedStringT`, najdete v části [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
### <a name="remarks"></a>Poznámky  
 Protože konstruktorů zkopírovat do nového úložiště přidělené vstupních dat, je třeba si uvědomit, že paměť, může způsobit výjimky. Všimněte si, že některé z těchto konstruktorů fungovat jako funkce pro převod.  
  
##  <a name="operator__eq"></a>CFixedStringT::operator =  
 Znovu inicializuje existující `CFixedStringT` objekt se nová data.  
  
```
CFixedStringT<StringType, t_nChars>& operator=(
  const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT<StringType, t_nChars>& operator=(const char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* psz);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& str);
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Řetězce ukončené hodnotou null zkopírovat do této `CFixedStringT` objektu.  
  
 `psz`  
 Existující `CFixedStringT` zkopírovat do této `CFixedStringT` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba věnovat pozornost že paměť výjimky může dojít při každém použití operátor přiřazení, protože nové úložiště je často přidělené k uchování výsledná `CFixedStringT` objektu.  
  
## <a name="see-also"></a>Viz také  
 [CStringT – třída](../../atl-mfc-shared/reference/cstringt-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [ATL a MFC sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md)




