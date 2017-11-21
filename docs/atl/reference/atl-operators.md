---
title: "Operátory ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs: C++
helpviewer_keywords: operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 46bc674a65e2ffc946a4806ce1440fec6e14c355
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atl-operators"></a>ATL – operátory
Tato část obsahuje referenční témata pro globální operátory ATL.  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[Operator ==](#operator_eq_eq)|Porovná dva `CSid` objekty nebo `SID` struktury rovnosti.|  
|[Operator! =](#operator_neq)|Porovná dva `CSid` objekty nebo `SID` struktury nerovnost.|  
|[operátor <](#operator_lt)|Testuje, pokud `CSid` objekt nebo `SID` struktura na levé straně operátoru je menší než `CSid` objekt nebo `SID` struktura na pravé straně (z důvodu kompatibility standardní knihovna C++).|  
|[operátor >](#operator_gt)|Testů, pokud `CSid` objekt nebo `SID` struktura na levé straně operátoru je větší než `CSid` objekt nebo `SID` struktura na pravé straně (z důvodu kompatibility standardní knihovna C++).|  
|[Operator < =](#operator_lt__eq)|Testuje, pokud `CSid` objekt nebo `SID` struktura na levé straně operátoru je menší než nebo rovno `CSid` objekt nebo `SID` struktura na pravé straně (z důvodu kompatibility standardní knihovna C++).|  
|[Operator > =](#operator_gt__eq)|Testuje, pokud `CSid` objekt nebo `SID` struktura na levé straně operátoru je větší než nebo rovna hodnotě `CSid` objekt nebo `SID` struktura na pravé straně (z důvodu kompatibility standardní knihovna C++).|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsecurity.h.  
  
##  <a name="operator_eq_eq"></a>Operator ==  
 Porovná `CSid` objekty nebo `SID` struktury (security identifier) rovnosti.  
  
```   
bool operator==(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 První `CSid` objekt nebo `SID` struktura k porovnání.  
  
 `rhs`  
 Druhý `CSid` objekt nebo `SID` struktura k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud objekty jsou stejné, **false** Pokud nejsou stejné.  
  
##  <a name="operator_neq"></a>Operator! =  
 Porovná `CSid` objekty nebo `SID` struktury (security identifier) nerovnost.  
  
```   
bool operator==(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 První `CSid` objekt nebo `SID` struktura k porovnání.  
  
 `rhs`  
 Druhý `CSid` objekt nebo `SID` struktura k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud objekty nejsou stejné, **false** Pokud jsou stejné.  
  
##  <a name="operator_lt"></a>operátor <  
 Testuje, pokud `CSid` objekt nebo `SID` struktura na levé straně operátoru je menší než `CSid` objekt nebo `SID` struktura na pravé straně (z důvodu kompatibility standardní knihovna C++).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 První `CSid` objekt nebo `SID` struktura k porovnání.  
  
 `rhs`  
 Druhý `CSid` objekt nebo `SID` struktura k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud adresu `lhs` objektu je menší než adresu `rhs` objekt, **false** jinak.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor funguje na adresu `CSid` objekt nebo `SID` struktury a je implementována zajistit kompatibilitu s standardní knihovna C++ – třídy kolekce.  
  
##  <a name="operator_gt"></a>operátor >  
 Testů, pokud `CSid` objekt nebo `SID` struktura na levé straně operátoru je větší než `CSid` objekt nebo `SID` struktura na pravé straně (z důvodu kompatibility standardní knihovna C++).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 První `CSid` objekt nebo `SID` struktura k porovnání.  
  
 `rhs`  
 Druhý `CSid` objekt nebo `SID` struktura k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud adresu `lhs` je větší než adresu `rhs`, **false** jinak.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor funguje na adresu `CSid` objekt nebo `SID` struktury a je implementována zajistit kompatibilitu s standardní knihovna C++ – třídy kolekce.  
  
##  <a name="operator_lt__eq"></a>Operator < =  
 Testuje, pokud `CSid` objekt nebo `SID` struktura na levé straně operátoru je menší než nebo rovno `CSid` objekt nebo `SID` struktura na pravé straně (z důvodu kompatibility standardní knihovna C++).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 První `CSid` objekt nebo `SID` struktura k porovnání.  
  
 `rhs`  
 Druhý `CSid` objekt nebo `SID` struktura k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud adresu `lhs` je menší než nebo rovna adresu `rhs`, **false** jinak.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor funguje na adresu `CSid` objekt nebo `SID` struktury a je implementována zajistit kompatibilitu s standardní knihovna C++ – třídy kolekce.  
  
##  <a name="operator_gt__eq"></a>Operator > =  
 Testuje, pokud `CSid` objekt nebo `SID` struktura na levé straně operátoru je větší než nebo rovna hodnotě `CSid` objekt nebo `SID` struktura na pravé straně (z důvodu kompatibility standardní knihovna C++).  
  
```   
bool operator<(const CSid& lhs, const CSid& rhs) throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 `lhs`  
 První `CSid` objekt nebo `SID` struktura k porovnání.  
  
 `rhs`  
 Druhý `CSid` objekt nebo `SID` struktura k porovnání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud adresu `lhs` je větší než nebo rovno adresu `rhs`, **false** jinak.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor funguje na adresu `CSid` objekt nebo `SID` struktury a je implementována zajistit kompatibilitu s standardní knihovna C++ – třídy kolekce.



