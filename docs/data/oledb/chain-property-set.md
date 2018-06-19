---
title: CHAIN_PROPERTY_SET | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CHAIN_PROPERTY_SET
dev_langs:
- C++
helpviewer_keywords:
- CHAIN_PROPERTY_SET macro
ms.assetid: 2bcf6d7d-f4e5-480d-9140-1e32a0994c94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9db57535f3f0bc7653c80b83c3e0115727eed707
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094332"
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