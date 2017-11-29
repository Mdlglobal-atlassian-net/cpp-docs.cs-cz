---
title: "Třída CComQIPtr | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
dev_langs: C++
helpviewer_keywords: CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6240b779977f99d362f7fd37ef5526ce08e89bd0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomqiptr-class"></a>Třída CComQIPtr
Chytré ukazatele třída pro správu ukazatele rozhraní COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T, const IID* piid= &__uuidof(T)>  
class CComQIPtr: public CComPtr<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Určení typu ukazatele k uložení rozhraní modelu COM.  
  
 `piid`  
 Ukazatel na identifikátory IID `T`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComQIPtr::CComQIPtr](#ccomqiptr)|Konstruktor|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComQIPtr::operator =](#operator_eq)|Přiřadí ukazatel člen ukazatele.|  
  
## <a name="remarks"></a>Poznámky  
 ATL používá `CComQIPtr` a [CComPtr](../../atl/reference/ccomptr-class.md) ke správě ukazatele rozhraní modelu COM, které jsou odvozeny od [CComPtrBase](../../atl/reference/ccomptrbase-class.md). Obě třídy provést automatické prostřednictvím volání při počítání referencí `AddRef` a **verze**. Přetížené operátory řídit tyto operace ukazatele.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 [CComPtr](../../atl/reference/ccomptr-class.md)  
  
 `CComQIPtr`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcomcli.h  
  
##  <a name="ccomqiptr"></a>CComQIPtr::CComQIPtr  
 Konstruktor  
  
```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lp`  
 Použitý k inicializaci ukazatel rozhraní.  
  
 `T`  
 Rozhraní modelu COM.  
  
 `piid`  
 Ukazatel na identifikátory IID `T`.  
  
##  <a name="operator_eq"></a>CComQIPtr::operator =  
 Operátor přiřazení.  
  
```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lp`  
 Použitý k inicializaci ukazatel rozhraní.  
  
 `T`  
 Rozhraní modelu COM.  
  
 `piid`  
 Ukazatel na identifikátory IID `T`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na aktualizaci `CComQIPtr` objektu.  
  
## <a name="see-also"></a>Viz také  
 [CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)   
 [CComQIPtr::CComQIPtr](#ccomqiptr)   
 [CComPtrBase – třída](../../atl/reference/ccomptrbase-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [CComQIPtrElementTraits – třída](../../atl/reference/ccomqiptrelementtraits-class.md)