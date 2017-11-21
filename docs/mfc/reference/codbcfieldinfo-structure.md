---
title: "Codbcfieldinfo – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CODBCFieldInfo
dev_langs: C++
helpviewer_keywords:
- ODBC [MFC], data source information
- CODBCFieldInfo structure [MFC]
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: db9eaca0857d2caedb525dc56ad3d99aaf1d4559
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="codbcfieldinfo-structure"></a>CODBCFieldInfo – struktura
`CODBCFieldInfo` Struktura obsahuje informace o pole ve zdroji dat rozhraní ODBC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CODBCFieldInfo  
{  
    CString m_strName;  
    SWORD m_nSQLType;  
    UDWORD m_nPrecision;  
    SWORD m_nScale;  
    SWORD m_nNullability;  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Název pole.  
  
 *m_nSQLType*  
 Datový typ SQL pole. To může být typ dat rozhraní ODBC SQL nebo typ ovladačem SQL. Seznam platných typů dat rozhraní ODBC SQL najdete v tématu "Datové typy SQL" v sadě Windows SDK. Informace o typech dat ovladačem SQL najdete v dokumentaci k ovladače.  
  
 *m_nPrecision*  
 Maximální přesnost pole. Podrobnosti najdete v tématu "Přesnost, měřítko, délku a zobrazovaná velikost" v sadě Windows SDK.  
  
 *m_nScale*  
 Měřítko pole. Podrobnosti najdete v tématu "Přesnost, měřítko, délku a zobrazovaná velikost" v sadě Windows SDK.  
  
 *m_nNullability*  
 Jestli přijímá pole hodnotu Null. To může být jedna ze dvou hodnot: **SQL_NULLABLE** Pokud pole přijímá hodnoty Null, nebo **SQL_NO_NULLS** Pokud toto pole neumožňuje použít hodnoty Null.  
  
## <a name="remarks"></a>Poznámky  
 Pro načtení těchto informací, volání [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)   
 [CRecordset::GetFieldValue](../../mfc/reference/crecordset-class.md#getfieldvalue)


