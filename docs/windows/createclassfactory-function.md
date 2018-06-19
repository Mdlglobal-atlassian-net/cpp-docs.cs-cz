---
title: Createclassfactory – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
dev_langs:
- C++
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 95d08573515bee89fd86d6b37e3982dde2b29978
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33870470"
---
# <a name="createclassfactory-function"></a>CreateClassFactory – funkce
Vytvoří objekt factory, který vytváří instance pro zadanou třídu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename Factory>  
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(  
   _In_ unsigned int *flags,   
   _In_ const CreatorMap* entry,   
   REFIID riid,   
   _Outptr_ IUnknown **ppFactory  
) throw();  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 Kombinace jednoho nebo více [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) hodnot výčtu.  
  
 `entry`  
 Ukazatel na [creatormap –](../windows/creatormap-structure.md) obsahující inicializace a registrační informace o parametru `riid`.  
  
 `riid`  
 Odkaz na rozhraní ID.  
  
 `ppFactory`  
 Pokud tato operace dokončí úspěšně, ukazatel na objekt pro vytváření tříd.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota HRESULT určující chyba.  
  
## <a name="remarks"></a>Poznámky  
 Chybu assert jsou vydávány, pokud parametr šablony `Factory` není odvozen z rozhraní IClassFactory.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers::Details – obor názvů](../windows/microsoft-wrl-wrappers-details-namespace.md)