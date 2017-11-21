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
ms.openlocfilehash: 206bc229de3de55d58121e10e1fa6f80cb7b48a4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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