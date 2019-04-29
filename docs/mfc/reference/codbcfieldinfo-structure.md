---
title: CODBCFieldInfo – struktura
ms.date: 11/04/2016
f1_keywords:
- CODBCFieldInfo
helpviewer_keywords:
- ODBC [MFC], data source information
- CODBCFieldInfo structure [MFC]
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
ms.openlocfilehash: bc2ad0c8319a60b773211dbd6b52b57bb2dbcafb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388188"
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

*m_strName*<br/>
Název pole.

*m_nSQLType*<br/>
SQL datový typ pole. To může být typem dat ODBC SQL nebo datový typ SQL specifické pro ovladač. Seznam platných typů dat ODBC SQL najdete v tématu "Datových typů SQL" v sadě Windows SDK. Informace o typech dat SQL specifické pro konkrétní ovladač najdete v dokumentaci ovladače.

*m_nPrecision*<br/>
Maximální přesnost pole. Podrobnosti najdete v tématu "Přesnost, měřítko, délku a velikost zobrazení" v sadě Windows SDK.

*m_nScale*<br/>
Škálování pole. Podrobnosti najdete v tématu "Přesnost, měřítko, délku a velikost zobrazení" v sadě Windows SDK.

*m_nNullability*<br/>
Určuje, zda lze do pole zadat hodnotu Null. Může to být jedna ze dvou hodnot: SQL_NULLABLE, pokud do pole zadat hodnoty Null, nebo SQL_NO_NULLS Pokud pole nepřijímá hodnoty Null.

## <a name="remarks"></a>Poznámky

Chcete-li tyto informace načíst, zavolejte [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo).

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdb.h

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)<br/>
[CRecordset::GetFieldValue](../../mfc/reference/crecordset-class.md#getfieldvalue)
