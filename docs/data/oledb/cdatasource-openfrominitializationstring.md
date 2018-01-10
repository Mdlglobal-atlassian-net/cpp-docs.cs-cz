---
title: CDataSource::OpenFromInitializationString | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
dev_langs: C++
helpviewer_keywords: OpenFromInitializationString method
ms.assetid: 5ef1f1fd-92a9-4e1c-ad80-d3601b094b8c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 294c5cd893b04dd477a002adb6dc03fa33c60a29
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdatasourceopenfrominitializationstring"></a>CDataSource::OpenFromInitializationString
Otevře se zdroji dat určeného uživatelem zadané inicializačního řetězce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT OpenFromInitializationString(   
   LPCOLESTR szInitializationString,   
   bool fPromptForInfo = false    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 *szInitializationString*  
 [v] Inicializačního řetězce.  
  
 *fPromptForInfo*  
 [v] Pokud tento argument je nastavený na **true**, pak `OpenFromInitializationString` nastaví **DBPROP_INIT_PROMPT** vlastnost **DBPROMPT_COMPLETEREQUIRED**, která určuje, že se uživatel výzva jenom v případě, že je potřeba další informace. To je užitečné v situacích, ve kterých inicializačního řetězce určuje databázi, která vyžaduje heslo, ale řetězec nebude obsahovat heslo. Uživatel vyzve k zadání hesla (nebo všechny chybějící informace) při pokusu o připojení k databázi.  
  
 Výchozí hodnota je **false**, která určuje, že se uživateli nikdy výzva (nastaví **DBPROP_INIT_PROMPT** k **DBPROMPT_NOPROMPT**).  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda otevře objekt zdroje dat pomocí součásti služby v oledb32.dll; Tento soubor DLL obsahuje implementace funkce součásti služby, například sdílení prostředků ve fondech, automatické zařazení transakce a tak dále.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDataSource – třída](../../data/oledb/cdatasource-class.md)