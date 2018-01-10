---
title: CUtlProps::OnInterfaceRequested | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CUtlProps
dev_langs: C++
helpviewer_keywords: OnInterfaceRequested method
ms.assetid: a5e1a879-cff3-4e01-b902-2249a152984f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c458eaf7c1e41ade5d29fa020bacfebb2b278e82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cutlpropsoninterfacerequested"></a>CUtlProps::OnInterfaceRequested
Zpracovává požadavky pro volitelné rozhraní, když příjemce volá metodu v jednom objektu vytvoření rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      virtual HRESULT CUtlPropsBase::OnInterfaceRequested(  
   REFIID riid  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 [v] Identifikátory IID pro požadované rozhraní. Další podrobnosti najdete v tématu Popis `riid` parametr `ICommand::Execute` v *referenční příručka programátora technologie OLE DB* (v *MDAC SDK*).  
  
## <a name="remarks"></a>Poznámky  
 **Oninterfacerequested –** zpracovává požadavky příjemce pro volitelné rozhraní, když příjemce volá metodu v jednom objektu vytvoření rozhraní (například **IDBCreateSession**, **IDBCreateCommand**, `IOpenRowset`, nebo `ICommand`). Nastaví vlastnost odpovídající OLE DB pro požadované rozhraní. Například pokud příjemce požaduje **IID_IRowsetLocate**, **oninterfacerequested –** nastaví **DBPROP_IRowsetLocate** rozhraní. Díky tomu udržuje správný stav během vytváření řádků.  
  
 Tato metoda je volána, když příjemce volá **IOpenRowset::OpenRowset** nebo `ICommand::Execute`.  
  
 Pokud příjemce otevře objekt a vyžádá volitelné rozhraní, zprostředkovatele měli nastavit vlastnost spojené s daným rozhraním k `VARIANT_TRUE`. Povolit zpracování podle vlastností **oninterfacerequested –** je volána před provedením poskytovatele **Execute** metoda je volána. Ve výchozím nastavení **oninterfacerequested –** zpracovává následující rozhraní:  
  
-   `IRowsetLocate`  
  
-   `IRowsetChange`  
  
-   `IRowsetUpdate`  
  
-   **IConnectionPointContainer**  
  
-   `IRowsetScroll`  
  
 Pokud chcete zpracovávat dalších rozhraní, funkci v datové zdroje, relace, příkazu nebo sady řádků třídě a proces funkce přepište. Přepsání by měl projít rozhraní normální sady nebo získat vlastnosti zajistit, že nastavení vlastností také nastaví všechny zřetězené vlastnosti (viz [OnPropertyChanged –](../../data/oledb/cutlprops-onpropertychanged.md)).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [CUtlProps – třída](../../data/oledb/cutlprops-class.md)