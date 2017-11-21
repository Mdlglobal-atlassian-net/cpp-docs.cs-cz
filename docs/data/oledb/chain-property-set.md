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
ms.openlocfilehash: 95a3c2fb12742600822720702d274f251b044cc7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Makra pro šablony zprostředkovatele technologie OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)