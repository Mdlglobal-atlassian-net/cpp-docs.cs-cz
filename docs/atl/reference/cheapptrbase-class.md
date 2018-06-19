---
title: Třída CHeapPtrBase | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ca18054509ab069722e632308b4d8f57706e548
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364565"
---
# <a name="cheapptrbase-class"></a>CHeapPtrBase – třída
Tato třída je základem pro několik tříd inteligentní haldy ukazatele.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, class Allocator = CCRTAllocator>  
class CHeapPtrBase
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ objektu k uložení v haldě.  
  
 `Allocator`  
 Třída přidělení paměti používat. Ve výchozím nastavení jsou rutiny CRT umožňuje přidělit a volné paměti.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CHeapPtrBase:: ~ CHeapPtrBase](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CHeapPtrBase::AllocateBytes](#allocatebytes)|Voláním této metody lze přidělit paměť.|  
|[CHeapPtrBase::Attach](#attach)|Volejte tuto metodu za účelem převzít vlastnictví existující ukazatele.|  
|[CHeapPtrBase::Detach](#detach)|Volejte tuto metodu za účelem uvolnění vlastnictví ukazatel.|  
|[CHeapPtrBase::Free](#free)|Volat tuto metodu za účelem odstranění nainstalovaného objektu, na kterou odkazuje `CHeapPtrBase`.|  
|[CHeapPtrBase::ReallocateBytes](#reallocatebytes)|Volejte tuto metodu a znovu přidělte paměť.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CHeapPtrBase::operator T *](#operator_t_star)|Operátor přetypování.|  
|[CHeapPtrBase::operator &](#operator_amp)|& Operátor.|  
|[-> CHeapPtrBase::operator](#operator_ptr)|Operátor ukazatele na člena.|  

  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CHeapPtrBase::m_pData](#m_pdata)|Členské proměnné ukazatele data.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída je základem pro několik tříd inteligentní haldy ukazatele. Odvozené třídy, například [CHeapPtr](../../atl/reference/cheapptr-class.md) a [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), přidejte vlastní konstruktory a operátory. Zobrazit tyto třídy příklady implementace.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcore.h  
  
##  <a name="allocatebytes"></a>  CHeapPtrBase::AllocateBytes  
 Voláním této metody lze přidělit paměť.  
  
```
bool AllocateBytes(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Počet bajtů paměti k přidělení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud je paměť úspěšně přiděleno, false jinak.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění k chybě assertion dojde v případě [CHeapPtrBase::m_pData](#m_pdata) členské proměnné aktuálně ukazuje na existující hodnotu; to znamená, není rovno hodnotu NULL.  
  
##  <a name="attach"></a>  CHeapPtrBase::Attach  
 Volejte tuto metodu za účelem převzít vlastnictví existující ukazatele.  
  
```
void Attach(T* pData) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pData`  
 `CHeapPtrBase` Objektu bude převzít vlastnictví tento ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 Když `CHeapPtrBase` objekt trvá vlastnictví ukazatel, automaticky odstraní se všechny přidělené data a ukazatele při přechodu mimo rozsah.  
  
 V sestavení pro ladění k chybě assertion dojde v případě [CHeapPtrBase::m_pData](#m_pdata) členské proměnné aktuálně ukazuje na existující hodnotu; to znamená, není rovno hodnotu NULL.  
  
##  <a name="dtor"></a>  CHeapPtrBase:: ~ CHeapPtrBase  
 Destruktor.  
  
```
~CHeapPtrBase() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
##  <a name="detach"></a>  CHeapPtrBase::Detach  
 Volejte tuto metodu za účelem uvolnění vlastnictví ukazatel.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí kopii ukazatele.  
  
### <a name="remarks"></a>Poznámky  
 Uvolní vlastnictví ukazatel, nastaví [CHeapPtrBase::m_pData](#m_pdata) členské proměnné na hodnotu NULL a vrátí kopii ukazatele.  
  
##  <a name="free"></a>  CHeapPtrBase::Free  
 Volat tuto metodu za účelem odstranění nainstalovaného objektu, na kterou odkazuje `CHeapPtrBase`.  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Objekt na kterou odkazuje `CHeapPtrBase` po uvolnění a [CHeapPtrBase::m_pData](#m_pdata) členské proměnné je nastaven na hodnotu NULL.  
  
##  <a name="m_pdata"></a>  CHeapPtrBase::m_pData  
 Členské proměnné ukazatele data.  
  
```
T* m_pData;
```  
  
### <a name="remarks"></a>Poznámky  
 Tato proměnná člena obsahuje informace ukazatele.  
  
##  <a name="operator_amp"></a>  CHeapPtrBase::operator &amp;  
 & Operátor.  
  
```
T** operator&() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí adresu objektu, na kterou odkazuje `CHeapPtrBase` objektu.  
  

##  <a name="operator_ptr"></a>  CHeapPtrBase::operator-&gt;  

 Operátor ukazatele na člena.  
  
```
T* operator->() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu [CHeapPtrBase::m_pData](#m_pdata) členské proměnné.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor k volání metody ve třídě, na kterou odkazuje `CHeapPtrBase` objektu. V sestavení pro ladění k chybě assertion dojde v případě `CHeapPtrBase` odkazuje na hodnotu NULL.  
  
##  <a name="operator_t_star"></a>  CHeapPtrBase::operator T *  
 Operátor přetypování.  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí [CHeapPtrBase::m_pData](#m_pdata).  
  
##  <a name="reallocatebytes"></a>  CHeapPtrBase::ReallocateBytes  
 Volejte tuto metodu a znovu přidělte paměť.  
  
```
bool ReallocateBytes(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Nové množství paměti přidělené v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu PRAVDA, pokud je paměť úspěšně přiděleno, false jinak.  
  
## <a name="see-also"></a>Viz také  
 [CHeapPtr – třída](../../atl/reference/cheapptr-class.md)   
 [CComHeapPtr – třída](../../atl/reference/ccomheapptr-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
