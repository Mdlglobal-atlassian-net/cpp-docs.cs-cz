---
title: Struktura _ATL_FUNC_INFO | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a5e184f1c78264304b8e4424ea3f9659689f333b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="atlfuncinfo-structure"></a>_ATL_FUNC_INFO Structure
Obsahuje informace o typu, které používají k popisu metody nebo vlastnosti na odesílajícím rozhraním.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```  
  
## <a name="members"></a>Členové  
 **cc**  
 Konvence volání. Při použití s Tato struktura [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) třídu, musí mít tento člen **CC_STDCALL**. `CC_CDECL` je jedinou možností v systém Windows CE pro podporované `CALLCONV` pole z `_ATL_FUNC_INFO` struktura. Žádné jiné hodnoty nejsou proto není definovaná své chování.  
  
 **vtReturn**  
 Typ varianty funkce vrátí hodnotu.  
  
 **nParams**  
 Počet parametrů funkce.  
  
 **pVarTypes**  
 Pole variantních typů parametrů funkce.  
  
## <a name="remarks"></a>Poznámky  
 ATL interně používá tato struktura k ukládání informací získaných z knihovny typů. Potřebujete poskytovat informace o typu pro obslužnou rutinu události použít s přímo upravit tato struktura [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) třídy a [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) – makro.  
  
## <a name="example"></a>Příklad  
 Zadané metody dispinterface definované v IDL:  
  
 [!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]  
  
 můžete nadefinovat `_ATL_FUNC_INFO` strukturu:  
  
 [!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
## <a name="see-also"></a>Viz také  
 [Struktury](../../atl/reference/atl-structures.md)   
 [IDispEventSimpleImpl – třída](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)





