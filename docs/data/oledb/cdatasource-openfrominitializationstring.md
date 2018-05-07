---
title: CDataSource::OpenFromInitializationString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
dev_langs:
- C++
helpviewer_keywords:
- OpenFromInitializationString method
ms.assetid: 5ef1f1fd-92a9-4e1c-ad80-d3601b094b8c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dac964f7c6c863f85769a164fab8c418e1c45430
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdatasourceopenfrominitializationstring"></a>CDataSource::OpenFromInitializationString
Otevře se zdroji dat určeného uživatelem zadané inicializačního řetězce.  
  
## <a name="syntax"></a>Syntaxe  
  
```
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString,   
   bool fPromptForInfo= false) throw();  
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