---
title: "Třída CAutoVectorPtr | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
dev_langs:
- C++
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b01bb9f74793e739ff0930bae070f00cb909dd61
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cautovectorptr-class"></a>CAutoVectorPtr – třída
Tato třída reprezentuje objekt chytré ukazatele pomocí vektoru nové a odstraňte operátory.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T>  
class CAutoVectorPtr
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ ukazatele.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|Konstruktor|  
|[CAutoVectorPtr:: ~ CAutoVectorPtr](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAutoVectorPtr::Allocate](#allocate)|Voláním této metody lze přidělit paměť vyžadovanou pole objektů, na kterou odkazuje `CAutoVectorPtr`.|  
|[CAutoVectorPtr::Attach](#attach)|Volejte tuto metodu za účelem převzít vlastnictví existující ukazatele.|  
|[CAutoVectorPtr::Detach](#detach)|Volejte tuto metodu za účelem uvolnění vlastnictví ukazatel.|  
|[CAutoVectorPtr::Free](#free)|Volat tuto metodu za účelem odstranění nainstalovaného objektu, na kterou odkazuje `CAutoVectorPtr`.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAutoVectorPtr::operator T *](#operator_t__star)|Operátor přetypování.|  
|[CAutoVectorPtr::operator =](#operator_eq)|Operátor přiřazení.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAutoVectorPtr::m_p](#m_p)|Členské proměnné ukazatele data.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje metody pro vytváření a správu inteligentní ukazatel, která vám pomůže ochranu před nevracení paměti, že automaticky tím uvolní prostředky, je-li mimo rozsah. `CAutoVectorPtr`je podobná `CAutoPtr`, přičemž jediným rozdílem je, `CAutoVectorPtr` používá [vektor – nový &#91; &#93;](../../standard-library/new-operators.md#op_new_arr) a [vector odstranit &#91; &#93;](../../standard-library/new-operators.md#op_delete_arr) alokace a uvolnit paměť, místo C++ **nové** a **odstranit** operátory. V tématu [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) Pokud kolekce tříd `CAutoVectorPtr` jsou povinné.  

  
 V tématu [CAutoPtr](../../atl/reference/cautoptr-class.md) příklad použití třídy chytré ukazatele.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="allocate"></a>CAutoVectorPtr::Allocate  
 Voláním této metody lze přidělit paměť vyžadovanou pole objektů, na kterou odkazuje `CAutoVectorPtr`.  
  
```
bool Allocate(size_t nElements) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nElements`  
 Počet prvků v poli.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud je paměť úspěšně přiděleno, false při selhání.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění k chybě assertion dojde v případě [CAutoVectorPtr::m_p](#m_p) členské proměnné aktuálně ukazuje na existující hodnotu; to znamená, není rovno hodnotu NULL.  
  
##  <a name="attach"></a>CAutoVectorPtr::Attach  
 Volejte tuto metodu za účelem převzít vlastnictví existující ukazatele.  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 `CAutoVectorPtr` Objektu bude převzít vlastnictví tento ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 Když `CAutoVectorPtr` objekt trvá vlastnictví ukazatel, automaticky odstraní se všechny přidělené data a ukazatele při přechodu mimo rozsah. Pokud [CAutoVectorPtr::Detach](#detach) je volána, programátorů je znovu daný odpovědnost za žádné uvolnění přidělené prostředky.  
  
 V sestavení pro ladění k chybě assertion dojde v případě [CAutoVectorPtr::m_p](#m_p) členské proměnné aktuálně ukazuje na existující hodnotu; to znamená, není rovno hodnotu NULL.  
  
##  <a name="cautovectorptr"></a>CAutoVectorPtr::CAutoVectorPtr  
 Konstruktor  
  
```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Existující ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 `CAutoVectorPtr` Objekt lze vytvořit pomocí existující ukazatele, v takovém případě přenosu vlastnictví ukazatele.  
  
##  <a name="dtor"></a>CAutoVectorPtr:: ~ CAutoVectorPtr  
 Destruktor.  
  
```
~CAutoVectorPtr() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky. Volání [CAutoVectorPtr::Free](#free).  
  
##  <a name="detach"></a>CAutoVectorPtr::Detach  
 Volejte tuto metodu za účelem uvolnění vlastnictví ukazatel.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kopii ukazatele.  
  
### <a name="remarks"></a>Poznámky  
 Uvolní vlastnictví ukazatel, nastaví [CAutoVectorPtr::m_p](#m_p) členské proměnné na hodnotu NULL a vrátí kopii ukazatele. Po volání **odpojení**, je maximálně programátorů uvolnit všechny přidělená prostředky přes který `CAutoVectorPtr` objekt může mít dříve předpokládá, že zodpovědnost.  
  
##  <a name="free"></a>CAutoVectorPtr::Free  
 Volat tuto metodu za účelem odstranění nainstalovaného objektu, na kterou odkazuje `CAutoVectorPtr`.  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Objekt na kterou odkazuje `CAutoVectorPtr` po uvolnění a [CAutoVectorPtr::m_p](#m_p) členské proměnné je nastaven na hodnotu NULL.  
  
##  <a name="m_p"></a>CAutoVectorPtr::m_p  
 Členské proměnné ukazatele data.  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>Poznámky  
 Tato proměnná člena obsahuje informace ukazatele.  
  
##  <a name="operator_eq"></a>CAutoVectorPtr::operator =  
 Operátor přiřazení.  
  
```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na **CAutoVectorPtr\< T >**.  
  
### <a name="remarks"></a>Poznámky  
 Operátor přiřazení odpojí `CAutoVectorPtr` objekt z jakékoli aktuální ukazatel a připojí nový ukazatel `p`, na jeho místo.  
  
##  <a name="operator_t__star"></a>CAutoVectorPtr::operator T *  
 Operátor přetypování.  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vrací ukazatel na objekt datového typu definovaného v šabloně třídy.  
  
## <a name="see-also"></a>Viz také  
 [CAutoPtr – třída](../../atl/reference/cautoptr-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
