---
title: Cautovectorptr – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 520e23432ee4691a5018221aa3a8d44553875f80
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882072"
---
# <a name="cautovectorptr-class"></a>Cautovectorptr – třída
Tato třída představuje objekt inteligentního ukazatele pomocí vektoru nové a odstranit operátory.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
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
|[Cautovectorptr –:: ~ cautovectorptr –](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAutoVectorPtr::Allocate](#allocate)|Volejte tuto metodu za účelem přidělení paměti požadované pole objektů, na které odkazuje `CAutoVectorPtr`.|  
|[CAutoVectorPtr::Attach](#attach)|Volejte tuto metodu za účelem převzít vlastnictví stávajícího ukazatele.|  
|[CAutoVectorPtr::Detach](#detach)|Volejte tuto metodu za účelem uvolní vlastnictví ukazatele.|  
|[CAutoVectorPtr::Free](#free)|Volejte tuto metodu za účelem odstranění objektu, na které odkazují `CAutoVectorPtr`.|  
  
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
 Tato třída poskytuje metody pro vytváření a správu inteligentního ukazatele, která pomůže zajistit ochranu před nevracení paměti, že automaticky uvolnění prostředků při spadá mimo rozsah. `CAutoVectorPtr` je podobný `CAutoPtr`, přičemž jediným rozdílem je, který `CAutoVectorPtr` používá [vektor – nový&#91; &#93; ](../../standard-library/new-operators.md#op_new_arr) a [odstranění vektoru&#91; &#93; ](../../standard-library/new-operators.md#op_delete_arr) k přidělují a uvolňují paměť místo C++ **nové** a **odstranit** operátory. V tématu [cautovectorptrelementtraits –](../../atl/reference/cautovectorptrelementtraits-class.md) Pokud kolekce tříd `CAutoVectorPtr` jsou povinné.  

  
 Zobrazit [CAutoPtr](../../atl/reference/cautoptr-class.md) příklad používání třídy inteligentního ukazatele.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="allocate"></a>  CAutoVectorPtr::Allocate  
 Volejte tuto metodu za účelem přidělení paměti požadované pole objektů, na které odkazuje `CAutoVectorPtr`.  
  
```
bool Allocate(size_t nElements) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nElements*  
 Počet prvků v poli.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud je paměť úspěšně přidělených false při selhání.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud [CAutoVectorPtr::m_p](#m_p) členská proměnná aktuálně ukazuje na existující hodnotu; to znamená, že není rovna hodnotě NULL.  
  
##  <a name="attach"></a>  CAutoVectorPtr::Attach  
 Volejte tuto metodu za účelem převzít vlastnictví stávajícího ukazatele.  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 `CAutoVectorPtr` Objektu bude převzít vlastnictví tohoto ukazatele.  
  
### <a name="remarks"></a>Poznámky  
 Když `CAutoVectorPtr` objekt převezme vlastnictví ukazatele, automaticky odstraní ukazatel a jakékoli přiděleného objemu dat při dostane mimo rozsah. Pokud [CAutoVectorPtr::Detach](#detach) je volána, programátor je znovu daný odpovědnost za žádné uvolnění při přidělování prostředků.  
  
 V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud [CAutoVectorPtr::m_p](#m_p) členská proměnná aktuálně ukazuje na existující hodnotu; to znamená, že není rovna hodnotě NULL.  
  
##  <a name="cautovectorptr"></a>  CAutoVectorPtr::CAutoVectorPtr  
 Konstruktor  
  
```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 Stávajícího ukazatele.  
  
### <a name="remarks"></a>Poznámky  
 `CAutoVectorPtr` Objektu lze vytvořit pomocí stávajícího ukazatele, v takovém případě ji převede vlastnictví ukazatele.  
  
##  <a name="dtor"></a>  Cautovectorptr –:: ~ cautovectorptr –  
 Destruktor.  
  
```
~CAutoVectorPtr() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky. Volání [CAutoVectorPtr::Free](#free).  
  
##  <a name="detach"></a>  CAutoVectorPtr::Detach  
 Volejte tuto metodu za účelem uvolní vlastnictví ukazatele.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kopii ukazatele.  
  
### <a name="remarks"></a>Poznámky  
 Uvolní vlastnictví ukazatele, nastaví [CAutoVectorPtr::m_p](#m_p) členskou proměnnou na hodnotu NULL a vrátí kopii ukazatele. Po volání `Detach`, ho je až programátorovi, aby uvolněte všechny přidělené prostředky nad tím, které `CAutoVectorPtr` objekt může mít dříve zodpovědnost.  
  
##  <a name="free"></a>  CAutoVectorPtr::Free  
 Volejte tuto metodu za účelem odstranění objektu, na které odkazují `CAutoVectorPtr`.  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Objekt, který odkazuje `CAutoVectorPtr` je uvolněn a [CAutoVectorPtr::m_p](#m_p) členská proměnná je nastavena na hodnotu NULL.  
  
##  <a name="m_p"></a>  CAutoVectorPtr::m_p  
 Členské proměnné ukazatele data.  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>Poznámky  
 Tato členská proměnná uchovává informace o ukazatel.  
  
##  <a name="operator_eq"></a>  CAutoVectorPtr::operator =  
 Operátor přiřazení.  
  
```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *p*  
 Ukazatel.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na **cautovectorptr –\< T >**.  
  
### <a name="remarks"></a>Poznámky  
 Operátor přiřazení odpojí `CAutoVectorPtr` objekt z jakékoli aktuální ukazatel a připojí nový ukazatel *p*, na příslušné místo.  
  
##  <a name="operator_t__star"></a>  CAutoVectorPtr::operator T *  
 Operátor přetypování.  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vrací ukazatel na objekt typu dat definovanému v šabloně třídy.  
  
## <a name="see-also"></a>Viz také  
 [Cautoptr – třída](../../atl/reference/cautoptr-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
