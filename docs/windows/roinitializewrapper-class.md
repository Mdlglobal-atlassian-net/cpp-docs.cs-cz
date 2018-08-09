---
title: Roinitializewrapper – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 41eb5e79ca1471fb8c12ffca420a134115fbfcc1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014036"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper – třída
Inicializuje modul Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class RoInitializeWrapper  
```  
  
## <a name="remarks"></a>Poznámky  
 **RoInitializeWrapper** je usnadnění práce, která inicializuje modul Windows Runtime a vrátí HRESULT, která určuje, zda operace byla úspěšná. Vzhledem k tomu volá destruktor třídy `::Windows::Foundation::Uninitialize`, výskyty **RoInitializeWrapper** musí být deklarovány v oboru globálním správcem nebo nejvyšší úrovně.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[RoInitializeWrapper::RoInitializeWrapper – konstruktor](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|Inicializuje novou instanci třídy **RoInitializeWrapper** třídy.|  
|[RoInitializeWrapper::~RoInitializeWrapper – destruktor](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|Odstraní aktuální instanci aplikace **RoInitializeWrapper** třídy.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[RoInitializeWrapper::HRESULT() – operátor](../windows/roinitializewrapper-hresult-parens-operator.md)|Načte hodnotu HRESULT vytvořené metodou **RoInitializeWrapper** konstruktoru.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `RoInitializeWrapper`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)