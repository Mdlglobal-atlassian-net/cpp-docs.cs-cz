---
title: "Třída CComPtr | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
dev_langs: C++
helpviewer_keywords: CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0fada073fd438bb2b3605c972f6598f2955b5f68
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomptr-class"></a>CComPtr – třída
Chytré ukazatele třída pro správu ukazatele rozhraní COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class CComPtr
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Určení typu ukazatele k uložení rozhraní modelu COM.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComPtr::CComPtr](#ccomptr)|Konstruktor|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComPtr::operator =](#operator_eq)|Přiřadí ukazatel člen ukazatele.|  
  
## <a name="remarks"></a>Poznámky  
 ATL používá `CComPtr` a [CComQIPtr](../../atl/reference/ccomqiptr-class.md) ke správě ukazatele rozhraní COM. Obě jsou odvozeny od [CComPtrBase](../../atl/reference/ccomptrbase-class.md), a jak provádět počítání automatické odkazů.  
  
 **CComPtr** a [CComQIPtr](../../atl/reference/ccomqiptr-class.md) třídy můžete omezit nevracení paměti provedením počítání automatické odkazů.  Následující funkce obou provádět stejné operace logické; ale Všimněte si, jak druhá verze může být méně náchylný pomocí **CComPtr** třídy:  
  
 [!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]  
  
 V sestavení pro ladění propojte atlsd.lib pro sledování v kódu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 `CComPtr`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="ccomptr"></a>CComPtr::CComPtr  
 Konstruktor  
  
```
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```  
  
### <a name="parameters"></a>Parametry  
 `lp`  
 Použitý k inicializaci ukazatel rozhraní.  
  
 `T`  
 Rozhraní modelu COM.  
  
##  <a name="operator_eq"></a>CComPtr::operator =  
 Operátor přiřazení.  
  
```
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na aktualizaci `CComPtr` objektu  
  
### <a name="remarks"></a>Poznámky  
 Tato operace AddRefs nový objekt a verzích, které je existující objekt, pokud existuje.  
  
## <a name="see-also"></a>Viz také  
 [CComPtr::CComPtr](#ccomptr)   
 [CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)   
 [Přehled třídy](../../atl/atl-class-overview.md)
