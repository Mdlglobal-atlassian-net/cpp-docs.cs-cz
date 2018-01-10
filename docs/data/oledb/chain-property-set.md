---
title: CHAIN_PROPERTY_SET | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CHAIN_PROPERTY_SET
dev_langs: C++
helpviewer_keywords: CHAIN_PROPERTY_SET macro
ms.assetid: 2bcf6d7d-f4e5-480d-9140-1e32a0994c94
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1de482b285f24ce9ed68bd70fa7b21b0b66a4d56
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="chainpropertyset"></a>CHAIN_PROPERTY_SET
Toto makro zřetězený vlastnost skupiny společně.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CHAIN_PROPERTY_SET(  
ChainClass   
)  
  
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