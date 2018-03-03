---
title: "Třída CAutoPtr | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtr
- ATLBASE/ATL::CAutoPtr
- ATLBASE/ATL::CAutoPtr::CAutoPtr
- ATLBASE/ATL::CAutoPtr::Attach
- ATLBASE/ATL::CAutoPtr::Detach
- ATLBASE/ATL::CAutoPtr::Free
- ATLBASE/ATL::CAutoPtr::m_p
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtr class
ms.assetid: 08988d53-4fb0-4711-bdfc-8ac29c63f410
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b8ded7bbf4dbe4e4f2ada7054cebab996934316
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cautoptr-class"></a>CAutoPtr – třída
Tato třída reprezentuje objekt chytré ukazatele.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T>  
class CAutoPtr
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ ukazatele.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAutoPtr::CAutoPtr](#cautoptr)|Konstruktor|  
|[CAutoPtr:: ~ CAutoPtr](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAutoPtr::Attach](#attach)|Volejte tuto metodu za účelem převzít vlastnictví existující ukazatele.|  
|[CAutoPtr::Detach](#detach)|Volejte tuto metodu za účelem uvolnění vlastnictví ukazatel.|  
|[CAutoPtr::Free](#free)|Volat tuto metodu za účelem odstranění nainstalovaného objektu, na kterou odkazuje `CAutoPtr`.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAutoPtr::operator T *](#operator_t_star)|Operátor přetypování.|  
|[CAutoPtr::operator =](#operator_eq)|Operátor přiřazení.|  
|[-> CAutoPtr::operator](#operator_ptr)|Operátor ukazatele na člena.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAutoPtr::m_p](#m_p)|Členské proměnné ukazatele data.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída poskytuje metody pro vytváření a správu inteligentní ukazatel, která vám pomůže ochranu před nevracení paměti, že automaticky tím uvolní prostředky, je-li mimo rozsah.  
  
 Další, `CAutoPtr`kopírovacího konstruktoru a přiřazení operátor přenos vlastnictví ukazatele, kopírování ukazatele zdrojové do cílové ukazatele a nastavení zdroje ukazatel na hodnotu NULL. Je možné, abyste měli dva `CAutoPtr` objektů každý ukládání stejné ukazatele, a to omezuje možnost odstranění stejné ukazatele dvakrát.  
  
 `CAutoPtr`také zjednodušuje vytváření kolekcí ukazatele. Místo odvození třídy kolekce a přepsáním destruktoru, je jednodušší, aby kolekce `CAutoPtr` objekty. Při odstranění kolekce `CAutoPtr` objekty se dostala mimo rozsah a automaticky se odstranit.  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md) a variant fungovat stejným způsobem jako `CAutoPtr`, s tím rozdílem, že přidělit a uvolnit paměť pomocí funkce různých hald místo C++ **nové** a **odstranit** operátory. [CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md) je podobná `CAutoPtr`, přičemž jediným rozdílem je, že používá **vector new []** a **odstranění vektoru []** přidělit a volné paměti.  
  
 Viz také [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) a [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) když jsou požadovaná pole nebo seznam chytré ukazatele.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
## <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#74](../../atl/codesnippet/cpp/cautoptr-class_1.cpp)]  
  
##  <a name="attach"></a>CAutoPtr::Attach  
 Volejte tuto metodu za účelem převzít vlastnictví existující ukazatele.  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 `CAutoPtr` Objektu bude převzít vlastnictví tento ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 Když `CAutoPtr` objekt trvá vlastnictví ukazatel, automaticky odstraní se všechny přidělené data a ukazatele při přechodu mimo rozsah. Pokud [CAutoPtr::Detach](#detach) je volána, programátorů je znovu daný odpovědnost za žádné uvolnění přidělené prostředky.  
  
 V sestavení pro ladění k chybě assertion dojde v případě [CAutoPtr::m_p](#m_p) – datový člen aktuálně ukazuje na existující hodnotu; to znamená, není rovno hodnotu NULL.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad v [CAutoPtr přehled](../../atl/reference/cautoptr-class.md).  
  
##  <a name="cautoptr"></a>CAutoPtr::CAutoPtr  
 Konstruktor  
  
```
CAutoPtr() throw();
explicit CAutoPtr(T* p) throw();

template<typename TSrc>
CAutoPtr(CAutoPtr<TSrc>& p) throw();

template<> 
CAutoPtr(CAutoPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Existující ukazatel.  
  
 `TSrc`  
 Typ spravován pomocí jiného `CAutoPtr`používané k chybě při inicializaci aktuálního objektu.  
  
### <a name="remarks"></a>Poznámky  
 `CAutoPtr` Objekt lze vytvořit pomocí existující ukazatele, v takovém případě přenosu vlastnictví ukazatele.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad v [CAutoPtr přehled](../../atl/reference/cautoptr-class.md).  
  
##  <a name="dtor"></a>CAutoPtr:: ~ CAutoPtr  
 Destruktor.  
  
```
~CAutoPtr() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky. Volání [CAutoPtr::Free](#free).  
  
##  <a name="detach"></a>CAutoPtr::Detach  
 Volejte tuto metodu za účelem uvolnění vlastnictví ukazatel.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kopii ukazatele.  
  
### <a name="remarks"></a>Poznámky  
 Uvolní vlastnictví ukazatel, nastaví [CAutoPtr::m_p](#m_p) data členské proměnné na hodnotu NULL a vrátí kopii ukazatele. Po volání **odpojení**, je maximálně programátorů uvolnit všechny přidělená prostředky přes který `CAutoPtr` objekt může mít dříve předpokládá, že reponsibility.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad v [CAutoPtr přehled](../../atl/reference/cautoptr-class.md).  
  
##  <a name="free"></a>CAutoPtr::Free  
 Volat tuto metodu za účelem odstranění nainstalovaného objektu, na kterou odkazuje `CAutoPtr`.  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Objekt na kterou odkazuje `CAutoPtr` po uvolnění a [CAutoPtr::m_p](#m_p) data členské proměnné je nastaven na hodnotu NULL.  
  
##  <a name="m_p"></a>CAutoPtr::m_p  
 Členské proměnné ukazatele data.  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>Poznámky  
 Tato proměnná člena obsahuje informace ukazatele.  
  
##  <a name="operator_eq"></a>CAutoPtr::operator =  
 Operátor přiřazení.  
  
```
template<>
CAutoPtr<T>& operator= (CAutoPtr<T>& p);

template<typename TSrc>
CAutoPtr<T>& operator= (CAutoPtr<TSrc>& p);
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel.  
  
 `TSrc`  
 Typ třídy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na **CAutoPtr\< T >**.  
  
### <a name="remarks"></a>Poznámky  
 Operátor přiřazení odpojí `CAutoPtr` objekt z jakékoli aktuální ukazatel a připojí nový ukazatel `p`, na jeho místo.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad v [CAutoPtr přehled](../../atl/reference/cautoptr-class.md).  
  
##  <a name="operator_ptr"></a>CAutoPtr::operator-&gt;  
 Operátor ukazatele na člena.  
  
```
T* operator->() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu [CAutoPtr::m_p](#m_p) data členské proměnné.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor k volání metody ve třídě, na kterou odkazuje `CAutoPtr` objektu. V sestavení pro ladění k chybě assertion dojde v případě `CAutoPtr` odkazuje na hodnotu NULL.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad v [CAutoPtr přehled](../../atl/reference/cautoptr-class.md).  
  
##  <a name="operator_t_star"></a>CAutoPtr::operator T *  
 Operátor přetypování.  
  
```  
operator T* () const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na objekt datového typu definovaného v šabloně třídy.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad v [CAutoPtr přehled](../../atl/reference/cautoptr-class.md).  
  
## <a name="see-also"></a>Viz také  
 [CHeapPtr – třída](../../atl/reference/cheapptr-class.md)   
 [CAutoVectorPtr – třída](../../atl/reference/cautovectorptr-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
