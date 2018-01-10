---
title: "Třída CHeapPtr | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHeapPtr
- ATLCORE/ATL::CHeapPtr
- ATLCORE/ATL::CHeapPtr::CHeapPtr
- ATLCORE/ATL::CHeapPtr::Allocate
- ATLCORE/ATL::CHeapPtr::Reallocate
dev_langs: C++
helpviewer_keywords: CHeapPtr class
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 47fe8c0d7475c67228fd7335b1aa167ced237202
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cheapptr-class"></a>CHeapPtr – třída
Chytré ukazatele třída pro správu haldy ukazatele.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T, class Allocator=CCRTAllocator>  
class CHeapPtr : public CHeapPtrBase<T, Allocator>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ objektu k uložení v haldě.  
  
 `Allocator`  
 Třída přidělení paměti používat.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CHeapPtr::CHeapPtr](#cheapptr)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CHeapPtr::Allocate](#allocate)|Voláním této metody lze přidělit paměť v haldě pro uložení objektů.|  
|[CHeapPtr::Reallocate](#reallocate)|Volejte tuto metodu a znovu přidělte paměť v haldě.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CHeapPtr::operator =](#operator_eq)|Operátor přiřazení.|  
  
## <a name="remarks"></a>Poznámky  
 `CHeapPtr`je odvozený od [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) a ve výchozím nastavení používá CRT rutiny (v [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)) a přidělit volné paměti. Třída [CHeapPtrList](../../atl/reference/cheapptrlist-class.md) lze vytvořit seznam haldy ukazatele. Viz také [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), který používá rutiny přidělení paměti COM.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)  
  
 `CHeapPtr`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcore.h  
  
##  <a name="allocate"></a>CHeapPtr::Allocate  
 Voláním této metody lze přidělit paměť v haldě pro uložení objektů.  
  
```
bool Allocate(size_t nElements = 1) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nElements`  
 Počet elementů používá k výpočtu množství paměti k přidělení. Výchozí hodnota je 1.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud je paměť byla úspěšně přiděleno, false při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Allocator rutiny se používají k vyhradit dostatek paměti v haldě k uložení *nElement* objektů typu definované v konstruktoru.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#77](../../atl/codesnippet/cpp/cheapptr-class_1.cpp)]  
  
##  <a name="cheapptr"></a>CHeapPtr::CHeapPtr  
 Konstruktor  
  
```
CHeapPtr() throw();
explicit CHeapPtr(T* p) throw();
CHeapPtr(CHeapPtr<T, Allocator>& p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatele existující haldy nebo `CHeapPtr`.  
  
### <a name="remarks"></a>Poznámky  
 Ukazatel haldy lze vytvořit volitelně pomocí stávající ukazatele, nebo `CHeapPtr` objektu. Pokud ano, nové `CHeapPtr` objekt odpovědnost za správu nový ukazatel a prostředky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#78](../../atl/codesnippet/cpp/cheapptr-class_2.cpp)]  
  
##  <a name="operator_eq"></a>CHeapPtr::operator =  
 Operátor přiřazení.  
  
```
CHeapPtr<T, Allocator>& operator=(
    CHeapPtr<T, Allocator>& p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Existující objekt `CHeapPtr`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na aktualizaci `CHeapPtr`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#80](../../atl/codesnippet/cpp/cheapptr-class_3.cpp)]  
  
##  <a name="reallocate"></a>CHeapPtr::Reallocate  
 Volejte tuto metodu a znovu přidělte paměť v haldě.  
  
```
bool Reallocate(size_t nElements) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nElements`  
 Nový počet elementů používá k výpočtu množství paměti k přidělení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud je paměť byla úspěšně přiděleno, false při selhání.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#79](../../atl/codesnippet/cpp/cheapptr-class_4.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [CHeapPtrBase – třída](../../atl/reference/cheapptrbase-class.md)   
 [CCRTAllocator – třída](../../atl/reference/ccrtallocator-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
