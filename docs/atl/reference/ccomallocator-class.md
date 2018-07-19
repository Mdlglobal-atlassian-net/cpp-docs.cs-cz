---
title: Ccomallocator – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9dbaa4631e50b14131418b902dd008e74060dbf6
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881920"
---
# <a name="ccomallocator-class"></a>Ccomallocator – třída
Tato třída poskytuje metody pro správu paměti používá rutiny COM paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComAllocator
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComAllocator::Allocate](#allocate)|Volejte tuto statickou metodu přidělení paměti.|  
|[CComAllocator::Free](#free)|Volání této statické metody pro uvolnění paměti přidělené.|  
|[CComAllocator::Reallocate](#reallocate)|Volání této statické metody, aby mohla znovu přidělit paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída používá [ccomheapptr –](../../atl/reference/ccomheapptr-class.md) k poskytnutí paměti modelu COM, rutin přidělení. Třída protějšek [ccrtallocator –](../../atl/reference/ccrtallocator-class.md), poskytuje stejné metody, pomocí rutiny CRT.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="allocate"></a>  CComAllocator::Allocate  
 Voláním této funkce statické přidělení paměti.  
  
```
static void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nBytes*  
 Počet bajtů k přidělení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací neplatný ukazatel do přiděleného místa nebo hodnota NULL, pokud není k dispozici dostatek paměti.  
  
### <a name="remarks"></a>Poznámky  
 Přidělí paměť. Zobrazit [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727) další podrobnosti.  
  
##  <a name="free"></a>  CComAllocator::Free  
 Voláním této funkce statických zdarma přidělené paměti.  
  
```
static void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 Ukazatel do přidělené paměti.  
  
### <a name="remarks"></a>Poznámky  
 Uvolní přidělené paměti. Zobrazit [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722) další podrobnosti.  
  
##  <a name="reallocate"></a>  CComAllocator::Reallocate  
 Voláním této funkce statické přidělení paměti.  
  
```
static void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 Ukazatel do přidělené paměti.  
  
 *nBytes*  
 Počet bajtů, které mají přidělit jinému uživateli.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací neplatný ukazatel do přiděleného místa nebo hodnota NULL, pokud je nedostatek paměti  
  
### <a name="remarks"></a>Poznámky  
 Změní velikost přidělené paměti. Zobrazit [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280) další podrobnosti.  
  
## <a name="see-also"></a>Viz také  
 [Ccomheapptr – třída](../../atl/reference/ccomheapptr-class.md)   
 [Ccrtallocator – třída](../../atl/reference/ccrtallocator-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
