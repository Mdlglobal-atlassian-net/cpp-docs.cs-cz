---
title: CDataSource::OpenWithServiceComponents | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataSource::OpenWithServiceComponents
- OpenWithServiceComponents
- CDataSource.OpenWithServiceComponents
dev_langs:
- C++
helpviewer_keywords:
- OpenWithServiceComponents method
ms.assetid: 49c1d037-36ae-4fde-8e54-ced623abe1a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 793f1fcb22ac0c57bc1cccb375a0be24b18116ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095713"
---
# <a name="cdatasourceopenwithservicecomponents"></a>CDataSource::OpenWithServiceComponents
Otevře objekt zdroje dat v oledb32.dll součásti služby.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT OpenWithServiceComponents (const CLSID clsid,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1);  


HRESULT OpenWithServiceComponents (LPCSTR szProgID,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1);  
```  
  
#### <a name="parameters"></a>Parametry  
 `clsid`  
 [v] **CLSID** dat zprostředkovatele.  
  
 `szProgID`  
 [v] Program ID zprostředkovatele dat.  
  
 `pPropset`  
 [v] Ukazatel na pole [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury obsahující vlastnosti a hodnoty nastavení. V tématu [sady vlastností a vlastnost skupiny](https://msdn.microsoft.com/en-us/library/ms713696.aspx) v *referenční příručka programátora prostředí OLE DB* ve Windows SDK. Pokud je inicializovat objekt zdroje dat, vlastnosti musí patřit do skupiny vlastnost zdroj dat. Pokud stejnou vlastnost je zadán více než jednou v `pPropset`, pak se používá hodnotu, která je specifický pro zprostředkovatele. Pokud `ulPropSets` rovná nule, je tento parametr ignorován.  
  
 `ulPropSets`  
 [v] Počet [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury předaná *pPropSet* argument. Pokud je to nula, ignoruje zprostředkovatele `pPropset`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda otevře objekt zdroje dat pomocí součásti služby v oledb32.dll; Tento soubor DLL obsahuje implementace funkce součásti služby, například sdílení prostředků ve fondech, automatické zařazení transakce a tak dále. Další informace najdete v tématu "OLE DB služby" v OLE DB referenční informace pro programátory v [ http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDataSource – třída](../../data/oledb/cdatasource-class.md)