---
title: Argtraits – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits
dev_langs:
- C++
helpviewer_keywords:
- ArgTraits structure
ms.assetid: 58ae4115-c1bc-48c8-b01b-e60554841c30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 667aa3d2d29e4ce541d957b20b2246380e237a6b
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462040"
---
# <a name="argtraits-structure"></a>ArgTraits – struktura
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename TMemberFunction>  
struct ArgTraits;  
template<typename TDelegateInterface>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(void)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7,  
   typename TArg8  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8)>;  
template<  
   typename TDelegateInterface,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7,  
   typename TArg8,  
   typename TArg9  
>  
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8, TArg9)>;  
```  
  
#### <a name="parameters"></a>Parametry  
 *TMemberFunction*  
 {{Parametr TypeName pro argtraits – struktura, která se nesmí odpovídat čemukoli `Invoke` podpis metody.  
  
 *TDelegateInterface*  
 Rozhraní delegáta.  
  
 *TArg1*  
 Typ prvního argumentu `Invoke` metody.  
  
 *TArg2*  
 Typ druhého argumentu `Invoke` metody.  
  
 *TArg3*  
 Typ třetího argumentu `Invoke` metody.  
  
 *TArg4*  
 Typ čtvrtého argumentu `Invoke` metody.  
  
 *TArg5*  
 Typ pátého argumentu `Invoke` metody.  
  
 *TArg6*  
 Typ šestého argumentu `Invoke` metody.  
  
 *TArg7*  
 Typ sedmého argumentu `Invoke` metody.  
  
 *TArg8*  
 Typ osmého argumentu `Invoke` metody.  
  
 *TArg9*  
 Typ devátého argumentu `Invoke` metody.  
  
## <a name="remarks"></a>Poznámky  
 `ArgTraits` Struktura deklaruje delegáta zadané rozhraní a anonymní členskou funkci, která má zadaný počet parametrů.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`Arg1Type`|Definice typu pro TArg1.|  
|`Arg2Type`|Definice typu pro TArg2.|  
|`Arg3Type`|Definice typu pro TArg3.|  
|`Arg4Type`|Definice typu pro TArg4.|  
|`Arg5Type`|Definice typu pro TArg5.|  
|`Arg6Type`|Definice typu pro TArg6.|  
|`Arg7Type`|Definice typu pro TArg7.|  
|`Arg8Type`|Definice typu pro TArg8.|  
|`Arg9Type`|Definice typu pro TArg9.|  
  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[ArgTraits::args – konstanta](../windows/argtraits-args-constant.md)|Sleduje počet parametrů `Invoke` metoda rozhraní delegáta.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ArgTraits`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)