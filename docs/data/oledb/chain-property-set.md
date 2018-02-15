---
title: CHAIN_PROPERTY_SET | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CHAIN_PROPERTY_SET
dev_langs:
- C++
helpviewer_keywords:
- CHAIN_PROPERTY_SET macro
ms.assetid: 2bcf6d7d-f4e5-480d-9140-1e32a0994c94
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f5a80f6c834c3359d3a4be40b892ff4e5600e9e1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="chainpropertyset"></a>CHAIN_PROPERTY_SET
Toto makro zřetězený vlastnost skupiny společně.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
CHAIN_PROPERTY_SET(ChainClass)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 *ChainClass*  
 [v] Název třídy vlastnosti řetězce. Toto je třída generované průvodcem knihovnou ATL projektu obsahující mapu (například relace, příkaz nebo data zdrojového objektu třídu).  
  
## <a name="remarks"></a>Poznámky  
 Zřetězené sadu vlastností z jiné třídy, na vlastní třídu a potom přístup k vlastnosti přímo z vaší třídy.  
  
> [!CAUTION]
>  Nepoužívejte toto makro. Nesprávné použití může způsobit selhání testů shodnosti technologie OLE DB příjemce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Makra pro šablony zprostředkovatele OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)