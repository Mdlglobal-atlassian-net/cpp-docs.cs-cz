---
title: Cdaoindexfieldinfo – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoIndexFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37149e2a4a2780c97cc7c2774c64e9a6037d37a7
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337876"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo – struktura
`CDaoIndexFieldInfo` Struktura obsahuje informace o objektu index polí definovaných pro datový přístup k objektům (DAO).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoIndexFieldInfo  
{  
    CString m_strName;          // Primary  
    BOOL m_bDescending;         // Primary  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 *m_strName*  
 Index pole objektu jedinečné názvy. Podrobnosti naleznete v tématu "Název vlastnosti" v nápovědě k DAO.  
  
 *m_bDescending*  
 Určuje index řazení objektu indexu definované. TRUE, pokud je sestupném pořadí.  
  
## <a name="remarks"></a>Poznámky  
 Objekt indexu může mít počet polí, označující pole, která na indexování tabledef (nebo sadu záznamů na základě tabulky). Odkazy na výše uvedené primární určit, jak vrácené informace v `m_pFieldInfos` členem [cdaoindexinfo –](../../mfc/reference/cdaoindexinfo-structure.md) získán voláním objektu `GetIndexInfo` členské funkce třídy [cdaotabledef –](../../mfc/reference/cdaotabledef-class.md#getindexinfo) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).  
  
 Index a index pole objekty nejsou reprezentovány třídy knihovny MFC. Místo toho objektem DAO objekty základní objekty třídy knihovny MFC [cdaotabledef –](../../mfc/reference/cdaotabledef-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obsahovat kolekce objektů index, volá kolekci indexů. Každý objekt index zase obsahuje kolekci objektů pole. Tyto třídy zadat členské funkce pro přístup k jednotlivým položkám index informace nebo je všechny najednou se dostanete `CDaoIndexInfo` objektu voláním `GetIndexInfo` členské funkce nadřazeného objektu. `CDaoIndexInfo` Objektu, pak má datový člen, `m_pFieldInfos`, který odkazuje na pole `CDaoIndexFieldInfo` objekty.  
  
 Volání `GetIndexInfo` členské funkce obsahující objektu tabledef nebo sadu záznamů, jejíž indexy kolekce je uložení objektu do indexu se zajímáte. Přejděte k `m_pFieldInfos` člena [cdaoindexinfo –](../../mfc/reference/cdaoindexinfo-structure.md) objektu. Délka `m_pFieldInfos` je pole uloženo v `m_nFields`. `CDaoIndexFieldInfo` Definuje také `Dump` členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoIndexFieldInfo` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)   
 [CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)

