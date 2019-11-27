---
title: CDaoIndexFieldInfo – struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: 10c786ef4fed9ecb3bbbb93526cd68a11e18d58c
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303661"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo – struktura

Struktura `CDaoIndexFieldInfo` obsahuje informace o objektu pole indexu definovaném pro objekty DAO (Data Access Object).

Rozhraní DAO je podporováno prostřednictvím sady Office 2013. Rozhraní DAO 3,6 je finální verze a je považována za zastaralou.

## <a name="syntax"></a>Syntaxe

```
struct CDaoIndexFieldInfo
{
    CString m_strName;          // Primary
    BOOL m_bDescending;         // Primary
};
```

#### <a name="parameters"></a>Parametry

*m_strName*<br/>
Jedinečný název objektu pole indexu. Podrobnosti najdete v nápovědě k rozhraní DAO v tématu "vlastnost názvu".

*m_bDescending*<br/>
Určuje pořadí indexů definované objektem indexu. TRUE, pokud je pořadí sestupně.

## <a name="remarks"></a>Poznámky

Objekt index může mít množství polí, která označují, která pole a tabledef (nebo sada záznamů založená na tabulce) jsou indexovány. Odkazy na primární výše označují, jak jsou vráceny informace v `m_pFieldInfos` členu objektu [CDaoIndexInfo –](../../mfc/reference/cdaoindexinfo-structure.md) získaného voláním členské funkce `GetIndexInfo` třídy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).

Objekty indexů a objekty pole indexu nejsou reprezentovány třídou MFC. Místo toho objekty DAO podkladové objekty knihovny MFC třídy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obsahují kolekci objektů indexů, které se nazývají kolekce indexů. Každý objekt index zase obsahuje kolekci objektů polí. Tyto třídy poskytují členské funkce pro přístup k jednotlivým položkám informací o indexu nebo k nim můžete přistupovat současně pomocí objektu `CDaoIndexInfo` voláním členské funkce `GetIndexInfo` objektu, který jej obsahuje. Objekt `CDaoIndexInfo` a potom má datový člen `m_pFieldInfos`, který odkazuje na pole objektů `CDaoIndexFieldInfo`.

Zavolejte členskou funkci `GetIndexInfo` objektu obsahujícího tabledef nebo Recordset, ve kterém je kolekce indexů uložena, v němž je uložen objekt indexu, který vás zajímá. Pak přejděte k `m_pFieldInfos`mu členu objektu [CDaoIndexInfo –](../../mfc/reference/cdaoindexinfo-structure.md) . Délka pole `m_pFieldInfos` je uložena v `m_nFields`. `CDaoIndexFieldInfo` také definuje členskou funkci `Dump` v sestaveních ladění. K výpisu obsahu `CDaoIndexFieldInfo` objektu můžete použít `Dump`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset:: GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)
