---
title: CDaoIndexFieldInfo – struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: a8b0ff991b8cc4988192b89d7f70309af9b9112a
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096094"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo – struktura

`CDaoIndexFieldInfo` Struktura obsahuje informace o objektu pole indexu definovaném pro objekty DAO (Data Access Object).

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

Objekt index může mít množství polí, která označují, která pole a tabledef (nebo sada záznamů založená na tabulce) jsou indexovány. Odkazy na primární výše označují, jak jsou vráceny informace v `m_pFieldInfos` členu objektu [CDaoIndexInfo –](../../mfc/reference/cdaoindexinfo-structure.md) `GetIndexInfo` získaném voláním členské funkce třídy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).

Objekty indexů a objekty pole indexu nejsou reprezentovány třídou MFC. Místo toho objekty DAO podkladové objekty knihovny MFC třídy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obsahují kolekci objektů indexů, které se nazývají kolekce indexů. Každý objekt index zase obsahuje kolekci objektů polí. Tyto třídy poskytují členské funkce pro přístup k jednotlivým položkám informací o indexu, nebo k nim můžete přistupovat současně `CDaoIndexInfo` pomocí objektu `GetIndexInfo` voláním členské funkce obsahujícího objektu. Objekt má datový člen, `m_pFieldInfos`, který `CDaoIndexFieldInfo` odkazuje na pole objektů. `CDaoIndexInfo`

`GetIndexInfo` Volání členské funkce obsahujícího objektu tabledef nebo Recordset, ve kterém je kolekce indexů uložena, je uložen do objektu indexu, který vás zajímá. Pak přejděte [](../../mfc/reference/cdaoindexinfo-structure.md) ke členuobjektu`m_pFieldInfos` CDaoIndexInfo –. Délka `m_pFieldInfos` pole je uložena v `m_nFields`. `CDaoIndexFieldInfo`také definuje `Dump` členskou funkci v sestavení ladění. Můžete použít `Dump` k výpisu obsahu `CDaoIndexFieldInfo` objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdao. h

## <a name="see-also"></a>Viz také:

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)
