---
title: "Třída CStringData | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
dev_langs: C++
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7523ca52c0ded8ec9b3cf02dd6798beca8be5cf8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cstringdata-class"></a>CStringData – třída
Tato třída reprezentuje data objektu řetězce.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct CStringData
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Addref –](#addref)|Zvýší počet odkazů datový objekt řetězec.|  
|[data](#data)|Načte textová data objektu string.|  
|[Islocked –](#islocked)|Určuje, jestli není uzamčen vyrovnávací paměť objekt přidružený řetězce.|  
|[IsShared](#isshared)|Určuje, pokud je aktuálně sdílené vyrovnávací paměti objektu přidružené řetězec.|  
|[Zámek](#lock)|Zamkne vyrovnávací paměť objekt přidružený řetězce.|  
|[Vydaná verze](#release)|Uvolní objekt zadaného řetězce.|  
|[Odemknutí](#unlock)|Odemkne vyrovnávací paměť objekt přidružený řetězce.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[nAllocLength](#nalloclength)|Délka přidělené dat v `XCHAR`s (bez zahrnutí ukončující null)|  
|[nDataLength](#ndatalength)|Délka dat aktuálně používané v `XCHAR`s (bez zahrnutí ukončující null)|  
|[nRefs](#nrefs)|Aktuální počet odkazů objektu.|  
|[pStringMgr](#pstringmgr)|Ukazatel na řetězec správce tohoto objektu řetězec.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída má být používána pouze vývojáři implementace správci vlastní řetězec. Další informace o Správci vlastním řetězcem, najdete v části [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)  
  
 Tato třída zapouzdří různých typů informací a dat souvisejících s vyšší objektu řetězce, například [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), nebo [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) objekty. Každý objekt vyšší řetězec obsahuje ukazatel přidružené `CStringData` objekt, povolení více objektů řetězec tak, aby odkazoval na stejný objekt dat řetězce. Tento vztah je reprezentována počet odkazů ( `nRefs`) z `CStringData` objektu.  
  
> [!NOTE]
>  V některých případech je typ string (například **CFixedString**) nebude sdílet data objektu řetězce s více než jeden objekt vyšší řetězec. Další informace najdete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
 Tato data tvoří:  
  
-   Správce paměti (typu [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) řetězce.  
  
-   Aktuální délka ( [nDataLength](#ndatalength)) řetězce.  
  
-   Přidělené délka ( [nAllocLength](#nalloclength)) řetězce. Z důvodů výkonu to může lišit od aktuální délka řetězce  
  
-   Aktuální počet odkazů ( [nRefs](#nrefs)) z `CStringData` objektu. Tato hodnota se používá při určení, kolik řetězec objekty sdílejí stejné `CStringData` objektu.  
  
-   Skutečný znak vyrovnávací paměti ( [data](#data)) řetězce.  
  
    > [!NOTE]
    >  Skutečný znak vyrovnávací paměti objektu řetězec je přidělena správce řetězec a připojí se k němu `CStringData` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsimpstr.h  
  
##  <a name="addref"></a>CStringData::AddRef  
 Zvýší počet odkaz na objekt řetězce.  
  
```
void AddRef() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Zvýší počet odkaz na objekt řetězce.  
  
> [!NOTE]
>  Tato metoda není volána na řetězec s počtem záporné odkaz, protože záporný počet označuje, že řetězec vyrovnávací paměť je uzamčen.  
  
##  <a name="data"></a>CStringData::data  
 Vrátí ukazatel do vyrovnávací paměti znak objektu string.  
  
```
void* data() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na znak vyrovnávací paměti objektu typu string.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce vrátit aktuální znak vyrovnávací paměti objekt přidružený řetězce.  
  
> [!NOTE]
>  Této vyrovnávací paměti není přidělena `CStringData` objektu, ale správcem řetězec v případě potřeby. Při přidělení, připojí se k datový objekt řetězec vyrovnávací paměti.  
  
##  <a name="islocked"></a>CStringData::IsLocked  
 Určuje, jestli není uzamčen znak vyrovnávací paměti.  
  
```
bool IsLocked() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud vyrovnávací paměť je uzamčené; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce k určení, pokud vyrovnávací paměť znak objektu string je aktuálně uzamčena.  
  
##  <a name="isshared"></a>CStringData::IsShared  
 Určuje, zda je sdílená znak vyrovnávací paměti.  
  
```
bool IsShared() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud vyrovnávací paměť je sdílený; jinak hodnota **false**.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce k určení, pokud znak vyrovnávací paměť dat objektu řetězec aktuálně sdílen více objektů řetězec.  
  
##  <a name="lock"></a>CStringData::Lock  
 Zamkne znak vyrovnávací paměti objektu přidružené řetězec.  
  
```
void Lock() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce k uzamčení vyrovnávací paměti znak řetězec datového objektu. Zamknutí a odemknutí se používá při vývojář vyžadují přímý přístup do vyrovnávací paměti znak. Dobrým příkladem zamykání prokazuje [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) a [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) metody `CSimpleStringT`.  
  
> [!NOTE]
>  Vyrovnávací paměť znak lze uzamknout, pouze pokud vyrovnávací paměť není sdílen vyšší řetězcových objektů.  
  
##  <a name="nalloclength"></a>CStringData::nAllocLength  
 Délka vyrovnávací paměti přidělené znak.  
  
```
int nAllocLength;
```  
  
### <a name="remarks"></a>Poznámky  
 Ukládá délka vyrovnávací paměti přidělené data v `XCHAR`s (bez zahrnutí ukončující null).  
  
##  <a name="ndatalength"></a>CStringData::nDataLength  
 Aktuální délka objektu typu string.  
  
```
int nDataLength;
```  
  
### <a name="remarks"></a>Poznámky  
 Ukládá délku aktuálně používané dat v `XCHAR`s (bez zahrnutí ukončující null).  
  
##  <a name="nrefs"></a>CStringData::nRefs  
 Odkaz na počet datový objekt řetězec.  
  
```
long nRefs;
```  
  
### <a name="remarks"></a>Poznámky  
 Ukládá počet odkazů datový objekt řetězec. Tento počet označuje počet vyšší řetězec objekty, které jsou spojeny s datový objekt řetězec. Záporná označuje, že datový objekt řetězec je aktuálně uzamčen.  
  
##  <a name="pstringmgr"></a>CStringData::pStringMgr  
 Správce paměti objektu přidružené řetězec.  
  
```
IAtlStringMgr* pStringMgr;
```  
  
### <a name="remarks"></a>Poznámky  
 Ukládá správce paměti pro objekt přidružený řetězce. Další informace o řetězce a správce paměti naleznete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="release"></a>CStringData::Release  
 Snižuje počet odkaz na objekt řetězce data.  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se sníží počet odkazů uvolnění `CStringData` struktury, pokud počet odkazů dotkne nula. To se obvykle provádí při objektu řetězce je odstranit a proto již musí odkazovat na objekt řetězce data.  
  
 Například následující kód by volat `CStringData::Release` datový objekt řetězec přidružené k `str1`:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]  
  
##  <a name="unlock"></a>CStringData::Unlock  
 Odemkne znak vyrovnávací paměti objektu přidružené řetězec.  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce k odemknutí vyrovnávací paměť znak řetězec datového objektu. Po odemknutí vyrovnávací paměť je ke sdílení a může být odkaz počítají.  
  
> [!NOTE]
>  Každé volání `Lock` musí odpovídat odpovídající volání `Unlock`.  
  
 Zamknutí a odemknutí se používá při vývojář musí zajistit, že data řetězec nelze sdílet. Dobrým příkladem zamykání prokazuje [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) a [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) metody `CSimpleStringT`.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [ATL a MFC sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md)


