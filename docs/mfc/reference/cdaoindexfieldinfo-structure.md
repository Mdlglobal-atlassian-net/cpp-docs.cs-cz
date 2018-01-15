---
title: "Cdaoindexfieldinfo – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDaoIndexFieldInfo
dev_langs: C++
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b745a6f450bdf96389f49c673dc623b614e04db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo – struktura
`CDaoIndexFieldInfo` Struktura obsahuje informace o objektu indexu pole definované pro přístup k objektům dat (DAO).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CDaoIndexFieldInfo  
{  
    CString m_strName;          // Primary  
    BOOL m_bDescending;         // Primary  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Jedinečné názvy objekt index pole. Podrobnosti naleznete v tématu "Název vlastnosti" v nápovědě rozhraní DAO.  
  
 *m_bDescending*  
 Označuje, index řazení objektu indexu definované. **Hodnota TRUE,** Pokud je sestupném pořadí.  
  
## <a name="remarks"></a>Poznámky  
 Index objekt může mít několik polí, která určuje, která pole tabledef (nebo záznamů založené na tabulku) je indexovaný na. Odkazy na primární výše označuje, jak se vrátí informace ve `m_pFieldInfos` členem [cdaoindexinfo –](../../mfc/reference/cdaoindexinfo-structure.md) objekt získá voláním `GetIndexInfo` funkce člena třídy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo).  
  
 Index objekty a index pole objekty nejsou reprezentované pomocí třídy knihovny MFC. Místo toho s objektem DAO objekty základní MFC objekty třídy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) nebo [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obsahovat kolekce objektů index názvem kolekce indexů. Každý objekt index, obsahuje kolekci pole objektů. Členské funkce pro přístup k jednotlivé položky index informace zadat tyto třídy nebo jejich najednou pomocí `CDaoIndexInfo` objekt voláním `GetIndexInfo` členské funkce obsahující objektu. `CDaoIndexInfo` Objekt, pak má datový člen `m_pFieldInfos`, která odkazuje na pole `CDaoIndexFieldInfo` objekty.  
  
 Volání `GetIndexInfo` – členská funkce objektu obsahujícího tabledef nebo sady záznamů v jejichž indexy kolekce je uložený objekt index vás zajímá. Potom přístup `m_pFieldInfos` členem [cdaoindexinfo –](../../mfc/reference/cdaoindexinfo-structure.md) objektu. Délka `m_pFieldInfos` pole je uložen v `m_nFields`. `CDaoIndexFieldInfo`také definuje `Dump` – členská funkce ladění sestavení. Můžete použít `Dump` Vypsat obsah `CDaoIndexFieldInfo` objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdao.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoTableDef::GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)   
 [CDaoRecordset::GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)

