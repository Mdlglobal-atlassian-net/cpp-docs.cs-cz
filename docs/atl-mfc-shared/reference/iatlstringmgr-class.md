---
title: "Třída IAtlStringMgr | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAtlStringMgr
- ATLSIMPSTR/ATL::IAtlStringMgr
- ATLSIMPSTR/ATL::Allocate
- ATLSIMPSTR/ATL::Clone
- ATLSIMPSTR/ATL::Free
- ATLSIMPSTR/ATL::GetNilString
- ATLSIMPSTR/ATL::Reallocate
dev_langs: C++
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 85b99b0b1f35ecbc35b4096ac8c2260d0a55680d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr – třída
Tato třída představuje rozhraní pro `CStringT` správce paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
__interface IAtlStringMgr
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Přidělit](#allocate)|Volejte tuto metodu za účelem přidělení nového datová struktura řetězec.|  
|[Klonování](#clone)|Volání této metody se vraťte do nového správce řetězec pro použití s jiná instance ukazatel `CSimpleStringT`.|  
|[Volné](#free)|Volejte tuto metodu k bezplatným datová struktura řetězec.|  
|[GetNilString](#getnilstring)|Vrátí ukazatel `CStringData` objekt použitý objektem objekty prázdný řetězec.|  
|[Přidělit jinému uživateli](#reallocate)|Volejte tuto metodu a znovu přidělte datová struktura řetězec.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní spravuje množství paměti používané řetězec třídy MFC nezávislé; například [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), a [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).  
  
 Tuto třídu můžete také použít k implementaci správce vlastní paměti pro vaše vlastní řetězec třídu. Další informace najdete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsimpstr.h  
  
##  <a name="allocate"></a>IAtlStringMgr::Allocate  
 Přiděluje nový datová struktura řetězec.  
  
```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nAllocLength`  
 Počet znaků v nového bloku paměti.  
  
 `nCharSize`  
 Velikost (v bajtech) tyto typy znaků pomocí Správce řetězec.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na nově přidělených paměti bloku.  
  
> [!NOTE]
>  Neúspěšné přidělení signál není podle došlo k výjimce. Místo toho by měla být neúspěšné přidělení signalizovala vrácením **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Volání [IAtlStringMgr::Free](#free) nebo [IAtlStringMgr::ReAllocate](#reallocate) k bezplatným je paměť přidělená touto metodou.  
  
> [!NOTE]
>  Příklady použití najdete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="clone"></a>IAtlStringMgr::Clone  
 Vrací ukazatel na nový správce řetězec pro použití s jiná instance `CSimpleStringT`.  
  
```
IAtlStringMgr* Clone() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kopii `IAtlStringMgr` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Běžně voláno rámcem správce řetězec je potřeba pro nový řetězec. Ve většině případů **to** ukazatel je vrácen.  
  
 Ale pokud správce paměti nepodporuje více instancí používá `CSimpleStringT`, ukazatel manažera lze sdílet řetězec má být vrácen.  
  
> [!NOTE]
>  Příklady použití najdete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="free"></a>IAtlStringMgr::Free  
 Uvolní datová struktura řetězec.  
  
```
void Free(CStringData* pData) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pData`  
 Ukazatel na blok paměti, který má být uvolněno.  
  
### <a name="remarks"></a>Poznámky  
 Uvolní zadaná paměťová bloku dříve přidělena [přidělte](#allocate) nebo [znovu přidělte](../../atl/reference/iatlmemmgr-class.md#reallocate).  
  
> [!NOTE]
>  Příklady použití najdete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="getnilstring"></a>IAtlStringMgr::GetNilString  
 Vrací ukazatel na strukturu dat řetězec pro prázdný řetězec.  
  
```
CStringData* GetNilString() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CStringData` objekt se používá k reprezentování prázdný řetězec.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce vrátit reprezentace prázdný řetězec.  
  
> [!NOTE]
>  Při implementaci vlastní řetězec manager, musí tuto funkci nikdy selhat. Lze toho docílit vložením instanci **CNilStringData** v třída manager řetězec a vrátí ukazatel do této instance.  
  
> [!NOTE]
>  Příklady použití najdete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="reallocate"></a>IAtlStringMgr::Reallocate  
 Přidělí datová struktura řetězec.  
  
```
CStringData* Reallocate(  
 CStringData* pData,
 int nAllocLength,
 int nCharSize) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pData`  
 Ukazatel na paměti, dříve přidělené tomuto správci paměti.  
  
 `nAllocLength`  
 Počet znaků v nového bloku paměti.  
  
 `nCharSize`  
 Velikost (v bajtech) tyto typy znaků pomocí Správce řetězec.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na začátku bloku nově přidělených paměti.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce ke změně velikosti stávající blok paměti určeného `pData`.  
  
 Volání [IAtlStringMgr::Free](#free) k bezplatným je paměť přidělená touto metodou.  
  
> [!NOTE]
>  Příklady použití najdete v tématu [Správa paměti a CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [ATL a MFC sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md)


