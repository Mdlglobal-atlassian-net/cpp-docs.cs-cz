---
title: CDBPropSet::AddProperty | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBPropSet::AddProperty
- CDBPropSet.AddProperty
- AddProperty
- ATL::CDBPropSet::AddProperty
- ATL.CDBPropSet.AddProperty
dev_langs: C++
helpviewer_keywords: AddProperty method
ms.assetid: dc9539d3-1ee4-40f3-9281-2068e6d65e93
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fa9c2d979bc98ebac543f0b17c7afdce2ab5f59b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdbpropsetaddproperty"></a>CDBPropSet::AddProperty
Přidá k vlastností nastavenou vlastnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      bool AddProperty(   
   DWORD dwPropertyID,   
   const VARIANT& var,   
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   LPCSTR szValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   LPCWSTR szValue,   
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   bool bValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   BYTE bValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   short nValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   long nValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   float fltValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
);  
bool AddProperty(  
   DWORD dwPropertyID,  
   double dblValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
bool AddProperty(  
   DWORD dwPropertyID,  
   CY cyValue,  
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 *dwPropertyID*  
 [v] ID vlastnosti má být přidán. Použitý k inicializaci **dwPropertyID** z `DBPROP` struktura přidat do sady vlastností.  
  
 `var`  
 [v] Hodnotu typu variant použitý k inicializaci hodnotu vlastností pro `DBPROP` struktura přidat do sady vlastností.  
  
 `szValue`  
 [v] Použitý k inicializaci hodnotu vlastností pro řetězec `DBPROP` struktura přidat do sady vlastností.  
  
 `bValue`  
 [v] A **BAJTŮ** nebo použitý k inicializaci hodnotu vlastností pro logickou hodnotu `DBPROP` struktura přidat do sady vlastností.  
  
 `nValue`  
 [v] Celočíselná hodnota použitý k inicializaci hodnotu vlastností pro `DBPROP` struktura přidat do sady vlastností.  
  
 *fltValue*  
 [v] Použitý k inicializaci hodnotu vlastností pro hodnotu s plovoucí desetinnou čárkou `DBPROP` struktura přidat do sady vlastností.  
  
 `dblValue`  
 [v] S plovoucí desetinnou čárkou dvojitou přesností použitý k inicializaci hodnotu vlastností pro `DBPROP` struktura přidat do sady vlastností.  
  
 `cyValue`  
 [v] Použitý k inicializaci hodnotu vlastností pro hodnotu měny CY `DBPROP` struktura přidat do sady vlastností.  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud vlastnost bylo úspěšně přidáno. V opačném **false**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDBPropSet – třída](../../data/oledb/cdbpropset-class.md)   
 [Struktura DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx)