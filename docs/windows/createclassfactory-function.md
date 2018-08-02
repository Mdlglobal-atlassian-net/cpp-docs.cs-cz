---
title: Createclassfactory – funkce | Dokumentace Microsoftu
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
ms.openlocfilehash: ff853fce39b2052b82df921bf6743b0db361408c
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461322"
---
# <a name="createclassfactory-function"></a>CreateClassFactory – funkce
Vytvoří objekt factory, který vytvoří instance dané třídy.  
  
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
 *příznaky*  
 Kombinace jedné nebo více [runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) hodnot výčtu.  
  
 *entry*  
 Ukazatel [creatormap –](../windows/creatormap-structure.md) , který obsahuje informace o parametru inicializace a registraci *riid*.  
  
 *riid*  
 Odkaz na identifikátor rozhraní.  
  
 *ppFactory*  
 Pokud se tato operace dokončí úspěšně, ukazatel na objekt pro vytváření tříd.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.  
  
## <a name="remarks"></a>Poznámky  
 Chyba vyhodnocení je vygenerován, pokud parametr šablony *Factory* není odvozen z rozhraní `IClassFactory`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers::Details – obor názvů](../windows/microsoft-wrl-wrappers-details-namespace.md)