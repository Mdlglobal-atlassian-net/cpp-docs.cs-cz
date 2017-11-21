---
title: "ISessionPropertiesImpl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ISessionPropertiesImpl
dev_langs: C++
helpviewer_keywords: ISessionPropertiesImpl class
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8824ac2081ffd214402a23c6a5975e027ecf9ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl – třída
Představuje implementaci objektu [ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ISessionPropertiesImpl :  
   public ISessionProperties,    
   public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `ISessionPropertiesImpl`.  
  
 `PropClass`  
 Uživatelská vlastnost třídu, která použije se výchozí hodnota `T`.  
  
## <a name="members"></a>Členové  
  
### <a name="interface-methods"></a>Metody rozhraní  
  
|||  
|-|-|  
|[GetProperties –](../../data/oledb/isessionpropertiesimpl-getproperties.md)|Vrátí seznam vlastností ve skupině vlastnost relace, která jsou aktuálně nastavené v relaci.|  
|[SetProperties –](../../data/oledb/isessionpropertiesimpl-setproperties.md)|Nastaví vlastnosti ve skupině vlastností relace.|  
  
## <a name="remarks"></a>Poznámky  
 Povinné rozhraní na relací. Tato třída implementuje vlastnosti relace voláním statické funkce definované [mapy sady vlastností](../../data/oledb/begin-propset-map.md). Mapy sady vlastností musí být zadán v třídě relace.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)