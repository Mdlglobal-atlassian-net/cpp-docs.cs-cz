---
title: CXMLAccessor::GetXMLColumnData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CXMLAccessor.GetXMLColumnData
- CXMLAccessor::GetXMLColumnData
- CXMLAccessor.GetXMLColumnData
- ATL::CXMLAccessor::GetXMLColumnData
- GetXMLColumnData
dev_langs: C++
helpviewer_keywords: GetXMLColumnData method
ms.assetid: 719e8efe-8758-4af7-a855-0e44ea196546
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b0e0d34a9e726912cd631972091df65157de061d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cxmlaccessorgetxmlcolumndata"></a>CXMLAccessor::GetXMLColumnData
Načte informace o typu sloupce tabulky jako řetězec ve formátu XML data podle sloupce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      HRESULT GetXMLColumnData(   
   CSimpleStringW& strOutput    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `strOutput`  
 [out] Odkaz na vyrovnávací paměť řetězec obsahující informace o sloupec typu mají být načteny. Řetězec je naformátován s názvy – značka XML, které odpovídají úložiště dat názvy sloupců.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jeden standardní `HRESULT` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Následující příklad zobrazuje, jak informace o typu sloupce je ve formátu XML. `type`Určuje datový typ sloupce. Všimněte si, že datové typy jsou založeny na datové typy OLE DB, není u databáze přistupuje.  
  
 `<columninfo>`  
  
 `<column type = I2/> ColumnName`  
  
 `</columninfo>`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CXMLAccessor – třída](../../data/oledb/cxmlaccessor-class.md)