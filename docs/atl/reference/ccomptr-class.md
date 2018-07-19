---
title: CComPtr – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComPtr
- ATLBASE/ATL::CComPtr
- ATLBASE/ATL::CComPtr::CComPtr
dev_langs:
- C++
helpviewer_keywords:
- CComPtr class
ms.assetid: 22d9ea8d-ed66-4c34-940f-141db11e83bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8513a3de54f8a99191936dfff5b894962c597381
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881588"
---
# <a name="ccomptr-class"></a>CComPtr – třída
Třída inteligentní ukazatel pro správu ukazatele rozhraní modelu COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class CComPtr
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Rozhraní modelu COM zadání typu ukazatel na Uložit.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComPtr::CComPtr](#ccomptr)|Konstruktor|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComPtr::operator =](#operator_eq)|Přiřadí ukazatel na ukazatel člen.|  
  
## <a name="remarks"></a>Poznámky  
 ATL – používá `CComPtr` a [CComQIPtr](../../atl/reference/ccomqiptr-class.md) ke správě ukazatele rozhraní modelu COM. Obě jsou odvozeny od [ccomptrbase –](../../atl/reference/ccomptrbase-class.md), a jak provádět automatické počítání odkazů.  
  
 `CComPtr` a [CComQIPtr](../../atl/reference/ccomqiptr-class.md) třídy může pomoct eliminovat nevrácené paměti pomocí provádí automatické počítání odkazů.  Následující funkce obou provádět stejné logické operace; Mějte však na paměti jak druhý verze může být méně náchylný pomocí `CComPtr` třídy:  
  
 [!code-cpp[NVC_ATL_Utilities#130](../../atl/codesnippet/cpp/ccomptr-class_1.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities#131](../../atl/codesnippet/cpp/ccomptr-class_2.cpp)]  
  
 V ladicím buildu odkaz knihovny atlsd.lib pro trasování kódu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 `CComPtr`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="ccomptr"></a>  CComPtr::CComPtr  
 Konstruktor  
  
```
CComPtr() throw ();
CComPtr(T* lp) throw ();
CComPtr (const CComPtr<T>& lp) throw ();
```  
  
### <a name="parameters"></a>Parametry  
 *LP*  
 Použít k inicializaci ukazatele rozhraní.  
  
 *T*  
 Rozhraní modelu COM.  
  
##  <a name="operator_eq"></a>  CComPtr::operator =  
 Operátor přiřazení.  
  
```
T* operator= (T* lp) throw ();
T* operator= (const CComPtr<T>& lp) throw ();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na aktualizovaný `CComPtr` objektu  
  
### <a name="remarks"></a>Poznámky  
 Tato operace AddRefs nový objekt a verzích existující objekt, pokud existuje.  
  
## <a name="see-also"></a>Viz také  
 [CComPtr::CComPtr](#ccomptr)   
 [CComQIPtr::CComQIPtr](../../atl/reference/ccomqiptr-class.md#ccomqiptr)   
 [Přehled tříd](../../atl/atl-class-overview.md)
