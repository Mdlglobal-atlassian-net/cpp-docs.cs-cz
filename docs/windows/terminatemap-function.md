---
title: Terminatemap – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
dev_langs:
- C++
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d33cbd46903a37bf42e417a100d26c9b706058c0
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645935"
---
# <a name="terminatemap-function"></a>TerminateMap – funkce
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline bool TerminateMap(  
   _In_ ModuleBase *module,   
   _In_opt_z_ const wchar_t *serverName,   
    bool forceTerminate) throw()  
```  
  
### <a name="parameters"></a>Parametry  
 *Modul*  
 A [modulu](../windows/module-class.md).  
  
 *název_serveru*  
 Název dílčí sady objekty pro vytváření tříd v modulu určené parametrem *modulu*.  
  
 *forceTerminate*  
 **Hodnota TRUE** ukončení třídy jsou aktivní, bez ohledu na to, že objekty pro vytváření **false** není ukončit objekty pro vytváření tříd, pokud je aktivní libovolný objekt pro vytváření.  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE** všechny objekty pro vytváření tříd byl ukončen; v opačném případě **false**.  
  
## <a name="remarks"></a>Poznámky  
 Třída továrny v zadaném modulu vypne.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)