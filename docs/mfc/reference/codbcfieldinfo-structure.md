---
title: Codbcfieldinfo – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CODBCFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- ODBC [MFC], data source information
- CODBCFieldInfo structure [MFC]
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1723e93320129fae232bb850caa123d1638a37b
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853079"
---
# <a name="codbcfieldinfo-structure"></a>CODBCFieldInfo – struktura
`CODBCFieldInfo` Struktura obsahuje informace o polích ve zdroji dat rozhraní ODBC.  
  
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
 *m_strName*  
 Název pole.  
  
 *m_nSQLType*  
 SQL datový typ pole. To může být typem dat ODBC SQL nebo datový typ SQL specifické pro ovladač. Seznam platných typů dat ODBC SQL najdete v tématu "Datových typů SQL" v sadě Windows SDK. Informace o typech dat SQL specifické pro konkrétní ovladač najdete v dokumentaci ovladače.  
  
 *m_nPrecision*  
 Maximální přesnost pole. Podrobnosti najdete v tématu "Přesnost, měřítko, délku a velikost zobrazení" v sadě Windows SDK.  
  
 *m_nScale*  
 Škálování pole. Podrobnosti najdete v tématu "Přesnost, měřítko, délku a velikost zobrazení" v sadě Windows SDK.  
  
 *m_nNullability*  
 Určuje, zda lze do pole zadat hodnotu Null. Může to být jedna ze dvou hodnot: SQL_NULLABLE Pokud do pole zadat hodnoty Null, nebo SQL_NO_NULLS Pokud pole nepřijímá hodnoty Null.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li tyto informace načíst, zavolejte [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdb.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)   
 [CRecordset::GetFieldValue](../../mfc/reference/crecordset-class.md#getfieldvalue)


