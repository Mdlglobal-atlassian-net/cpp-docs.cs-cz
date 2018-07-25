---
title: RoInitializeWrapper – třída | Microsoft Docs
ms.custom: ''
ms.date: 05/20/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cac71857e6b472f11d1c9eaba48d181ea78fb456
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705589"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper – třída
Inicializuje prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class RoInitializeWrapper  
```  
  
## <a name="remarks"></a>Poznámky  
 RoInitializeWrapper je pro vaše pohodlí, která inicializuje prostředí Windows Runtime a vrátí HRESULT určující, zda operace byla úspěšná. Protože volání destruktoru třídy `::Windows::Foundation::Uninitialize`, instancí `RoInitializeWrapper` musí být deklarován v oboru globální nebo nejvyšší úrovně.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[RoInitializeWrapper::RoInitializeWrapper – konstruktor](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|Inicializuje novou instanci třídy RoInitializeWrapper.|  
|[RoInitializeWrapper::~RoInitializeWrapper – destruktor](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|Zničí aktuální instance třídy RoInitializeWrapper.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[RoInitializeWrapper::HRESULT() – operátor](../windows/roinitializewrapper-hresult-parens-operator.md)|Načte HRESULT vyprodukované RoInitializeWrapper konstruktor.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `RoInitializeWrapper`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)